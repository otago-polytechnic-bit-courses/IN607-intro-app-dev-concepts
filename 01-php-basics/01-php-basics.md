# PHP Basics

## What is PHP?
**PHP** or **PHP Hypertext Preprocessor** is one of the most widely-used open-source general-purpose scripting languages used mainly for web development.  

A **PHP** page contains **HTML** with embedded **PHP** code, for example:

```php
<html>
  <head>
    <title>PHP Examples</title>
  </head>
  <body>
    <?php
    echo "Hello, World!"
    ?>
  </body>
</html>
```

Much like the `<script>` & `</script>` in **JavaScript**, **PHP** uses `<?php` & `?>` to enclose its code. 

So, what is the difference between **PHP** & **JavaScript**?
The code is executed on the server, generating **HTML** which is then sent to the client. The client receives the **HTML**, but does not know how it was generated or even the underlying code.

## Basic Syntax 

### Variables
In **PHP**, a variable starts with the `$` sign, followed by the name of the variable:

```php
<?php 
$a = "Hello, World!"; // string
$b = 1; // integer
$c = 1.5; // float or double
$d = false; // boolean
echo $a // Hello, World!
?> 
```

**Question:** What is one syntax difference between **C#** & **PHP**?

**PHP** also allows type casting or explicit casting & is handled by the interpreter. 

```php
<?php 
$x = 1;
$y = 1.5;
$z = $x + $y;
$z = $x + (int) $y;
echo $z; // 2
?> 
```

`var_dump` is use to check a variable's data type.

```php
<?php 
$a = "Hello, World!";
$b = 1; 
var_dump($a); // string(13) "Hello, World!"
var_dump($b); // int(1) 
?> 
```

**Question:** What does 13 in `string(13)` represent?

**Resource:** https://www.php.net/manual/en/language.variables.php

There are **four** main types of operators - arithmetic, assignment, comparison & logical. 

**Resource:** https://www.php.net/manual/en/language.operators.php

Other rules for **PHP** variables:
- Must start with a letter or the `_` underscore character.
- Can not start with a number.
Can only contain alpha numeric characters & underscores.
- Names are case sensitive, i.e., `$hello` & `$HELLO` are two different variables.

### Control Structures
Code is grouped into two categories:
- sequential - executing the code in the order in which it is written.
- decision - executing the code depending on the value of a condition.

**Question:** What is a control structure?

Lets look at an example:

```php
<?php
if (condition is true) { 
    block one
} else {
    block two
}
?>
```

- `if (condition is true)` - the control structure.
- block one - the code to be executed, if the condition is `true`.
- `else` is the fallback, if the condition is `false`.
- block two - the code to be executed if the condition is `false`.

As you can see, this is same as **C#** & **JavaScript**.

Another example:

```php
<?php
    $first_number = 5;
    $second_number = 10;

    if ($first_number > $second_number) {
        echo "$first_number is greater than $second_number";
    } else {
        echo "$second_number is greater than $first_number";
    }
?>
```

**Output:** `10 is greater than 5`

**Resources:** 
- https://www.php.net/manual/en/control-structures.if.php
- https://www.php.net/manual/en/control-structures.else.php
- https://www.php.net/manual/en/control-structures.elseif.php
- https://www.php.net/manual/en/control-structures.alternative-syntax.php

**PHP** also has a **switch statement**.

```php
<?php
switch (condition) {
    case one:
        block one
    break;

    case two:
        block two
    break;

    default:
    break;
}
?>
```

- `switch (condition)` - the control structure.
- `case` - the code to be executed depending on the value of the condition.
- `default` - the code to be executed if the value of the condition is not met.


Lets look at example:

```php
<?php
$today = "Wednesday";

switch ($today) {
    case "Friday":
        echo "I think it is time to quit my job";
    break;

    case "Saturday":
        echo "Lets do some housework";
    break;

    case "Sunday":
        echo "Church";
    break;

    default:
        echo "Have a nice day at work...ha";
    break;
}
?>
```

**Resource:** https://www.php.net/manual/en/control-structures.switch.php

### Loops
For, for-each, do & do-while loop much the same as **C#** & **JavaScript**.

Here are some examples:

```php
<?php
for ($i = 0; $i < 10; $i++) {
    $value = 10 * $i;
    echo "$value \n";
}
?>
```

**Output:** `0 10 20 30 40 50 60 70 80 90`

```php
<?php
$numbers = array(0, 1, 2, 3, 4, 5);

foreach($numbers as $nums){
    $value = 10 * $nums;
    echo "$value \n";
}
?>
```
**Output:** `0 10 20 30 40 50`

**Resources:**
- https://www.php.net/manual/en/control-structures.for.php
- https://www.php.net/manual/en/control-structures.foreach.php
- https://www.php.net/manual/en/control-structures.while.php
- https://www.php.net/manual/en/control-structures.do.while.php

### Functions
**Resources:**
You may define a function such as the following:
```php
<?php
function sum ($arg_one, $arg_two) {
    return $arg_one + $arg_two;
}

echo sum(1, 2); // 3
?>
```

**Resource:** https://www.php.net/manual/en/functions.user-defined.php

You can define a function without a name. This called an **anonymous function** or a **closure**. 

```php
<?php
$greeting = function($name) {
    printf("Hello my name is $name");
};

$greeting("John Doe"); // Hello my name is John Doe
?>
```

**Resource:** https://www.php.net/manual/en/functions.anonymous.php

Below are additional resources to other types of functions.
- https://www.php.net/manual/en/functions.arrow.php
- https://www.php.net/manual/en/functions.internal.php
- https://www.php.net/manual/en/functions.variable-functions.php

### Error Handling

Firstly, we must answer the following questions:
- What is an error? 

  An unexpected result that cannot be handled by the program itself. Errors are resolved by fixing the program. An example of error is an infinite loop. 

- What is an exception?

  An exception is an unexpected result that can be handled by the program itself. An example of an exception is opening a file that does not exist. 
  
  **How do we handle this?** by either creating the file or giving the option to select a file from your file system.
  
- Why exception handling? 

  Avoid unexpected results that can annoy end users and improving security by not exposing information which malicious may use. 

Let look at a common example:

```php
<?php
$denominator = 0;
echo 2 / $denominator;
?>
```

**Question:** What is the value of `2 / $denominator`?

Modified example:

```php
<?php
$denominator = 0;

if ($denominator != 0) {
    echo 2 / $denominator;
} else {
    echo "Cannot divide by zero (0)";
}
?>
```

For more thorough exception handling, we will look at try/catch blocks:

```php
<?php
try {
    // Code that could potentially throw an exception
}
catch (Exception $e) {
    // Exception handling code
}
?>
```

A more practical example:
```php
<?php
try {
    $some_msg = "Some exception message...";
    throw new Exception($some_msg); // Throwing a new exception
}
catch (Exception $e) {
    echo "Error message: " . $e->getMessage();
}
?>
```

From here, we will go on a small tangent...what is the `.` equivalent to in **C#** & **JavaScript**?

**Resource:** https://www.php.net/manual/en/language.exceptions.php

### File Processing
There may be a time where you need to create, update or delete a file. 

The example below is checking if a file exists:

```php
<?php
if (file_exists("sample.txt")) {    
    echo "sample.txt does exist";
} else {
    echo "sample.txt does not exist";
} 
?>
```

How about reading the contents:
```php
echo file_get_contents("sample.txt");
```

or deleting the file:

```php
<?php
if (!unlink("sample.txt")) {
     echo "Could not delete sample.txt";
} else {
     echo "sample.txt successfully deleted"; 
}
?>
```

**Resource:** https://www.php.net/manual/en/ref.filesystem.php
