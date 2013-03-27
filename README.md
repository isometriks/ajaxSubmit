ajaxSubmit
==========

ajaxSubmit is used to submit multipart form data. It checks the enctype of your form and tries to use FormData if possible. 



Usage
==

HTML

    <form id="myform" method="post" enctype="multipart/form-data">
        <input type="file" name="myfile">
        <input type="text" name="filename">
        <button type="submit">Upload</button>
    </form>

Javascript

    $('#myform').submit(function(e){
    
        $(this).ajaxSubmit(function(data, textStatus, xhr){
            // ...
        }); 
        
        e.preventDefault();
    }); 

Note that ajaxSubmit still works without multipart data, and no enctype. If you forget the enctype it does not add it for you and files will not be uploaded. Here is a simple example (the javascript will be exactly the same):

    <form id="myform" method="post" action="/ping">
        <input type="url" name="url">
        <button type="submit">Ping</button>
    </form>

Some things to note:

- If you supply no method, POST is chosen by default. 
- If you supply no action, the current url is used (location.href)
- You can supply any `option` that is normally supplied to $.ajax
- Currently this only takes the first file in the element. (PER input element, not total)
