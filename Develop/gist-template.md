# Title (Regex Tutorial)

Introductory paragraph (This guide we will dive into what regular expressions are and how they work)

## Summary

Regex to get started basically stands for regular expression, it's a pattern describing a certain amount of text. Their name comes from the mathematical theory on which they are based. Below is an example to validate E-mail address

/[A-Z0-9._%+-]+@[A-Z0-9-]+.+.[A-Z]{2,4}/igm

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components
Regular expressions can contain multiple components to accomplish tasks when Requirements Gateway analyzes intermediate files, for example:
-Matching Fixed Strings.
-Matching Special Characters.
-Matching Character Sets.
-Specifying Groups and Fields.
-Evaluating Occurrences.
-Specifying Location.
-Specifying Alternatives.

another exapmle:
colou?r	contains {color, colour}

### Anchors
Anchors are different, they do not match any character. They match a position before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret ^ matches the position before the first character in the string. Applying ^a to abc matches a. ^b does not match abc at all, because the b cannot be matched right after the start of the string, matched by ^

$ matches right after the last character in the string. c$ matches c in abc, while a$ does not match at all.

Syntax Example:
String anchor	$ (dollar)	.$ matches f in abc\ndef\n
Line anchor	^ (caret)	^. matches a and d in abc\ndef

### Quantifiers
Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. The following table lists the quantifiers supported by .NET The quantities n and m are integer constants. Ordinarily, quantifiers are greedy, they cause the regular expression engine to match as many occurrences of particular patterns as possible. Appending the ? character to a quantifier makes it lazy, it causes the regular expression engine to match as few occurrences as possible. Here are some examples 

Lazy quantifier repeats the previous item zero or more times. Lazy, so the engine first attempts to skip the previous item, before trying permutations with ever increasing matches of the preceding item ".*?" matches "def" and "ghi" in abc "def" "ghi" jkl

Greedy quantifier (question mark) Makes the preceding item optional. Greedy, so the optional item is included in the match if possible.	abc? matches abc or ab

greedy *	        lazy *?	          Match zero or more times.
greedy +	        lazy +?	          Match one or more times.
greedy ?	        lazy ??	          Match zero or one time.
greedy { n }	    lazy { n }?       Match exactly n times.
greedy { n ,}	    lazy { n ,}?      Match at least n times.
greedy { n , m }	lazy { n , m }?   Match from n to m times.

### Grouping Constructs
Grouping constructs delineate the subexpressions of a regular expression and capture the substrings of an input string. You can use grouping constructs to match a subexpression that is repeated in the input string, apply a quantifier to a subexpression that has multiple regular expression language elements. For more information about quantifiers & see quantifiers, include a subexpression in the string that is returned by the Regex.Replace and Match.Result methods, retrieve individual subexpressions from the Match.Groups property and process them separately from the matched text as a whole.

(expr)	    Match or capture group. Captures the information that matches the expression in parentheses

(?:expr)	Non-capturing group. Groups the contained expressions together (e.g., to apply a quantifier to multiple symbols at once), but does not restrict the information to be captured to only that group.

(?=expr)	Captures information that is followed by the expression if the expression is true and the input matches the pattern that follows this expression.

(?<>)	    Named capture group.*

\k<>	    Named back reference. *

### Bracket Expressions
A bracket expression is either a matching list expression or a non-matching list expression. It matches any single character in that list. If the first character of the list is the caret ‘^’, then it matches any character not in the list, and it is unspecified whether it matches an encoding error. It matches any single character that sorts between the two characters, inclusive. In the default C locale, the sorting sequence is the native character order. certain named classes of characters are predefined within bracket expressions, Their interpretation depends on the LC_CTYPE locale. Here are some examples:

‘[:alnum:]’
Alphanumeric characters: ‘[:alpha:]’ and ‘[:digit:]’; in the ‘C’ locale and ASCII character encoding, this is the same as ‘[0-9A-Za-z]’.

‘[:alpha:]’
Alphabetic characters: ‘[:lower:]’ and ‘[:upper:]’; in the ‘C’ locale and ASCII character encoding, this is the same as ‘[A-Za-z]’.

‘[:blank:]’
Blank characters: space and tab.


### Character Classes
With characret classes you can tell the regex engine to match only one out of several characters. Simply place the characters you want to match between square brackets, a character class matches only a single character. The order of the characters inside a character class does not matter. You can use a hyphen inside a character class to specify a range of characters. Below are some examples 

\d	
Matches any digit (Arabic numeral). Equivalent to [0-9]. For example, /\d/ or /[0-9]/ matches "2" in "B2 is the suite number".

\D	
Matches any character that is not a digit (Arabic numeral). Equivalent to [^0-9]. For example, /\D/ or /[^0-9]/ matches "B" in "B2 is the suite number".

\w	
Matches any alphanumeric character from the basic Latin alphabet, including the underscore. Equivalent to [A-Za-z0-9_]. For example, /\w/ matches "a" in "apple", "5" in "$5.28", "3" in "3D" and "m" in "Émanuel".

### The OR Operator
"Or" in regular expressions there are a few approaches to follow, logical “or” is more difficult to achieve using tools external to the regular expression engine itself, but it is achievable by combining results of multiple regular expressions using the native “or” logical feature of your programming language of choice. This can sometimes be simpler and easier for others to maintain in the future, with only minimal performance impacts over moderate data sets. for example:

^I like (mountains|climbing), but not (cold|snow).$

The expression above will match any of the following strings:

I like mountains, but not cold
I like mountains, but not snow 
I like climbing, but not cold
I like climbing, but not snow

### Flags
A flag is an optional parameter to a regex that modifies its behavior of searching. A flag changes the default searching behaviour of a regular expression. It makes a regex search in a different way. A flag is denoted using a single lowercase alphabetic character. Below are some examples of each of them serving a different purpose:

The ignore casing "i" and global "g" flags makes the expression search case-insensitively.
The dot all "s" and multiline "m" flags. Makes the wild character "." match newlines as well.
The sticky "y" flag Makes the expression start its searching from the index indicated in its lastIndex property.
The unicode "u" flag Makes the expression assume individual characters as code points, not code units, and thus match 32-bit characters as well.

### Character Escapes
Escape characters use the backslash character to escape a single character or symbol. Only the character immediately following the backslash is escaped. You also escape certain letters that represent common character classes

"Are you almost here, Jack?, asked Zach.", // source
	"(here|there).+(\w+).+(said|asked)(\s)(\w+)\." ); // regular expression
"here, Jack?, asked Zach."

## Author

I am a student at the University Of Denver learning computer programming, on my free time I enjoy hanging out with friends, playing video games and going out to new places. I want to keep improving and expanding my skills in the computer science field or in any information technology field.

contact me via email: irvinruiz44@yahoo.com
github profile: https://github.com/irvruiz)
