# Git을 뿌셔보자
<br/>

## 목차
[1. 기본 설정](#📌-기본-설정)  
[2. 파일 작성 ~ 커밋](#📌-파일-작성--커밋)  
[3. 풀 리퀘스트](#📌-풀-리퀘스트)  
[4. 깃헙 파일을 내 컴퓨터로 받는 방법](#📌-깃헙-파일을-내-컴퓨터로-받는-방법)

<br/>

***

## 📌 기본 설정
### 🧩 1. github 에서 fork
- 내 계정에 repository(레포지토리) 생성

### 🧩 2. git 초기화
```
git init
```

### 🧩 3. 내 계정의 repository(레포지토리) 주소를 clone 
```
git clone https://github.com/jongryeol/codestates-study.git
```

### 🧩 4. 원격 저장소 주소 확인
```
git remote -v 
```
#### <p style="color:lightgreen">4-1. 아래와 같이 터미널에 표시된다면 <b style="color:yellow">5번</b>으로</p>

origin /*...(주소)...*/ (fetch)  
origin  /*...(주소)...*/ (push)

#### <p style="color:lightgreen">4-2. 위와 같이 origin이 안뜨면 </p> 
내 계정의 repository(레포지토리) 주소를 연결해준다.
```
git remote add origin https://github.com/jongryeol/codestates-study.git
```

### 🧩 5. 메인 저장소의 코드를 싱크하기 위해 upstream 설정 
```
git remote add upstream https://github.com/YHJ96/codestates-study.git
```

## 📌 파일 작성 ~ 커밋
### 🧩 1. 파일을 작성 후 나의 로컬에 저장

#### <p style="color:lightgreen">1-1. 파일 일부만 저장하고 싶을 때  </p>
(파일 이름은 다르겠죠?)
```
git add 서종렬연봉3억원달성.md
```

#### <p style="color:lightgreen">1-2. 수정한 파일 전체를 저장하고 싶을 때</p>
```
git add .
```
### 🧩 2. 수정한 파일이 잘 업데이트 되었는지 확인
```
git status
```

### 🧩 3. 로컬 > 내 깃헙 레포지토리로 커밋
```
git commit -m "docs:서종렬연봉3억원달성.md 작성완료 [서종렬]"
```

### 🧩 4. 깃허브 내 레포지토리에 잘 올라갔는지 확인

***

## 📌 풀 리퀘스트  

### 🧩 1. 깃허브 > 내 레포지토리 > 풀리퀘스트 > New pull request

***

## 📌 깃헙 파일을 내 컴퓨터로 받는 방법

### 🧩 1. 다른 사람이 수정해서 깃헙에 올린 파일이 있는지 확인합니다.
```
git fetch upstream
```

### 🧩 2. 수정한 파일이 있다면, 내가 포크한 레포지토리로 파일을 불러옵니다.
```
git merge upstream/main
```

#### <p style="color:lightgreen">Tip1. 여기서 main 은 branch(브런치)입니다.  </p>
브런치를 확인하는 방법은
```
git branch
```

#### <p style="color:lightgreen">Tip2. fetch + merge == push  </p>
Q. 그럼 왜 두번으로 나눠서 하는가?  
> 💡 상대방이 수정한 파일을 굳이 내가 받아올 필요가 없을 수도 있기 때문

### 🧩 3. 내 레포지토리에서 로컬로 파일을 불러옵니다
```
git push origin main
```