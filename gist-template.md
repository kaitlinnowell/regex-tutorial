# Regex Tutorial

This tutorial will walk through a specific regular expression and explain the significance of each character used.

## Summary

For this demonstration we will be disecting and explaining a regular expression that is used to match an email inside of a string. The regular expression is as follows:

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components
Below outlines the different components of a regular expression and how they are used in this scenario.

### Anchors

* ^: Matches the start of a string. In this context, it ensures that the email address starts with the characters described in the first group ([a-z0-9_\.-]+).
* $: Matches the end of a string. In this context, it ensures that the email address ends with the characters described in the third group ([a-z\.]{2,6}).

^ at the beginning and $ at the end ensure that the entire string is matched against the pattern, not just a part of it. This means that the string being tested must conform exactly to the pattern specified between these anchors. In this particular example we are ensuring the string matches the pattern: user@domain.top-level-domain

### Quantifiers

* +: The plus sign being using after a character class means that one or more of those characters must be present. For example, The + after the character class [a-z0-9_\.-] means that the username part must contain one or more of the specified characters (lowercase letters, digits, underscores, periods, or hyphens). Similarly, the + after the character class [\da-z\.-] means that the domain part must contain one or more of the specified characters (digits, lowercase letters, periods, or hyphens).

* {x, y}: The curly brackets with two numbers means that the preceeding group is limited to being between x and y characters in length. For this example, the {2,6} after the character class [a-z\.] means that the top-level domain (TLD) part must contain between 2 and 6 of the specified characters (lowercase letters and periods).


### OR Operator

There is no |(OR) symbol in this regular expression, which means there is no alternative pattern being matched.

### Character Classes

Character classes in regular expressions define a set of characters that you want to match. They are specified using square brackets [] and match any one character from the set.

* [a-z0-9_\.-]

    - [ and ]: Defines a character class.
    - a-z: Matches any lowercase letter.
    - 0-9: Matches any digit.
    - _: Matches an underscore.
    - \.: Matches a literal period (dot). The backslash escapes the dot, which is otherwise a special character in regex.
    - -: Matches a hyphen.

    Any of the items defined inside the character class definition will satisfy a match.

* '@' Matches the @ symbol in an email address.

* [\da-z\.-]

    - \d: Matches any digit (equivalent to [0-9]).
    - a-z: Matches any lowercase letter.
    - \.: Matches a literal period (dot).
    - -: Matches a hyphen.

* '\\.' Matches a literal period (dot).

* [a-z\.]

    - a-z: Matches any lowercase letter.
    - \.: Matches a literal period (dot).

### Flags

In regular expressions, flags (or modifiers) are used to change the behavior of the pattern matching. They are typically placed after the closing delimiter of the regular expression. There are no flags used in this example expression.

### Grouping and Capturing

Grouping and capturing in regular expressions allow you to treat multiple characters as a single unit, extract matched substrings, and perform additional operations on matched text.  Grouping is done using parentheses (). It allows you to  apply quantifiers to a group of characters and create subpatterns within the main pattern. Capturing is a specific use of grouping that allows you to extract the text matched by a group. Below are some of the groups used in this example:

* ([a-z0-9_\.-]+)

    - Matches the username part of the email.
    - Captures one or more characters that are lowercase letters, digits, underscores, periods, or hyphens.
    - Example match: user.name

* ([\da-z\.-]+)

    - Matches the domain part of the email.
    - Captures one or more characters that are digits, lowercase letters, periods, or hyphens.
    - Example match: example-domain

* ([a-z\.]{2,6})

    - Matches the top-level domain (TLD) part of the email.
    - Captures between 2 and 6 characters that are lowercase letters or periods.
    - Example match: com, co.uk

Full Example:

* The entire regex matches: user.name@example-domain.com
    - First capture group: user.name
    - Second capture group: example-domain
    - Third capture group: com

### Bracket Expressions

Bracket expressions, also known as character classes, define a set of characters enclosed within square brackets []. We can match any one of the literal characters or can define a range of characters to match. Since we have already explained the character classes used in this example above, we will not dive further into this here.

### Greedy and Lazy Match

By default, quantifiers are greedy. This means they will try to match as much of the input string as possible while still allowing the overall pattern to succeed. In this example, all of our modifiers are greedy:

* '+' (Plus)

    - Matches 1 or more occurrences of the preceding element.
    - Example: a+ in aaa matches aaa.

* {n,m} (Between n and m times)

    - Matches between n and m occurrences of the preceding element.
    - Example: a{2,4} in aaaaa matches aaaa.

Lazy quantifiers, also known as non-greedy quantifiers, match as little of the input string as possible while still allowing the overall pattern to succeed. You can make a quantifier lazy by following it with a question mark.

### Boundaries

In regular expressions, boundaries are markers or assertions that do not match any characters themselves, but rather assert something about the characters around them or the position in the string. In this example the only boundaries used are the anchor characters ^ and $ which have been previously described in the section above. 

### Back-references

Backreferences in regular expressions allow you to refer to previously captured groups within the same pattern. This is useful for matching repeated substrings or ensuring that certain parts of the string match other parts exactly. Backreferences are created by using parentheses for capturing and then referring to those captures using a backslash followed by the group number. This example does not use any back-references.

### Look-ahead and Look-behind

Look-ahead and look-behind assertions in regular expressions are used to match patterns based on what precedes or follows them without including those preceding or following characters in the match. These are also not used in this example.

## Author

This tutorial is written by Kaitlin Nowell with definitions referenced from chatGPT. More work by the author can be found at: https://github.com/kaitlinnowell
