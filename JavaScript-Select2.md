Source:  
https://select2.org/  

- **What is Select2?**  
The jQuery replacement for select boxes.  
Select2 gives a customizable select box with support for searching, tagging, remote data sets, infinite scrolling, and many other highly used options.  

- **What is Asynchronous Module Definition (AMD) loader?**  
Asynchronous module definition (AMD) is a specification for the programming language JavaScript. It defines an application programming interface (API) that defines code module and their dependencies, and loads them asynchronously if desired. Implementations of AMD provide the following benefits:  
  - Website performance improvements. AMD implementations load smaller JavaScript files, and then only when they are needed.
  - Fewer page errors. AMD implementations allow developers to define dependencies that must load before a module is executed, so the module does not try to use outside code that is not available yet.  
  
In addition to loading multiple JavaScript files at runtime, AMD implementations allow developers to encapsulate code in smaller, more logically-organized files, in a way similar to other programming languages such as Java. For production and deployment, developers can concatenate and minify JavaScript modules based on an AMD API into one file, the same as traditional JavaScript.  

The AMD specification is implemented by Dojo Toolkit, RequireJS, and ScriptManJS.  
Read more:  
https://en.wikipedia.org/wiki/Asynchronous_module_definition  

- **Explain: `$.fn.select2.defaults.set('amdBase', 'select2/');`**  
Specifies the base AMD loader path to be used for select2 dependency resolution. This option typically doesn't need to be changed, but is available for situations where module names may change as a result of certain build environments.  

- **Explain: `$.fn.select2.defaults.set('amdLanguageBase', 'select2/i18n/');`**  
Specifies the base AMD loader language path to be used for select2 language file resolution. This option typically doesn't need to be changed, but is available for situations where module names may change as a result of certain build environments.  

- **To which element and to where Select2 attaches the dropdown by default?**  
By default, Select2 will attach the dropdown to the end of the body and will absolutely position it to appear above or below the selection container.  
Select2 will display the dropdown above the container if there is not enough space below the container, but there is enough space above it.  
Read more:  
https://select2.org/dropdown#dropdown-placement  

- **Explain the following:**  
```
<div id="myModal" class="modal fade" tabindex="-1" role="dialog" aria-hidden="true">
    ...
    <select id="mySelect2">
        ...
    </select>
    ...
</div>

...

<script>
    $('#mySelect2').select2({
        dropdownParent: $('#myModal')
    });
</script>
```

The ansswer:  
We attach the dropdown to the modal itself with the dropdownParent setting. This will cause the dropdown to be attached to the modal, rather than the <body> element.  
**Alternatively**, we may simply globally override Bootstrap's behavior:  
```
// Do this before you initialize any of your modals
$.fn.modal.Constructor.prototype.enforceFocus = function() {};
```
  
- **Explain the following:**  
```
$('.js-example-basic-single').select2({
  placeholder: 'Select an option'
});
```
We configure custom options when initialize Select2. This is done by passing an object in the call to `.select2()`.  


