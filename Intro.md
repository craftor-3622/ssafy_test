## 0) Markdown 파일에 대하여

개발자들이 텍스트와 코드를 작성해 문서화하기 위하여 사용한다.   
MD 파일 작성 관련 문법은 아래 주소 참조. <br><br>


[Markdown 홈페이지](https://www.markdownguide.org/basic-syntax/)

[나무위키 Markdown](https://namu.wiki/w/마크다운)

## 1) Git 사용하기 (VS code)

git(분산 버전 관리 시스템) 사용하기 - 작업 변경 사항 작업 및 저장, 공유하는 데 최적화되어 있다. <br><br>

- cmd 문법
    - .  : 현재 디렉토리
    - .. : 현재의 상위 디렉토리
    - touch : 파일 생성
    - mkdir : 디렉토리(폴더) 생성
    - ls : 현재 작업 중인 디렉토리 내부 폴더 파일 목록 출력
    - cd : 해당 디렉토리로 이동
    - start : 폴더/파일 열기
    - rm : 파일 삭제(디렉토리는 -r을 추가로 사용)
<br>
<br>

- git 동작
    - git init : 현재 디렉토리를 기준으로 local 저장소 설정
    - git add : 변경 사항이 있는 파일을 staging area(중간 준비 영역)에 추가
    - git commit -m “변경 제목” : staging area 내 파일을 저장소 기록, 변경 이력 등록
<br>
<br>
    
- git 사용 방법
    1. 디렉토리를 생성 후, local 저장소 설정(git init)
    2. 코드 변경 이후, git add를 통해 변경 사항 등록 (-A로 변경 사항을 모두 등록할 수 있다.)
    3. 이후 git commit을 통해 변경 사항을 확정한다.

## 2) Hello! GitHub

GitHub에 가입 후 git remote origin (remote url) 을 활용해 원격 저장소를 추가한다.

- git push origin master : 원격 저장소에 commit 목록을 업로드한다.
    
    주의할 점 - commit 목록의 변경된 파일이 원격 저장소와 다르면 error가 나는 것에 유의.
    
    commit 목록에 변경 사항이 없다면 push도 되지 않는다. (up-to-date)
    
- git pull origin master : 원격 저장소에서 변경 사항을 local로 다운로드

- git clone (remote_url) : 원격 저장소 전체를 복제 (다른 사람 소유의 것도 가능!)

- .gitignore : Git에서 특정 파일/디렉토리를 추적하지 않도록 설정하는데 사용한다.
    
    사용법 - .gitignore 파일에 공유하고 싶지 않은 파일 이름을 등록하면 된다.
    
<br>

어디에 활용할까?

개인 - 학습 및 개발자 포트폴리오로 활용하며, commit 빈도수로 기여도 및 활동을 파악 가능 

집단 - 프로젝트 협업에 활용하며, 오픈 소스 프로젝트에서도 사용할 수 있다.