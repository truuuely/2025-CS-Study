# 면접 대비 Q&A 모음

## 컴퓨터 구조

### 컴퓨터 구조 개요

<details>

<summary>컴퓨터 구조란 무엇이며, 왜 중요한가요? </summary>

<div markdown=”1”>

- 컴퓨터 시스템의 동작 원리와 구성 요소 간의 관계를 정의하는 기술
  - 명령 실행, 데이터 처리 방법, SW와 HW의 소통 등을 규정
- 성능 분석, 병목 해소 등 효율적인 SW 설계가 가능

</div>

</details>

<details>

<summary>ISA란 무엇인가요? 어떤 역할을 하나요?</summary>

<div markdown=”1”>

- HW가 이해할 수 있는 명령어 집합 - 명령어의 형식, 연산 종류, 레지스터 구성, 주소 지정 방식 등
- HW와 SW의 인터페이스 역할

</div>

</details>

<details>

<summary>Von Neumann 구조의 특징과 장단점은 무엇인가요?</summary>

<div markdown=”1”>

- 명령어와 데이터를 하나의 메모리에 저장하는 구조, CPU가 순차적으로 명령어를 가져와 실행
- 장점: 구조가 단순하고 구현이 쉬움
- 단점: 병목 현상이 발생할 수 있음

</div>

</details>

<details>

<summary>Von Neumann 병목현상은 무엇이며, 어떤 문제가 발생하나요?</summary>

<div markdown=”1”>

- 폰 노이만 구조에서 발생하는 문제로, 명령어와 데이터가 하나의 메모리와 같은 버스를 공유하기 때문에, CPU가 명령을 가져오는 도중에 데이터를 접근해야 할 때 충돌이 발생하고 처리 속도가 떨어짐

</div>

</details>

<details>

<summary>Harvard 구조는 Von Neumann 구조와 어떤 차이가 있나요?</summary>

<div markdown=”1”>

- 하버드 구조는 폰 노이만 구조와 달리,
  명령어와 데이터를 분리된 메모리와 버스에 저장하는 구조
- CPU가 명령어를 가져오면서 동시에 데이터에 접근할 수 있어 처리 속도가 향상됨
- 구현은 복잡하지만, 폰 노이만 병목 문제를 줄일 수 있음

</div>

</details>

<details>

<summary>명령어 사이클(Instruction Cycle)이란 무엇이며, 각 단계는 어떤 역할을 하나요?</summary>

<div markdown=”1”>

- CPU가 하나의 명령어를 처리하는 과정
- `Fetch - Decode - Execute - Memory Access - Writeback`

</div>

</details>

<details>

<summary>RISC와 CISC의 차이를 설명해보세요. 각각의 장단점도 함께 이야기해주세요.</summary>

<div markdown=”1”>

- RISC: 명령어가 단순함
  <br>🙂 HW 처리 속도 빠름, 파이프라이닝과 병렬 처리에 유리  
  <br>😞 컴파일러 구현 어려움
- CISC: 하나의 명령어로 여러가지 수행 가능: 명령어가 복잡함
  <br>🙂 코드가 짧고 컴파일러 구현 간단  
  <br>😞 HW 처리 속도 느림

</div>

</details>

<details>

<summary>ARM과 x86 아키텍처의 구조적 차이를 설명해보세요.</summary>

<div markdown=”1”>

- ARM: RISC 기반 - 명령어 간단, 전력 소모 적음 → 임베디드나 모바일에 적합 (효율성이 강점)
- x86: CISC 기반 - 명령어 복잡하고 풍부→ 데스크탑, 서버같은 고성능 컴퓨팅 (성능과 호환성이 강점)

</div>

</details>

<details>

<summary>CPU는 어떻게 명령어와 데이터를 구분하나요? 구조적 관점에서 설명해보세요.</summary>

<div markdown=”1”>

- 폰노이만 구조에서는 PC를 통해 명령어 위치 추적, 주소 연산을 통해 데이터 구분
- 하버드 구조에서는 명령어와 데이터의 버스 구조 자체가 (물리적으로) 다름

</div>

</details>

<details>

<summary>컴퓨터 구조가 소프트웨어 성능에 어떤 영향을 미치는지 예시와 함께 설명해보세요.</summary>

<div markdown=”1”>

- 명령어 실행 속도, 병렬 처리 가능성, 메모리 접근 효율 등이 달라짐 + 캐시 구조, 브랜치 예측 등의 마이크로 아키텍처도 성능에 직접적인 영향을 줌
- 예를 들어, 파이프라이닝이 잘 설계된 CPU 구조는 동일 프로그램을 훨씬 빠르게 실행

</div>

</details>

### 수의 표현

> 2의 보수, 부동소수점

<details> <summary>컴퓨터는 음수를 어떻게 저장하나요?</summary> <div markdown="1"> - 2의 보수 방식 사용</br>- 최상위 비트를 부호 비트로 쓰고, 나머지 비트로 2의 보수 값을 저장 </div> </details> <details> <summary>2의 보수는 어떻게 구하나요?</summary> <div markdown="1"> - 1의 보수(NOT 연산)를 취한 뒤 1을 더함 </br>- 또는 `2ⁿ - x`로 계산 가능 </div> </details> <details> <summary>왜 2의 보수를 사용하나나요?</summary> <div markdown="1"> - 뺄셈을 덧셈 회로로 처리할 수 있어 하드웨어가 간단해짐 </br>- 0이 하나만 존재해 오버플로 감지도 쉬움 </div> </details> <details> <summary>1의 보수와 2의 보수의 차이는?</summary> <div markdown="1"> - 1의 보수: 모든 비트를 반전 </br>- 2의 보수: 1의 보수 + 1 </br>- 1의 보수는 +0과 -0 두 개 존재 → 비효율 </div> </details> <details> <summary>컴퓨터는 실수를 어떻게 표현하나요?</summary> <div markdown="1"> - IEEE 754 부동소수점 방식 사용 </br>- 부호(1비트) + 지수(8 or 11비트) + 가수(23 or 52비트) </div> </details> <details> <summary>부동소수점에서 지수에 Bias를 더하는 이유는?</summary> <div markdown="1"> - 지수를 항상 양수로 만들어 비트 단위 정렬/비교가 쉬워짐 </br>- 예: float는 bias 127을 더해 표현 </div> </details> <details> <summary>부동소수점에서 정규화란 무엇인가요?</summary> <div markdown="1"> - 가수를 `1.xxxx` 형태로 표현해 정밀도 확보 </br>- 첫 1은 저장하지 않고 생략함 (암시적 비트) </div> </details> <details> <summary>0.1을 정확하게 표현할 수 없는 이유는?</summary> <div markdown="1"> - 2진수로 0.1은 무한 반복 소수 </br>- 근사값으로 저장되며 오차 발생 </div> </details> <details> <summary>실수 연산에서 오차를 줄이는 방법은?</summary> <div markdown="1"> - Java: `BigDecimal` / Python: `Decimal` 사용 </br>- 또는 소수를 정수로 바꿔서 처리 </div> </details> <details> <summary>float와 double의 차이는?</summary> <div markdown="1"> - float: 32비트 (정밀도 낮음), double: 64비트 (정밀도 높음)</br> - double은 더 많은 소수점 이하 자릿수를 정확히 표현 가능 </div> </details> <details> <summary>부동소수점 대신 고정소수점을 쓸 때는 언제인가요?</summary> <div markdown="1"> - 표현 범위가 작아도 되고 정밀도 요구가 낮은 임베디드 시스템 등 </br>- 구조가 단순하고 하드웨어 구현이 쉬움 </div> </details> <details> <summary>왜 정수 연산이 실수 연산보다 빠른가요?</summary> <div markdown="1"> - 실수 연산은 가수·지수 분리, 정규화 등 복잡한 연산 포함 </br>- 하드웨어 회로도 더 복잡하고 오차 보정도 필요 </div> </details>

### 캐시 메모리

<details>
<summary>캐시가 왜 필요한가요?</summary>
<div markdown="1">
- CPU와 메모리 속도 차이를 줄여서 성능 병목을 완화함
</div>
</details>
<details>
<summary>지역성의 원리는?</summary>
<div markdown="1">
- 최근 접근한 데이터나 그 주변 데이터가 반복적으로 사용됨
</div>
</details>
<details>
<summary>캐시 미스는 왜 발생하나요?</summary>
<div markdown="1">
- 새로 요청한 데이터가 캐시에 없기 때문 </br>
1) Compulsory (Cold start) </br>
2) Conflict</br>
3) Capacity </br>
</div>
</details>
<details>
<summary>직접 매핑 vs 세트 연관?</summary>
<div markdown="1">
- 직접 매핑은 단순하지만 충돌에 약하고, 세트 연관은 유연하게 저장 가능
</div>
</details>
<details>
<summary>Write-Back과 Write-Through 차이?</summary>
<div markdown="1">
- Write-Back은 성능 좋지만 복잡, Write-Through는 간단하지만 느림
</div>
</details>
<details>
<summary>캐시 일관성은 무엇인가요? (심화)</summary>
<div markdown="1">
- 멀티코어에서 여러 캐시 간 데이터 일관성을 유지하는 메커니즘 (ex. MESI (캐시 상태 플래그))
</div>
</details>

### Bus

> 시스템 버스 & Bus Arbitration (버스 중재)

<details>
<summary>시스템 버스란 무엇인가요?</summary>
<div markdown="1"></br>
- CPU, 메모리, I/O 장치 간 데이터를 주고받기 위한 물리적 경로<br>
- Address Bus, Data Bus, Control Bus로 구성됨</br></br>
</div>
</details>

<details>
<summary>주소 버스, 데이터 버스, 제어 버스의 차이는?</summary>
<div markdown="1"></br>
- 주소 버스: 메모리 또는 장치의 주소를 지정 (단방향)<br>
- 데이터 버스: 데이터를 주고받는 통로 (양방향)<br>
- 제어 버스: 읽기/쓰기, 인터럽트 같은 제어 신호 전송 (양방향, CPU 중심)</br></br>
</div>
</details>

<details>
<summary>버스 마스터와 슬레이브란 무엇인가요?</summary>
<div markdown="1"></br>
- 마스터: 버스를 요청하고 제어권이 있는 장치 (예: CPU, DMA)<br>
- 슬레이브: 명령을 받고 응답하는 대상 (예: 메모리, I/O 디바이스)</br></br>
</div>
</details>

<details>
<summary>버스 중재가 필요한 이유는?</summary>
<div markdown="1"></br>
- 버스는 공유 자원: 여러 마스터가 동시에 버스를 사용하려고 하면 충돌이 발생함<br>
- 중재기는 이를 조정해 단 하나의 마스터만 사용 가능하도록 허용</br></br>
</div>
</details>

<details>
<summary>버스 중재에서 사용되는 주요 신호는?</summary>
<div markdown="1"></br>
- BREQ: 마스터가 버스를 요청<br>
- BGNT: 중재기가 사용 권한 부여<br>
- BBUSY: 현재 버스가 사용 중임을 알림</br></br>
</div>
</details>

<details>
<summary>병렬식 중재와 직렬식 중재의 차이는?</summary>
<div markdown="1"></br>
- 병렬식: 각 마스터가 독립된 BREQ/BGNT 선을 가짐 → 빠르나 회로 복잡<br>
- 직렬식: BGNT 신호를 Daisy Chain 방식으로 직렬 연결 → 단순하나 우선순위 고정</br></br>
</div>
</details>

<details>
<summary>고정 우선순위 방식의 단점은?</summary>
<div markdown="1"></br>
- 우선순위가 낮은 마스터는 계속 버스를 사용하지 못할 수 있음 (Starvation)</br></br>
</div>
</details>

<details>
<summary>가변 우선순위 방식의 예시에는 어떤 것이 있나요?</summary>
<div markdown="1"></br>
- Round Robin: 순서대로 돌아가며 우선순위 부여<br>
- FIFO: 먼저 요청한 마스터 우선<br>
- LRU: 오랫동안 사용하지 않은 마스터에게 우선권 부여</br></br>
</div>
</details>

<details>
<summary>중앙집중식 vs 분산식 중재 방식?</summary>
<div markdown="1"></br>
- 중앙집중식: 하나의 중재기가 전체를 제어 → 단순하지만 단일 실패점 존재<br>
- 분산식: 각 마스터가 중재기 포함 → 구조 복잡하지만 신뢰성 높음</br></br>
</div>
</details>

<details>
<summary>하드웨어 폴링 vs 소프트웨어 폴링?</summary>
<div markdown="1"></br>
- H/W 폴링: 고정된 순서로 하드웨어가 질의 → 빠름<br>
- S/W 폴링: 소프트웨어가 질의 순서를 결정 → 유연하지만 느림, CPU 부하</br></br>
</div>
</details>

<details>
<summary>직렬식 분산 중재 방식은 어떻게 동작하나요?</summary>
<div markdown="1"></br>
- 각 마스터가 자신의 Arbiter를 가지며, DBGNT 신호를 원형 구조로 전달<br>
- 요청 중인 마스터가 DBGNT를 받으면 버스를 사용, 아니면 다음에 전달</br>
</div>
</details>

</br>
</br>

## 자료구조

### 선형 자료구조와 비교

> 고정 배열 vs 동적 배열 vs 연결 리스트

<details>
<summary>Array와 ArrayList의 차이?</summary>
<div markdown="1"><br>
- Array는 고정 길이 자료구조, ArrayList는 가변 길이 자료구조<br>
- ArrayList는 내부적으로 배열로 구성되어 있으며, 용량(capacity)을 초과하면 일반적으로 배열 크기를 1.5배로 증가시키며 resizing<br><br>
</div>
</details>

<details>
<summary>Array와 LinkedList의 메모리 할당 차이는?</summary>
<div markdown="1"><br>
- Array는 정적으로 선언되며, 컴파일 시 메모리가 Stack 영역에 할당됨<br>
- ArrayList는 Stack에 객체 참조가 저장되며, 내부 배열은 Heap에 저장됨<br>
- LinkedList는 각 노드가 Heap 영역에 동적 할당되며 포인터로 연결됨<br><br>
</div>
</details>

<details>
<summary>배열이란 무엇인가요?</summary>
<div markdown="1"><br>
- 동일한 데이터 타입의 집합이며, 기본 타입과 객체 참조를 모두 저장할 수 있음<br>
- 크기가 고정되어 있고, 순차적으로 데이터가 저장됨<br><br>
</div>
</details>

<details>
<summary>Array의 특징과 장단점은?</summary>
<div markdown="1"><br>
- 순차적으로 데이터를 저장하며, index를 통한 임의 접근이 가능<br>
- 장점: `O(1)` 시간에 요소 접근 가능<br>
- 단점: 중간 삽입/삭제 시 뒤 요소들을 이동해야 하므로 `O(N)` 시간 소요<br><br>
</div>
</details>

<details>
<summary>Array를 적용하기 좋은 데이터 예시는?</summary>
<div markdown="1"><br>
- 주식 차트처럼 데이터가 시간 순으로 저장되고, 중간 삽입/삭제가 필요 없는 경우에 적합함<br><br>
</div>
</details>

<details>
<summary>링크드 리스트란?</summary>
<div markdown="1"><br>
- 각 노드가 데이터를 저장하고, 다음 노드를 가리키는 포인터를 가지는 선형 자료구조<br>
- 메모리는 연속적이지 않고, 노드는 Heap에 흩어져 저장됨<br><br>
</div>
</details>

<details>
<summary>Array와 LinkedList의 차이는?</summary>
<div markdown="1"><br>
- Array는 인덱스를 통한 임의 접근이 빠르며 연속된 메모리 사용<br>
- LinkedList는 임의 접근은 느리지만, 삽입/삭제가 빠름<br><br>
</div>
</details>

<details>
<summary>링크드 리스트의 삽입/삭제 시간 복잡도는?</summary>
<div markdown="1"><br>
- 맨 앞 삽입/삭제: `O(1)`<br>
- 중간/끝 삽입/삭제: 위치 탐색 비용 포함하여 `O(N)`<br><br>
</div>
</details>

<details>
<summary>LinkedList를 뒤집는 방법은?</summary>
<div markdown="1"><br>
- 반복문으로 각 노드의 `next` 포인터를 역방향으로 재설정<br><br>
</div>
</details>

<details>
<summary>LinkedList에 사이클이 있는지 확인하는 방법은?</summary>
<div markdown="1"><br>
- 플로이드 순환 탐지 알고리즘 사용<br>
- 두 포인터(fast, slow)를 이동시키다가 둘이 만나면 사이클 존재<br><br>
</div>
</details>

<details>
<summary>LinkedList는 언제 유리한가요?</summary>
<div markdown="1"><br>
- 삽입과 삭제가 빈번하고, 요소 수가 자주 변하는 경우<br>
- 큐, 스택, 캐시, Undo/Redo와 같은 기능 구현에 적합함<br><br>
</div>
</details>

### 스택과 큐

<details>
<summary>스택과 큐의 차이는?</summary>
<div markdown="1">

- 스택은 **LIFO** 구조로, **마지막에 들어간 요소가 먼저** 나옵니다.
- 큐는 **FIFO** 구조로, **먼저 들어간 요소가 먼저** 나옵니다.

</div>
</details>

<details>
<summary>스택은 어떤 상황에서 사용되나요?</summary>
<div markdown="1">

- 함수 콜 스택, 재귀 호출 관리, 수식 계산, 괄호 검사, 백트래킹, 깊이 우선 탐색(DFS)

</div>
</details>

<details>
<summary>큐는 어떤 상황에서 적합한가요?</summary>
<div markdown="1">

- 요청 순서대로 처리해야 할 때
  - 예: 너비 우선 탐색(BFS), 프린터 큐, 프로세스 스케줄링 등

</div>
</details>

<details>
<summary>큐의 종류에는 어떤 것이 있나요?</summary>
<div markdown="1">

- **일반 큐 (Queue)**
- **원형 큐 (Circular Queue)**
  - 일반 큐의 overflow 방지를 위해 앞과 뒤를 논리적으로 연결한 구조
- **우선순위 큐 (Priority Queue)**
  - 우선 순위가 존재하는 작업을 처리하며, 내부적으로 **힙(Heap)** 사용
- **덱 (Deque)**
  - 큐의 양쪽에서 삽입/삭제 가능 → 유연한 자료구조

</div>
</details>

<details>
<summary>스택 오버플로우란?</summary>
<div markdown="1">

- **콜스택 크기를 초과**하여 더 이상 데이터를 넣을 수 없는 상태
- 주로 **재귀 함수가 무한 호출**될 때 발생

</div>
</details>

### 힙

<details>
<summary>힙 자료구조란?</summary>
<div markdown="1"><br>
- 완전 이진 트리 기반의 반정렬 자료구조<br>
- 부모-자식 간 대소 관계 유지 (전체 정렬 X)<br>
- 삽입/삭제 O(logN)<br>
- 우선순위 큐의 구현에 활용됨<br><br>
</div>
</details>

<details>
<summary>힙의 삽입 연산이 O(logN)인 이유는?</summary>
<div markdown="1"><br>
- 힙은 이진 트리 구조 → 트리 높이가 logN<br>
- 삽입 후 최악의 경우에도 logN번 부모 노드와 비교<br><br>
</div>
</details>

### 트리
<details>
<summary>트리와 그래프의 차이점은?</summary>
<div markdown="1">

- 트리는 **사이클이 없음**, `간선 수 = 정점 수 - 1 (V-1 = E)`
- 계층적

</div>
</details>

<details>
<summary>트리의 순회 방법은?</summary>
<div markdown="1">

- 전위(Pre), 중위(In), 후위(Post) 순회. 일반적으로 DFS로 구현
- 레벨 순회 (bfs)

</div>
</details>

<details>
<summary>이진 트리와 이진 탐색 트리(BST)의 차이?</summary>
<div markdown="1">

- 이진 트리는 자식 최대 2개, BST는 왼쪽 < 루트 < 오른쪽 조건 추가

</div>
</details>

<details>
<summary>완전(complete)/포화(perfect)/균형(balanced) 이진 트리란?</summary>
<div markdown="1">

- 완전: 왼쪽부터 채움
- 포화: 모든 레벨 완전히 채움
- 균형: depth차 ≤ 1

</div>
</details>

<details>
<summary>힙(Heap) 구조에 대해 트리의 관점으로 설명하라.</summary>
<div markdown="1">

- **완전 이진 트리 기반**의 자료구조로, 우선순위 큐에 사용됨

</div>
</details>

<details>
<summary>TreeSet과 HashSet의 차이는?</summary>
<div markdown="1">

- 정렬
- TreeSet은 정렬 + 중복 제거 / HashSet은 순서 없음, 성능 빠름

</div>
</details>

<details>
<summary>TreeMap이 HashMap보다 느린 이유는?</summary>
<div markdown="1">

- TreeMap은 **정렬 유지 위한 logN 연산 필요**, 내부적으로 레드 블랙 트리 사용

</div>
</details>

<details>
<summary>자바의 트리 자료구조 예시는?</summary>
<div markdown="1">

- TreeMap, TreeSet 등 (둘 다 java.util)

</div>
</details>

### 이진 탐색 트리 (BST)

<details>
<summary>BST에서 탐색·삽입·삭제의 평균과 최악 시간 복잡도는 어떻게 되나요?</summary>
<div markdown="1">

- 평균적으로는 logN의 시간 복잡도
- 최악의 경우, 선형적으로 편향될 경우, O(N)

</div>
</details>

<details>
<summary>BST가 선형적으로 편향될 경우 어떤 문제가 생기나요?</summary>
<div markdown="1">

- LinkedList의 탐색과 같이 비효율적인 탐색을 하게 됨 (O(N))
- 즉, 이진 탐색의 장점(log 시간)이 사라짐

</div>
</details>

<details>
<summary>AVL 트리는 어떤 방식으로 균형을 유지하나요?</summary>
<div markdown="1">

- 모든 노드의 좌우 서브트리의 높이의 차이가 1보다 작거나 같도록, 삽입/삭제 시마다 회전시키며 균형을 유지함

</div>
</details>

<details>
<summary>AVL 트리의 삽입/삭제 시 어떤 회전이 필요한지 예시와 함께 설명해주세요.</summary>
<div markdown="1">

- **LL 회전**: 왼쪽 자식의 왼쪽에 삽입 → 오른쪽으로 단일 회전
- **RR 회전**: 오른쪽 자식의 오른쪽에 삽입 → 왼쪽으로 단일 회전
- **LR 회전**: 왼쪽 자식의 오른쪽에 삽입 → 왼쪽 회전 후 오른쪽 회전
- **RL 회전**: 오른쪽 자식의 왼쪽에 삽입 → 오른쪽 회전 후 왼쪽 회전

</div>
</details>

<details>
<summary>Red-Black 트리의 주요 규칙과 균형 유지 방식은 무엇인가요?</summary>
<div markdown="1">

- 모든 노드를 Red/Black 색상으로 표시함
- 루트 노드와 리프 노드는 항상 Black
- Red 노드의 자식은 항상 Black
- 어떤 노드에서 리프까지 경로의 Black 노드 수는 동일
- 등의 규칙에 따라 삽입/삭제 시 회전/색 변경을 통해 균형을 유지함

</div>
</details>

<details>
<summary>AVL 트리와 Red-Black 트리의 차이점과 각각의 장단점을 비교해보세요.</summary>
<div markdown="1">

- RBT는 색상을 저장하는 추가 비트가 필요하고 구현이 복잡하며, AVL의 탐색보다는 느림
- 그렇지만 AVL보다 더 느슨하게 균형을 유지하기 때문에 삽입/삭제 시 오버헤드가 적고 회전 횟수가 적음 → 속도(성능) 면에서 더 효율적임

</div>
</details>

### 트라이

<details>
<summary> 트라이 자료구조란? </summary>
<div markdown="1">
- 트리 자료구조 중 하나로 문자열을 저장, 탐색하는 데 유용 </br>
- 각 노드는 key-value로 구성되는 Map을 가지며, key는 알파벳, value는 그의 자식 노드다. </br></br>
</div>
</details>

<details>
<summary>트라이의 장단점 </summary>
<div markdown="1">
- 장점: 문자열 검색, 추가가 빠름 O(M). </br>
- 단점: 각 노드에서 자식들의 포인터를 갖고 있기 때문에 필요한 메모리의 크기가 큼</br></br>
</div>
</details>

<details>
<summary> 트라이 자료구조가 이용되는 상황</summary>
<div markdown="1">
- 사전 검색, 자동 완성, 압축, 인코딩 등 대량의 문자열을 다룰 때
</div>
</details>

</br>
</br>

## 데이터베이스

### 키

<details>
<summary> Key란 무엇이고, 종류는 무엇이 있나요? </summary>
<div markdown="1">

</br>

- Key = 튜플을 구분할 수 있는 기준이 되는 속성

1. 후보키
2. 기본키
3. 대체키
4. 슈퍼키
5. 외래키

</div>
</details>
