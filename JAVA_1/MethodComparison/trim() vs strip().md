# 20230220
***
## trim() vs strip()

```
두 메소드 모두 문자열 앞뒤 공백을 제거해준다
차이점은 범위와 버전에 있다.

<범위>
trim() - '\u0020' 이하의 공백들만 제거
strip() -  유니코드의 공백들을 모두 제거

<버전>
trim() - 
strip() -  JAVA11 이후 사용가능

자바의 버전에 맞게 사용하는게 첫번째, 버전만 된다면 strip을 사용하는게 좋다
```

---
### 사용법 <br>
String a = " test "; <br>

trim() -> a.trim(); <br>
strip() -> a.strip();
```java
String a = " test ";

String testTrim = a.trim();
String testStrip = a.strip();

System.out.println(testTrim);
//출력결과 : test
System.out.println(testStrip);
//출력결과 : test
```