# 1. Array
- 미리 할당된 크기에 연관된 데이터를 메모리 상에 연속적이고 순차적으로 저장하는 선형 자료구조

<img width="703" height="228" src="https://github.com/user-attachments/assets/7cbef648-9973-47aa-b971-6227b6072d20" />

## 1.1. 특징
- 저장공간 고정
- 순차적 저장
- 인덱스로 원소 접근 가능
- 마지막 원소가 아닌 원소를 제거하면 인덱스를 조정하는 shifting이 일어나 O(n)만큼의 시간 소요
- lookup, append가 빨라 원소를 빈번히 조회해야하는 경우 유리
- 크기가 고정되어 있어 사용하지 않는 공간이 있을 경우 메모리 낭비 발생
- 크기가 고정되어 있어 크기를 변경하려면 새로운 배열을 만든 후 옮겨줘야 함

## 1.2. 예시코드
```
int[] arr = new int[3];
arr[0] = 1;
arr[1] = 2;
arr[2] = 3;
```

***

# 2. LinkedList
- 노드라는 구조체에 데이터값과 다음 노드의 주소를 저장하고 있는 자료구조
- 기존 배열 자료구조의 삽입/삭제 비효율성을 해소하기 위해 등장
- 데이터는 물리적으로 비연속적인 저장이지만, 각 노드들이 다음 노드의 주소를 가리키고 있으므로 논리적으로는 연속적 저장

<img width="635" height="215" src="https://github.com/user-attachments/assets/7de62ab4-477e-405a-b619-ab14fc10ab56" />

## 2.1. 특징
- 데이터가 추가되는 시점에 메모리 할당으로 효율적 사용 가능
- 데이터 이동 속도 빠름
- 데이터 조회 속도 느림 (랜덤 엑세스 불가능)
- Head 주소 기억 필요

## 2.2. 단점
- 실 연산 속도 저하
- 주소 저장으로 인한 공간 낭비
- 복잡한 연산으로 인한 오버헤드

## 2.3. 예시코드
### 2.3.1. Singly LinkedList
```
class Node {
    int data;
    Node next;

    public Node (int data) {
        this.data = data;
        this.next = null;
    }
}

class SinglyLinkedList {
    Node head;

    public SinglyLinkedList() {
        this.head = null;
    }

    public void append (int data) {
        Node node = new Node(data);

        if (head == null) {
            head = node;
            return;
        }

        Node current = head;
        while (current.next != null) {
            current = current.next;
        }

        current.next = node;
    }
}
```
### 2.3.2. Doubly LinkedList
```
class Node {
    int data;
    Node next;
    Node prev;

    public Node (int data) {
        this.data = data;
        this.next = null;
        this.prev = null;
    }
}

class DoublyLinkedList {
    Node head;
    Node tail;

    public DoublyLinkedList() {
        this.head = null;
        this.tail = null;
    }

    public void append (int data) {
        Node node = new Node(data);

        if (head == null) {
            head = node;
            tail = node;
            return;
        }

        tail.next = node;
        node.prev = tail;
        tail = node;
    }
}
```

***

# 3. Stack
- '쌓다', '쌓이다'
- 데이터를 순서대로 쌓는 자료 구조

<img width="700" height="300" src="https://github.com/user-attachments/assets/5ef17334-ac20-4813-8743-91489cd98c1e" />

## 3.1. 특징
- LIFO(Last In First Out, 후입선출)
- 데이터의 삽입과 삭제는 top이라고 일컫는 한 쪽 끝에서만 이루어지도록 제한하여 만든 자료구조
## 3.2. 기본 연산
1. push()
- stack의 제일 위에 데이터를 추가하는 연산
2. pop()
- stack의 제일 위의 데이터를 제거하고 반환하는 연산
3. peek()
- stack의 제일 위의 데이터를 반환하는 연산
4. isEmpty()
- stack이 비어있는지 확인하는 연산
## 3.3. 장단점
- 장점
    - 간단한 구현
    - 빠른 속도
- 단점
    - 크기 제한
## 3.4. 예시코드
```
public class ArrayStack {
    int top;
    int size;
    int [] stack;

    public ArrayStack(int size) {
        this.size = size;
        stack = new int[size];
        top = -1;
    }

    public void push (int item) {
        stack[++top] = item;
    }

    public void pop () {
        int pop = stack[pop];
        stack[top--] = 0;
    }
}
```

***

# 4. Queue
- '줄을 서서 기다린다', '대기행렬'

## 4.1. 특징
- FIFO(First In First Out)
- 데이터는 하나씩 출입 가능
- 두 개의 입출력 방향

## 4.2. 기본 연산
1. add()
- Queue의 rear에 데이터 추가
2. poll()
- Queue의 front의 데이터를 제거하고 반환
- 비어있을 경우 null 반환
3. remove()
- poll()과 동일하지만 큐가 비어있으면 NoSuchElement 에러 반환
4. peek()
- Queue의 front 데이터 반환
5. isEmpty()
- Queue가 비어있는지 확인
## 4.3. 장단점
- 장점
    - 순서가 중요한 상황에 활용
    - 배열이나 연결 리스트 구현에 적합
- 단점
    - 큐에서 임의의 위치에 있는 항목에 접근 어려움
    - ㅂ열 기반의 구현에서 크기가 고정되어 있어 확정 어려움
## 4.4. 종류

| 종류 | 정의 |
| :---: | :--- |
| 선형 큐 | 일반적인 큐로, 데이터가 선형적으로 저장 <br>배열이나 연결리스트로 구현가능 |
| 원형 큐 | 선형 큐의 한 종류로, rear와 front가 순환적으로 움직임 |
| 우선순위 큐 | 각 데이터의 우선순위가 정해져 있고, 우선순위에 따라 삭제 및 검색이 이루어지는 큐 <br> Heap과 같은 자료구조 규현 |
| 덱 | 양쪽 끝에서 데이터의 삽입과 삭제가 가능한 큐로, 스택과 큐의 기능을 모두 가짐 |

***



***
# 참고자료
## Array
https://velog.io/@newdana01/CS-Array%EC%99%80-LinkedList-%EC%A0%95%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90
## LinkedList
https://hoehen-flug.tistory.com/29
https://mongsil-jeong.tistory.com/58
## Stack
https://velog.io/@rlvy98/CS-%EC%8A%A4%ED%83%9DStack
## Queue
https://jyunslog.tistory.com/56