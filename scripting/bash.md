## Shebang
#! /bin/bash  </br>
This helps the os understand that the script is a executable and can be directly run using 'bash'.

## Fail fast
'set -eo pipefail'  </br>
-u option can also be included along with '-eo'. to capture unbounded variable. </br>
shopt -s inherit_errexit  : is also added to inherit the -e option in subscript shell sessions. </br> 
Reference: https://dougrichardson.us/2018/08/03/fail-fast-bash-scripting.html