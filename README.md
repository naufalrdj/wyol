# WYOL (Write Your Own Linter) -- Tokopedia EP Initiatives 

Introduction
------------------------------
WYOL is initiatives that comes up, because Katalon IDE doesnt solves our Design Pattern, and Agreement about Design Pattern. 
WYOL currently only works with TS / JS files in Katalon

How to Run WYOL
------------------------------
Should be run in Linux System

Place the bash script below in your environment path and name it "rat".

```
#!/bin/bash

deno run --allow-read --allow-env ~/wyol/main.js "$@"
```

There are 3 modes to use WYOL.
            
1) Inside the target folder, enter "rat". Dirtyrat will lint all JS files, including subfolders recursively, except when the name of the folder is IGNORE.

2) Enter ```"rat example.js"``` WYOL will lint just example.js.

3) Enter "rat example.html". WYOL will lint all JS files that are linked by example.html as long as the links follow exactly the syntax shown below (whitespaces are meaningful). Any linked script that is not supposed to be linted like (Google Analytics, for example) must have its link written in a slightly different syntax, like inserting an excedent whitespace.

```        
<script type="module" src="/example.js"></script>
```
        
WYOL issues errors and warnings. In case of error it exits when finds the first one or else it could point tens of errors that really don't exist, just because the first error breaks the structure of the following lines of code.
        
WARNING: WYOL erases the content of your terminal (the history of shell remains intact). If you don't want this, just comment the first line of the function showOpenMessage in the file main.js.
