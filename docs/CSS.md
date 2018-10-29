# CSS代码规范

## 规则

- 使用两个空格作为缩进

  ```css
  /* Bad */
  .selector {
  	margin: 0;
  	padding: 0;
  }

  /* Good */
  .selector {
    margin: 0;
    padding: 0;
  }
  ```

- 每段CSS规则使用空行分隔

  ```css
  /* Bad */
  input {
    /* ... */
  }
  select {
    /* ... */
  }

  /* Good */
  input {
    /* ... */
  }

  select {
    /* ... */
  }
  ```

- 选择器与`{`之间包含一个空格

  ```css
  /* Bad */
  .box1   {
    /* ... */
  }

  .box2{
    /* ... */
  }

  /* Good */
  .box1 {
    /* ... */
  }

  .box2 {
    /* ... */
  }
  ```

- 属性值后必须用引号结尾

  ```css
  /* Bad */
  a {
    color: black
  }

  /* Good */
  a {
    color: black;
  }
  ```

- 使用双引号

  ```css
  /* Bad */
  .selector {
    family: 'Microsoft YaHei';
    content: '';
  }

  /* Good */
  .selector {
    family: "Microsoft YaHei";
    content: "";
  }
  ```

- 属性名和`:`之间没有空格

  ```css
  /* Bad */
  color : black;

  /* Good */
  color: black;
  ```

- `:`与属性值之间包含一个空格

  ```css
  /* Bad */
  color:black;

  /* Good */
  color: black;
  ```

- 属性值列表单行书写时，`,`后必须加空格

  ```css
  /* Bad */
  font-family: "Source Sans Pro",Arial,sans-serif;

  /* Good */
  font-family: "Source Sans Pro", Arial, sans-serif;
  ```

- 属性值列表多行书写时，换行必须缩进

  ```css
  /* Bad */
  font-family:
  "Source Sans Pro",
  Arial,
  sans-serif;

  /* Good */
  font-family:
    "Source Sans Pro",
    Arial,
    sans-serif;
  ```

- 包含多个选择器时，每个选择器必须独占一行

  ```css
  /* Bad */
  .post, .page, .comment {
      line-height: 1.5;
  }

  /* Good */
  .post,
  .page,
  .comment {
      line-height: 1.5;
  }
  ```

- `>`、`+`、`~`选择器的两边各一个空格

  ```css
  /* Bad */
  main>nav {
    padding: 10px;
  }

  label+input {
    margin-left: 5px;
  }

  input:checked~button {
    background-color: #FF0000;
  }

  /* Good */
  main > nav {
    padding: 10px;
  }

  label + input {
    margin-left: 5px;
  }

  input:checked ~ button {
    background-color: #FF0000;
  }
  ```

- 小数属性值不省略小数点前的`0`

  ```css
  /* Bad */
  .box {
    opacity: .8;
  }

  /* Good */
  .box {
    opacity: 0.8;
  }
  ```

- 长度单位为`0`时，省略`px`

  ```css
  /* Bad */
  .container {
    padding: 0px 12px;
  }

  /* Good */
  .container {
    padding: 0 12px;
  }
  ```

- 尽量不使用`!important`

## 属性书写顺序

1. 显示相关属性：

  - `position` / `top` / `right` / `bottom` / `left` / `z-index`
  - `display` / `flex` / `visibility` / `float`

2. 盒子相关属性：

  - `border` / `margin` / `padding` / `width` / `height` / `overflow`

3. 文本相关属性：

  - `line-height` / `vertical-algin` / `text-align` / `text-decoration`
  - `word-wrap` / `word-break` / `word-spacing` / `white-space`
  - `font` / `color` / `background` 

4. 转换、动画相关属性：

  - `opacity` / `transform` / `transition` / `animation`
