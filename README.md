# 볼링 게임 점수판
## 진행 방법
* 볼링 게임 점수판 요구사항을 파악한다.
* 요구사항에 대한 구현을 완료한 후 자신의 github 아이디에 해당하는 브랜치에 Pull Request(이하 PR)를 통해 코드 리뷰 요청을 한다.
* 코드 리뷰 피드백에 대한 개선 작업을 하고 다시 PUSH한다.
* 모든 피드백을 완료하면 다음 단계를 도전하고 앞의 과정을 반복한다.

## 온라인 코드 리뷰 과정
* [텍스트와 이미지로 살펴보는 온라인 코드 리뷰 과정](https://github.com/next-step/nextstep-docs/tree/master/codereview)

# 2단계 - 볼링 점수판(그리기)
## Step 2
### 요구사항
* 최종 목표는 볼링 점수를 계산하는 프로그램을 구현한다. 1단계 목표는 점수 계산을 제외한 볼링 게임 점수판을 구현하는 것이다.
* 각 프레임이 스트라이크이면 "X", 스페어이면 "9 | /", 미스이면 "8 | 1", 과 같이 출력하도록 구현한다.
  * 스트라이크(strike) : 프레임의 첫번째 투구에서 모든 핀(10개)을 쓰러트린 상태
  * 스페어(spare) : 프레임의 두번재 투구에서 모든 핀(10개)을 쓰러트린 상태
  * 미스(miss) : 프레임의 두번재 투구에서도 모든 핀이 쓰러지지 않은 상태
  * 거터(gutter) : 핀을 하나도 쓰러트리지 못한 상태. 거터는 "-"로 표시
* 10 프레임은 스트라이크이거나 스페어이면 한 번을 더 투구할 수 있다.

### Model 
* Player
  * [x] Player 는 플레이어의 이름을 관리한다.
  
* BowlingGame
  * [x] BowlingGame 는 볼링 게임을 관리한다.
  * [x] Player 와 BowlingFrames 를 가지고 있다.
  
* BowlingFrame
  * [x] BowlingFrame 는 볼링 프레임을 관리한다.
  * [x] interface 로 bowl, isOver, sum, getFrameScore 의 메소드를 강제한다.
    
* BowlingFrames
  * [x] BowlingFrames 는 BowlingFrame 의 일급 컬렉션이다.
  
* CommonBowlingFrame
  * [x] CommonBowlingFrame 은 BowlingFrame 의 구현체이다.
  * [x] 1~9 프레임을 구현한다.
  * [x] FrameScore 와 Pins 를 관리한다.
  
* LastBowlingFrame
  * [x] LastBowlingFrame 는 BowlingFrame 의 구현체이다.
  * [x] 10 프레임임을 구현한다.
  * [x] FrameScore 와 Pins 를 관리한다.
  
* FrameScore
  * [x] FrameScore 는 Score 를 가지고 있다.

* Score
  * [x] Score 는 점수를 나타낸다.
  
* Pins
  * [x] Pins 볼링 프레임의 남은 핀 수를 구현한다.
  
* FrameScoreResult
  * 스트라이크(strike)
    * 프레임의 첫번째 투구에서 모든 핀(10개)을 쓰러트린 상태 (Ex. X)
  * 스페어(spare)
    * 프레임의 두번재 투구에서 모든 핀(10개)을 쓰러트린 상태 (Ex. 7|/)
  * 미스(miss)
    * 프레임의 두번재 투구에서도 모든 핀이 쓰러지지 않은 상태 (Ex. 7|-)
  * 거터(gutter)
    * 핀을 하나도 쓰러트리지 못한 상태. 거터는 "-"로 표시 (Ex. -|-)
  
# 3단계 - 볼링 점수판(점수 계산)
## Step 3
### 요구사항
* 사용자 1명의 볼링 게임 점수를 관리할 수 있는 프로그램을 구현한다.
* 각 프레임이 스트라이크이면 "X", 스페어이면 "9 | /", 미스이면 "8 | 1"과 같이 출력하도록 구현한다.
* 스트라이크(strike) : 프레임의 첫번째 투구에서 모든 핀(10개)을 쓰러트린 상태
* 스페어(spare) : 프레임의 두번재 투구에서 모든 핀(10개)을 쓰러트린 상태
* 미스(miss) : 프레임의 두번재 투구에서도 모든 핀이 쓰러지지 않은 상태
* 거터(gutter) : 핀을 하나도 쓰러트리지 못한 상태. 거터는 "-"로 표시
* 스트라이크는 다음 2번의 투구까지 점수를 합산해야 한다. 스페어는 다음 1번의 투구까지 점수를 합산해야 한다.
* 10 프레임은 스트라이크이거나 스페어이면 한 번을 더 투구할 수 있다.