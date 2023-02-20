# 20230220
***
## toString() vs String.valueOf()
```
두 메소드 모두 Object 형태의 값을 String 형태로 변환하지만
Object가 null인 상황에서 차이를 보인다

<Object가 null일때>
1. toString() - NullPointerException 발생
2. String.valueOf() - "null" 이라는 문자열을 반환

예외를 방지하고 싶다면 String.valueOf()를 사용하는것이 좋아보인다
```

---
### 사용법 <br>
Objects a = null; <br>

toString() -> a.toString(); <br>
String.valueOf() -> String.valueOf(a);
```java
Objects a = null;

System.out.println(String.valueOf(a));
//출력결과 : null

System.out.println(a.toString());
//NullPointerException발생
```
