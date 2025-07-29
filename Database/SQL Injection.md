# SQL Injection

: 응용 프로그램 보안 상의 허점을 의도적으로 이용해 악의적인 SQL문을 실행되게 함으로써 데이터베이스를 비정상적으로 조작하는 공격 방법

</br>

## 공격

### 1. 인증 우회 / 논리 훼손

: 쿼리문을 변형해 프로그램의 다양한 기능을 악의적으로 사용한다.

</br>

- **Subverting application logic**

> to change a query to inferfere with the application’s logic

예를 들어, 로그인을 할 때 SQL Injection 공격으로 동시에 다른 쿼리문을 입력할 수 있다.

```sql
// id input에 admin';-- 자체를 입력한 경우
SELECT * FROM USER WHERE ID = 'admin';-- AND PASSWORD = ''**;

// pw input**에 **1234';** DELETE * USER FROM ID = "1";--을 입력한 경우
SELECT * FROM USER WHERE ID = 'abc' AND PASSWORD = '**1234';**
DELETE * USER FROM ID = '1';--';
```

</br>

### 2. 데이터 노출

: 쿼리 변경, 에러 발생, 유니온 명령 등을 통해 숨겨진 데이터를 탈취한다.

- **Retrieving hidden data**

> to modify a SQL query to return additional results

- Error Based

> to get data from errors

- Union Attack

> to retrieve data from different database tables

```sql
// category input에 Gifts' OR 1=1;-- 자체를 입력해 출시되지 않은 상품 정보를 가져온다.
SELECT * FROM products WHERE category = 'Gifts' OR '1'='1';--' AND released = 1;
```

```sql
// 의도적으로 오류를 발생시켜 정보를 탈취할 수 있다.
GET 방식 URL 쿼리 스트링 추가해 에러 발생
-> 에러를 통해 디비 구조 유추
```

```sql
// category input에 Gifts' UNION ... 와 같이 UNION 명령어를 사용해 정보를 탈취할 수 있다.
SELECT name, description FROM products WHERE category = 'Gifts'
UNION SELECT username, password FROM users--';
```

</br>

### 3. Blind SQL Injection

> 오류 메시지를 확인할 수 없는 환경에서 참/거짓 판단을 통해 DB 정보를 유추하는 공격 기법

- 쿼리 논리를 변경해 → 단일 조건의 T/F 여부에 따라 → 감지 가능한 차이를 유발한다.
- SQL 쿼리에 조건을 삽입해 → 서버 응답 결과, 시간 등의 차이를 통해 → 조건의 참/거짓 판별한다.
- OAST 기술을 사용해 → 대역외 네트워크 상호작용을 유발시켜 → 데이터를 직접 유출한다.

</br>

예를 들어, 각 테이블/컬럼/데이터의 전체 개수를 확인하고 SUBSTR함수를 사용해 각 테이블/컬럼/데이터의 문자를 1개씩 추출하고 ASCII 함수를 활용해 숫자로 변환해 비교한다. 행 번호와 자릿수를 증가시켜가며 문자열을 추적하는 과정을 반복하면 원하는 데이터를 추출할 수 있다.

다른 예로, 0으로 나누기와 같은 오류를 조건부로 발생시키는 방법도 있다.

또다른 예로는, 다른 대역 채널을 통해 제어 도메인의 DNS 조회에 데이터를 추가할 수 있다.

</br></br>

## 방어/대응

### 1. 파라미터 바인딩 & 입력 필터링

- 파라미터 바인딩 (**PreparedStatement**)

> 쿼리문을 템플릿 형태로 만들어두고 입력을 파라미터화해 전달함

```java
PreparedStatement stmt = conn.prepareStatement("SELECT * FROM users WHERE username = ?");
stmt.setString(1, input);
ResultSet rs = stmt.executeQuery();
```

- 입력값 검증 및 필터링

> 한정된 패턴으로 제한하고 특수문자나 예약어 등의 위험한 문자를 제거, 인코딩, 이스케이프 처리함

→ 사용자 입력을 적절히 필터링해 쿼리 실행 시점에 파라미터로 안전하게 전달

</br>

### 2. DB 계정 권한 제한

> 일반 웹앱 계정과 관리자 계정 분리 및 각각 최소 권한만을 부여

예를 들어, View를 활용해 원본 DB Table에는 접근 권한을 높이고, 일반 사용자는 View로만 접근하게 제한한다. 이렇게 하면 오류가 발생했을 때, 일반 사용자는 Error Message를 볼 수 없다.

</br>

### 3. 보안 도구 활용 (Burp Suite 등)

https://portswigger.net/burp/vulnerability-scanner

</br></br>

<aside>

# cf. XSS vs SQL Injection

| XSS (Cross Site Scripting)             |      | SQL Injection                        |
| -------------------------------------- | ---- | ------------------------------------ |
| 사용자 브라우저에서 악성 스크립트 실행 | 목표 | 데이터 베이스에서 악성 SQL 코드 실행 |
| 부적절한 입력 필터링 / 출력 인코딩     | 원인 | 주로 입력 값을 SQL 쿼리에 직접 삽입  |

| 사용자 쿠키/세션 탈취,
개인 정보 유출,
웹 페이지 변조,
악성 코드 유포 등 | 피해 | 데이터 베이스 정보 탈취,
시스템 권한 탈취,
데이터 위조/변조,
서비스 거부 공격 등 |

</aside>

</br></br>

---

</br>

**참고자료**

https://portswigger.net/web-security/sql-injection

https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Database/SQL%20Injection.md

https://www.fis.kr/ko/major_biz/cyber_safety_oper/attack_info/security_news?articleSeq=2568

https://www.skshieldus.com/blog-security/security-trend-idx-45
