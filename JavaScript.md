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

- **Explain the following. `null > 0` results to `false`, `null < 0` results to `false`, `null == 0` results to `false`. Why `null >= 0` results to `true`?**  
Read more:  
???  



