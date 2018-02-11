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
Sass preprocessing stands for translating (compiling) the code written in sass-compatible format (`*.scss`) to regular CSS format (`*.css`).  We can use `sass` command to compile scss files into css (example: `sass input.scss output.css`). The compilation may be done on the directories level as well (example: `sass app/sass:public/stylesheets` - sass would compile all files in the `app/sass` folder to the css files in `public/stylesheets` folder).
 ">⌘</a>
 
 - What does "Watcher of Sass preprocessing" mean?
 <a href="#" title="
Adding flag `--watch` to sass command will compile on-the-fly, it is on the time you save the file (example: `sass --watch input.scss output.css` compiles `output.css` every time `input.scss` is saved). The compilation may be done on the directory level as well (example: `sass --watch app/sass:public/stylesheets` - sass would watch all files in the `app/sass` folder for changes, and compile CSS to the `public/stylesheets` folder).
 ">⌘</a>
 
 
