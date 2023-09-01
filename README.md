# LiveChatDjango
Django와 Channels를 활용하여 구축한 실시간 채팅 어플리케이션입니다.
# 프로젝트 일정 관리
https://www.notion.so/sungbinlee/e177dd0169e24b34826149a405e5a21d?pvs=4 
# ERD
![1-1](https://github.com/ESTsoft-Ormi-1/LiveChatDjango/assets/52542229/b2190861-6e89-4809-9d19-7e7d442b98e2)
# 시작하기
1. 이 레포지토리를 복사합니다.
```
git clone https://github.com/ESTsoft-Ormi-1/LiveChatDjango
```
2. 복사한 폴더로 들어가기
```
cd LiveChatDjango
```
3. 가상환경 생성
```
python -m venv venv
source venv/bin/activate  # Windows에서는 "venv\Scripts\activate" 실행
pip install -r requirements.txt
```

4. migrate
```
python manage.py migrate
```

5. 개발 서버 실행
```
python manage.py runserver
```

# API 
### 게시글 목록
* URL : api/post/
* Method : GET
* Description : 게시된 모든 게시물의 목록을 볼 수 있습니다.
* Response :
```
[
{
"id": 1,
"tags": [
{
"name": "{'name': '태그1 수정'}"
}
],
"title": "제목 수정1",
"content": "내용 수정",
"created_at": "2023-08-22T08:11:42.241124Z",
"updated_at": "2023-08-25T04:37:38.446555Z",
"hit": 1
}
] 
```
### 게시글 상세 조회
* URL : api/post/detail/1/
* Method : GET
* Description : 특정 게시물에 대한 내용, 작성자 및 기타 세부 정보를 확인할 수 있습니다.
* Response :
```
{
"post_id": 1,
"title": "제목 1",
"content": "내용",
"tags": [
{
"name": "{'name': '태그1'}"
}
],
"hit": 1
}
```
### 게시글 작성
* URL : api/post/write
* Method : POST
* Description : 제목, 내용 및 관련 정보를 제출하여 새 게시물을 만들 수 있습니다.
* Request Body : 
```
{
"title": "제목",
"content": "내용",
"tags": [
{"name": "태그"},
]
}
```
* Response :
```
{
"id": 1,
"tags": [
{
"name": "{'name': '태그1'}"
}
],
"title": "제목 1",
"content": "내용 1",
"created_at": "2023-08-22T08:11:42.241124Z",
"updated_at": "2023-08-25T07:26:47.254487Z",
"hit": 0
}
```
### 게시글 수정
* URL : api/post/detail/1/edit/
* Method : GET, POST
* Description : 특정 게시물의 내용, 해시태그 및 기타 세부 정보를 수정할 수 있습니다. 
* Request Body : 
```
{
"title": "제목",
"content": "내용",
"tags": [
{"name": "태그"},
]
}
```
* Response :
```
{
"id": 1,
"tags": [
{
"name": "{'name': '태그1 수정'}"
},
{
"name": "{'name': '태그2 추가'}"
}
],
"title": "제목 수정1",
"content": "내용 수정1",
"created_at": "2023-08-22T08:11:42.241124Z",
"updated_at": "2023-08-25T07:26:47.254487Z",
"hit": 1
}
```
### 게시글 삭제
* URL : api/post/detail/1/delete/
* Method : POST
* Description : 특정 게시물을 웹 사이트에서 제거할 수 있습니다. 
* Response :
```
{
"msg": "Post deleted",
}
```
