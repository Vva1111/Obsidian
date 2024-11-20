##### Tip.
1. gitignore 내부에 ignore할 목록들은 이미 추적되고 있는 파일들에 대해서 적용되지 않는다. gitignore에 새로운 규칙을 추가해도 이미 추적하고 있는 파일들은 그대로 남아있기 때문에 계속 추적되고, 업데이트 된다.
2. 1은 pull 명령어에도 동일하게 적용된다.
3. git config --list의 credential 항목은 Git에서 사용하는 인증 정보에 관련된 설정을 나타낸다.
	 원격 저장소와의 통신에는 매번 사용자 인증 정보가 필요한데, 이를 기억하게 하기 위한 기능이다.
	 - Credential.helper : Git이 인증 정보를 어떻게 저장하고 찾을지 결정
		 - store : 인증 정보를 평문으로 파일에 저장, git-credentials 파일
		 - cache : 인증 정보를 일정 시간 동안 메모리에 저장
4.  이전 커밋을 되돌리거나 하는 상황 이후에 다시 pull을 받았을 때, 변경사항이 이전의 커밋에서 변경되지 않을때는 브랜치를 삭제한 후 새로 브랜치를 받고 pull을 받아 변경사항을 적용해야 한다. 해당 로컬 브랜치와 원격 브랜트는 서로 다른커밋을 가지고 있기 때문
5. 
##### 명령어
- **Git 초기 설정에 필요한 명령어**
	1. git config
		- git config --list : 현재 Git 설정 정보 확인
		- git config (--global) user.name(user.email) : 로컬(혹은 글로벌) 이름(이메일) 설정
		- 
	2. git remote
		- git remote add origin https://git~~~~~ : 현재 로컬의 원격 저장소를 설정
		- git remote set-url https://git~~~~~ : 현재 설정된 원격 저장소를 변경
		- git remote remove origin : 현재 설정된 원격 저장소를 삭제

- git rm --cached {file} : Tip. 1의 경우에서 로컬 파일은 그대로 남겨두고 추적만 중지하는 명령어

###### **upstream**
- 업스트림 브랜치는 로컬 브랜치가 추적하는 원격 브랜치를 의미한다.
- 업스트림 설정 이후에는 git push/pull 명령의 경우 자동으로 해당 원격 브랜치와 상호 작용한다.
- 업스트림 브랜치를 해제하면 git pull/push 명령어를 사용할 때 기본적으로 어떤 브랜치와 상호작용할지 git이 알 수 없다.

- **명령어**
	- **git branch -vv** : 현재 upstream 확인
	- **git branch --set-upstream-to origin/{remote branch name}**
	- **git push --set-upstream origin {remote branch name}**
		- 업스트림 브랜치 설정 명령어 
		- git branch~ 명령어는 기존 브랜치에 업스트림을 설정할 때 사용
		- git push~ 명령어는 해로운 브랜치를 푸시하면서 업스트림을 같이 설정할 경우 사용
	- **git branch --unset-upstream**
		- 현재 체크아웃한 브랜치의 업스트림 브랜치를 설정 해제하는데 사용

###### **브랜치 삭제**
- git branch -d {브랜치 이름} : 브랜치 삭제
- git push origin --delete {브랜치 이름} : 원격 저장소 브랜치 삭제

###### **push**
- git push --force origin main : 원격 main 브랜치에 강제 push
###### **stash**
- **\*stash 된 내역은 브랜치와 상관 없이 전역에 존재한다**
- git stash show -p stash@{0} : stash 된 내용 보기
- git stash list : stash 되어 있는 목록 보기
- git stash pop : stash 된 모든 사항을 디렉토리로 복구한 뒤 stash 내역 삭제
	- git stash pop stash@{0/1/2/3~}
- git stash apply : stash 된 모든 사항을 디렉토리로 복구하고 stash 된 내역은 삭제되지 않는다.
	- git stash apply stash@{0/1/2/3~}

###### **git status** : 현재 stage할 내용이 있는지 확인

###### **git diff** 
- 수정된 파일들의 변경사항을 자세히 보여준다. 아직 스테이징 되지 않은 변경사항을 보여준다.
- **git diff --staged(--cached)** : 스테이징 된 변경사항과 마지막 커밋 사이의 차이를 보여준다.

###### **git log**
- 커밋 히스토리를 보여준다.
- **git log -p** : 각 커밋에서 변경된 내용을 보여준다.
- **git log --stat** : 각 커밋에서 변경된 파일의 목록과 각 파일에서 추가/삭제된 줄의 수를 보여준다.
- **git log --oneline --graph** : 깃 로그를 그림으로 보여준다

**git show {커밋 아이디}** : 특정 커밋의 상세한 변경 사항을 보여준다 .

**git checkout -b v1.0.3-v6419 origin/v1.0.3** : origin의 v1.0.3 브랜치를 바라보는 로컬 v1.0.3-v6419 브랜치를 생성하고, 해당 브랜치로 이동
