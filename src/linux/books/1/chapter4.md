# 프로세스 스케줄러

리눅스 커널에는 '프로세스 스케줄러' 기능이 있는데 이 기능은 여러 개의 프로세스를 동시에 동작시킨다. 정확히는 동시에 동작시키는 것처럼 보이게 한다.

- 하나의 CPU는 동시에 하나의 프로세스만 처리할 수 있다.
- 하나의 CPU에 여러 개의 프로세스를 실행해야 할 때는 각 프로세스를 적절한 시간으로 쪼개서(타임 슬라이스) 번갈아 처리한다.

- 프로세스를 종료시킬 때까지의 경과 시간은 프로세스 수에 비례하여 증가한다.
- 각 프로세스는 대략 같은 타임 슬라이스를 가진다.


## 라운드 로빈
- 프로세스들 사이에 우선순위를 두지 않고, 순서대로 시간단위(타임 퀀텀)로 CPU를 할당하는 방식

## 컨텍스트 스위치

논리 CPU상에서 동작하는 프로세스가 바뀌는 것을 '컨텍스트 스위치'라고 부른다.

## 프로세스의 상태

프로세스의 상태는 다음과 같다.
- 실행 상태: 현재 논리 CPU를 사용하고 있다
- 실행 대기 상태: CPU 시간이 할당되기를 기다리고 있다.
- 슬립 상태: 이벤트가 발생하기를 기다리고 있으며 이벤트 발생까지는 CPU시간을 사용하지 않는다.
- 좀비 상태: 프로세스가 종료한 뒤 부모 프로세스가 종료 상태를 인식할 때까지 기다리고 있다.
  
## idle 상태

- '아무것도 하지 않는' 특수한 프로세스가 동작한다.
- 시스템 전체가 CPU 시간을 거의 사용하지 않을 때

## 스루풋과 레이턴시

각종 성능지표인 스루풋과 레이턴시에 대해 정리한다.

- 스루풋: 단위 시간당 처리된 일의 양이며 높을수록 좋다. 
  ( 완료한 프로세스의 수 / 경과 시간 )
- 레이턴시: 각각의 처리가 시작부터 종료까지의 경과된 시간으로 짧을수록 좋다. 
  ( 처리 종료 시간 - 처리 시작 시간 )
  
## 실제 시스템

실제 시스템에 돌아가는 논리 CPU는 다음과 같은 상태를 정신 없이 오고 간다.

- idle 상태: 논리 CPU가 쉬고 있기 때문에 스루풋이 떨어지는 경향이 있다.
- 프로세스가 동작 중: 실행 대기의 프로세스가 없기 때문에 이상적인 상태이다. 그러나 이러한 상태는 다음의 프로세스가 실행 가능한 상태가 되면, 2개의 프로세스의 레이턴시가 양쪽 다 길어진다.
- 프로세스가 대기 중: 실행 대기 프로세스가 있다. 스루풋은 높지만 레이턴시가 길어지는 경향이 있다.

## 논리 CPU가 여러 개일 때 스케줄링

논리 CPU가 여러 개일 때 스케줄링은 어떻게 될까? 이 때는 로드밸런서 혹은 글로벌 스케줄러라는 기능이 동작한다. 로드밸런서란 여러 개의 논리 CPU에 프로세스를 공평하게 분배해주는 역할을 한다.
프로세스를 할당받은 각 논리 CPU안에서 1개의 논리 CPU가 있을 떄와 마찬가지로 각 프로세스에 공평하게 CPU 시간을 분배한다.

