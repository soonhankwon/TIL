# TIL (Today I Learned)
<details>
<summary>221017 About Branch & Naming (GIT)</summary>
<div markdown="1">
<hr/>

**Acheivement** : 항해99 WEEK5 SPRING 팀 프로젝트ING🤝 

팀원 각자의 GIT Branch에서 작업하고 Merge하는 과정을 실제로 해보았다. 

티스토리에서 하던 TIL을 GIT으로 **MOVE** & 작성해보았다. Notion에서 마크다운 Export하는 방식으로 기본 template 작성.
  
**Problem** : Team project 중 좋아요한 게시글 불러오는 기능을 구현하는데, 데이터베이스 간 일대다, 다대일, 다대다 관계가 꽤나 헷갈림🥲.
    
**Feedback** : One to One, Many to One, One to Many에 대한 심화 이해 필요 및 Service의 비즈니스 로직구현에 대한 연습필요🔥
<hr/>
  
- **Branch의 종류**
    - Main branch
    중앙 저장소에는 수명이 무한한 두 가지 메인브랜치가 있다.
    **Master, Develop** 브랜치이다.
    - Master branch
    제품으로 출시될 수 있는 브랜치
    
    사용자에게 배포 가능한 상태만을 관리한다. 여기서는 배포(release) 이력을 관리하기 위해 사용한다. 즉, 함부로 master브랜치에 Merge하게 되면 상사에게 끌려갈 수 도 있다. **항상 master 브랜치는 주의**하라!
    
    - Develop branch
    다음 출시 버전을 개발하는 브랜치
    
    기능 개발을 위한 브랜치들을 병합하기 위해 사용한다. 즉, 모든 기능이 추가되고 버그가 수정되어 배포가능한 안정적인 상태라면 develop 브랜치를 master브랜치에 merge한다. 평소에는 이 브랜치를 기반으로 개발을 진행한다.
    
    - Release branch
    이번 출시 버전을 준비하는 브랜치
    
    배포를 위한 전용브랜치를 사용함으로써 한팀이 해당 배포를 준비하는 동안 다른 팀은 다음 배포를 위한 기능 개발을 계속할 수 있다. 
    release 브랜치는 배포를 위한 최종적인 버그 수정, 문서 추가 등 배포와 직접적으로 관련된 작업을 수행한다. 이러한 작업들 이외에 새로운 기능을 추가로 merge하지 않는다. 
    
    - hotfix brance
    출시 버전에서 발생한 버그를 수정하는 브랜치
    
    배포한 버전에 긴급하게 수정을 해야 할 필요가 있을 경우, master 브랜치에서 분기하는 브랜치이다. develop 브랜치에서 문제가 되는 부분을 수정하여 배포 가능한 버전을 만들기에는 시간도 많이 소요되고 안정성을 보장하기도 어려우므로 바로 배포가 가능한 master 브랜치에서 직접 브랜치를 만들어 필요한 부분만 수정한 후 다시 master 브랜치에 병합하여 이를 배포하는 것이다.
    
    **Branch 네이밍 규칙**
    
    어떤 방식으로 브랜치의 이름을 정하는지 브랜치 종류에 따라 살펴보자.
    
    **1) master branch, develop branch**
    
    master와 develop 브랜치는 본래 이름 그대로 사용하는 경우가 일반적이다.
    
    **2) feature branch**
    
    - 어떤 이름도 가능하다. 단, `master`, `develop`, `release-...`, `hotfix-...` 같은 이름은 사용할 수 없다.
    - `feature/기능요약` 형식을 추천한다. ex) feature/login
    - `feature/{issue-number}-{feature-name}` 이슈추적을 사용한다면 이와 같은 형식을 따른다.ex) feature/1-init-project, feature/2-build-gradle-script-write
    
    **3) release branch**
    
    - `release-RB_...` 또는 `release-...` 또는 `release/...`같은 이름이 일반적이다.
    - `release-...` 형식을 추천한다. ex) release-1.2
    
    **4) hotfix branch**
    
    - `hotfix-...` 형식을 추천한다. ex) hotfix-1.2.1
    
    - `hotfix-...` 형식을 추천한다. ex) hotfix-1.2.1
    
   
    </div>
</details>
