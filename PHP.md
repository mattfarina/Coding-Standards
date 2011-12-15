# PHP Coding Standard

This coding standard is one projects can use and reference for their own needs.

## Indenting and Whitespace

Use and indentation of two (2) spaces and no tabs. This part of a coding standard can be debated on the level of arguing religions. As the creator of this spec I'm going with two spaces.

Line endings should have no trailing space. I cannot believe I need to write this but all too often trailing spaces end up in a file.

New lines shall use the Unix line ending (\n) and not the Windows line ending (\r\n). The [history of new lines](https://en.wikipedia.org/wiki/Newline#History) can be quite fascinating as our digital age is tied to line ending characters from an era of machines printing characters.

## Line length and wrapping

Limit lines to 80 characters. While screens are wider than they used to be 80 characters lets some of use use split screens, read files in terminals (when needed), and play nice with others who work this way. I suggest using a monospace font and having your text editor or IDE provide a gutter at 80 characters so you can easily see the cut off.

Word wrapping is dangerous to use in code files as it can introduce hard to track down bugs. Turn off word wrapping in your text editor or IDE. For code see below.

_Right:_

    $foo = 'This is a reeeeeeeeeeeeeeeeeaaaaaaly long line that wraps to the'
         . 'next line.';

_Bad:_

    $foo = 'This is a reeeeeeeeeeeeeeeeeaaaaaaly long line that wraps to the
            next line.';

Control structure can exceed 80 characters. They should be written simply and clearly.

## Naming Conventions

* Classes should be named in capital CamelCase.
* Methods should be named in lower camelCase.

## Operators

Operators that come between two values (e.g., +, -, =, !=, ==, >, <) shall have a space before and after the operator.

_Right:_

    $foo + $bar

_Wrong:_

    $foo+$bar

This is done for readability. Unary operators do not have a space between the value and the operator (e.g., `$foo++`).

## Casting

For readability, when casting put a space between the type and the variable.

_Right:_

    $foo = (int) $bar;

_Wrong:_

    $foo = (int)$bar;

## Braces

The opening braces go on the same line as the statement.

_Right:_

    if (TRUE) {
      print "Winner, winner, chicken dinner!";
    }

_Wrong:_

    if (TRUE)
    {
      print "Noooooooooo!";
    }

## Control Structures

Control structures should have a single space between the statement and the opening parentheses.

### If Statements

If statements should use the format `if`, `elseif`, `else`. `else if` should not be used.

_Right:_

    if (condition1 || condition2) {
        action1;
    }
    elseif (condition3 && condition4) {
        action2;
    }
    else {
        defaultaction;
    }

_Wrong:_

    if (condition1 || condition2) {
        action1;
    } else if (condition3 && condition4) {
        action2;
    } else {
        defaultaction;
    }

#### Ternary vs. If/Else

Ternary operators should be used in lieue of `if/else` statements only
if:

* There are actually two values
* The ternary does not result in re-assigning a variable to itself
* The line does not exceed the maximum line length
* The values to be assigned are scaler (int, float, boolean, string,
  etc.)

Ternaries should _never_ be nested.

Parens may be used for grouping whenever doing so increases readibility.

Finally, there is nothing wrong with writing out an `if/else`. It is
almost always more readible and rarely has counterintutive side effects.

_Right:_


```php
<?php
$foo = $use_magic ? 'magic' : 'no magic';
?>
```

_Wrong:_


```php
<?php
// Don't re-assign the same value
$foo = empty($foo) ? $bar : $foo;
?>
```

_Wrong:_


```php
<?php
// Don't use complex types:
$foo = $use_array ? $my_array : $my_object;
?>
```

_Wrong and bug prone:_

```php
<?php
$a = $b ? $c : $d ? $e : $g;
?>
```


### Switch Statements

Use a switch statement to test multiple conditions.

It is a good idea to use switch statements instead of `if/else` when:

* The test is a simple equality test.
* There are more than two possibilities, OR
* Multiple conditions map to the same action

Do not us a switch statement when there are only one or two conditions.
`if/else` is easier to read (and faster to execute).

_Good:_

```php
<?php

switch (condition) {
  case 1:
    action1;
    break;

  case 2:
  case 3:
    action2;
    break;

  default:
    defaultaction;
}

?>
```

### do-while Statements

_Good:_

    do {
      actions;
    } while ($condition);

## Function Calls

Function calls should not have a space between the end of the function name and the first parentheses. This helps them be read differently from control structures. There should be no space between the first parentheses and the first argument or the last parentheses and the last argument.

_Right:_

    $foo = bar($first, $second, $third);

_Wrong:_

    $foo = bar ( $first, $second, $third );

When a function call exceeds the 80 character limit, the call can be
split across multiple lines, preferably by putting the arguments one on
each line.

```php
<?php
$very_long_variable_name = very_long_function_with_lots_of_arguments(
  $argument1,
  $argument2,
  $argument3
);
?>
```

## Function Declarations

Between the name of the function and the first parentheses there is no space. There is, also, no space between the first parentheses and first argument or the last parentheses and last argument.

Argument with default options should come after required arguments.

_Right:_

``php
<?php
function funfun($arg1, $arg2, $arg3 = array()) {
  // Do something here.
}
?>
```

_All Kinds of Wrong:_

```php
<?php
function funfun ( $arg1, $arg2 = array(), $arg3 )
{
  // Don't even think of writing it like this or doing anything here if your
  // style looks remotely like this. Instead go put yourself in timeout.
}
?>
```

_So wrong that if you write it this way we will disavow any knowledge of
you_

```php
<?php
function
  funfun(
    $arg1 = 123,
    $arg2
  )
  {
    return;
  }
?>
```

When a function declaration is very long, it can be declared on multiple
lines. But the format should be as follows:

_Right:_

```php
<?php
function my_inexplicably_and_ridiculously_long_function_name(
    $argument1, // Double indent.
    $argument2
  ) {
  // First line goes here.
}
?>
```

### Varargs

PHP allows you to use "varargs"-style argument passing. In this case, a
function allows an unspecified number of parameters. The caller is
responsible for passing in the desired number of arguments.

Varargs should be used when:

* A function really does allow an arbitary number of arguments. Example:
  `printf()`.
* The function is passing unknown parameters to an inner function.

Varargs should _not_ be used when:

* A function has many, but not arbitrarily many, paramters. Varargs is not a shortcut for declaring
  parameters.

Other usage guidelines for varargs:

If there are known parameters, they should be declared, leaving
variable arguments at the end. This will improve the readibility of the
code and also help IDEs that attempt to aid code completion.


_Right:_

```php
<?php
/**
 * Echo everything that is passed in.
 */
function printAll() {
  $args = func_get_args();
  foreach ($args as $arg) {
    print $arg . PHP_EOL;
  }
}
?>
```

_Right:_

```php
<?php
function slow_printf($format) {
  $args = func_get_args();
  array_shift($args);

  vprintf($format, $args);
}
?>
```

_Okay:_

```php
<?php
function mildCurry() {
  $args = func_get_args();

  array_unshift("some value", $args);

  return call_user_func_array('foo', $args);
}
?>
```

_Wrong:_


```php
<?php
function login() {
  // We know what the expected args are:
  $args = func_get_args();
  $name = $args[0];
  $password = $args[1];
  if (isset($args[2])) {
    $backend = $args[2];
  }

  // Do stuff that has nothing to do with args.
}
?>
```


### Anonymous functions, lamdas, and closures

PHP provides three ways of creating functions "inline":

* A function can be declared in a string and passed to
  `create_function()`.
* A lambda function is declared inline.
* A closure (with explicit context) is declared inline.

The `create_function()` variety should only be used when absolutely
necessary.

When anonymous functions and closures are declared, they should follow the
rules specified for other functions, allowing for the fact that they
may be the values of variables or function arguments.

One space should be left between the `function` keyword and
the opening paren for the arguments list, as well as between the
closure's `use` keyword and its context: `function ($arg) use ($cxt) {}`

_Right:_

```php
<?php
usort($data, function ($a, $b) {
  // Do something clever.
});
?>
```

## Class Definitions

## Arrays

## Quotes

## String Concatenation

## Comments

## Including Code

## PHP Code Tags

## Semicolons

* Use them whenever they are required. DUH.
* Use the one with a dot at the top and a comma at the bottom.

## Example URLs

## References

Two other coding standards worth being familiar with and that have influenced this one (because they influenced me) are the [PEAR Coding Standard](http://pear.php.net/manual/en/standards.php) and the [Drupal Coding Standard](http://drupal.org/coding-standards).
