# Git

## 기본용어
blob: 소스나 파일등의 수정사항
tree: 수정사항에 대한 부가정보(누가, 언제, 무엇을 수정했는지) / 수정일시를 조작가능함
commit: 일종의 스냅샷
remote: 원격저장소(ex, github, bitbucket, gitlab 등)
local: 본인 컴퓨터 저장소
head: 마지막 작업했던 커밋 
fetch: 참고하여 받는 주소
push: 내가 업로드하는 주소


## git과 github는 동일의미가 아님
git방식을 사용하여 소스관리를 하고 소스를 저장하는 저장소 중 하나가 github임

본인 플로우따라 일을 할 수 있도록 localrepo가 존재함
(add, commit, push 순으로 진행하면 문제없음)

## git설치확인
$ git -v

## git환경설정 리스트
$ git config --list

## git환경설정
$ git config --global user.name "당신의유저네임"
$ git config --global user.email "당신의메일주소"
$ git config --global core.editor "vim"
$ git config --global core.pager "cat"
* lg alias 설정(log볼때 가독성을 높여줌):[https://gist.github.com/johanmeiring/3002458](https://gist.github.com/johanmeiring/3002458)

## git 세팅수정(또는 되돌리기)
$ vi ~/.gitconfig
$ git config --global --unset user.email

## repo 주소복사
github > repo > code > 주소복사

## 클론
$ git clone 주소
(저장소에서 만들어진 repo를 로컬로 클론하는 방법이 깔끔함)

## 상태확인
$ git status
$ git status -uall
* -uall:  폴더안 파일까지 확인가능

## 변경사항 stage에 올리기
$ git add 해당파일
$ git add index.html

## 커밋하기
$ git commit
* 커밋할 때 내용입력은 필수(미입력시 진행이 안됨)
* Conventional Commits: [https://www.conventionalcommits.org/ko/v1.0.0/](https://www.conventionalcommits.org/ko/v1.0.0/)

## 푸시하기
$ git push origin main
* 처음 push하는 경우 github에서 생성한 토큰을 계정과 함께 비번에 입력해야함

## gitignore
commit 대상에서 제외시킴
* 개발환경세팅을 조사하여 제외시키는 항목을 넣어줌
* ignore항목자동생성사이트: [https://www.toptal.com/developers/gitignore](https://www.toptal.com/developers/gitignore)

## remote(실제 주소에 대한 별명)
$ git remote
origin
$ git remote -v
origin	https://github.com/soheedev/first-repo.git (fetch)
origin	https://github.com/soheedev/first-repo.git (push)

## remote 별명 수정가능(ex. cat으로 변경)
$ git remote add cat 주소

* 주소를 미리 등록해서 구분지어 사용가능
$ git remote add upstream 주소
$ git remote add downstream 주소

* 별명제거
$ git remote remove cat
$ git remote remoce upstream


