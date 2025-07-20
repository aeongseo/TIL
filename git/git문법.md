> ### 📌문법에서 
> `< >`는 필수 입력
> 
> `[ ]`는 선택 사항

#  GIT의 동작

## 📑`git init`
- 로컬 저장소 설정(초기화)
- git의 버전 관리 시작할 디렉토리에서 진행
- git init의 범위 설정은 개발자의 영역
- 진행하는 프로젝트에서 적당하게 관리할 수 있는 범위를 찾는 것이 중요!
    > ### 📌git init 주의사항
    > 
    > 이미 `git init`한 폴더 내부 하단에 또 `git init` 입력하지 말 것
    > 
    > 가장 바깥 git 저장소가 안 쪽 git 저장소의 변경사항 추적할 수 없기 때문
> ### 📌 홈 디렉토리에 git init한 경우
>
> `cd ~` -> `ls -a` -> .git 폴더 확인 -> `rm -rf .git`으로 폴더 삭제!

## 📑`git add <file>`
- 변경사항 있는 파일을 staging area에 추가
- `git add .` : working directory에 있는 모든 파일을 staging area에 추가

## 📑`git commit -m <commit message>`
- staging area에 있는 파일들 저장소에 기록
- 해당 시점 버전 생성하고 변경 이력 남기는 것
- commit 생성 위해서는 commit 작성자 정보 필요추가

## 📑`git status`
- 로컬 저장소 파일 상태 확인
- `nothing to commit, working tree clean`  
   -> 작업 디렉토리와 staging area에 아무것도 없다.
- `git restore --staged <file>` : 파일을 working directory로 옮김 (unstage) -> tracked 파일 해당.
- `git rm --cached <file>` : 파일을 working directory로 옮김 (unstage)

> ### 📌 git bash에서 출력이 끝나지 않을 때
>
> `esc` -> `:` -> `q` 누르기!

> ### ✅ git은 로컬 저장소 내 모든 파일의 *변경사항*을 감시하고 있다. -> track
>
> `git add` 전 파일은 untracked 상태. (working directory에 존재)
>
> `git add` 후 파일은 added 상태로 변환. (staging area에 존재)
>
> `git commit` 후 변경된 파일은 modified 상태.
>

## 📑`git log`
- 지금까지의 모든 commit 출력
- `git log --oneline` : commit 목록 한 줄로 보기

## 📑`git config --global -l`
- git global 설정 정보 보기
- `git config list` : 다른 global 설정 정보 모두 뜸
- `git config --global user.name "your name"` : 유저 네임 설정
- `git config --global user.email "your email"` : 유저 닉네임 설정

## 📑`git commit --amend`
- 불필요한 commit 생성 않고, 직전 commit을 수정할 수 있기 때문에 git에서 꼭 필요한 기능
- `기능1` : commit 메시지 수정 가능
  - git commit의 개수는 바뀌지 않지만, commit 메시지와 해시값 변경됨
  - vim 에디터 열림 (뷰잉과 편집 구분됨)
  - 직전 commit 메시지 수정 가능
  - 고치려면 `i` 입력 (insert 모드)
  - 다 고쳤으면 `esc` -> `:wq` `enter` 입력 (wrtie(저장) & quit)
- `기능2` : commit 전체 수정 가능
  - vim 에디터 열림
  - 새로운 commit 정보 확인, 수정 가능
  - staging area에 있는 모든 피알이 직전 commit에 추가됨

# Remote Repository

> ### ✅ 원격 저장소
>
> - 코드, 버전 관리 이력을 온라인 상 특정 위치에 저장
> - 여러 개발자가 협업하고 코드 공유할 수 있는 저장 공간

## 📑`git remote add <name> <url>`
- `<name>` : 별칭 사용해 로컬 저장소 한 개에 여러 우ㅝㄴ격 저장소 추가 가능
- `<url>` : 추가하는 원격 저장소의 URL

## 📑`git push <name> master` 
- 원격 저장소에 commit 목록 업로드

> ### ✅ pull & clone
> #### pull
> - 이미 존재하는 원격/로컬 저장소, 원격에서 로컬로 내용만 갖고 옴.
>
> #### clone
> - remote(원격)를 복제해 local로 갖고 옴.
> - local이 없어야 함.

## 📑`git pull <name> master`
- 원격 저장소의 변경사항만 받아옴 (업데이트)

## 📑`git clone <url>`
- 원격 저장소 전체를 복제 (다운로드)
- clone으로 받은 프로젝트는 이미 `git init` 되어 있음.

## 📑gitignore
- git에서 특정 파일이나 디렉토리 추적하지 않도록 설정하는 데 사용되는 텍스트 파일
- 프로젝트에 따라 공유하지 않아야 하는 것들도 존재
- `.gitignore` 파일 생성 (`git init` 전에 하기)
- 이미 git 관리받은 이력 있는 파일 / 디렉토리는 나중에 gitignore 작성해도 적용 X (방법 있긴 함. 나중에-!)
- gitignore 목록 생성 서비스: http://www.toptal.com/developers/gitignore

## 📑`git revert <commit id>`
- 특정 commit을 없었던 일로 만드는 작업
- "재설정", 단일 commit을 실행 취소 하는 것
- commit을 없애고, 없앴다는 사실을 새로운 commit으로 추가
- vim 에디터 실행되면 `:wq` 치고 나오기
- 변경사항을 안전하게 실행 취소할 수 있도록 도와주는 순방향 실행 취소 작업
- 장점
  - git에서 기록 손실 방지
  - 기록의 무결성과 협업의 신뢰성 높임

## 📑`git revert --no-edit <commit id>`
- vim 편집기 열지 않고 자동으로 commit 진행

## 📑`git revert --no-commit <commit id>`
- 자동으로 commit하지 않고, staging area에만 올림 (이후 직접 commit해야 함)
- 여러 commit을 revert할 때 하나의 commit으로 묶는 것 가능

## 📑`git reset [option] <commit id>`
- 특정 commit으로 되돌아 갔을 때, 되돌아간 commit 이후의 commit은 모두 삭제
- "되돌리기", 시계를 마치 과거로 돌리는 듯한 행위
- 삭제되는 commit들의 기록을 어떤 영역에 남겨둘 것인지 옵션 활용해 조정 가능
- 옵션
  - `--soft` : 삭제된 commit의 기록을 staging area에 남김
  - `--mixed` : 삭제된 commit의 기록을 working directory에 남김
  - `--hard` : 삭제된 commit의 기록을 남기지 않음

## 📑`git reflog`
- HEAD가 이전에 가리켰던 모든 commit 보여줌
reset의 --hard 옵션 통해 지워진 commit도 복구 가능