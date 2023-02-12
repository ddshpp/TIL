# 20230212
***
## String 배열의 정렬, Arrays.sort()
```
여느때와 다름없이 백준문제를 풀고있었다 (4153번)
숫자 3개가 담긴 문자열이 주어지는데 
각각 숫자가 삼각형의 변이라 친다면
주어진 숫자가 직각삼각형인지 알아내는 문제였다
(ex "3 4 5" > 직각삼각형 맞음!!)

아무튼 
숫자는 "a b c" 이렇게 스트링으로 주어지는데
나는 이걸 

1. 스캐너로 입력받아
2. 입력받은 문자열을 split으로 공백(" ")으로 쪼개면
3. 각각 숫자로 이루어진 문자열을 얻을 수 있겠구나!
4. 그걸 정렬해서 비교해보자!

라고 생각했다.

※ 4번의 이유는 숫자가 크기대로 안들어올 수도 있으니
큰숫자를 뒤로 보내서 앞에 두개를 제곱한게 뒤에랑 같은지 보면되니까
(5 3 4 이렇게 입력이 들어왔을때 25 + 9 == 16 이러면 안되니까) 

아무튼 비교를 하는데
어디서 주워듣기론 스트링도 정렬이 된다하더라 

근데 안됐다

뭐가 문제였을까?
```
---
### 0단계  - 우선 잘 쪼개지는지 봐보자
```java
import java.util.Scanner;

public class Test {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();
        //"13 5 12"라고 입력할예정

        String[] result = input.split(" ");
        //쪼개면 result[0] = "13" , result[1] = "5" , result[2] = "12" 이 되겠지??

        for (int i = 0; i < result.length; i++) {
            System.out.println(result[i]);
        }
        //그럼 13, 5, 12 가 출력되겠군!?
    }
}
```
과연 결과는??<br>
<a href="https://imgbb.com/"><img src="https://i.ibb.co/JHKdBbb/1.png" alt="1" border="0"></a><br>
역시나 잘 쪼개지고 순서대로 잘 나온다

---
### 1단계  - 그럼 정렬을 해봐야지?
```java
import java.util.Arrays;
import java.util.Scanner;

public class Test {
    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();
        //"13 5 12"라고 입력할예정

        String[] result = input.split(" ");
        //쪼개면 result[0] = "13" , result[1] = "5" , result[2] = "12" 이 되겠지??

        Arrays.sort(result);
        //정렬을 했다!!

        for (int i = 0; i < result.length; i++) {
            System.out.println(result[i]);
        }
        //그럼 5, 12, 13 이 출력되겠군!?
    }
}
```
예상대로라면 5, 12, 13이 출력되어야 한다 과연??<br>
<a href="https://imgbb.com/"><img src="https://i.ibb.co/M5pN3hS/2.png" alt="2" border="0"></a><br>
?????

---
### 2단계  - 이유는 바로 사전식 정렬이였다
```
국어사전이나 영어사전을보면
가나다순으로 되어있다

마찬가지로
저 문자열들도 크기로 정렬을 하는게 아니라
사전식 정렬을 하기때문에 
1이 앞에오는 12가 처음, 그다음 13, 그리고 5가 마지막으로 된것이다
(String형 변수이기 때문...)

설명이 서툴지만 이해했을꺼라 생각한다
```
---
### 3단계  - 그래서 해결방법은?
```
여러가지가 있겠지만 초보자인 내가 해결한 방법은 

쪼갠걸 int로 바꿔서 List<Integer>에 담은다음 
Collections.sort()로 정렬해서 풀었다

원래 저렇게 안하고 
그냥 int로 바꿔서 int배열에 담아 Arrays.sort()해도 되는건데
오타가 났던건지 자꾸 안되길래 
아주 고생스럽게도 리스트로 만들어서 풀었다
(다시해보니 됨)
```
