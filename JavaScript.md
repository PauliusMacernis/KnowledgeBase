- **What is the difference between JavaScript and ECMAScript?**  
ECMAScript is a standard, JavaScript is implementation of this standard. By reading the ECMAScript specification, you learn how to create a scripting language. By reading the JavaScript documentation, you learn how to use a scripting language.  
Read more:  
https://medium.freecodecamp.org/whats-the-difference-between-javascript-and-ecmascript-cba48c73a2b5  

- **What is the difference between ECMAScript 2015 and ECMAScript 6th Edition (known as "ES6")?**  
`ECMAScript 2015` is the new name for `ECMAScript 6th Edition` so we may say it is equivalent (names are different, but the content of both is the same).  
Read more:  
https://en.wikipedia.org/wiki/ECMAScript#6th_Edition_-_ECMAScript_2015  

- **What is `ES.Next`?**  
ES.Next is a dynamic name that refers to whatever the next version is at time of writing. ES.Next features are more correctly called proposals, because, by definition, the specification has not been finalized yet.  
Read more:  
https://en.wikipedia.org/wiki/ECMAScript#ES.Next  

- **What is the difference between JavaScript and TypeScript?**  
TypeScript is an open-source programming language developed and maintained by Microsoft. It is a strict syntactical **superset of JavaScript**, and adds optional static typing to the language.  
TypeScript is designed for development of large applications and transcompiles to JavaScript. As TypeScript is a superset of JavaScript, existing JavaScript programs are also valid TypeScript programs. TypeScript may be used to develop JavaScript applications for both client-side and server-side (Node.js) execution.  
Read more:  
http://www.typescriptlang.org/  
https://en.wikipedia.org/wiki/TypeScript  
https://stackoverflow.com/questions/12694530/what-is-typescript-and-why-would-i-use-it-in-place-of-javascript  

- **Do browsers understand TypeScript?**  
Not really. Existing JavaScript programs are also valid TypeScript programs. However, the opposite is not always true. You may use `.ts` files (TypeScript files) as `.js` (JavaScript) files and it will work most of the time. In case you want the whole language support by the JavaScript engine (simply saying - a browser running JavaScript engine), you need to transpile the code from TypeScript to JavaScript by using TypeScript transpiler (`tsc`).  
TypeScript starts from the same syntax and semantics that millions of JavaScript developers know today. Use existing JavaScript code, incorporate popular JavaScript libraries, and call TypeScript code from JavaScript.  
As of year of 2018, TypeScript compiles to clean, simple JavaScript code which runs on any browser, in Node.js, or in any JavaScript engine that supports ECMAScript 3 (or newer).  
Read more:  
https://www.typescriptlang.org/  
http://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html  
https://en.wikipedia.org/wiki/TypeScript  
https://david-barreto.com/introduction-to-the-typescript-transpiler/  

- **How does TypeScript convert to JavaScript?**  
You need transpiler for this.  
Read more:  
http://www.typescriptlang.org/docs/handbook/typescript-in-5-minutes.html  

- **Explain `tsc ts/*.ts --target ES5 --outDir js --watch`**  
The `--outDir` flag tells the transpiler where to put all the javascript files, in this case the `js` folder. Now, whenever we make a change to any file in the `ts` folder, the transpiler kicks in and creates all the associated javascript files and put them in the `js` folder.  
`--target ES5` - specifies ECMAScript target version, in this case it is ES5 (equivalent to version of ECMAScript in 2014).  
`--watch` - watch input files.  
Read more:  
https://david-barreto.com/introduction-to-the-typescript-transpiler/  

- **What is the difference between JavaScript and JScript?**  
Microsoft script technologies including VBScript and JScript were released in 1996. **JScript, a reverse-engineered implementation of Netscape's JavaScript**, was part of Internet Explorer 3. JScript was also available for server-side scripting in Internet Information Server.  
JScript is Microsoft's dialect of the ECMAScript standard that is used in Microsoft's Internet Explorer.  
JScript is implemented as an Active Scripting engine. This means that it can be "plugged in" to OLE Automation applications that support Active Scripting, such as Internet Explorer, Active Server Pages, and Windows Script Host. It also means such applications can use multiple Active Scripting languages, e.g., JScript, VBScript or PerlScript.  
JScript was first supported in the Internet Explorer 3.0 browser released in August 1996. Version JScript 9.0 is included in Internet Explorer 9.  
JScript 10.0 is a separate dialect, also known as JScript .NET, which adds several new features from the abandoned fourth edition of the ECMAScript standard. It must be compiled for .NET Framework version 2 or version 4, but static type annotations are optional.  
Read more:  
https://en.wikipedia.org/wiki/JScript  

- **How JScript engine is different from usual JavaScript engines?**  
Read more:  
???  

- **Can JScript be run on any browser (JavaScript engine)? If yes then how does that happen without the use of the transpiler from JScript to JavaScript (ECMAScript)?**  
Read me:  
???  

- **What is the difference between JavaScript and JS?**  
JS is a common abbreviation of JavaScript. So it means the same while talking to someone. However, as a side note, recently (year of 2018) there was a discussion about renaming “ECMAScript” to “JS”, idea has a lot of support.  
Read more:  
https://medium.freecodecamp.org/whats-the-difference-between-javascript-and-ecmascript-cba48c73a2b5 (comments)  
https://en.wikipedia.org/wiki/JavaScript  

- **What is the difference between JavaScript and "Vanilla JavaScript" (sometimes called "Vanilla JS")?**  
The terms Vanilla JavaScript and Vanilla JS refer to JavaScript not extended by any frameworks or additional libraries. Scripts written in Vanilla JS are plain JavaScript code.  
Read more:  
https://en.wikipedia.org/wiki/JavaScript#Vanilla_JavaScript  

- **Who owns JavaScript?**  
"JavaScript" is a trademark of Oracle Corporation in the United States. It is used under license for technology invented and implemented by Netscape Communications and current entities such as the Mozilla Foundation.  
Read more:  
http://tsdr.uspto.gov/#caseNumber=75026640&caseType=SERIAL_NO&searchType=statusSearch  
https://en.wikipedia.org/wiki/JavaScript  

- **What is JavaScript engine?**  
A JavaScript engine is a program or interpreter which executes JavaScript code. A JavaScript engine may be a traditional interpreter, or it may utilize just-in-time compilation to bytecode in some manner. Although there are several uses for a JavaScript engine, it is most commonly used in Web browsers.  
Read more:  
https://en.wikipedia.org/wiki/JavaScript_engine  

- **What JavaScript-related engines (also termed JavaScript interpreters or JavaScript implementations) do you know?**  
  - SpiderMonkey is the code name for the first JavaScript engine, written by Brendan Eich at Netscape Communications, later released as open source and currently maintained by the Mozilla Foundation. SpiderMonkey provides JavaScript support for **Mozilla Firefox** and various embeddings such as the GNOME 3 desktop. 
  - Chakra (**JScript** engine) developed by Microsoft for its 32-bit version of the Internet Explorer 9 (IE9) web browser. The JScript engine is developed as closed source proprietary software. Microsoft has developed a different JavaScript engine based on the JScript, for the newer Microsoft Edge browser (also called Chakra).  
  - Chakra (**JavaScript** engine) developed by Microsoft for its Microsoft Edge web browser. It is a fork of the JScript engine used in Internet Explorer. Like the Edge layout engine and unlike previous versions in Internet Explorer the declared intention is that it will reflect the "Living Web". On December 5 of 2015, it was announced that core components of Chakra will be open-sourced as ChakraCore. ChakraCore is essentially the same as the Chakra engine that powers the Microsoft Edge browser, but with platform-agnostic bindings, i.e. without the specific interfaces utilised within the Windows Universal App platform. On January 13, 2016, Microsoft released ChakraCore under the MIT license on GitHub as promised.  
  - Chrome V8, or simply V8, is an open-source JavaScript engine developed by The Chromium Project for Google Chrome and Chromium web browsers. The project’s creator is Lars Bak. The first version of the V8 engine was released at the same time as the first version of Chrome: September 2, 2008. It has also been used in Couchbase, MongoDB and Node.js that are used server-side. V8 compiles JavaScript directly to native machine code before executing it, instead of more traditional techniques such as interpreting bytecode or compiling the whole program to machine code and executing it from a filesystem. The compiled code is additionally optimized (and re-optimized) dynamically at runtime, based on heuristics of the code's execution profile. Optimization techniques used include inlining, elision of expensive runtime properties, and inline caching. The garbage collector is a generational incremental collector. V8 can compile to x86, ARM or MIPS instruction set architectures in both their 32- and 64-bit editions; as well, it has been ported to PowerPC and IBM s390 for use in servers.  
  - JavaScriptCore is a framework that provides a JavaScript engine for WebKit implementations, and provides this type of scripting in other contexts within macOS.  

  Read more:  
  https://en.wikipedia.org/wiki/JavaScript  
  https://en.wikipedia.org/wiki/JavaScript_engine  
  https://en.wikipedia.org/wiki/Chakra_(JScript_engine)  
  https://en.wikipedia.org/wiki/Chakra_(JavaScript_engine)  
  https://msdn.microsoft.com/en-us/library/dn903710(v=vs.94).aspx
  https://en.wikipedia.org/wiki/SpiderMonkey  
  https://en.wikipedia.org/wiki/Chrome_V8  
  https://en.wikipedia.org/wiki/WebKit#JavaScriptCore  
  https://en.wikipedia.org/wiki/List_of_ECMAScript_engines  
  http://kangax.github.io/compat-table/es6/  

- **What implementations of the ECMAScript standard do you know, except web browsers?**  
  - ActionScript, the programming language used in Adobe Flash, is another implementation of the ECMAScript standard.
  - Adobe AIR (Adobe Integrated Runtime) is a JavaScript runtime that allows developers to create desktop applications.
  - Electron is an open-source framework developed by GitHub.
  - Apache Cordova is a mobile application development framework.
  - GNOME Shell, the shell for the GNOME 3 desktop environment, made JavaScript its default programming language in 2013.
  - The Mozilla application framework (XPFE) platform, which underlies Firefox, Thunderbird, and some other Web browsers, uses JavaScript to implement the graphical user interface (GUI) of its various products.
  - Ubuntu Touch provides a JavaScript API for its unified usability interface.
  - WinJS provides a special Windows Library for JavaScript functionality in Windows 8 that enables the development of Modern style (formerly Metro style) applications in HTML5 and JavaScript.
  - NativeScript is an open-source framework to develop apps on the Apple iOS and Android platforms.
  - Weex is a framework for building Mobile cross-platform UI, created by China Tech giant Alibaba.
  - XULRunner is packaged version of the Mozilla platform to enable standalone desktop application development.
  - others

  Read more:  
  https://en.wikipedia.org/wiki/JavaScript#Application_platform  

- **What types of values JavaScript use?**  
  - `Number`
    - Float - Double-precision 64-bit format IEEE 754 values
    - (Int - 32-bit integer)
    - `NaN` (Not a Number)
    - `Infinity`
    - `-Infinity`
  - `String`
  - `Boolean`
  - `Symbol` (new in ES2015)
  - `Object`
    - `Function`
    - `Array`
    - `Date`
    - `RegExp`
    - `Math` - provides advanced mathematical functions and constants
  - `null`
  - `undefined` - a constant, by default assigned to the new variable declared, and with no initial value assigned yet
  - some built-in Error types

  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

## Number

- **What type of precision JavaScript uses for `Number` type of value?**  
Double-precision 64-bit format IEEE 754 values.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Is there `integer` type of value?**  
Accoring to the ECMAScript standard - no. However, some ECMAScript implementations treat integer values as `32-bit ints`, and some implementations even store it that way until they are asked to perform an instruction that's valid on a `Number` but not on a `32-bit integer`.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Explain why `0.1 + 0.2` equals to `0.30000000000000004`**  
??? It is correct behaviour when both interacting values are in IEEE 754 Double-precision 64-bit format.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  
https://en.wikipedia.org/wiki/IEEE_754  

- **Lets say I want to convert text to number, what options do I have?**  
  - To integer-alike type:
    - `parseInt()` function. The second parameter is optional - the base. For example: `parseInt('123', 10); // 123` , `parseInt('010', 10); // 10`
    - `parseInt()` function without base specified while the **text starts with `0`**, for example `parseInt('010');  //  8`. In older browsers, strings beginning with a `0` are assumed to be in octal (radix 8), but this hasn't been the case since 2013 or so.
    - `parseInt()` function without base specified while the **text starts with `0x`**, for example `parseInt('0x10');  //  16`. The `0x` part indicates the text is hexadecimal (base 16). However, the example of `parseInt('0x10', 10);` would result to `0` because we force the base to be exactly decimal (base 10) instead of interpretating for hexadecimal (base 16).
  - To floating-point-alike type:
    - `parseFloat()` - the number is always treated as decimal (base 10).
  - To integer-alike or floating-point-alike numbers:
    - Unary `+` operator. For example: `+ '42';   // 42`, `+ '010';  // 10`, `+ '0x10'; // 16`, `+ '0.25' // 0.25`  
 
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  
    
- **What happens if the `String` we want to convert to `Number` is not numeric?**  
A special value called `NaN` (short for `Not a Number`) is returned if the string is non-numeric. For example: `parseInt('hello', 10); // NaN`, `parseInt('hello'); // NaN`, `parseFloat('hello', 10); // NaN`, `parseFloat('hello'); // NaN`.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What happens if we provide `NaN` as an operand to any mathematical operation?**  
The result will be `NaN`. `NaN` is toxic: if you provide it as an operand to any mathematical operation the result will also be `NaN`.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Is it possible to somehow make sure I am not pasing `NaN` to mathematical operation?**  
Use `isNaN()` built-in function to test if something is `NaN`. Examples:`isNaN(result = 1); // false`, `isNaN(NaN); // true`, etc.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Explain `1 / 0`**  
The result will be `Infinity` - the special JavaScript value.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Explain `-1 / 0`**  
The result will be `-Infinity` - the special JavaScript value.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Is it possible to somehow make sure I am not passing "bad values" (non-numeric ones) like `NaN`, `Infinity` and `-Infinity` to mathematical operation?**  
Use `isFinite` built-in function to test if something is not `NaN`, not `Infinity` and not `-Infinity`. For example: `isFinite(1 / 0); // false`, `isFinite(-Infinity); // false`, `isFinite(NaN); // false`, **`isFinite('test'); // false, because 'test' is Not A Number (NaN)`**, `isFinite(108); // true`, `isFinite(0.1); // true`  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result after someone tries to `parseInt()` or `parseFloat()` String which is partly numeric, for example: `parseInt('123Hello')`, `parseInt('123Hello4')`, `parseFloat('123Hello4')`, etc?**  
The parseInt() and parseFloat() functions parse a string until they reach a character that isn't valid for the specified number format, then return the number parsed up to that point. So all the examples provided (`parseInt('123Hello')`, `parseInt('123Hello4')`, `parseFloat('123Hello4')`) will result to `123`.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result after someone tries to use the unary operator `+` for String to convert to Number while the String is partly numeric, for example: `+ '123Hello'`, `+ '123Hello4'`, `+'123Hello4'`, etc?**  
The `+` operator simply converts the string to `NaN` if there is an invalid character contained within it. So all the examples provided (`+ '123Hello'`, `+ '123Hello4'`, `+'123Hello4'`) will result to `NaN`.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


## String

- **What type of precision JavaScript uses for `String` type of value?**  
Strings in JavaScript are sequences of Unicode characters. More accurately, they are sequences of UTF-16 code units; each code unit is represented by a 16-bit number. Each Unicode character is represented by either 1 or 2 code units.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the difference between 'single' and "double" quotes when quoting text as String values?**  
???  

- **How do I find the length of the string?**  
Use `.length`, for example: `'hello'.length; // 5`  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Can I use String as Object?**  
Yes. String type has methods as well that allows to manipulate the string and access information about it. For example: `'hello'.charAt(0); // "h"`, `'hello, world'.replace('world', 'mars'); // "hello, mars"`, `'hello'.toUpperCase(); // "HELLO"`, etc.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


## Other types

- **What is the value of variable after declaring the variable without assigning a value to it?**  
In JavaScript it is possible to declare a variable without assigning a value to it. If you do this, the variable's type is `undefined`. `undefined` is actually a constant.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the difference between `null` and `undefined` data types?**  
`null` - a value that indicates **a deliberate non-value** (and is only accessible through the `null` keyword). `undefined`- a value of type `undefined` that indicates an uninitialized value — that is, **a value hasn't even been assigned yet**.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What are the value types of Boolean type?**  
`true` and `false`, of course :)  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What does the `Boolean()` function do?**  
Prforms any value to Boolean conversion explicitly.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What types and/or values of types converts to Boolean `false`?**  
`false`, `0`, empty strings (`""`), `NaN`, `null`, and `undefined`.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of `Boolean(0.1)`, `Boolean('123Hello')`, ?**  
Each results to `true`.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of `Boolean(123Hello)`?**  
`SyntaxError: identifier starts immediately after numeric literal (Firefox)`  
`SyntaxError: Unexpected number (Chrome)`  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Identifier_after_number  

- **Do I always need to use `Boolean()` function when I want to use values as Boolean s? For example, do I have to use Boolean within `if` statement, between `>` math operator, etc?**  
JavaScript will silently perform this (`Boolean()`) conversion when it expects a boolean, such as in an `if` statement. For this reason, we sometimes speak simply of "true values" and "false values," meaning values that become `true` and `false`, respectively, when converted to booleans. Alternatively, such values can be called "truthy" and "falsy", respectively.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What does `&&` mean?**  
This is boolean operator (logical "and").  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What does `||` mean?**  
This is boolean operator (logical "or").  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What does `!` mean?**  
This is boolean operator (logical "not").  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


## Variables

- **How do I declare variables?**  
  - `let` - block-level variables, declared variable is available from the block it is enclosed in.  
  - `const` - variables whose values are never intended to change. The variable is available from the block it is declared in.  
  - `var` - the most common declarative keyword. It does not have the restrictions that the other two keywords (`let` and `const`) have. This is because it was traditionally the only way to declare a variable in JavaScript. A variable declared with the var keyword is available from the function it is declared in.  

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the scope of variable declared with `let`?**  
```
// myLetVariable is *not* visible out here

for (let myLetVariable = 0; myLetVariable < 5; myLetVariable++) {
  // myLetVariable is only visible in here
}

// myLetVariable is *not* visible out here
```

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


- **What is the scope of variable declared with `var`?**  
```
// myVarVariable *is* visible out here 

for (var myVarVariable = 0; myVarVariable < 5; myVarVariable++) { 
  // myVarVariable is visible to the whole function 
} 

// myVarVariable *is* visible out here
```

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


- **Can I change the value assigned with `const`?**  
No. Will throw an error.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Can I change the value assigned with `let`?**  
Yes.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **Can I change the value assigned with `var`?**  
Yes.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

### Variables scope: `const`

- **What is the result of the following, explain:**  
```
const a1=5; 
console.log(a1, a2, a3, b, c); 
for(var b=0; b < 5; b++) { 
  const a2=6; 
  var c=77; 
  console.log(a1, a2, a3, b, c); 
} 
const a3=7; 
console.log(a1, a2, a3, b, c);
```  
The result is:  
`ReferenceError: "a2" is not defined`  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Not_defined  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of the following, explain:**  
```
const a1=5; 
console.log(a1, a2, b); 
for(var b=0; b < 5; b++) { 
  console.log(a1, a2, b); 
} 
console.log(a1, a2, b);
```  
The result is:  
`ReferenceError: "a2" is not defined`  

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors/Not_defined  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of the following, explain:**  
```
const a1=5; 
console.log(a1, a3, b, c); 
for(var b=0; b < 5; b++) { 
  const a2=6; 
  var c=77; 
  console.log(a1, a2, a3, b, c); 
} 
const a3=7; 
console.log(a1, a2, a3, b, c);
```
The result is:  
`ReferenceError: can't access lexical declaration 'a3' before initialization`  

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of the following, explain:**  
```
const a1=5; 
console.log(a1, b, c); 
for(var b=0; b < 5; b++) { 
  const a2=6; 
  var c=77; 
  console.log(a1, a2, a3, b, c); 
} 
const a3=7; 
console.log(a1, a2, a3, b, c);
```
The result is:  
`ReferenceError: can't access lexical declaration 'a3' before initialization`  

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of the following, explain:**  
```
const a1=5; 
console.log(a1, b, c); 
for(var b=0; b < 5; b++) { 
  const a2=6; 
  var c=77; 
  console.log(a1, a2, b, c); 
} 
const a3=7; 
console.log(a1, a2, a3, b, c);
```
The result is:  
```
5 undefined undefined
5 6 0 77
5 6 1 77
5 6 2 77
5 6 3 77
5 6 4 77
ReferenceError: a2 is not defined
```

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of the following, explain:**  
```
const a1=5; 
console.log(a1, b, c); 
for(var b=0; b < 5; b++) { 
  const a2=6; 
  var c=77; 
  console.log(a1, a2, b, c); 
} 
const a3=7; 
console.log(a1, a3, b, c);
```
The result is:  
```
5 undefined undefined
5 6 0 77
5 6 1 77
5 6 2 77
5 6 3 77
5 6 4 77
5 7 5 77
undefined
```

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

### Variables scope: `let`

- **What is the result of the following, explain:**
```
let a=1; 
console.log(a, b, c, d); 
for(let b=2; b < 5; b++) { 
  let c=3; 
  console.log(a, b, c, d); 
} 
let d=4; 
console.log(a, b, c, d);  
```
The result is:  
`ReferenceError: b is not defined`  

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of the following, explain:**
```
let a=1; 
console.log(a, c, d);
for(let b=2; b < 5; b++) { 
  let c=3; 
  console.log(a, b, c, d); 
} 
let d=4; 
console.log(a, b, c, d);  
```

The result is:  
`ReferenceError: c is not defined`  

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the result of the following, explain:**
```
let a=1; 
console.log(a, d);
for(let b=2; b < 5; b++) { 
  let c=3; 
  console.log(a, b, c, d); 
} 
let d=4; 
console.log(a, b, c, d);  
```  

The result is:  
`ReferenceError: can't access lexical declaration 'd' before initialization`  

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


- **What is the result of the following, explain:**
```
let a=1; 
console.log(a);
for(let b=2; b < 5; b++) { 
  let c=3;
  console.log(a, b, c); 
} 
let d=4; 
console.log(a, b, c, d);  
```

The result is:  
```
1 
1 2 3 
1 3 3 
1 4 3 
ReferenceError: b is not defined
```

Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


### Variables scope: `var`

- **What is the result of the following, explain:**
```
var a=1; 
console.log(a, b, c, d);
for(var b=2; b < 5; b++) { 
  console.log(a, b, c, d); 
  var c=3;
} 
var d=4; 
console.log(a, b, c, d);  
```

The result is:  
```
1 undefined undefined undefined
1 2         undefined undefined
1 3         3         undefined
1 4         3         undefined
1 5         3         4
```
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What does the "variable visibility scope" mean in JavaScript when talking about variables created by using `var`, `let` or `const` keywords?**  
This means that each keyword encloses the related variable in a visibility scope.  
**Values** of any (`var`, `let`, `const`) are not assigned until the assignment statement is reached in the script-flow - this works all the time.  
However, **the variable itself** may be seen and be in use before the assignment scope, just the value of it will be treated as `undefined`. `var` - lets to see the variable in a global scope (the entire script), `let` - lets to see the variable in a block scope only, `const` - cannot see and use the variable (actually, constant) until it's assignment sentence is reached, error will be thrown otherwise.  
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What is the difference between "block scope" and "function scope" in JavaScript?**  
In JavaScript, **blocks do not have scope**; only **functions have a scope**.  
So if a variable is defined using `var` in a compound statement (for example inside an `if` control structure), it will be visible to the entire function.  
However, starting with ECMAScript 2015, `let` and `const` declarations allow you to create block-scoped variables.  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


## Operators

- **What are the numeric operators in JavaScript? Explain them all.**  
  - `+` - The addition operator produces the sum of numeric operands **or string concatenation**.
  - `-` - The subtraction operator subtracts the two operands, producing their difference.
  - `*` - The multiplication operator produces the product of the operands.
  - `/` - The division operator produces the quotient of its operands where the left operand is the dividend and the right operand is the divisor.
  - `%` - The remainder operator returns the remainder left over when one operand is divided by a second operand. It always takes the sign of the dividend.
  - `**` - The exponentiation operator returns the result of raising first operand to the power second operand. that is, var1 ^var2, in the preceding statement, where var1 and var2 are variables. Exponentiation operator is right associative. a ** b ** c is equal to a ** (b ** c).
  - `++` - The increment operator increments (adds one to) its operand and returns a value.
    - If used postfix, with operator after operand (for example, x++), then it returns the value before incrementing.
    - If used prefix with operator before operand (for example, ++x), then it returns the value after incrementing.
  - `--` - The decrement operator decrements (subtracts one from) its operand and returns a value.
    - If used postfix (for example, x--), then it returns the value before decrementing.
    - If used prefix (for example, --x), then it returns the value after decrementing.
  - `-` - The unary negation operator precedes its operand and negates it.
  - `+` - The unary plus operator precedes its operand and evaluates to its operand but attempts to convert it into a number, if it isn't already. Although unary negation (`-`) also can convert non-numbers, unary plus is the fastest and preferred way of converting something into a number, because it does not perform any other operations on the number. It can convert string representations of integers and floats, as well as the non-string values `true`, `false`, and `null`. Integers in both decimal and hexadecimal ("0x"-prefixed) formats are supported. Negative numbers are supported (though not for hex). If it cannot parse a particular value, it will evaluate to `NaN`.  
  - `=` - assignment of values
  - `+=` - compound assignment statement
  - `-=` - compound assignment statement
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators

- **What happens to the numbers and/or other values if it is mixed with String type values and `+` operator?**  
If you add a string to a number (or other value) everything is converted in to a string first. For example: 
  - `'3' + 4 + 5;  // "345"` 
  - `'3' + '4' + 5; // "345"`
  - `3 + '4' + 5; // "345"`
  - `3 + 4 + '5'; // "75"`
  - `3 + 4 + true; // 8 // Number!` 
  - `3 + 4 + false // 7 // Number!`
  - `3 + "4" + true; // "34true"`
  - `3 + 4 + '4' + true // "74true"`
  - `3 + 4 + '4' + true + '4' + 4 + 3; // "74true443"`
  - etc.
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  

- **What are the ways to convert something into a String?**  
  - Add an empty string to something
  - ???
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  
  
- **What are the comparission operators in JavaScript?**  
`<`, `>`, `<=`, `>=`, `==` (performs type coercion, for example: `123 == '123'; // true`, `1 == true; // true`), `===` (to avoid type coercion, for example: `123 === '123'; // false`, `1 === true;    // false`), `!=`, `!==`  
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators  

- **Are there any bitwise operators in JavaScript?**  
Yes, there is.  
  - Bitwise AND (`a & b`) Returns a 1 in each bit position for which the corresponding bits of both operands are 1's.
  - Bitwise OR (`a | b`) Returns a 1 in each bit position for which the corresponding bits of either or both operands are 1's.
  - Bitwise XOR (`a ^ b`) Returns a 1 in each bit position for which the corresponding bits of either but not both operands are 1's.
  - Bitwise NOT (`~ a`) Inverts the bits of its operand.
  - Left shift (`a << b`) Shifts a in binary representation b (< 32) bits to the left, shifting in 0's from the right.
  - Sign-propagating right shift (`a >> b`) Shifts a in binary representation b (< 32) bits to the right, discarding bits shifted off.
  - Zero-fill right shift (`a >>> b`) Shifts a in binary representation b (< 32) bits to the right, discarding bits shifted off, and shifting in 0's from the left.  
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Bitwise_Operators  


## Control structures

- **What control structures does JavaScript have?**  
JavaScript has a similar set of control structures to other languages in the C family.  
  - `if` and `else`:  
  ```
  var name = 'kittens';
  if (name == 'puppies') {
    name += ' woof';
  } else if (name == 'kittens') {
    name += ' meow';
  } else {
    name += '!';
  }
  name == 'kittens meow';
  ```
  - `while`:
  ```
  while (true) {
    // an infinite loop!
  }
  ```
  - `do-while`:
  ```
  var input;
  do {
    input = get_input();
  } while (inputIsNotValid(input));
  ```
  - `for` loop:
  ```
  for (var i = 0; i < 5; i++) {
    // Will execute 5 times
  }
  ```
  - **`for`...`of`**:
  ```
  for (let value of array) {
    // do something with value
  }
  ```
  - **`for`...`in`**:
  ```
  for (let property in object) {
    // do something with object property
  }
  ```
  - `&&` - This is boolean operator (logical "and"). The `&&` operator uses short-circuit logic, which means whether it will execute their second operand is dependent on the first. This is **useful for checking for `null` objects before accessing their attributes**, for example: `var name = o && o.getName();`
  - `||` - This is boolean operator (logical "or"). The `||` operator uses short-circuit logic, which means whether it will execute their second operand is dependent on the first. This is **useful for caching values** (when falsy values are invalid), for example: `var name = cachedName || (cachedName = getName());`
  - Ternary operator for conditional expressions. For example: `var allowed = (age > 18) ? 'yes' : 'no';`  
  - `switch`:
  ```
  switch (action) {
    case 'draw':
      drawIt();
      break;
    case 'eat':
      eatIt();
      break;
    default:
      doNothing();
  }
  
  switch (a) {
    case 1: // fallthrough
    case 2:
      eatIt();
      break;
    default:
      doNothing();
  }
  
  switch (1 + 3) {
    case 2 + 2: // Will hit this, because (1 + 3) === (2 + 2)
      yay();
      break;
    default:
      neverhappens();
  }
  ```
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  
  
- **Which of equality checks (`==` or `===`) is being performed between `switch` and `case` statement?**  
Comparisons take place between the two using the `===` operator.  
Read more:  
https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  


## Objects

- **What kind of data structures implemented in other languages are the most similar to `Object` data structure in JavaScript?**  
  - Dictionaries in Python.
  - Hashes in Perl and Ruby.
  - Hash tables in C and C++.
  - HashMaps in Java.
  - Associative arrays in PHP.
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  
  
- **What type of variable is used for Object property and what type of variable is used for Object property value? For example: `{name: value}`**  
  - The "name" part is a JavaScript string
  - The value can be any JavaScript value — including more objects.
  
  Read more:  
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript  
  
- **What are thay ways to create an empty object in JavaScript?**  
  1. `var obj = new Object();`
  2. `var obj = {};`  - Object literal syntax. This syntax is also the core of JSON format and should be preferred at all times.  
  
- **What is the way of initializing object with values?**  
You just add `name: value` pairs, separate by `,`. For example:  
```
var obj = {
  name: 'Carrot',
  for: 'Max', // 'for' is a reserved word, use '_for' instead.
  details: {
    color: 'orange',
    size: 12
  }
};
```

- **What are the ways to access attributes of the Object?**  
Use one of two ways: "dot notation" or "brackets notation". For example:  
```
obj.details.color; // orange
obj['details']['size']; // 12

obj.name = 'Simon';
var name = obj.name;
```

- **How can I create a class (like in PHP, Java, etc.) and object out of it (again, like in PHP, Java, etc.)?**  
In JavaScript you create `Prototype` (aka. class, for example `Person`) and then `instance` of that prototype (aka. object, for example `you`). Which in code looks like this:  
```
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Define an object
var you = new Person('You', 24); 
// We are creating a new person named "You" aged 24.
```
- **Explain the following usage of brackets notation and `prompt`:**  
```
var user = prompt('what is your key?')
obj[user] = prompt('what is its value?')
```
The method has the advantage that the name of the property is provided as a string, which means it can be calculated at run-time. However, using this method prevents some JavaScript engine and minifier optimizations being applied.

- **How can I set the value to property named `for` (or a value to other property with the name of JavaScript keyword) for my own object?**  
Use barckets notation. For example:  
```
obj.for = 'Simon'; // Syntax error, because 'for' is a reserved word
obj['for'] = 'Simon'; // works fine
```

  
  




## Etc.


- **Explain the following. `null > 0` results to `false`, `null < 0` results to `false`, `null == 0` results to `false`. Why `null >= 0` results to `true`?**  
Read more:  
???  



