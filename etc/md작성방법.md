블로그에만 정리를 하다가 git에도 TIL을 조금씩이라도 적어놓고 싶어졌다.
앞으로 더 친해져야할 markdown 문법들을 짤막하게 정리해보려고 한다.  
<br></br>

# 1. 제목 작성

#의 개수를 다르게 하거나 `<h1>제목작성</h1>`부터 `<h6>제목작성</h6>` 까지 제목 크기를 조절할 수 있다.  
<br></br>

# 2. 강조 표시

`<em>으로 강조하기 </em>`
<em>강조</em>

`<strong>으로 강조하기</strong>`
<strong>강조</strong>

`<del>으로 강조하기</del>`
<del>강조</del>

`<u>으로 강조하기</u>`
<u>강조</u>

<br></br>

# 3. 줄바꿈

`<br>`태그를 사용하거나, 글 라인 마지막에 공백을 두 칸 입력하면 줄바꿈이 가능하다. 문단 구분시 enter를 두 번 입력하면 된다.
<br></br>

# 4. 인용문

맨 앞에 `>` 기호를 사용하면 된다.

> 이렇게 인용문이 사용된다.  
> 인용문 안에서도 줄바꿈이 잘 된다.

<br></br>

# 5. 소스코드

```javascript
소스코드는 백틱(``)을 6개 사용해서 쓸 수 있다.
javascript 대신 다른 언어를 써주면 그 언어 문법대로 표시된다.
const one = 1
```

<br></br>

# 6. 링크

외부 링크의 경우에는 `[Title(=보여지는내용)](link(=url))` 형식으로 사용할 수 있다.  
이렇게 쓰면 `[내 github 프로필주소](https://github.com/kim-yejin20)` 아래와 같이 나타난다.

[내 github 프로필주소](https://github.com/kim-yejin20)

목차를 만들고, 목차 제목을 누르면 문서의 해당 내용으로 이동하고 싶다면,

```
목차

[1.인용문](#1-인용문)
[2.소스코드](#2-소스코드)


# 1. 인용문
# 2. 소스코드
```

위와같이 `[보여질 내용이나 제목](#이동할-헤드의-제목)`으로 써주면된다.

- 띄어쓰기는 -로 연결
- 영어는 소문자로 작성
- 제목에 괄호()가 있을 경우에는 생략하는 것 같다.
- 제목에 붙은 .도 -로 연결해주면 되는 것 같다 `3.이건이렇게` -> (#3-이건이렇게)

<br>
<br>

# 7. 글씨 색 변경

<span style="color:yellow">노란 글씨입니다.</span>

- 글씨 자체 색 변경  
  `<span style="color:yellow">노란 글씨입니다.</span>`

<br>

<span style="font-size:23px; color:white; padding:5px 13px; background-color:#f29e74; ">바탕색변경 </span>

- 글씨 바탕 색 변경
  `<span style="font-size:23px; color:white; padding:5px 13px; background-color:#f29e74; "> 바탕색변경 </span>`

</h4>
