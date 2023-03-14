# 20230315
***
## retainAll()
```
여느때와 다름없이 꾸준히 알고리즘 문제를 풀던 도중...

문자열을 담고있는 리스트가 2개 있을때
중복되는 값을 추출해야하는 문제를 만났다 (No1764)

뭔가 좋은 방법이 있을껏만 같은 느낌...
그러다 엄청난 친구를 알게되었다
```

---

## [설명]  - retainAll()
listA, listB가 있을 때 <br>
두 리스트의 공통요소만 남기고 나머지는 제거한다
```java
public static void main(String[] args) {
    List<String> listA = new ArrayList<>(Arrays.asList("aa", "bb", "cc"));
    List<String> listB = new ArrayList<>(Arrays.asList("ww", "bb", "cc", "zz"));
    
    listA.retainAll(listB);
    
    for (String s : listA) {    
        System.out.println(s);
    }
    //출력결과 : bb,cc
}
```
뭐 너무 간단한 사용방법이라 별 설명이 없어도 될듯하다 <br>
하지만 문제는 있었다

---

## [문제발생]  - 시간복잡도 
백준 1764 문제를 풀때 <br> 
왜 그랬는진 기억이 안나는데 <br>
리스트를 해시셋에 담아서 retainAll()을 사용했었다, 그리고 정답이였고. <br><br>
근데 가만 생각해보니 리스트를 굳이 해시셋에 옮겨서 할 필요가 있나? 싶었다 <br>
그래서 그냥해봤더니 시간초과가 나오고 말았다. <br>
왜일까 <br>


```java
//1번방법 - 정답코드 일부 (첫번째 도전했던 풀이)
public static List<String> solution(List<String> noHear, List<String> noView) {
    Set<String> set1 = new HashSet<>(noHear);
    Set<String> set2 = new HashSet<>(noView);
    set1.retainAll(set2);
    
    List<String> result = new ArrayList<>(set1);
    Collections.sort(result);
    result.add(0, String.valueOf(result.size()));
    return result;
}
```
```java
//2번방법 - 실패코드 일부
public static List<String> solution(List<String> noHear, List<String> noView) {
    //보면 그냥 바로 retainAll()을 사용한걸 볼 수 있다.
    noHear.retainAll(noView);
    
    List<String> result = new ArrayList<>(noHear);
    Collections.sort(result);
    result.add(0, String.valueOf(result.size()));
    return result;
}
```

그냥 여기서 알수있는건 1번방법이 뭔진 모르지만 빠르구나 였다. <br>
그래서 요즘 핫한 chatGPT에 물어봤다.

```
HashSet을 사용하는 것이 ArrayList을 사용하는 것보다 더 빠른 이유는 
HashSet은 내부적으로 해시 테이블을 사용하여 검색을 수행하기 때문입니다. 
해시 테이블은 원하는 값을 빠르게 찾아낼 수 있으므로 
HashSet에서 retainAll() 메소드를 사용하여 중복 값을 찾는 것이 더 빠르게 수행됩니다.

그러나 ArrayList에서 retainAll()을 사용하면 
리스트의 모든 원소를 반복하여 중복 값을 찾는 방식으로 수행됩니다. 
따라서 HashSet을 사용하는 것이 더 빠르게 수행됩니다.

결론적으로, 
noHear.retainAll(noView)과 같이 ArrayList에서 retainAll()을 사용하는 것보다 
HashSet을 사용하는 것이 더 빠릅니다.
```

느낌은 알겠다만 정확한 이유는 아직 모르므로 조만간 공부해서 TIL에 올리도록 하겠다!