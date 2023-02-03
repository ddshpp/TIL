# 20230201
***
## unmappable character (0xec) for encoding x-windows-949 오류 해결법
``` 
Intellij로 공부를 하는중
얼마전 알게된 //TODO 를 이용하여 메모를 하였다
다음날 또 공부를 이래저래 하다보니 갑자기
unmappable character (0xec) for encoding x-windows-949 라며 안되더라
//TODO에 쓰인 한글이 말썽을 부린듯하다
해결해보자
```

### 1단계  - 설정을해보자
1. IntelliJ 상단에 Help > Edit Custom VM options... 클릭 
2. 아래 두문장을 입력
   1. -Dfile.encoding=UTF-8 
   2. -Dconsole.encoding=UTF-8 
2. IntelliJ 재시작
3. 해결되었다면 박수 아니라면 다른설정을 해보자 (나는 해결됨)
---
