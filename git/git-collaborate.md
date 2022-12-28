# Collaborate with your teammates
* git 협업

## 팀장역할
* organization 생성
* plan 선택 (무료)
* organization account name 설정
* 팀원 추가 (invite member/ role은 Member로 선택)

### Repository 생성 (팀장)
* public
* add README file
* MIT License 추가
* remote에 develop 브랜치 생성
* 환경설정(.gitignore)

### 개발환경설정 (팀장)
```
$ git clone 주소
$ git branch # main 위치인지 확인

# git flow 시작
$ git flow init 

# develop 브랜치 생성 확인 
$ git flow feature start proj-init #이름은 임의로(proj-init)

# .gitignore 설정 (참고: https://www.toptal.com/developers/gitignore)
$ touch .gitignore

$ git add .gitignore
$ git commit
conf: Create .gitignore

Settings
 - MacOS, Windows, Node, Python, vim, VS Code

$ touch fizzbuzz.py
$ vi fizzbuzz.py
print('Python works!!')

$ Python3 fizzbuzz # 정상실행여부 확인

$ git add fizzbuzz.py
$ git commit # 메시지입력
feat: Create fizzbuzz.py

$ git flow feature finish proj-init

$ git branch # develop으로 switch된걸 확인가능
$ ls -a # 작업했던 .gitignore, fizzbuzz.py 파일등이 생성된걸 확인가능

$ git push -u origin develop #첫 push이기 때문에 -u 사용

```

## 팀원역할
* 해당 organization에 들어가서 이슈등록
* 이슈란 보통 개선, 제안, 버그 리포트 등록으로 많이 사용되나 팀프로젝트에서는 본인의 해야할일을 정의하는 용도로 사용
* 타이틀: Do fizzbuzz
* 설명: for와 if를 이용해 fizzbuzz를 수행하겠습니다
* Tasks: []Do fizz, []Do buzz, []Do fizzbuzz
* Reference
* 팀장도 확인 가능: 코멘트남기기, 담당자 assign, Label등록(enhancement)

## Fork (팀원)
* 팀원본인 로컬에 사본을 만들어서 작업
* Create fork 누르기 전에 `Copy the main branch only` 체크박스 해제할 것(develop에서 작업하기 때문)
* 잘못 fork했다면 저장소에서 fork를 지우고 다시 fork 하면 됨
* repository가 팀 저장소에서 본인 저장소 아래로 생성됨(soheedev/fizzbuzz)
* 주소복사

## 팀원 로컬 세팅
* 작업방향
1. 팀프로젝트를 본인 로컬로 가져와서(fork)
2. 본인로컬에서 작업한 다음 
3. 본인저장소로 push하고
4. 본인저장소에서 pull requests를 팀프로젝트로 요청
5. 다른 팀원들의 작업내용은 팀repo의 주소를 이용해 가져온다

```
$ git clone 주소
$ cd fizzbuzz

$ git flow init #branch가 develop으로 변경되면서 팀장이 만든 fizzbuzz.py가 보임

$ git remote #remote 설정이 필요
$ git remote -v #본인 저장소를 바라보고 있음 
$ git remote add upstream 팀repo주소 #위 작업방향 5번을 위해
 
$ git remote -v #본인과 팀의 주소가 모두 보이나 upstream에 push 할 일은 없음
```

## 팀원 작업
```
$ git flow feature start fb
#동작하는 하나하나가 commit대상임

#첫번째 Tasks
$ vi fizzbuzz.py
for i in range(1, 15+1):
    if i%3 == 0:
      print("fizz")
    else:
      print(i)
$ python fizzbuzz.py #정상작동여부 확인
$ git status
$ git add fizzbuzz.py
$ git commit  #이슈 첫번째 Tasks 체크
feat: Do fizz if i is times of 3

Otherwise, Print i itself

# 두번째 Tasks 
$ vi fizzbuzz.py
for i in range(1, 15+1):
    if i%3 == 0:
      print("fizz")
    elif i%5 == 0:
      print("buzz")
    else:
      print(i)
$ python fizzbuzz.py #정상작동여부 확인
$ git status
$ git add fizzbuzz.py
$ git commit  #이슈 두번째 Tasks 체크
feat: Print buzz if i is times of 5


# 세번째 Tasks 
$ vi fizzbuzz.py
for i in range(1, 15+1):
    if i%15 == 0:
      print("fizzbuzz")
    elif i%3 == 0:
      print("fizz")
    elif i%5 == 0:
      print("buzz")
    else:
      print(i)
$ python fizzbuzz.py #정상작동여부 확인
$ git status
$ git add fizzbuzz.py
$ git commit  #이슈 세번째 Tasks 체크
feat: fizzbuzz Done

Print fizzbuzz if i is times of 15

$ git flow feature finish fb # Switched to branch 'develop'
$ git push -u origin develop #팀원으로 첫 push (-u 사용)

```

## Pull Request (팀원)
* develop은 본인뿐만 아니라 다른사람들과 함께 개발을 하고 있는 공간
* 본인develop에서 팀의 develop으로 소스반영을 해야함(pull request)
* develop 브런치에 가서 본인 저장소에서 push한 소스가 정상적으로 올라왔는지 확인
* `Compare & pull request` 버튼 눌러도 되고
* `Contribute` > `Open pull request` 눌러도 됨
* `Pull requests` > `New pull request` 눌러도 됨
* 중요: `base repository: team/fizzbuzz``base:develop` <- `head repository: member/fizzbuzz``compare:develop` 반드시 확인할 것
* 제목: Do fizzbuzz with if, for
* 내용: resolve 샾1 (번호로 팀원이 생성했던 이슈와 연결) > `create pull request` 클릭

## Code Review (팀장)
* 리뷰작성후 > `Finish your review` > `Request changes`

## 팀장의 코드리뷰 후 팀원의 추가작업(팀원)
* 바로 develop에서 수정
```
$ vi fizzbuzz.py # range 수정(20으로)
$ python fizzbuzz.py #정상작동여부 확인
$ git status
$ git add fizzbuzz.py
$ git commit  #추가요청사항 수정
fit: Edit Range 15 to 20

$ vi fizzbuzz.py # if문 줄이기
for i in range(1, 20+1):
    if i%3 == 0 or i%5 == 0:
      print('fizz'*(i%3==0) + 'buzz'*(i%5==0))
    else:
      print(i)
$ python fizzbuzz.py #정상작동여부 확인
$ git status
$ git add fizzbuzz.py
$ git commit  #추가요청사항 수정(코드결과는 동일하나 소스가 변경-> refactoring)
refactor: Do fizzbuzz with 1 if Statement

What else?

$ git push origin develop
```

## 팀장의 재코드리뷰 후 승인(팀장)
* `Viewed` 체크 > Nicely Done!!!(코멘트달기) > `Approve` 선택 > `Submit review`
* pull request처리전 팀 develop 브랜치에 변경사항없음
* `Merge pull request` > `Confirm merge` => 팀원이 작업한 내용이 간접적으로 기여가 됨(소스가 업데이트됨)

## 다른 팀원들의 (팀레포의) 해당 작업사항 fetch & merge(pull)하기
```
$ git remote
origin
upstream
```
* 위 상태에서 upstream을 참조하기1
```
$ git fetch upstream develop
$ git merge FETCH_HEAD
```
* 위 상태에서 upstream을 참조하기2
```
$ git pull upstream develop #pull: fetch & merge를 합쳐서 한번에 하는 방법
```
