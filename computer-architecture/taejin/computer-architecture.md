# 1. 폰 노이만 구조

초기 컴퓨터는 새로운 계산을 하려면 전선을 재배치하고 스위치를 조작하여 하드웨어를 변경해야 했다. <br>
그래서 폰 노이만이 프로그램 내장 방식(Stored Program Concept)을 제안했고, 이것이 현대 컴퓨터의 구조가 되었다. <br>

<img width="300" height="300" alt="image" src="https://github.com/user-attachments/assets/eb7f013e-f987-48e8-a11a-26615bfee730"/>

- 컴퓨터에서 다른 작업을 진행할 때 하드웨어의 재배치 없이 소프트웨어만 변경하면 된다. (범용성 향상)
- 컴퓨터는 CPU, 메모리, 버스, 입출력 장치로 구성된다.
- 명령어(Instruction)와 데이터(Data)가 같은 메모리 공간에 저장되며, 같은 버스를 통해 CPU로 전달된다.
- fetch -> decode -> excute -> store 사이클로 명령어를 처리한다.

## 폰 노이만 구조 단점
프로그램 메모리와 데이터 메모리가 하나의 버스를 공유하기 때문에 병목 현상(bottleneck)이 발생한다. <br>
즉, CPU가 아무리 빨라도 메모리에서 데이터를 가져오는 속도(전송 속도)가 느리면 전체 시스템 성능이 저하되는 것이다. <br>
(기억장치의 속도가 전체 시스템의 속도를 결정)

---

# 참고자료

https://jiwondev.tistory.com/109
https://wikidocs.net/63816
https://m.blog.naver.com/with_msip/221981730449
