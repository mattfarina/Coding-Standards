# PHP Coding Standard

This coding standard is one projects can use and reference for their own needs.

## Indenting and Whitespace

Use and indentation of two (2) spaces and no tabs. This part of a coding standard can be debated on the level of arguing religions. As the creator of this spec I'm going with two spaces.

Line endings should have no trailing space. I cannot believe I need to write this but all too often trailing spaces end up in a file.

New lines shall use the Unix line ending (\n) and not the Windows line ending (\r\n). The [history of new lines](https://en.wikipedia.org/wiki/Newline#History) can be quite fascinating as our digital age is tied to line ending characters from an era of machines printing characters.

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


## Line length and wrapping

## Function Calls

## Function Declarations

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