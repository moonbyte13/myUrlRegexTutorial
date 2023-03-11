# URL Regex Tutorial

Regular expressions, also known as regex, are powerful tools for matching and manipulating text in various programming languages and applications. They provide a flexible and efficient way to search for patterns in strings of text, and can be used for tasks such as data validation, text parsing, and pattern matching. While regular expressions may appear daunting at first, mastering the syntax and functionality can greatly improve your ability to work with text in a programming context. In this gist, we will explore the basics of regular expressions and how they can be used to match and manipulate text in different scenarios.

<br>

## Summary

This regex matches URLs that start with "http://" or "https://" (or have no protocol at all), followed by a domain name and an optional path or query parameters.

`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`

<br>

## Table of Contents

- [URL Regex Tutorial](#url-regex-tutorial)
  - [Summary](#summary)
  - [Table of Contents](#table-of-contents)
  - [Regex Components](#regex-components)
    - [Anchors](#anchors)
    - [Quantifiers](#quantifiers)
    - [Grouping Constructs](#grouping-constructs)
    - [Bracket Expressions](#bracket-expressions)
    - [Character Classes](#character-classes)
    - [The OR Operator](#the-or-operator)
    - [Flags](#flags)
    - [Character Escapes](#character-escapes)
  - [Author](#author)

<br>

## Regex Components

> * `/ ` represents the start and end of a regex. 
> 
> * `^ ` means that it matches the start of the line. 
> 
> * `(https?:\/\/)? ` means that it matches the `http://` or `https://` protocol, and the `?` indicates the s is optional. 
> 
> * `([\da-z\.-]+)` means that it matches one or more characters that can be digits `(\d)`, letters `(a-z)`, dots `(.)`, or hyphens `(-)`. This captures the domain name of the URL.
> 
> * `\.([a-z\.]{2,6})` means that it matches a dot followed by a top-level domain name that has 2 to 6 letters, including dots. For example, this would match `.ca`, `.com`, `.edu`, or `.co.uk`. 
> 
> * `([\/\w \.-]*)*` means that it matches zero or more groups of characters that can be forward slashes (/), word characters (\w), spaces, dots, or hyphens. This captures any subdirectories or parameters in the URL.
> 
> * `\/?` means that it matches an optional trailing forward slash.
> 
> * `$` means that it matches the end of the line.


<br>

### Anchors

> The `^` symbol at the beginning of the regex matches the start of a line, and the `$` symbol at the end of the regex matches the end of a line are both anchors. These anchors ensure that the entire string being matched by the regular expression starts with the protocol or domain name and ends with an optional trailing forward slash. Without these anchors, the regular expression could potentially match a substring within a larger string that contains a valid URL, 

<br>

### Quantifiers

> There are three quantifiers used in this regex:
>
> The `+` symbol after `([\da-z\.-])` matches one or more instances of the character group that includes digits, letters, dots, and hyphens. This means that the domain name must contain at least one character from this character group, but can contain more than one.
>
> The `{2,6}` expression after `([a-z\.])` is a quantifier that matches the previous character or character group `([a-z\.])` between 2 and 6 times. This matches the top-level domain name, which can have between 2 and 6 letters, including dots.
>
> The `*` symbol after `([\/\w \.-])` matches zero or more instances of the character group that includes forward slashes, word characters, spaces, dots, and hyphens. This allows for subdirectories and parameters to be present in the URL, but it is not required.
>
> Overall, these quantifiers make the regex more flexible and able to match a wide variety of valid URLs, while still ensuring that the structure of the URL is maintained.

<br>

### Grouping Constructs

> There are several grouping constructs used in this regex which are used to match and capture parts of the text being searched.
>
> `(https?:\/\/)?` this group includes the optional `http://` or `https://` protocol at the beginning of the URL. The parentheses define this group as a capturing group, which means that any text that matches this pattern will be stored as a separate match that can be accessed later in the code.
> 
> `([\da-z\.-]+)` this group matches one or more characters that can be digits, letters, dots, or hyphens. This group captures the domain name of the URL, and like the previous group, is defined as a capturing group.
> 
> `([a-z\.]{2,6})` this group matches the top-level domain name that has 2 to 6 letters, including dots. It is also defined as a capturing group.
> 
> `([\/\w \.-]*)*` this group matches zero or more groups of characters that can be forward slashes, word characters, spaces, dots, or hyphens. This captures any subdirectories or parameters in the URL. This group is defined as a non-capturing group, meaning that any text that matches this pattern will not be stored as a separate match.
> 
> Overall, these grouping constructs allow the regex to capture and manipulate specific parts of the text being searched, which can be useful for tasks such as extracting data from a URL.

<br>

### Bracket Expressions

> There are several bracket expressions in this regex which define character classes that can match certain types of characters.
>
> `[\da-z\.-]` this bracket expression matches any character that is a digit `(\d)`, a lowercase letter `(a-z)`, a dot `(.)`, or a hyphen `(-)`. This character class is used to match the characters in the domain name of the URL.
>
> `[a-z\.]` this bracket expression matches any character that is a lowercase letter `(a-z)` or a dot `(.)`. This character class is used to match the characters in the top-level domain name of the URL.
> 
> `[\w \.-]` this bracket expression matches any character that is a word character `(\w)`, a space `( )`, a dot `(.)`, or a hyphen `(-)`. This character class is used to match the characters in the subdirectories and parameters of the URL.
>
> By using bracket expressions, the regex can match a variety of characters in different contexts, while still maintaining the structure and format of a valid URL.

<br>

### Character Classes

> There are several character classes in this which define groups of characters that can be matched by the regular expression.
>
> * `(\d)` this character class matches any digit, from 0 to 9. It is used in the bracket expression `([\da-z\.-]+)` to match any digit in the domain name of the URL.
>
> * `(a-z)` this character class matches any lowercase letter, from a to z. It is used in the bracket expression `([\da-z\.-]+)` to match any letter in the domain name of the URL.
>
> * `(.)` this character class matches any dot character. It is used in the bracket expressions `([\da-z\.-]+)` and `([a-z\.]{2,6})` to match the dots in the domain name and top-level domain name of the URL, respectively.
>
> * `({2,6})` this character class is not a character class in the traditional sense, but rather a quantifier that specifies a range of character repetitions. It is used in the bracket expression `([a-z\.]{2,6})` to match top-level domain names that consist of between 2 and 6 characters.
>
> * `(\w)` this character class matches any word character, which includes letters, digits, and underscores. It is used in the bracket expression `([\/\w \.-]*)` to match any subdirectories and parameters in the URL.
>
> * `( )` this character class matches a space character. It is used in the bracket expression `([\/\w \.-]*)` to match spaces that may appear in subdirectories and parameters of the URL.
>
> * `(-)` this character class matches a hyphen character. It is used in the bracket expressions `([\da-z\.-]+)` and `([\/\w \.-]*)` to match hyphens that may appear in the domain name and subdirectories/parameters of the URL, respectively.
>
>By using character classes, the regex can match a wide variety of characters in different contexts, while still maintaining the structure and format of a valid URL.

<br>

### The OR Operator

> The `OR` operator in the regular expressions is denoted by the `|` symbol, and is used to match either one pattern or another. In this particular regex, the `OR` operator is not explicitly used, but the `?:\/\/` sequence within the optional group `(https?:\/\/)` serves a similar function.
>
> The `(https?:\/\/)` group matches either the string `http://` or `https://`, where the `s?` portion specifies that the `s` character is optional. This means that the regular expression will match URLs that begin with either `http://` or `https://`. By using the `OR` operator (in this case, the `s?` optional character), the regular expression can match multiple patterns with a single expression, making it more flexible and versatile.

<br>

### Flags

> Flags are additional settings that can be added to the end of a regular expression to modify its behavior. Thid regular expression does not have any flags specified, but it is worth noting some of the common flags that can be used in regular expressions:
>
> i - This flag makes the regular expression case-insensitive, so that it can match characters regardless of their capitalization.
>
> g - This flag makes the regular expression global, meaning that it will match all occurrences of a pattern in a given string, rather than just the first occurrence.
> 
> m - This flag makes the regular expression treat a string as having multiple lines, so that it can match patterns across line breaks.
> 
> In general, flags can be useful for customizing the behavior of a regular expression to suit a particular use case. They can help to make regular expressions more powerful and flexible, and can make it easier to write regular expressions that match complex patterns.

<br>

### Character Escapes

> There are several character escapes used in this regex. A character escape is a way to indicate that a certain character should be treated as a literal character instead of being interpreted as part of the regular expression syntax. Here are the character escapes used in this regex:
>
> `\d` This matches any digit character `(0-9)`.
>
> `\.` - This matches a period `(.)` character. The backslash is used to escape the period so that it is treated as a literal character rather than a metacharacter.
> 
> `\/` - This matches a forward slash `(/)` character. The backslash is used to escape the forward slash so that it is treated as a literal character.
>
> `\w` - This matches any word character `(a-z, A-Z, 0-9, and underscore)`.
> 
> By using these character escapes, the regular expression can match specific characters without them being interpreted as part of the regular expression syntax. This allows for greater flexibility and precision when matching patterns in text.

<br>

## Author

> Hi my name is Michael I am a UofT student living in Edmonton, I am trying to pursue my dream of being a Software Developer in videogames.
>
> What is my Github link?
> * <a href='https://github.com/moonphase13' target='_blank'>***Github***</a>
> 
> What is my Repo for this project?
> * <a href='https://github.com/moonphase13/myUrlRegexTutorial' target='_blank'>***Repo***</a>