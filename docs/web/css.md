# CSS (Cascading Style Sheet)

## CSS 란

웹 페이지의 디자인과 레이아웃을 구성하는 언어

![css1](css1.png)

## CSS 적용 방법

### Inline

```html
<p style="color:blue;">blue</p>
```

### Internal

```html
<style>
    p {
        color:blueviolet;
    }
</style>
```

### External

```html
<link href="css_test.css" rel="stylesheet" type="text/css">
```

```css
p {
    color:white;
}
```

## CSS Selectors

- 전체 선택자 : *
    - 모든 부분을 선택
- 요소 선택자 : tag
    - 지정한 모든 태그 선택
- 클래스 선택자 : class
    - 지정한 모든 클래스 선택
- 아이디 선택자 : id
    - 지정한 모든 아이디 선택
- 속성 선택자 : attr
    - 지정한 속성 선택

우선순위

1. !important
2. Inline -> id -> class -> tag
3. 코드 순서 (코드 아래가 우선순위)

```html
<style>
    h2 {
        color:brown !important; 
    }
    p {
        color:blueviolet;
    }
    .blue {
        color:blue;
    }
    .green {
        color:green;
    }
    #red {
        color:red;
    }
</style>

<p>1</p>
<p class="blue">2</p>
<p class="blue green">3</p>
<p class="green blue">4</p>
<p id="red" class="blue">5</p>
<p id="red" class="blue" style="color:black;">6</p>
<h2 id="red" class="blue" style="color:black;">7</h2>
```

![css2](css2.png)

1 : tag p blueviolet 적용

2 : tag p, class blue / 우선 순위로 class blue 적용

3 : tag p, class blue, class green / 코드 순서로 class green 적용

4 : tag p, class blue, class green / 코드 순서로 class green 적용

5 : id red, class blue / 우선 순위로 id red 적용

6 : id red, class blue, inline black / 우선 순위로 inline black 적용

7 : tag h2, id red, class blue, inline black / 우선 순위로 tag h2 brown 적용
