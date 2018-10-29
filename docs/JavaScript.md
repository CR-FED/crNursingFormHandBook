# JavaScript代码规范

本文档基于[JavaScript Standard Style](https://standardjs.com/rules.html)进行编写，其中`+`为追加规则。

## 命名

- 变量名和函数名使用小驼峰命名法 `camelcase`

  ``` js
  // Bad
  let Count = 5
  const job_title = 'front-end engineer'

  // Good
  let count = 5
  const jobTitle = 'front-end engineer'
  ```

- 类名使用大驼峰（帕斯卡）命名法 `+` `[no-rule]`

  ```js
  // Bad
  class animal { }
  class whiteBear { }

  // Good
  class Animal { }
  class WhiteBear { }
  ```

- 配置型常量名使用大写下划线命名法 `+` `[no-rule]`

  ```js
  // Bad
  const env = 'test'
  const rootPath = '/src'

  // Good
  const ENV = 'test'
  const ROOT_PATH = '/src'
  ```

## 变量

- 禁止使用var定义变量，使用const、let代替 `+` `no-var`

  ```js
  // Bad
  var count = 5
  count = count + 1

  var name = 'Tom'

  // Good
  let count = 5
  count = count + 1

  const name = 'Tom'
  ```

- 优先使用const定义变量 `+` `prefer-const`

  ```js
  // Bad
  let a = 3
  console.log(a)

  for (let i of [1, 2, 3]) {
    console.log(i)
  }

  // Good
  const a = 3
  console.log(a)

  for (const i of [1, 2, 3]) {
    console.log(i)
  }

  for (let i = 0; i < 10; i++) {
    console.log(i)
  }
  ```

- 一次单独声明一个变量 `one-var`

  ```js
  // Bad
  let i = 0, j, k = 'test'

  // Good
  let i = 0
  let j
  let k = 'test'
  ```

- 禁止重复声明变量 `no-redeclare`

  ``` js
  // Bad
  let i = 5
  let i = 10

  // Good
  let i = 5
  let j = 10
  ```

- 禁止使用未声明变量 `no-undef`

  ```js
    // Bad
    const a = 5
    b = a + 10

    // Good
    const a = 5
    const b = a + 10
  ```

- 禁止对const定义的变量重新赋值 `no-const-assign`

  ```js
  // Bad
  const a = 5

  // Good
  let a = 5
  ```

- 禁止同作用域内重复变量名 `+` `no-shadow`

  ```js
  // Bad
  let i = 5

  function foo () {
    let i = 10
  }

  // Good
  let i = 5

  function foo () {
    let j = 10
  }
  ```

- 禁止定义冗余变量 `no-unused-vars`

  ```js
  // Bad
  const i = 1
  console.log('hello')

  // Good
  console.log('hello')
  ```

- 禁止对声明过的函数重新赋值 `no-func-assign`

  ```js
  // Bad
  function foo () { }
  function bar () { }
  foo = bar

  // Good
  let foo = () => { }
  const bar = () => { }
  foo = bar
  ```

- 禁止对全局只读对象重新赋值 `no-global-assign`

  ```js
  // Bad
  window = {}
  ```

- 禁止对类名重新赋值 `no-class-assign`

  ```js
  // Bad
  class Dog () { }
  Dog = 'Fido'
  ```

- 禁止解构空值 `no-empty-pattern`

  ```js
  // Bad
  const { data: { } } = response
  ```

- 禁止更改关键字的值 `no-shadow-restricted-names`

  ```js
  // Bad
  undefined = 10
  function NaN () { }
  class Object { }
  ```

- 禁止使用 undefined 来初始化变量 `no-undef-init`

  ```js
  // Bad
  let name = undefined
  name = 'Tom'

  // Good
  let name
  name = 'Tom'
  ```

- 禁止将变量赋值给自己 `no-self-assign`

  ```js
  // Bad
  name = name
  ```

- 禁止将变量与自己进行比较操作 `no-self-compare`

  ```js
  // Bad
  if (score === score) { }
  ```

## 类、构造函数

- 构造函数要以大写字母开头 `new-cap`

  ```js
  // Bad
  function animal () { }
  const dog = new animal()

  // Good
  function Animal () { }
  const dog = new Animal()
  ```

- 无参的构造函数调用时要带上括号 `new-parens`

  ```js
  // Bad
  const dog = new Animal

  // Good
  const dog = new Animal()
  ```

- new 创建对象实例后需要赋值给变量 `no-new`

  ```js
  // Bad
  new Animal()

  // Good
  const instance = new Animal()
  ```

- 子类的构造函数中一定要调用 super `constructor-super`

  ```js
  // Bad
  class Dog extends Animal {

    constructor () {
      this.legs = 4
    }

  }

  // Good
  class Dog extends Animal {

    constructor () {
      super()
      this.legs = 4
    }

  }
  ```

- 子类的构造函数中使用 this 前请确保 super() 已调用 `no-this-before-super`

  ```js
  // Bad
  class Dog extends Animal {

    constructor () {
      this.legs = 4
      super()
    }

  }

  // Good
  class Dog extends Animal {

    constructor () {
      super()
      this.legs = 4
    }

  }
  ```

- 禁止多余的构造函数 `no-useless-constructor`

  ```js
  // Bad
  class Animal {

    constructor () { }

  }

  // Good
  class Animal {

  }
  ```

- 禁止使用Array构造函数 `no-array-constructor`

  ```js
  // Bad
  const arr = new Array(1, 2, 3)

  // Good
  const arr = [1, 2, 3]
  ```

- 禁止使用 Object 构造函数器 `no-new-object`

  ```js
  // Bad
  const obj = new Object()

  // Good
  const obj = {}
  ```

- 禁止使用 Symbol 构造函数器 `no-new-symbol`

  ```js
  // Bad
  const foo = new Symbol('foo')

  // Good
  const foo = Symbol('foo')
  ```

- 禁止使用 Function 构造函数 `no-new-func`

  ```js
  // Bad
  const sum = new Function('a', 'b', 'return a + b')

  // Good
  function sum (a, b) {
    return a + b
  }
  ```

- 禁止使用基础类型构造函数 `no-new-wrappers`

  ```js
  // Bad
  const str = new String('hello')
  const num = new Number(233)
  const bool = new Boolean(false)

  // Good
  const str = 'hello'
  const num = 233
  const bool = false
  ```

## 属性

- 对象中定义了存值器，一定要对应的定义取值器 `accessor-pairs`

  ```js
  // Bad
  const person = {
    set name (value) {
      this._name = value
    }
  }

  // Good
  const person = {
    set name (value) {
      this._name = value
    },
    get name () {
      return this._name
    }
  }
  ```

- 对象字面量中不要定义重复的属性 `no-dupe-keys`

  ```js
  // Bad
  const person = {
    name: 'Tom',
    name: 'Tim'
  }
  ```

- 对象属性换行时使用统一风格 `object-property-newline`

  ```js
  // Bad
  const person = {
    name: 'Tom', age: 23,
    job: 'developer'
  }

  // Good
  const person = {
    name: 'Tom',
    age: 23,
    job: 'developer'
  }

  // Good
  const person = { name: 'Tom', age: 23, job: 'developer' }
  ```

- 避免使用不必要的计算值作对象属性 `no-useless-computed-key`

  ```js
  // Bad
  const person = { ['name']: 'Tom' }
  console.log(person['name'])

  // Good
  const person = { name: 'Tom' }
  console.log(person.name)
  ```

## 函数

- 禁止函数多余绑定 `no-extra-bind`

  ```js
  // Bad
  function getName () {
    return 'Steve'
  }

  getName.bind(person)

  // Good
  function getName () {
    return this.name
  }

  getName.bind(person)
  ```

- 禁止不必要的嵌套代码块 `no-lone-blocks`

  ```js
  // Bad
  function foo () {
    {
      bar()
    }
  }

  // Good
  function foo () {
    bar()
  }
  ```

- 自调用匿名函数 (IIFEs) 使用括号包裹 `wrap-iife`

  ```js
  // Bad
  const foo = function () { }()

  // Good
  const foo = (function () { }) ()
  ```

- 禁止不必要的 .call() 和 .apply() `no-useless-call`

  ```js
  // Bad
  function sum (a, b) {
    return a + b
  }

  sum.call(null, 1, 2)

  // Good
  function sum (a, b) {
    return a + b
  }

  sum(1, 2)
  ```

## 符号

- 不允许行末分号 `semi`

  ```js
  // Bad
  console.log('hello');

  // Good
  console.log('hello')
  ```

- 字符串使用单引号 `quotes`

  ```js
  // Bad
  console.log("hello")
  const el = "<div class=\"box\"></div>"

  // Good
  console.log('hello')
  const el = '<div class="box"></div>'
  ```

- 禁止多余的行末逗号 `comma-dangle`

  ```js
  // Bad
  const person = {
    name: 'Tom',
  }

  // Good
  const person = {
    name: 'Tom'
  }
  ```

- 禁止逗号出现在行首 `comma-style`

  ```js
  // Bad
  const person = {
    name: 'Tom'
    , age: 23
  }

  // Good
  const person = {
    name: 'Tom',
    age: 23
  }
  ```

- 点号操作符须与属性需在同一行 `dot-location`

  ```js
  // Bad
  const arr = [0, 1, 2]
  arr.
    filter(Boolean).
    map((i) => i + 1)

  // Good
  const arr = [0, 1, 2]
  arr
    .filter(Boolean)
    .map((i) => i + 1)
  ```

- 避免使用逗号操作符 `no-sequences`

  ```js
  // Bad
  const a = (2, 3)
  if (foo(), !!test) { }
  while (b = next(), a && a > 2) { }
  ```

- 禁止多余的括号 `no-extra-parens`

  ```js
  // Bad
  const a = (2 * 5)
  const b = (a * 4) + 3
  const t = typeof (a)
  const foo = (function () { })

  // Good
  const a = 2 * 5
  const b = a * 4 + 3
  const t = typeof a
  const foo = () => { }
  ```

## 运算符

- 禁止运算符后断行 `operator-linebreak`

  ```js
  // Bad
  const a = 'The best preparation ' +
    'for tomorrow is doing ' +
    'your best today'

  const b = name.length > 5 &&
    age > 18 &&
    !!job

  const c = env === 'development' ?
    'localhost' :
    'www.api.com'

  // Good
  const a = 'The best preparation '
    + 'for tomorrow is doing '
    + 'your best today'

  const b = name.length > 5
    && age > 18 
    && !!job

  const c = env === 'development'
    ? 'localhost'
    : 'www.api.com'
  ```

- 始终使用===代替== `eqeqeq`

  ```js
  // Bad
  if (name == 'Tom') { }

  // Good
  if (name === 'Tom') { }
  ```

- 避免不必要的布尔转换 `no-extra-boolean-cast`

  ```js
  // Bad
  const result = false
  if (!!result) { }

  // Good
  const result = false
  if (result) { }
  ```

- 避免不必要的三元表达式 `no-unneeded-ternary`

  ```js
  // Bad
  const score = value ? value : 0

  // Good
  const score = value || 0
  ```

- 关系运算符的左值不要做取反操作 `no-unsafe-negation`

  ```js
  // Bad
  if (!key in obj) { }
  if (!obj instanceof Animal) { }

  // Good
  if (!(key in obj)) { }
  if (!(obj instanceof Animal)) { }
  ```

- 禁止非法的typeof比较操作 `valid-typeof`

  ```js
  // Bad
  typeof name === 'undefimed'

  // Good
  typeof name === 'undefined'
  ```

## 语句

- if、else关键字与花括号同行 `brace-style`

  ```js
  // Bad
  if (condition)
  {
    // ...
  }
  else
  {
    // ...
  }

  // Good
  if (condition) {
    // ...
  } else {
    // ...
  }
  ```

- 多行代码块中花括号不能省略 `curly`

  ```js
  // Bad
  if (foo)
    foo()

  while(bar)
    bar--
  
  if (foo) {
    foo()
  } else baz()

  // Good
  if (foo) foo()

  if (foo) {
    foo()
  }

  while(bar) {
    bar--
  }

  if (foo) {
    foo()
  } else {
    baz()
  }
  ```

- 避免使用常量作为条件表达式的条件，循环语句除外 `no-constant-condition`

  ```js
  // Bad
  if (false) {
    // ...
  }

  // Good
  if (x === 0) {
    // ...
  }

  while (true) {
    // ...
  }
  ```

- 循环语句中必须更新循环变量 `no-unmodified-loop-condition`

  ```js
  // Bad
  for (let i = 0; i < 10; i) { }

  // Good
  for (let i = 0; i < 10; i++) { }
  ```

- switch语句中不要定义冗余的case分支 `no-duplicate-case`

  ```js
  // Bad
  switch (id) {
    case 1:
      // ...
    case 1:
      // ...
  }

  // Good
  switch (id) {
    case 1:
      // ...
  }
  ```

- switch 一定要使用 break 来将条件分支正常中断 `no-fallthrough`

  ```js
  // Bad
  switch (id) {
    case 1:
      doSomething()
    case 2:
      doSomethingElse()
  }

  // Good
  switch (id) {
    case 1:
      doSomething()
      break
    case 2:
      doSomethingElse()
      break
  }
  ```

- finally 代码块中不要再改变程序执行流程 `no-unsafe-finally`

  ```js
  // Bad
  try {
    // ...
  } catch (err) {
    // ...
  } finally {
    return 42
  }
  ```

- 禁止使用Yoda条件语句 `yoda`

  ```js
  // Bad
  if (42 === age) { }

  // Good
  if (age === 42) { }
  ```

- 条件语句中使用赋值必须用括号包裹 `no-cond-assign`

  ```js
  // Bad
  while (m = text.match(expr)) { }

  // Good
  while ((m = text.match(expr))) { }
  ```

## 异常

- 必须处理回调中error参数 `handle-callback-err`

  ```js
  // Bad
  run((err) => {
    console.log('done')
  })

  // Good
  run((err) => {
    if (err) throw err
    console.log('done')
  })
  ```

- catch中不要对错误重新赋值 `no-ex-assign`

  ```js
  // Bad
  try {
    // ...
  } catch (error) {
    error = 5
  }
  ```

- 禁止throw抛出字符串，应抛出Error对象 `no-throw-literal`

  ```js
  // Bad
  function foo () {
    throw 'message'
  }

  // Good
  function foo () {
    throw new Error('message')
  }
  ```

- 禁止Promise的reject函数中字符串，应传入Error对象 `+` `prefer-promise-reject-errors`

  ```js
  // Bad
  const promise1 = new Promise((resolve, reject) => {
    reject('message')
  })

  const promise2 = Promise.reject('message')

  // Good
  const promise1 = new Promise((resolve, reject) => {
    reject(new Error('message'))
  })

  const promise2 = Promise.reject(new Error('message'))
  ```

## 模块

- 同一模块有多个导入时一次性写完 `no-duplicate-imports`

  ```js
  // Bad
  import { foo } from './utils'
  import { bar } from './utils'

  // Good
  import { foo, bar } from './utils'
  ```

- 禁止使用 new require `no-new-require`

  ```js
  // Bad
  const foo = new require('foo')
  ```

- 使用 __dirname 和 __filename 时避免使用字符串拼接 `no-path-concat`

  ```js
  // Bad
  const pathToFile = __dirname + '/app.js'

  // Good
  import path from 'path'

  const pathToFile = path.join(__dirname, 'app.js')
  ```

- import、export 和解构操作中，禁止赋值到同名变量 `no-useless-rename`

  ```js
  // Bad
  import { config as config } from './config'

  // Good
  import { config } from './config'

  // Good
  import { config as appConfig } from './config'
  ```

## 正则表达式

- 禁止正则中使用控制符 `no-control-regex`

  ```js
  // Bad
  const pattern = /\x1f/

  // Good
  const pattern = /\x20/
  ```

- 禁止正则中使用空字符 `no-empty-character-class`

  ```js
  // Bad
  const regex = /^abc[]/

  // Good
  const regex = /^abc/
  ```

- 禁止非法的正则表达式字符串 `no-invalid-regexp`

  ```js
  // Bad
  const regex = RegExp('[a-z')

  // Good
  const regex = RegExp('[a-z]')
  ```

- 禁止正则中使用多个空格 `no-regex-spaces`

  ```js
  // Bad
  const regexp = /test   value/

  // Good
  const regexp = /test {3}value/
  ```

## 空格

- 两个空格作为缩进 `indent`

  ```js
  // Bad
  if (a) {
      const b = 1

      const foo = () => {
          return b + 10
      }
  }

  // Good
  if (a) {
    const b = 1

    const foo = () => {
      return b + 10
    }
  }
  ```

- 禁止空格和制表符混用 `no-mixed-spaces-and-tabs`

  ```js
  // Bad
  if (a) {
      const b = 1

      const foo = () => {
      	return b + 10
      }
  }

  // Good
  if (a) {
      const b = 1

      const foo = () => {
          return b + 10
      }
  }
  ```

- 禁止使用制表符 `no-tabs`

  ```js
  // Bad
  function sum (a, b) {
  	return a + b
  }
  

  // Good
  function sum (a, b) {
    return a + b
  }
  ```

- 关键字后面加空格 `keyword-spacing`

  ```js
  // Bad
  if() {
    // ...
  }else{
    // ...
  }

  while() {
    // ...
  }

  // Good
  if () {
    // ...
  } else {
    // ...
  }

  while () {
    // ...
  }
  ```

- 函数声明时，标识符和括号间加空格 `space-before-function-paren`

  ```js
  // Bad
  function foo() {
    // ...
  }

  // Good
  function foo () {
    // ...
  }
  ```

- 函数调用时，标识符与括号间不留空格 `func-call-spacing`

  ```js
  // Bad
  foo ()
  console.log ()

  // Good
  foo()
  console.log()
  ```

- 运算符前后加空格 `space-infix-ops`

  ```js
  // Bad
  a+b
  b +c
  c+     d
  z?x:y
  e=   f*g
  h=i++

  // Good
  a + b
  b + c
  c + d
  z ? x : y
  e = f * g
  h = i++
  ```

- 逗号后面加空格 `comma-spacing`

  ```js
  // Bad
  const arr = [1 ,2,3]
  const obj = { a: 1 ,b: 2 }

  // Good
  const arr = [1, 2, 3]
  const obj = { a: 1, b: 2 }
  ```

- 空格放在分号后面而不是前面 `semi-spacing`

  ```js
  // Bad
  for (let i = 0 ;i < 10 ;i++) {
    // ...
  }

  // Good
  for (let i = 0; i < 10; i++) {
    // ...
  }
  ```

- 禁止行末多余空格 `no-trailing-spaces`

  ```js
  // Bad
  const sum = a + b/*space*//*space*//*space*/

  // Good
  const sum = a + b
  ```

- 键值对当中冒号与值之间要加空格 `key-spacing`

  ```js
  // Bad
  const obj = { key:'value'}
  const obj = { key :'value'}
  const obj = { key : 'value'}

  // Good
  const obj = { key: 'value'}
  ```

- 禁止调用属性时前面加空格 `no-whitespace-before-property`

  ```js
  // Bad
  person .name

  // Good
  person.name
  ```

- 除了缩进，禁止使用多个空格 `no-multi-spaces`

  ```js
  // Bad
  const id =      1234

  // Good
  const id = 1234
  
  ```

- 注释首尾留空格 `spaced-comment`

  ```js
  // Bad
  const a = 5//comment
  const a = 5/*comment*/
  

  // Good
  const a = 5 // comment
  const a = 5 /* comment */
  ```

- 禁止使用非法的空白符 `no-irregular-whitespace`

  ```js
  // Bad
  function foo\u2000() { }

  // Good
  function foo () { }  
  ```

- 禁止展开运算符与它的表达式间的空格 `rest-spread-spacing`

  ```js
  // Bad
  const newObj = { ... obj }

  // Good
  const newObj = { ...obj }
  ```

- 代码块前加空格 `space-before-blocks`

  ```js
  // Bad
  if (isAdmin){ }

  // Good
  if (isAdmin) { }
  ```

- 单行代码块花括号之间加空格 `block-spacing`

  ```js
  // Bad
  function foo () {return true}

  // Good
  function foo () { return true }
  ```

- 圆括号间不留空格 `space-in-parens`

  ```js
  // Bad
  const total = ( 5 + 8 ) *2
  sum( 1, 2 )


  // Good
  const total = (5 + 8) *2
  sum(1, 2)
  
  ```

- 一元运算符后加空格 `space-unary-ops`

  ```js
  // Bad
  typeof!foo
  delete(foo.bar)

  // Good
  typeof !foo
  delete foo.bar
  ```

- yield * 中的 * 前后都要有空格 `yield-star-spacing`

  ```js
  // Bad
  function *foo () {
    yield *bar()
  }

  // Good
  function * foo () {
    yield * bar()
  }
  ```

- 模板字符串花括号间不加空格 `template-curly-spacing`

  ```js
  // Bad
  const message = `Hello, ${ name }`

  // Good
  const message = `Hello, ${name}`
  ```

## 空行

- 禁止连续多行空行 `no-multiple-empty-lines`

  ```js
  // Bad
  const value = 'hello world'



  console.log(value)

  // Good
  const value = 'hello world'
  console.log(value)
  ```

- 禁止代码块中多余空行 `padded-blocks`

  ```js
  // Bad
  if (user) {

    const name = getName()

  }

  // Good
  if (user) {
    const name = getName()
  }
  ```

- 文件末尾留一空行 `eol-last`

- 类中的属性用空行隔开 `+` `lines-between-class-members`

  ```js
  // Bad
  class MyClass {
    foo() {
      //...
    }
    bar() {
      //...
    }
  }

  // Good
  class MyClass {
    foo() {
      //...
    }

    bar() {
      //...
    }
  }
  ```

## 杂项

- 禁止函数定义冗余的参数 `no-dupe-args`

  ```js
  // Bad
  function foo (a, b, a) {
    // ...
  }

  // Good
  function foo (a, b, c) {
    // ...
  }
  ```

- 禁止类中定义冗余的属性 `no-dupe-class-members`

  ```js
  // Bad
  class Dog {
    bark () {}

    bark () {}
  }

  // Good
  class Dog {
    bark () {}
  }
  ```

- 禁止使用 eval() `no-eval`

  ```js
  // Bad
  eval('alert("hello")')
  ```

- 避免隐式的 eval() `no-implied-eval`

  ```js
  // Bad
  setTimeout('alert("Hello world")')

  // Good
  setTimeout(function () { alert('Hello world') })
  ```

- 禁止扩展原生对象 `no-extend-native`

  ```js
  // Bad
  Object.prototype.age = 21
  ```

- 禁止省去小数点前面的0 `no-floating-decimal`

  ```js
  // Bad
  const discount = .5

  // Good
  const discount = 0.5
  ```

- 禁止在嵌套的代码块中再定义函数 `no-inner-declarations`

  ```js
  // Bad
  if (authenticated) {
    function setAuthUser () {}
  }
  ```

- 禁止对变量使用 delete 操作 `no-delete-var`

  ```js
  // Bad
  const name = 'Tom'

  delete name
  ```

- 禁止定义与label同名变量 `no-label-var`

  ```js
  // Bad
  let score = 100

  function game () {
    score: while (true) {
      score -= 10

      if (score > 0) continue score
      break
    }
  }
  ```

- 禁止使用label语句 `no-labels`

  ```js
  // Bad
  label:
  while (true) {
    break label
  }
  ```

- 禁止使用多行字符串 `no-multi-str`

  ```js
  // Bad
  const message = 'Hello \
    world'

  // Good
  const message 'Hello '
    + 'world'
  ```

- 禁止不合理的多行语句 `no-unexpected-multiline`

  > 禁止使用`[ ( \` + * / - , .`开头

  ```js
  // Bad
  (function () {
    window.alert('ok')
  }())
  ```

- 禁止全局对象作为函数调用 `no-obj-calls`

  ```js
  // Bad
  const math = Math()
  ```

- 禁止使用八进制字面量 `no-octal`

  ```js
  // Bad
  const num = 042

  // Good
  const num = '042'
  ```

- 禁止字符串字面量使用八进制转义字符 `no-octal-escape`

  ```js
  // Bad
  const copyright = 'Copyright \251'
  ```

- 禁止使用__proto__，用 getPrototypeOf 来替代 `no-proto`

  ```js
  // Bad
  const foo = obj.__proto__

  // Good
  const foo = Object.getPrototypeOf(obj)
  ```

- return 语句中的赋值必需用括号包裹 `no-return-assign`

  ```js
  // Bad
  function sum (a, b) {
    let result
    return result = a + b
  }

  // Good
  function sum (a, b) {
    let result
    return (result = a + b)
  }
  ```

- 禁止使用稀疏数组 `no-sparse-arrays`

  ```js
  // Bad
  const fruits = ['apple', , 'orange']
  ```

- 正确使用 ES6 中的字符串模板 `no-template-curly-in-string`

  ```js
  // Bad
  const message = 'Hello ${name}'

  // Good
  const message = `Hello ${name}`
  ```

- 禁止不可触及的代码 `no-unreachable`

  ```js
  // Bad
  function doSomething () {
    return true
    console.log('never called')
  }
  ```

- 禁止不必要的字符串转义 `no-useless-escape`

  ```js
  // Bad
  let message = 'Hell\o'

  // Good
  let message = 'Hello'
  ```

- 禁止使用NaN作判断，使用isNaN函数代替 `use-isnan`

  ```js
  // Bad
  if (price === NaN) { }

  // Good
  if (isNaN(price)) { }
  ```

- 禁止使用 with `no-with`

  ```js
  // Bad
  with (val) { }
  ```

- 禁止使用 arguments.callee 和 arguments.caller `no-caller`

  ```js
  // Bad
  function foo (n) {
    if (n <= 0) return
  
    arguments.callee(n - 1)
  }

  // Good
  function foo (n) {
    if (n <= 0) return
  
    foo(n - 1)
  }
  ```

- 禁止使用 debugger `no-debugger`

  ```js
  // Bad
  function sum (a, b) {
    debugger
    return a + b
  }
  ```

- 禁止使用 __iterator__ `no-iterator`

  ```js
  // Bad
  Foo.prototype.__iterator__ = function () { }
  ```
