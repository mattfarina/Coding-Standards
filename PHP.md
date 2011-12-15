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

## Function Declarations

Between the name of the function and the first parentheses there is no space. There is, also, no space between the first parentheses and first argument or the last parentheses and last argument.

Argument with default options should come after required arguments.

_Right:_

    function funfun($arg1, $arg2, $arg3 = array()) {
      // Do something here.
    }

_All Kinds of Wrong:_

    function funfun ( $arg1, $arg2 = array(), $arg3 )
    {
      // Don't even think of writing it like this or doing anything here if your
      // style looks remotely like this. Instead go put yourself in timeout.
    }

## Class Definitions

## Arrays

## Quotes

## String Concatenation

## Comments

## Including Code

## PHP Code Tags

## Semicolons

## Example URLs

## Naming Conventions

## References

Two other coding standards worth being familiar with and that have influenced this one (because they influenced me) are the [PEAR Coding Standard](http://pear.php.net/manual/en/standards.php) and the [Drupal Coding Standard](http://drupal.org/coding-standards).
