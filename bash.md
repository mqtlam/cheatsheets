Bash
====

for loop
--------

Traditional for loop:

```bash
for i in $(seq 1 10); do
    echo $i
done
```

"defensive bash scripting"
--------------------------

http://www.kfirlavi.com/blog/2012/11/14/defensive-bash-programming/

```bash
#!/bin/bash

# global variables
readonly PROGRAM_NAME=$(basename $0)

# print usage function
usage() {
    echo "${PROGRAM_NAME} string1 string2"
    echo "this program prints two strings..."
    echo "flags: string1 string2 ..."
}

# check arguments: require two arguments
if [ "$#" -ne 2 ]; then
    echo "Illegal number of parameters"
    usage
    exit 1
fi

readonly STRING1=$1
readonly STRING2=$2

# meaningful function names
do_stuff() {
    # local variables
    local argument1=$1
    local argument2=$2

    # do stuff...
    echo "${argument1} ${argument2}"
}

# main function is the main script
main() {
    do_stuff $STRING1 $STRING2
}
main
```
