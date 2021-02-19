---
template: BlogPost
slug: /javascript-coersion  
date: 2020-12-06T13:19:34.627Z
title: Type Coercion in JavaScript 
tags:
  - javascript
  - fundamentals
  
  
metaDescription: >-
  Learn how what is coersion JavaScript 
thumbnail: /images/javascript.png
---

Type Coercion is just a fancy name for implicit typecasting in JavaScript.

### Type Coercion Definition
As per MDN, Type Coercion refers to the automatic or implicit conversion of values from one type to another.

👉 In JavaScript, if we execute the following statement

```js
var val = '10' + 10;
console.log(val);
```

String ‘1010’ will get printed in the console. The number 10 is implicitly converted to string ‘10’ while executing the code. That’s what implicit type casting or type coercion.


No matter if we write the same statement as
var val = 10 + '10';
console.log(val);
The same output ‘1010’ will get printed.

The following are some more examples for which we can see type coercion in action.

```js
'10' - 10  // 0
10 - '10'  // 0
'10' + 10  // '1010'
10 + '10'  // '1010'
null + ''  // 'null'
null + undefined  // NaN
```
## Type Coercion with + operator

When adding the two operands with the + operator, the JavaScript engine will try to add the values if both the values are of integer type.
// No Implicit Type casting needed

```js
10 + 10   // 20
```

But if any of the value is a string type, JavaScript will try to automatically convert the other values to a string so that they can be appended.

// With Implicit type casting
```js
10 + '10'   // 1010
```

As soon as we tried to add null and undefined, the JavaScript engine tries to convert the values to integer resulting in NaN.


### Type Coercion with the - operator

Using the - operator, the JS engine to subtract the values and tried to cast the values into integers implicitly. So we get the result as
```js
'10' - 10  // 0
10 - '10'  // 0
null - undefined // NaN
'2' - 1  // 1
```
Here are some of the strange conversions with reasons why they are converted like that.
'' - 1  // -1 as in JS Number('') is 0
false - true  // -1 as JS parses true as 1 and false as 0
null + 10   // 10 as Number(null) is 0
Type Coercion with == operator
In JS, == operator is very common to compare values. It compares the values based on their values ignoring their types.
For example,
10 == '10'  // true
This expression evaluated to true, as String(10) is 10. So JavaScript internally typecasts the String 10 to integer type and the values are equal for both. Hence, the expression evaluated to true.
Some more complex scenarios with == equality operator
true == 1  // true as Boolean(1) is true
1 == '01'  // true as Number('01') is 1
What if both the values are either not a string or boolean?
null == ''
// false as String(null) converts to 'null' &
// 'null' is not equal to ''
Can you also guess the output of the following expression?
true == 'true'
Make a guess and scroll to the solution…
```js
true == 'true'  // false
```
In JavaScript, true is evaluated as 1. So JavaScript tries to cast String ‘true’ to Number which evaluates to NaN. Hence evaluating to false.
```js
{} == {}
// false as Objects get compared by their references not by their values
```

👉 Comparison between null and undefined
```js
null == undefined  // true
```
This is because null and undefined, both are evaluated as falsiness in terms of boolean in JavaScript. Hence, we get the values implicitly converted to Booleans.
```js
Boolean(null)  // false
Boolean(undefined)  // false
```
Hence, null == undefined yields true.
Object and String comparison
```js
var obj = {};
console.log(obj.toString());  // "[object Object]"
```
Output for the following expressions:

```js
obj == obj  // true
obj.toString() == obj
// true as obj on the right side is implicitly casted to string
```