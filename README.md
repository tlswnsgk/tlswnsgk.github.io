# tlswnsgk.github.io
신준하의 개발일지 
2년차 개발자의 업무, 자기계발을 기록하는 블로그.

---
## * 기술스택
```
  *Java 8
  *Spring
  *Rest API
  *AWS
  *JSP
  *SQLD(sql 개발자 자격증)
   
  *mariaDB
  *JavaScript
  *Ajax
  *Git
```
---

*2022.08 - 국비과정 시작.

*2023.01 - (주)데이타이음 입사 교육계 기반의 it 솔루션,si 회사.

*2023.06 - 경**도 교육청 미래**원 체험누리집 프로젝트(온라인 교육, 오프라인 체험, 숙박 시설 예약) 시작,
           sqld 자격증 취득,
           프로젝트 오픈, 운영 및 고도화 진행 중.
           
*2023.10 - 충**도 교육청 다*움 프로젝트(학교 수업 교과서, 과제를 온라인으로 수행하는 프로젝트) 시작,
           프로젝트 오픈, 운영 및 고도화 진행 중.

*2024.03 - 건국사이버평생교육원 학점은행제 시작
           컴퓨터공학 학사 학위 취득을 목표
           

시간대 별로, 이벤트 별로 추가적으로 블로그를 작성해보려고 합니다.

# tlswnsgk.github.io
#Spring - Activity 
Activity 프로젝트는 체험 제공 서비스 웹 서비스입니다.
host가 제공해주는 체험을 참여하고 일반 서비스 이용 고객도 host가 되어 체험을 제공 할 수 있는 양방향 플랫폼입니다.

---
## * 기술스택
```
  *Java
  *Spring
  *Spring Security
  *Rest API
  *AWS 
  
  *mariaDB
  *JavaScript
  *Ajax
  *HTML/CSS
  *BootStrap
  *GitHub(프로젝트 협업)
```
---

*기능적 요구사항

1. 사용자는 회원가입을 하고 이를 통해 로그인을 할 수 있다.

2.로그인 후에는 해당 회원의 정보를 토대로 마이페이지 기능을 이용할 수 있다.

3.마이페이지에서는 사용자의 포로필을 수정할 수 있다. 프로필 수정 시 회원정보 및  프로필 사진 수정이 가능하다.

4.사용자가 예약한 체험의 목록을 볼 수 있으며, 호스트와의 채팅이 가능하다

5.메인화면에서는 체험 서비스들이 제공되며, 날짜 및 인원을 설정하여 예약이 가능하다.

6.체험 이용 고객은 host 신청 후 관리자의 승인 하에 체험을 제공할 수 있다.

7.host 승인 완료된 후 체험 게시글을 올리면 관지라의 적합 판정 후 체험 게시글이 업로드 된다.

8.고객센터(Qna 게시판)을 통하여 문의를 하면 관리자가 답변을 할 수 있다.

9.관리자로 로그인하면 처리해야 할 업무 리스트가 뜨며 고객센터 답변여부로 조회 가능하고, host 승인여부, 체험 승인여부로 조회가 가능하다.

---
## Project planning
  * 프로젝트 진행과정 : 35일
---


---
#Data Base Design

+DB ERD
![ErdCloud](https://user-images.githubusercontent.com/110441845/210218731-d7f2ffd3-5989-48ca-9791-98d1c7f5f222.JPG)
---

## LayOut Design
```
1.메인화면
```
![main](https://user-images.githubusercontent.com/110441845/210218998-b7648e20-a171-47cd-8e4b-540b4d1e8309.JPG)
![체험 게시글](https://user-images.githubusercontent.com/110441845/210219080-b8d473ad-2110-4fbe-bf39-907ab17b40ba.JPG)
![마이페이지](https://user-images.githubusercontent.com/110441845/210219090-05d52d2a-f126-4df0-b041-3fa8dc9ae05b.JPG)
![예약내역](https://user-images.githubusercontent.com/110441845/210219092-19dc4566-0997-4a0e-b6ac-761676b1090b.JPG)
```
2.결제 페이지
```
![결제페이지](https://user-images.githubusercontent.com/110441845/210219239-dd0a1c0a-6793-47b5-95bf-1e8870bbe4bf.JPG)
![결제페이지2](https://user-images.githubusercontent.com/110441845/210219243-73c454be-37ca-4acb-9238-b719da8af81c.JPG)
```
3.고객센터 
```
![qnaGet](https://user-images.githubusercontent.com/110441845/210219322-cfcec1ec-03ae-471c-a172-59381856a275.JPG)
![qnaList](https://user-images.githubusercontent.com/110441845/210219327-e45c3f8b-77e7-4346-960f-2565e64f816c.JPG)
![qnamodify](https://user-images.githubusercontent.com/110441845/210219331-b700fe2e-bf91-457b-991f-9076111f3f75.JPG)
![qnaRegister](https://user-images.githubusercontent.com/110441845/210219346-123aca52-aa8b-47b9-9eb9-fc468cc6c159.JPG)

```
4.호스트 페이지
```
![호스트페이지](https://user-images.githubusercontent.com/110441845/210219727-43a17fd7-0fbb-4ddc-9a2e-3dbfc090a6a2.JPG)
![체험 등록](https://user-images.githubusercontent.com/110441845/210219732-e771156f-ab16-4466-8618-6e6169f2b7fe.JPG)

```
5.admin이 아니면 접근 불가
```
![not admin](https://user-images.githubusercontent.com/110441845/210219752-05eee830-29fa-4c0c-a213-58d0f199d73f.JPG)
![not admin2](https://user-images.githubusercontent.com/110441845/210219764-594de060-19ab-4819-a400-af0c68f03068.JPG)



























