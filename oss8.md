# 8 병합과 충돌
### 1. 병합
> 브랜치 생성 목적 : 원본 코드에 영향을 주지 않고 **분리 개발**을 위해 

**병합** : 분리된 브랜치를 한 브랜치로 합치는 작업

깃의 브랜치 사용 : 자동 병합이 가능

<br>

#### 1. 하나씩 직접 비교하는 수동 병합

<img src="https://user-images.githubusercontent.com/107173046/200468936-63733e29-f388-48a6-97f8-46a3fb624125.png" width="300">

<br>

#### 2. 깃으로 자동 병합

1. 깃의 병합은 **브랜치**를 기준으로 함 <br>
2. 분리된 각각의 브랜치에서 수정된 사항을 하나의 브랜치로 병합. 이때 병합하고자 하는 브랜치는 **같은 로컬 저장소**에 있어야 함. <br>
3. 모든 코드의 병합을 완벽 처리하기 힘들다. 아무리 좋은 도구라 해도 자동으로 반영하지 못하는 것이 있는데 이것을 **충돌**이라 함.

<br>

#### 3. 병합 방식

깃은 브랜치를 기반으로 실행. 브랜치를 비교하여 자동 병합하는 형태. 병합을 위해 브랜치를 만들어 브랜치 안에서 수정 작업을 해야 함. **충돌 없이 병합**을 하려면 두 방식의 차이를 알아야 함.

1. Fast-Forward
2. 3-way

<br>

#### 4. 실습 셋팅

1. 별도 저장소 생성

<img src="https://user-images.githubusercontent.com/107173046/200469589-6a2ed774-e4d3-42d2-88c8-8c911b047a65.png" width="500">

2. index.html 파일을 만들어 코드 입력

<img src="https://user-images.githubusercontent.com/107173046/200469597-e016b8e6-02e5-4040-aecc-a4d8e96a3642.png" width="500">

3. 파일 등록, 첫 번째 커밋

<img src="https://user-images.githubusercontent.com/107173046/200469621-90e67804-e3c7-4de0-b208-f51b9a104fc4.png" width="500">

병합을 위해 모든 브랜치가 단일 저장소에 있어야 함. **같은 저장소의 브랜치를 병합**할 수 있다는 점 잊지 말기

<br>

---

### 2.Fast-Forward 병합

깃의 가장 간단한 브랜치 병합 방식. 혼자 개발할 때 사용. 

**순차적으로 커밋에 맞추어 병합을 처리하는 방식**

#### 1. 브랜치 생성과 수정 작업

1. feature 브랜치 생성, 체크아웃
<img src="https://user-images.githubusercontent.com/107173046/200470920-88617c19-1306-4246-b23f-e97fa18e4a0a.png" width="500">

2. 포인터를 확인할 수 있는 rev-parse 명령어로 확인

<img src="https://user-images.githubusercontent.com/107173046/200470930-e77bb903-a1f8-45e3-b656-1149940ebf45.png" width="500">

3. 소스트리에서 생성된 브랜치 확인 (feature 브랜치와 main 브랜치의 시작 위치가 동일한 것을 확인, html 파일 수정)

<img src="https://user-images.githubusercontent.com/107173046/200470950-4d7c6966-269c-4cc8-b688-d3779b2043d4.png" width="500">

4. 코드에 태그 삽입

<img src="https://user-images.githubusercontent.com/107173046/200470961-5e1055c4-f651-4afc-8130-224bb8372c71.png" width="500">

5. 수정 파일 커밋 (소스트리에 커밋이 하나 더 있는 것을 볼 수 있음)

<img src="https://user-images.githubusercontent.com/107173046/200470975-2eb34ae8-335a-44a5-b977-adbd740f602e.png" width="500">

6. 태그 추가, 두 번 커밋

<img src="https://user-images.githubusercontent.com/107173046/200470985-d98342b0-2a84-45f8-a48a-1075c050d654.png" width="500">

<img src="https://user-images.githubusercontent.com/107173046/200470999-ad740dd9-9309-4b17-86e8-bfb608de3561.png" width="500">

<img src="https://user-images.githubusercontent.com/107173046/200471010-af292ef0-48f4-4c4a-a66a-ecdbd48b5767.png" width="500">

7. html 수정 2

<img src="https://user-images.githubusercontent.com/107173046/200471021-d19aae61-40da-47be-b23f-1081882c3812.png" width="500">

<img src="https://user-images.githubusercontent.com/107173046/200471029-f640e149-cdc5-4d4b-b0c7-c71cdeb953c3.png" width="500">

<img src="https://user-images.githubusercontent.com/107173046/200471040-7d7cc91e-ae4e-4615-9f35-49d4bd816a13.png" width="500">

8. feature 브랜치에 추가된 커밋 로그 확인

<img src="https://user-images.githubusercontent.com/107173046/200471050-ca0c505d-5ef3-4275-9dcd-9fcfe98de6bf.png" width="500">

9. 소스트리에서 커밋 로그 확인

<img src="https://user-images.githubusercontent.com/107173046/200471064-f0b3b344-2e3b-4a41-85f7-f60719980ee1.png" width="500">

> 브랜치를 만들어 feature 브랜치에 기능을 추가함. 하지만 소스트리에서 브랜치 **경로가 일직선으로 1개**만 있음. 서로 다른 브랜치이지만 **순차적으로 커밋**을 했기 때문에 일직선으로 보임. 이러한 모양의 브랜치 병합을 작업할 때는 Fast-Forward 방식의 알고리즘이 적용

#### 2. 병합 위치

> marge 명령어 : 브랜치를 **병합**함. 현재 브랜치를 기준으로 다른 브랜치의 모든 커밋을 병합.

<img src="https://user-images.githubusercontent.com/107173046/200472230-244f9290-e8bb-4503-8b3c-bd21ae9ef88b.png" width="500">

브랜치를 병합하려면 **기준**과 **대상**이 있어야 함. 기준이 되는 브랜치로 이동해야 됨 

**기준** : 체크아웃 된 현재 브랜치

<img src="https://user-images.githubusercontent.com/107173046/200472448-97fbb0d0-afca-41ba-ab6e-7de49fadfd76.png" width="500">

main 브랜치로 이동 후 파일 확인 시 feature 브랜치에서 작업한 내용이 사라짐.

<img src="https://user-images.githubusercontent.com/107173046/200472465-4aae24f3-aadc-4cc0-95bb-902da1f37e58.png" width="500">


#### 3. Fast-Forward 병합 적용

1. main 브랜치에 추가된 커밋이 없는 상태에서 두 브랜치를 병합
2. 메시지 확인 > Fast-Forward 방식을 사용하여 병합했다고 출력

<img src="https://user-images.githubusercontent.com/107173046/200472802-84251c70-2f1a-42c0-a327-8e9bcd1716ff.png" width="500">

3. 소스트리에서 병합 결과를 확인하려면 main 브랜치의 마지막 커밋 위치와 feature 브랜치의 마지막 커밋 위치가 같기 때문에 동일한 HEAD 포인터를 갖게 되는 것을 알 수 있음

<img src="https://user-images.githubusercontent.com/107173046/200472975-7dd0b964-0f15-4a87-96f6-691ee254d2fb.png" width="500">

4. 작업한 브랜치를 원본 브랜치에 병합할 때 작업한 브랜치의 시작 커밋을 원본 브랜치 이후의 커밋으로 가리킴

<img src="https://user-images.githubusercontent.com/107173046/200473008-7fd2af1f-78ca-4821-b4fc-94d44c500594.png" width="500">

5. main 브랜치의 index.htm 파일을 확인하여 병합이 잘 됐는지 확인.

<img src="https://user-images.githubusercontent.com/107173046/200473051-ba4b1c0d-20c2-475c-99c6-ef3a8b0a5084.png" width="500">

---

### 3. 3-way 병합

**3-way** : 복잡한 병합을 처리할 수 있는 방법

#### 1. 브랜치 생성과 수정 작업

1. 새로운 작업을 할 hotfix 브랜치를 생성, 체크아웃. 소스 코드에 <footer>태그를 추가하고 저장
  
<img src="https://user-images.githubusercontent.com/107173046/200473756-78ef58eb-50b5-42b4-a22b-ff558ae3a1d3.png" width="500">

2. 수정한 파일을 다시 스테이지에 등록한 후 커밋
  
<img src="https://user-images.githubusercontent.com/107173046/200473820-63fc2ed6-782c-446b-8ca7-a54d99f55b15.png" width="500">

3. 다시 <footer> 파일에 내용을 추가한 후 커밋.
  
<img src="https://user-images.githubusercontent.com/107173046/200473892-600a80bc-5eb6-4039-8834-195fa0b77792.png" width="500">

4. 이 과정을 그림으로 나타냄
  
<img src="https://user-images.githubusercontent.com/107173046/200473927-fa6fbf8e-b6bd-409d-885e-2bb873f0c47d.png" width="500">

5. 커밋 로그 기록을 확인하여 hotfix 브랜치에 새로운 커밋이 2개 추가된 것을 확인할 수 있음. 

<img src="https://user-images.githubusercontent.com/107173046/200473955-a81f958d-4a98-482c-9aad-705bfbd2fcb4.png" width="500">
  
#### 2. 마스터 변경
 
1. 브랜치 모양 변경하기 (master 브랜치에도 새로운 커밋을 추가해 실습 진행)
2. hotfix 브랜치에서 master 브랜치로 이동
  
<img src="https://user-images.githubusercontent.com/107173046/200478333-1ecd2405-40d8-4e32-89ea-bf8657d8794a.png" width="500">

  
3. 시간적으로 더 앞 단계인 master 브랜치에 새로운 커밋을 추가
  
<img src="https://user-images.githubusercontent.com/107173046/200478347-3d83493a-b512-4259-88d1-40847ab45d6f.png" width="500">

<img src="https://user-images.githubusercontent.com/107173046/200478359-2de27d50-e3dc-46fb-881d-01206449c9c1.png" width="500">

  
4. master 브랜치에 등록 및 커밋
  
<img src="https://user-images.githubusercontent.com/107173046/200478370-3279995a-d1df-4f1e-abf9-029847bf8c1e.png" width="500">

  
5. 소스트리에서 그래프 확인
  
<img src="https://user-images.githubusercontent.com/107173046/200478385-3a7d5b05-c87f-40a6-8e45-f0de60f6aa1b.png" width="500">

  
#### 3. 공통 조상  
 
브랜치 모양이 갈라지는 형태로 나뉠 때에는 Fast-Forward 방식의 알고리즘으로 병합할 수 없음.
 
1. 두 커밋의 기준 커밋. 즉, 조상 커밋을 찾아야 함.
2. 공통 조상 커밋을 포함하는 브랜치와 새로운 두 브랜치, 이렇게 3개를 하나로 병합해야 하기 때문에 브랜치가 3개가 있다고 해서 3-way 병합이라고 함.
  
<img src="https://user-images.githubusercontent.com/107173046/200479139-05c6c014-7d8d-464b-b031-2f77cdf3fa35.png" width="500">

  
#### 4. 병합 커밋 

병합은 각 브랜치에서 독립적으로 작업된 소스를 파일 하나로 결합하지만, 브랜치별로 각각 작업한 내용을 병합하는 과정은 어려움.
  
3-way 병합은 두 브랜치에서 공통 조상 커밋을 자동으로 찾아주고, 공통 조상 커밋을 기준으로 브랜치 병합을 하고난 뒤 병합을 성공적으로 완료한 후에는 새로운 커밋을 추가로 하나 생성.
  
  
#### 5. 병합 메시지
  
1. 3-way 병합은 Fast-Forward와 달리 병합 메시지가 필요
2. “Merge branch ‘hotfix’”라고 커밋 메시지가 자동 삽입. 
3. 깃은 두 브랜치를 병합한 후 새로운 커밋과 동시에 메시지를 자동 생성함. Merge 명령어를 실행할 때 -e 또는 –-edit 옵션을 사용하면 됨.   
  
<img src="https://user-images.githubusercontent.com/107173046/200479281-005df00e-eb2d-4c9f-a611-cf4155809480.png" width="500">
  
<img src="https://user-images.githubusercontent.com/107173046/200479292-07e25258-1bb7-4dd4-8992-738b9f149ddb.png" width="500">

  
---

### 4. 브랜치 삭제
  
일반적으로 병합한 이후, 병합된 브랜치는 삭제됨.
  
#### 1. 병합 후 삭제
  
병합된 브랜치 커밋은 원본 브랜치에 적용되기 때문에 중복되는 브랜치는 branch -d 명령어 사용
  
<img src="https://user-images.githubusercontent.com/107173046/200474414-55b74708-1c0b-4e9d-9a73-2e09fa5ae9ae.png" width="500">
  
**-d** 옵션 : 병합을 완료한 브랜치만 삭제할 수 있음  

<img src="https://user-images.githubusercontent.com/107173046/200474449-2a3079de-370f-48a3-8ff9-6687b2ae49b3.png" width="500">
  
