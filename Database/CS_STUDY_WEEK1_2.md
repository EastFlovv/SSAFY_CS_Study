# CS Study WEEK2 2ND

# 1주차 2 - Shared / Exclusive Lock의 차이와 Lock으로 인한 문제

## Lock이란?

> 데이터베이스에서는 트랜잭션이 동시에 여러개 실행될 수 있습니다.
이 때, 여러 트랜잭션이 같은 데이터를 동시에 참조한다면 데이터의 일관성이 깨질 수 있기 때문에 트랜잭션이 하나씩 실행되는 것처럼 스케쥴링 할 필요가 있습니다.
> 

> 여러 트랜잭션 방법들이 있는데, Lock은 자신이 데이터를 수정하고 있다는 것을 알리는 방법의 일종으로 다른 트랜잭션이 사용할 수 없도록 잠근 상태를 말합니다.
> 

## 그렇다면 Lock으로 인한 문제는?

> 기본적으로 Lock(로킹)은 lock 연산과 unlock 연산을 사용합니다.
> 
- 트랜잭션 T가 공유 데이터 x를 접근하려면 lock(x) 수행
- 공유 데이터를 사용한 T는 반드시 unlock(x)를 수행해야 함
- 만약, 다른 트랜잭션이 lock(x)를 수행한 상태라면 
해당 트랜잭션이 unlock(x)을 수행하기 전까지 트랜잭션 T는 lock(x) 수행 불가

> 이러한 로킹은 하나의 트랜잭션만이 공유 데이터를 사용할 수 있는데, 오직 읽기(Read) 작업만 하는 경우에는 동시에 접근해도 문제가 없기 때문에 효율적이지 못합니다.
> 

> 또한 여러 트랜잭션이 특정 데이터에 lock을 수행한 채로 서로가 사용중인 데이터에 접근하려고 할 때 교착상태(Dead lock)에 빠지는 문제가 발생할 수도 있습니다.
> 

## Shared Lock(공유 락)과 Exclusive Lock(배타 락)

### Shared Lock

- 공유할 수 있는 락으로 **Read Lock**이라고도 불립니다.
- 주로 읽는 작업(Read)에 사용되며, Shared Lock 끼리는 서로를 막지 않으므로 여러 개가 동시에 적용될 수 있습니다.
즉, 공유 자원에 대해서 여러 사람이 동시에 읽을 수 있지만, 변경(쓰는 작업)은 불가능합니다.

### Exclusive Lock

- 공유할 수 없는 락으로 **Write Lock**이라고도 불립니다.
- 무조건 하나의 트랜잭션만 공유자원에 Exclusive Lock을 걸 수 있으며, 
Exclusive Lock이 걸리면 다른 트랜잭션에서 해당 공유자원에 접근할 수 없습니다.

## 참조 사이트

- [https://onduway.tistory.com/103](https://onduway.tistory.com/103)
- [https://jeong-pro.tistory.com/94](https://jeong-pro.tistory.com/94)