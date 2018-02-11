# Sass
There are some questions that needs to be answered by every senior web developer anytime. 


## General
- What is Sass?
<a href="#" title="
 Sass is a CSS extension language. Sass lets you use features that don't exist in CSS yet like variables, nesting, mixins, inheritance, etc.
 ">⌘</a>

- Do you need Ruby for sass to work on your machine?
<a href="#" title="
Yes, you need it. Before you start using Sass you will need to install Ruby. Ruby uses Gems to manage its various packages of code like Sass. However, can I hack somehow and install sass without Ruby???
 ">⌘</a>
 
 - What is the difference between `sass` and `scss`?
 <a href="#" title="Sass (CSS extension language) 3 introduces a new syntax known as SCSS which is fully compatible with the syntax of CSS, while still supporting the full power of Sass. This means that every valid CSS stylesheet is a valid SCSS file with the same meaning. In addition, SCSS understands most CSS hacks and vendor-specific syntax, such as IE's old filter syntax.
 ">⌘</a>
 
 - What is the comand `sass` for?
<a href="#" title="
Converts SCSS or Sass files to CSS. Usage: `sass [options] [INPUT] [OUTPUT]`
 ">⌘</a>
 
 - What does "Sass preprocessing" mean?
<a href="#" title="
Sass preprocessing stands for translating (compiling) the code written in sass-compatible format (`*.scss`) to regular CSS format (`*.css`).  We can use `sass` command to compile scss files into CSS (example: `sass input.scss output.css`).
">⌘</a>
 
 - What does "Watcher of Sass preprocessing" mean?
 <a href="#" title="
Adding flag `--watch` to sass command will compile on-the-fly, it is on the time you save the file (example: `sass --watch input.scss output.css` compiles `output.css` every time `input.scss` is saved). The compilation may be done on the directory level as well (example: `sass --watch app/sass:public/stylesheets` - sass would watch all files in the `app/sass` folder for changes, and compile CSS to the `public/stylesheets` folder).
 ">⌘</a>
 
 - Can we compile directory containing Saas files into CSS files on another directory without using `--watch` option?
 <a href="#" title="
The compilation IS NOT POSSIBLE on the directories level without a special option added (NOT WORKING example1: `sass app/sass:public/stylesheets`, NOT WORKING example2: `sass app/sass public/stylesheets` - sass would NOT compile on directory level these ways on Sass 3.5.5 (Bleeding Edge)). Adding `--watch` option may be the solution to compile files on a directory-level.
 ">⌘</a>
 
 - What does "Sass variable" mean?
 <a href="#" title="
Sass uses the `$` symbol to make something a variable. When the Sass is processed, it takes the variables we define for the $variable and outputs normal CSS with our variable value placed in the CSS. Example: `$primary-color: #333; body { font: 100% $font-stack; color: $primary-color; }` converts to `body { font: 100% Helvetica, sans-serif; color: #333; }`.
">⌘</a>
 
 - What does "Sass nesting" mean?
 <a href="#" title="
Sass will let you nest your CSS selectors in a way that follows the same visual hierarchy of your HTML. For example: `nav { ul { list-style: none; } li { display: inline-block; } a { display: block; } }` will become `nav ul { list-style: none; } nav li { display: inline-block; } nav a { display: block; }`
">⌘</a>

 - What does "Sass partials" mean?
 <a href="#" title="
You can create partial Sass files that contain little snippets of CSS that you can include in other Sass files. This is a great way to modularize your CSS and help keep things easier to maintain. A partial is simply a Sass file named with a leading underscore. You might name it something like `_partial.scss`. The underscore lets Sass know that the file is only a partial file and that it should not be generated into a CSS file. Sass partials are used with the `@import` directive.
">⌘</a>

 - What is the difference between "CSS import" and "Sass import"?
 <a href="#" title="
CSS has an import option that lets you split your CSS into smaller, more maintainable portions. The only drawback is that each time you use `@import` in CSS it creates another HTTP request. Sass builds on top of the current CSS `@import` but instead of requiring an HTTP request, Sass will take the file that you want to import and combine it with the file you're importing into so you can serve a single CSS file to the web browser. When you import a file over Sass import you don't need to include the file extension `.scss`. Sass will figure it out. 
">⌘</a>

 - What does "Sass mixins" mean?
 <a href="#" title="
We can think of Sass mixins as functions for CSS. Some things in CSS are a bit tedious to write, especially with CSS3 and the many vendor prefixes that exist. A mixin lets you make groups of CSS declarations that you want to reuse throughout your site. You can even pass in values to make your mixin more flexible. To create a mixin you use the `@mixin` directive and give it a name. After you create your mixin, you can then use it as a CSS declaration starting with `@include` followed by the name of the mixin. Example: `@mixin border-radius($radius) { -webkit-border-radius: $radius; -moz-border-radius: $radius; -ms-border-radius: $radius; border-radius: $radius;} .box { @include border-radius(10px); }`
">⌘</a>

 - What is the difference between `@import` and `@include` in Sass?  
 Sass `@import` is for importing files - Sass partials (for example: `@import 'reset'`). Sass `@include` is for using different "CSS-like functions" - Sass mixins (for example: `@include border-radius(10px);`). Worth visiting: https://github.com/madskristensen/WebEssentials2013/issues/1571

