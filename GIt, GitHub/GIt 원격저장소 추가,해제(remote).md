# 20230202
***
## GIt 원격저장소 추가,해제 (remote)
``` 
터미널에서 git 명령어로 repository의 연결을하거나, 해제하는 방법을 알아보자
```

---
## 1. 연결된 저장소 확인
```
git remote -v : 현재 git에 등록된 원격저장소 리스트를 보여줌

<예시>
$ git remote -v
origin  https://github.com/ddshpp/TIL.git (fetch)
origin  https://github.com/ddshpp/TIL.git (push)
```

---
## 2. 저장소 연결해제
```
git remote remove <name> : 해당 원격저장소의 연결해제

<예시>
$ git remote remove origin

이후 git remote -v 를 통해 확인해보면 연결된 저장소가 없음을 확인할 수 있음
```

---
## 3. 저장소 연결
```
git remote add <name> <url> : 해당 원격저장소를 등록

<예시>
$ git remote add origin <url>

이후 git remote -v 를 통해 확인해보면 연결된 저장소를 확인할 수 있음
```