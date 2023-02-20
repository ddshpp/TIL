# 20230212
***
## int형 숫자의 각각 자릿수 구하기
```
예를들어 12345 라는 숫자가 있을때 1, 2, 3, 4, 5 이렇게 각각의 자릿수를 구하고 싶다면??? 

[방법 1] - 나머지연산
[방법 2] - 문자열로 변환후 chatAt()
[방법 2] - 문자열로 변환후 split()
```

---
## [방법1]  - 나머지연산
```java
int a = 12345;

Set<Integer> test = new HashSet<>();

while (a > 0) {
    test.add(a % 10);
    a /= 10;
}

System.out.println(test);
//출력결과 : [1, 2, 3, 4, 5]
```

---
## [방법2]  - 문자열로 변환 후 chatAt()
```java
int a = 12345;

String temp = String.valueOf(a);

for (int i = 0; i < temp.length(); i++) {
    System.out.println(temp.charAt(i));
}

//출력결과 : 
1
2
3
4
5
```

---
## [방법3]  - 문자열로 변환 후 split()
```java
int a = 12345;

String temp = String.valueOf(a);

String[] split = temp.split("");

for (int i = 0; i < split.length; i++) {
    System.out.println(split[i]);   
}

//출력결과 : 
1
2
3
4
5
```