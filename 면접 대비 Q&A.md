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






