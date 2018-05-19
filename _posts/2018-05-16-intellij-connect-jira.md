---
layout: post
title: "IntelliJ에서 Jira 티켓 관리하기"
categories: dev
author: josh
meta: "Springfield"
---


1. Task Management Plugin 확인
    1. Preference -> Plugins에서 Task Management 검색 후 체크 확인, 없다면 설치

       **체크가 되어있지 않다면 Task 관련 기능을 사용할 수 없다**

2. IntelliJ에서 Jira 연동
    1. Preferences -> Tools -> Tasks -> Servers로 이동

       Ctrl + N 또는 +버튼 클릭 후 Jira 선택

       ![1](https://user-images.githubusercontent.com/37292134/40098497-b29b788a-5916-11e8-9e76-6f8008460ca7.png)

    2. General 탭에서 해당 Jira의 정보를 입력한다.

       Server URL : 티켓을 관리 사이트 URL

       Username : Jira 사용자 이름

       Password : Jira 사용자 비밀번호

       Search : assignee = currentUser() and resolution = Unresolved order by updated

       **(Search의 정보는 기본적으로 위의 값으로 입력되어 있으나 없을 경우 입력)**

       이후 Test 버튼을 클릭하여 Connection 확인
       ![1](https://user-images.githubusercontent.com/37292134/40098838-71af37d8-5918-11e8-9e4f-12a2159912b3.png)

    3. Connection is successful 확인 후 OK 버튼 클릭2

       ![2](https://user-images.githubusercontent.com/37292134/40098900-b49034b2-5918-11e8-8179-93dd749d65b3.png)

3. 업무 플로우 확인
    1. Jira Ticket을 생성

       IntelliJ Task 기능은(2018.1.3 기준) 티켓 생성은 지원하지 않기에 Jira 사이트에서 직접 생성해야 한다.

       <img width="1438" alt="3" src="https://user-images.githubusercontent.com/37292134/40099192-f6d63154-5919-11e8-88ab-b52cf6eb83ea.png">

    2. IntelliJ IDE에서 Tools -> Tasks&Contents -> Open Task를 선택 후 해당 티켓 ID를 검색

       ![2018-05-16 3 03 10](https://user-images.githubusercontent.com/37292134/40099270-47f87826-591a-11e8-8d4e-7e972a176f8d.png)

       아래의 팝업이 생성된다.

       ![2018-05-16 3 04 30](https://user-images.githubusercontent.com/37292134/40099314-76e2aa12-591a-11e8-82ea-4ca878edd5d4.png)

       Create changelist는 티켓ID + 이슈 요약으로, branch 이름은 티켓 ID로 자동 설정된다.

       새 branch를 이용하고 싶으면 이 설정을 유지하고 기존 branch를 이용하고픈 경우

       Create branch의 체크를 해지 후, Use branch에서 원하는 branch를 선택 후 체크를 선택한다.

       Update issue state를 In Progress를 선택하고 체크 후 OK버튼을 클릭한다.

       Jira 사이트에서도 확인 가능하다.

       <img width="1427" alt="2018-05-16 3 06 40" src="https://user-images.githubusercontent.com/37292134/40099507-4a674226-591b-11e8-92a5-d66571fd2012.png">

    3. 개발이 완료될 경우 변경사항을 commit한다

       VCS -> commit을 선택하면 아래와 같은 팝업이 생성된다.

       ![2018-05-16 3 13 18](https://user-images.githubusercontent.com/37292134/40099737-3b12b020-591c-11e8-87a2-52ffc2c6127a.png)

       기본적으로 Commit Message는 티켓ID + 이슈 요약으로 생성된다.

    4. 해당 티켓의 Task가 완료되면 Tools -> Tasks&Contents -> Close Active Task... 를 선택하여 이슈를 Done 상태로 변경한다.

       Jira 사이트에서도 확인가능하다.
       ![2018-05-16 3 19 01](https://user-images.githubusercontent.com/37292134/40099795-8043bcde-591c-11e8-859a-3edbadee2b18.png)
       <img width="1437" alt="2018-05-16 3 19 53" src="https://user-images.githubusercontent.com/37292134/40099882-d910cb0e-591c-11e8-9870-8cc947148669.png">

4. 추가 설정
    1. Preferences -> Tasks 에서 브렌치명 설정을 변경할 수 있다.

    ![2018-05-16 3 24 40](https://user-images.githubusercontent.com/37292134/40100006-5d9a477e-591d-11e8-86a3-a93890b0fdb3.png)

    2. Preferences -> Tools -> Tasks -> Servers에서 Commit Message에서 커밋 시 메시지 규칙을 설정할 수 있다.

    ![2018-05-16 3 26 47](https://user-images.githubusercontent.com/37292134/40100088-ae5eb974-591d-11e8-8591-85d9b82cce52.png)
