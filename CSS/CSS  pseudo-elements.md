# ::before ::after

- pseudo-element 로서, HTML에 추가하지 않고도 컨텐츠를 추가할 수 있게 해주는 CSS 속성이다
- 결과는 DOM에 반영되지 않고 페이지에만 나타난다. 

```css
div::before{
    content:"before"
}

div::after{
    content:"after"
}
```

결과

```html
<div>
    before
    /// 기존 컨텐츠
    after
</div>
```

- before와 after에서 정의돈 컨텐츠는 해당 컨테이너를 벗어나지 않는다.



### pseudo element를 이용해 list에서 counter 속성 꾸미기

- ordered list에서 counter(숫자) 속성을 꾸밀 수 있다.

```css
ol {
	counter-reset:li; /* Initiate a counter */
	margin-left:0; /* Remove the default left margin */
	padding-left:0; /* Remove the default left padding */
}

ol > li {
	position:relative; /* Create a positioning context */
	margin:0 0 6px 2em; 
	padding:4px 8px; 
	list-style:none; /* Disable the normal item numbering */
}
ol > li:before {
	content:counter(li); /* Use the counter as content */
	counter-increment:li; /* Increment the counter by 1 */
	/* Position and style the number */
	position:absolute;
	top:-2px;
	left:-2em;
	-moz-box-sizing:border-box;
	-webkit-box-sizing:border-box;
	box-sizing:border-box;
	width:2em;
	/* Some space between the number and the content in browsers that support
	   generated content but not positioning it (Camino 2 is one example) */
	margin-right:8px;
	padding:4px;
	border-top:2px solid #666;
	color:#fff;
	background:#666;
	font-weight:bold;
	font-family:"Helvetica Neue", Arial, sans-serif;
	text-align:center;
}
```



# :: first-letter , ::first-line

- block level에만 적용 가능 
- font 속성 , color 속성, background 속성, margin / padding, border 속성, text-decoration, vertical-align (float이 none일때만), text-transform, line-height, float,clear 적용 가능



# ::selection

- user가 선택한 요소에 대해 적용 가능 (드래그)
- color,background,cursor,outline 적용 가능 



