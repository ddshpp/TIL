# 20230208
***
## isEmpty() vs isBlank()
```
문자열이 null, 또는 공백인지 체크하기위해 사용하는 메소드이다
차이점은 빈 공백의 처리법과 버전이다

<처리법>
isEmpty() - 문자열의 길이를 체크해 0이라면 true
isBlank() - 빈 문자열이나, 공백만으로 이루어진 문자열인 경우 true를 리턴

<버전>
isEmpty() - 
isBlank() -  JAVA11 이후 사용가능

간단한 사용예시를 살펴보자
```

---
## [방법1]  - isEmpty()
문자열이 null이거나 길이가0이라면 true, 아니라면 false를 리턴 <br>
방법은 간단하다 <br>
```java
public class test {
    public static void main(String[] args) {

        String a = "";
        String b = " ";
        String c = "a";
        String d = null;

        System.out.println(a.isEmpty());
        //출력결과 : true

        System.out.println(b.isEmpty());
        //출력결과 : false - 공백이 있기때문에

        System.out.println(c.isEmpty());
        //출력결과 : false

        System.out.println(d.isEmpty());
        //출력결과 : 예외발생(NullPointerException)
    }
}
```
보면 null인경우는 isEmpty를 사용했을때 true,false가 아닌 예외가 발생해버린다 <br>
특정 문자열이 null인지 아닌지 매번 번거롭게 확인하지말고 <br>
간단한 메소드를 만들면 a,b,c,d 한번에 확인가능해진다 <br>
```java
public class test {
    public static void main(String[] args) {

        String a = "";
        String b = " ";
        String c = "a";
        String d = null;

        System.out.println(test(a));
        //출력결과 : true

        System.out.println(test(b));
        //출력결과 : false - 공백이 있기때문에

        System.out.println(test(c));
        //출력결과 : false

        System.out.println(test(d));
        //출력결과 : true
    }

    public static boolean test(String str) {
        return str == null || str.isEmpty();
    }
}
```
test라는 메소드를 만들었다 boolean을 리턴하며 작동방식은 코드와 같다. <br><br>

### 상황1) 공백도 처리안됨?? (예시에서 String b = " ")
근데 만약 공백도 빈 문자열로 하고싶다면? isEmpty 하기전에 trim() 메소드를 활용하면 된다<br>
trim()은 문자열 앞뒤 공백을 제거해준다 <br>
(trim()말고도 다른 공백제거 방법이 있는데 그건 따로 정리하고 우선 trim()으로 설명하겠다)
```java
public class test {
    public static void main(String[] args) {

        String a = "";
        String b = " ";
        String c = "a";
        String d = null;

        System.out.println(test(a));
        //출력결과 : true

        System.out.println(test(b));
        //출력결과 : true - 이제 true로 나온다

        System.out.println(test(c));
        //출력결과 : false

        System.out.println(test(d));
        //출력결과 : true
    }

    public static boolean test(String str) {
        return str == null || str.trim().isEmpty();
    }
}
```

---
## [방법2]  - isBlank()
JAVA11 이상부터는 isBlank()메소드를 사용할수있다 사용해보자
```java
public class test {
    public static void main(String[] args) {

        String a = "";
        String b = " ";
        String c = "a";
        String d = null;

        System.out.println(test(a));
        //출력결과 : true

        System.out.println(test(b));
        //출력결과 : true

        System.out.println(test(c));
        //출력결과 : false

        System.out.println(test(d));
        //출력결과 : true
    }

    public static boolean test(String str) {
        return str == null || str.isBlank();
    }
}
```
isBlank()는 빈 문자열이나, 공백만으로 이루어진 문자열인 경우 true를 리턴 <br>
앞에 예시처럼 trim()을 호출하지 않아도 됨