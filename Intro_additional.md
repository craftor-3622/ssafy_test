## 1) 추가 Git 개념

### **commit 수정**

실제 현업에서는 실수가 자주 나오며 교정 과정에서 commit을 새로 덮어쓰면 된다. ssafy 과정에서는 프로젝트 단계에서 사용하다가 혼란을 빚을 수 있어 사용을 권장하지 않는다. 현업에서는 하술할 Git Flow를 통해 commit 수정 문제 자체를 최대한 방지한다.

- **git commit --amend**
    
    commit의 내용을 수정하는 명령어다.
    
- **git revert**
    
    특정 commit을 없던 일로 만드는 명령어이다. 정확히는 commit 삭제 작업에 대한 commit을 만드는 과정이다.
    
    (즉, 기록 무결성을 위해 commit 기록 상에는 남아있다.)
    
- **git reset [옵션]**
    
    특정 commit의 상태로 돌아간다. 가끔씩 쓰기는 하나, 코드 충돌 및 문제가 발생했을 때 사용하는 방법이다. (애초에 문제를 만들지 않도록 하는 것이 가장 중요하다.)
    
    옵션 별 동작은 다음과 같다.
    
    - -soft : 삭제된 commit을 staging area에 남긴다.
    - -mixed : 삭제된 commit을 working directory에 남긴다. (기본 옵션)
    - -hard : 삭제된 commit의 기록을 남기지 않는다.

- **git restore <파일명>**
    
    Staging Area에 올라와 있는 작업 내용을 취소한다. 말 그대로 작업 내용이 사라지기 때문에 복구할 수 없다. 아래 옵션을 추가해서 쓰거나, 후술할 git stash 명령어를 사용한다.
    
    - 옵션 --staged : Staging Area의 내용을 Working Directory로 복구한다.

- **git stash <파일명>**
    
    Staging Area에 올라와 있는 작업 내용을 창고(stash)로 돌려보낸다. git restore와 유사하나, 작업한 내용을 삭제하는 대신 임시 저장공간으로 보낸다. 해당 명령어를 통해 다시 사용하고자 하는 코드를 stash에서 꺼내와 쓸 수 있다.
    
    관련 명령어는 다음과 같다.
    
    - git stash list : 창고에서 이전에 작업한 내용을 리스트로 출력한다.
    - git stash pop : 창고에 저장된 stash의 내용이 다시 Working Directory와 Staging Area로 올라간다. 이 때 창고에 저장된 내용은 사라진다.

<br>

### **협업 관련**

해당 내용은 학습을 위해 잘 사용하지 않는다. 다만 그룹 스터디를 통해 코드를 공유하고 교정하거나, 실제 현업에서는 분기 및 하술할 내용을 통해 자주 사용하니 개념 정도는 알고 가는 것이 좋다.

- **Git Branch <새 branch 이름>**
    
    repository에 있는 내용에서 새로 분기하여 사용하는 독립적인 작업 공간이다. Repository 내에서 작동한다.
    

- **Git merge <병합할 Branch>**
    
    병합할 Branch를 현재 작업 중인 Branch와 병합한다. 추가 사항 및 수정 사항 등이 동시에 적용된다.
    
    - **Git Conflict**
        
        병합 도중 같은 파일의 같은 내용을 둘 다 수정한 경우 발생한다. 이 때 둘 사이에 서로 상의하여 어떤 코드를 사용할 지 의논해 병합한다. 병합하기 전, git merge --abort 명령어를 이용해 병합을 취소할 수도 있다.
        

- **Git Flow**
    
    현업에서는 Branch를 이용해 작업 및 실행 공간을 나누고 작업하는 한편, 협업 중의 코드 충돌을 방지하고 실전에서 활용하는 프로그램 운영에 방해가 되지 않도록 아래의 그림을 활용한다.
    
    ![Git Flow](https://nvie.com/img/git-model@2x.png)
    
    - Master
        
        정식 배포되는 소스 코드이다. 안정성이 높은 검증된 코드만이 올라오며, Tag(version)이 붙어있다.
        
    - Feature
        
        새로운 기능 개발 또는 버그 수정을 위한 일련의 코드 수정이 이루어지는 Branch다. 개발자 혼자 또는 여러 명이 공동 작업하는 공간이다.
        
    - Develop (dev)
        
        Feature에서 추가 또는 수정된 코드를 PR 요청하는 공간이다. 이 공간에서 또 다른 리뷰어가 기능 및 수정 사항을 검토한다.
        
    - Release
        
        Develop을 기반으로 하여 배포할 기능셋 및 버그픽스를 병합한 Branch다. 해당 병합 과정에서 발생한 버그 및 수정 사항들이 다음 Branch에 적용되며, 안정성이 확정되면 Master Branch에 병합되거나, 수정 사항은 Develop으로 다시 반영된다.
        
    - Hotfix
        
        Master에서 발생한 버그를 긴급하게 수정해야 할 때 활용한다. 긴급 패치 사항은 Master Branch 또는 이후 Develop Branch에 병합된다.

## 2) 기타 IT 용어

- Chat GPT(Generative Pre-trained Transformer)
- UI/UX
- Client / Server
- API(Application Programming Interface) & API Key
    
    두 소프트웨어/시스템이 서로 통신할 수 있게, 특정 규칙에 따라 데이터를 요청하고 응답하는 매커니즘. Json 또는 Xml 파일로 나타낸다.
    
    → 해당 API에 접근하기 위하여 데이터베이스를 담당하는 기업에서 Key를 제공한다. **해당 키는 비공개 키이며, 절대로 타인에게 보여주거나 노출해서는 안된다!**
    
- 프롬프트 엔지니어링 (feat. GPT OpenAI API)
    - 페르소나
    - 명시적 지시
    - Few-shot
    - 생각의 사슬
    - 자기 일관성
    - 생각의 나무, 사고 구조도
    - 인터넷 검색 기반 응답