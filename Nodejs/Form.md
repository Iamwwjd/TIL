# Form

```jsx
<input type = "text" name="title"> // 사용자가 직접 텍스트를 입력할 수 있다. , 이름을 title로 설정
```

```jsx
<textarea> </textarea> // 여러줄의 텍스트를 입력할 수 있다.
```

```jsx
<input type = "submit"> // 전송버튼을 생성한다.
```

```jsx
<form action="주소"> </form> // 위 태그들을 form으로 감싸주면 적혀져있는 주소에 적용이 된다. 
```

파일을 수정할때에는 필요한 데이터를 url로 보내면 절대 안된다. 눈에 보이지 않는 방식으로 보내야 하는데, 이는

```jsx
<form action="주소" method="post">  // 메소드를 post로 바꿔주면 된다.
```

서버로 부터 사용자가 데이터를 가져올때는 `method = “gety” 혹은 method 생략` 로 바꿔주어야 한다.

하지만 서버의 데이터를 cud 할때는 꼭 post 방식으로 해야한다!!

서버로 부터 사용자가 데이터를 가져올때는 `method = “gety” 혹은 method 생략` 로 바꿔주어야 한다.

하지만 서버의 데이터를 cud 할때는 꼭 post 방식으로 해야한다!!

글을 쓸 수 있는 경로로 가는 링크 만들기

`templateHTML` 함수에

```jsx
<a href ="/create">create</a> // create를 누르면 create 페이지로 넘어감
```