# 20230214
***
## List 2차원 배열 만들기
```
백준 문제를 풀던중(10250번) 
2차원배열처럼 리스트를 만들 수 있으면 편하겠다 생각이 들어 찾아보았다
생각보다 어렵진 않았다

[방법 1] List<List< 타입 >> list = new ArrayList<>();

[방법 2] ArrayList[] list = new ArrayList[ 크기 ];
```


---
## [방법1]  - 내가 했던방법
<상황> list를 5개 가지는 list를 만들려면
```java
List<List<Integer>> test = new ArrayList<>();

for (int i = 0; i < 5; i++) {
    test.add(new ArrayList<>());
}

System.out.println(test.size());
//출력결과 : 5
```
그리고 값을 넣을땐 아래와 같이 하면된다. 잘들어갔는지 출력해보면
```java
List<List<Integer>> test = new ArrayList<>();

for (int i = 0; i < 5; i++) {
    test.add(new ArrayList<>());
}

System.out.println(test.size());
//출력결과 : 5

test.get(0).add(1);
test.get(0).add(2);
test.get(1).add(123);
test.get(2).add(5555);
test.get(2).add(6666);

System.out.println(test.get(0));
//출력결과 [1, 2]
System.out.println(test.get(1));
//출력결과 [123]
System.out.println(test.get(2));
//출력결과 [5555, 6666]

System.out.println(test.get(0).get(0));
//출력결과 1
System.out.println(test.get(0).get(1));
//출력결과 2
```

예상대로 잘들어간다<br>

---
## [방법2]  - 검색하다 찾은 방법. <br> (리스트를 원소로 가지는 배열을 만드는듯)
<상황> list를 3개 가지는 배열을 만들려면 (위와 같은 값을 넣어보았다)
```java
ArrayList[] test = new ArrayList[3];

for (int i = 0; i < 3; i++) {
    test[i] = new ArrayList<Integer>();
}

System.out.println(test.length);
//출력결과 : 3

test[0].add(1);
test[0].add(2);
test[1].add(123);
test[2].add(5555);
test[2].add(6666);

System.out.println(test[0]);
//출력결과 : [1, 2]
System.out.println(test[1]);
//출력결과 : [123]
System.out.println(test[2]);
//출력결과 : [5555, 6666]

System.out.println(test[0].get(0));
//출력결과 : 1
System.out.println(test[0].get(1));
//출력결과 : 2

System.out.println(test[0].size());
//출력결과 : 2
```
이런방법도 있다. <br>
실제로 어떤 방식이 더 나은지는 잘 모르겠지만 <br>
나는 1번방식을 사용할듯 하다 <br>
<br>
이유는 <br>
아래 방법은 코드를 보면 <br>
1. 리스트를 원소로 가지는 test의 크기를 구할땐 length를 써야한다 
2. 각각 원소의 크기를 구할땐 size()를 써야한다

왜 그렇게 해야하는지는 알겠다 <br>
하지만 test라는 저 덩어리를 볼때 일관성이 없다해야하나? 그래보인다 <br>
뭔가 실수할 여지를 만드는거 같아서 별로...<br>


