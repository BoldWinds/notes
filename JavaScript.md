# JavaScript

## Basics

### Grammer&Types

#### declaration

- `var`: Declares a variable, optionally initializing it to a value.  
- `let`: Declares a block-scoped, local variable, optionally initializing it to a value.  
- `const`: Declares a block-scoped, read-only named constant.  

#### initialization

const必须初始化，var和let可以先不做初始化

#### scope

变量的scope有3+1种：

- `Global scope`: The default scope for all code running in script mode.
- `Module scope`: The scope for code running in module mode.
- `Function scope`: The scope created with a function.
- Block scope: The scope created with a pair of curly braces (a block).

注意var类型变量不受Block scope的限制，也就是说即使它在大括号内被定义，它的scope也会延伸到大括号外的function

#### variable hoisting

前面提到了var类型变量在block scope上的特殊性，除此以外，var类型变量的scope会`hoist`。具体的，看个例子，下面两段代码是等价的：

```javascript
console.log(x === undefined); // true
var x = 3;

var x;
console.log(x === undefined); // true
x = 3;
```

其实也就是说，**所有var类型变量的declaration会被提前到它所在scope的最开始位置**；而let和const的scope是从他们被定义的地方开始



### Data Structure & Types

#### primitives

1. `Boolean:`  `true` and `false`.
2. `null`: A special keyword denoting a null value. (Because JavaScript is case-sensitive, `null` is not the same as Null, NULL, or any other variant.)
3. `undefined`:  A top-level property whose value is not defined.
4. `Number`:  An integer or floating point number. For example: `42` or `3.14159`.
5. `BigInt`:  An integer with arbitrary precision. For example: `9007199254740992n`.
6. `String`:  A sequence of characters that represent a text value. For example: `"Howdy"`.
7. `Symbol:` A data type whose instances are unique and immutable.

#### conversion

js的类型是动态的，当使用`+`运算符的时候体现的特别明显：

```javascript
x = "The answer is " + 42; // "The answer is 42"
y = 42 + " is the answer"; // "42 is the answer"
z = "37" + 7; // "377"
```

还有其他办法可以转换类型：
```javascript
parseInt("101", 2); // 5
```



### Literals

literal有以下种类：

- `Array literals`
- `Boolean literals`
- `Numeric literals`: 分为Integer literals和Floating-point leterals
- `Object literals`
- `RegExp literals`
- `String literals`

下面对于其中一些特性较为复杂的做出介绍

#### array literals

一般的array literal定义是这样的：

```javascript
const coffees = ["French Roast", "Colombian", "Kona"];
```

但是array literal可以支持"extram comma"，即可以这样定义：

```javascript
const fish = ["Lion", , "Angel"];
console.log(fish);
// [ 'Lion', <1 empty item>, 'Angel' ]
```

fish数组的长度是3，当你打印时，index为1的元素显示"<1 empty item>"；而当你直接用index访问时，则会返回`undefined`。不仅如此，extra comma会且仅会忽略最后一个comma，如下：

```javascript
const fish1 = ["Lion", , "Angel"];
const fish2 = ["Lion", , "Angel",];
```

fish1和fish2是完全相同的两个array，长度都为3









