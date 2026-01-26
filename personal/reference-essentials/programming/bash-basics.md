# Bash Basics

## Running Your Script

To ensure the script runs, use the **shebang** (`#!/bin/bash`) at the top of your script file, which indicates what program to use to execute the file. For example:

{% code title="shebang.sh" fullWidth="false" %}
```bash
#!/bin/bash

Code goes here
```
{% endcode %}

In addition, you must ensure that the script has execute permissions, which can be done with the `chmod` command. For example:

{% code title="CLI" %}
```bash
chmod +x shebang.sh
```
{% endcode %}

After this, you can execute your script by using `./`_`filename`_. For example:

{% code title="CLI" %}
```bash
./shebang.sh
```
{% endcode %}

## Printing and Comments

To print out text, use the `echo` command preceded by a variable or text, wrapped in single or double quotes. Comments are indicated by the `#` preceding text/.

```shellscript
#!/bin/bash

# This is a comment!
echo "Hello World!" # This prints "Hello World!
```

## Command Chaining

To execute multiple commands on the same line, use the semicolon (`;`) at the end of each command.

```shellscript
echo "Hello"; echo "World"
# This outputs "HelloWorld"
```

## Variables

Variables store and save data. Do not include spaces between the variables. To access a variable, use the `$` sign.

```shellscript
age=22
name="Ben"

echo "My age is $age and my name is $name" 
# The output is: "My age is 22 and my name is Ben" 
```

### Global vs. Local

All variables are considered global unless declared otherwise. To declare a local variable, use the `local` keyword before defining the variable. A local variable is only accessible to the function scope in which it is defined. For example, if a local variable is defined inside of a function, it will not be accessible outside of that function, as it is **local to the function**.&#x20;

```shellscript
local age=22 # This is local
name="Ben" # This is global
```

## Functions

Functions are blocks of code that can be called using an identifier and can be called multiple times.

{% code title="functions.sh" %}
```shellscript
functionName () {
    echo "Test"
}

functionName # Outputs "Test"
```
{% endcode %}

## Reading Input

User input can be read using the `read` command followed by the variable name to assign the input to.

```shellscript
echo "Please input your name."
read name
echo "Your name is $name"
```

