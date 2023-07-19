# Git

- 분산 버전 관리 시스템
- 동시에 다양한 작업 수행 가능
- 백업/복구 용이



- 순서 : add -> commit -> push 



- **add** : 내 컴퓨터 => 임시공간 추가
- **commit** : 임시 공간으로 추가한 것에 변경사항/메모 추가 . snapshot
- **push** : 임시공간 => 외부 저장소 



``````

💡 github 에서 빈 repository 생성 시 볼 수 있음

echo "# test" >> [README.md](http://readme.md/)
git init
git add [README.md](http://readme.md/)
git commit -m "first commit"
git branch -M main
git remote add origin https://github.com/id/repo.git
git push -u origin main

``````

- git remote add origin remote_repo_url
  - 로컬 저장소에 원격 저장소 주소 추가
- git push -u origin master
  - 원격 저장소에 commit 목록 업로드
- git pull 
  - 원격 저장소의 변경사항 받아옴(업데이트)
  - **작업시작 전 항상 pull 먼저 하기**

- git clone remote_repo_url
  - 원격 저장소 전체 복제(다운로드)
  - git init, remote 등록 불필요
- gitignore
  - git에서 특정 파일/디렉토리 추적하지 않도록 설정
  - 이미 git의 관리를 받은 파일/디렉토리는 적용 불가
  - API key, 보안, 개인정보, 무거운 파일 등에 적용 
  - [gitignore생성 사이트](https://www.toptal.com/developers/gitignore/)



### branch

- git branch 이름 = "이름" branch 생성

- git branch = 브랜치 목록 보기

- git checkout 이름 = "이름" branch로 이동

- git branch -d 이름 = "이름" branch 삭제

  
