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

- **Can JScript be run on any browser (JavaScript engine)?**  
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

- **Is JScript engine different from JavaScript engines?**  
Read more:  
???  

- **Explain the following. `null > 0` results to `false`, `null < 0` results to `false`, `null == 0` results to `false`. Why `null >= 0` results to `true`?**  
Read more:  
???  



