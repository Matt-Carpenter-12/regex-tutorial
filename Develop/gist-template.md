# Regex for Beginners

Regular expressions, commonly known as regex, are sequences of characters that form search patterns. These patterns can be used to match strings of text, facilitating tasks such as finding specific words, validating formats, and extracting or replacing segments of text. Regex is a powerful tool in programming and data processing, enabling efficient text manipulation across various applications and programming languages.

## Summary

Matching a Hex Value involves using a regular expression to identify valid hexadecimal color codes. The regex /^#?([a-f0-9]{6}|[a-f0-9]{3})$/ is designed for this purpose. It matches hex codes with or without a leading hash (#), and ensures they are either three or six characters long, using only valid hexadecimal digits (0-9 and a-f).
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

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
Regular expressions (regex) are built from various components, each serving a specific function to create complex search patterns. Here are some key components:

Literals: Plain characters that match themselves. For example, a matches the character 'a'.

Character Classes: Sets of characters enclosed in square brackets [ ]. For example, [a-z] matches any lowercase letter.

Predefined Character Classes: Shorthands for common sets of characters. For example, \d matches any digit (equivalent to [0-9]).

Quantifiers: Specify how many times the preceding element must occur. For example, {3} means exactly three times, + means one or more times, and * means zero or more times.

Anchors: Indicate the position within the string. For example, ^ matches the start of a string and $ matches the end.

Groups and Alternation: Parentheses () are used to group parts of the pattern, and the pipe | denotes alternation (logical OR). For example, (abc|def) matches either "abc" or "def".

Escaping Special Characters: The backslash \ is used to escape characters that have special meanings, like . which matches any character except a newline.

Understanding these components helps in constructing and interpreting complex regex patterns.

### Anchors

Anchors are special components in regular expressions that match positions within a string rather than specific characters. They help define where a pattern must occur in the text. Here are the main anchors:

Caret (^): Matches the start of a string. For example, ^hello matches "hello" only if it appears at the beginning of the string.

Dollar ($): Matches the end of a string. For example, world$ matches "world" only if it appears at the end of the string.

Word Boundary (\b): Matches a position where a word character is not followed or preceded by another word character. For example, \bword\b matches "word" in "word boundary" but not in "swordfish".

Non-Word Boundary (\B): Matches a position where a word character is followed or preceded by another word character. For example, \Bword\B matches "word" in "swordfish" but not in "word boundary".

Using anchors, you can precisely control where your patterns should match within a string, making your regular expressions more powerful and accurate.

### Quantifiers
Quantifiers in regular expressions specify the number of times an element (character, group, or character class) should occur. They are crucial for matching patterns of varying lengths. Here are the main types of quantifiers:

Exact Quantifiers:

{n}: Matches exactly n occurrences of the preceding element. For example, a{3} matches "aaa".
Range Quantifiers:

{n,m}: Matches between n and m occurrences of the preceding element. For example, a{2,4} matches "aa", "aaa", or "aaaa".
{n,}: Matches at least n occurrences of the preceding element. For example, a{2,} matches "aa", "aaa", "aaaa", and so on.
Greedy Quantifiers (default behavior):

*: Matches zero or more occurrences of the preceding element. For example, a* matches "", "a", "aa", "aaa", and so on.
+: Matches one or more occurrences of the preceding element. For example, a+ matches "a", "aa", "aaa", and so on.
?: Matches zero or one occurrence of the preceding element. For example, a? matches "" or "a".
Lazy Quantifiers (non-greedy, match as few as possible):

*?: Lazy version of *. For example, a*? matches as few "a" characters as possible.
+?: Lazy version of +. For example, a+? matches as few "a" characters as possible.
??: Lazy version of ?. For example, a?? matches as few "a" characters as possible.
Possessive Quantifiers (greedy but do not backtrack):

*+: Possessive version of *. For example, a*+ matches as many "a" characters as possible without backtracking.
++: Possessive version of +. For example, a++ matches as many "a" characters as possible without backtracking.
?+: Possessive version of ?. For example, a?+ matches as many "a" characters as possible without backtracking.
Quantifiers allow for flexible and powerful pattern matching, accommodating variations in the input text's structure and length.
### OR Operator
The OR operator in regular expressions is represented by the pipe symbol (|). It allows you to match one pattern or another, providing a way to specify alternative patterns that can match the same input text. The OR operator is used within a regular expression to create branches of possible matches. Here are some key points and examples:

Basic Usage:

pattern1|pattern2: Matches either pattern1 or pattern2. For example, cat|dog matches "cat" or "dog".
Grouping with Parentheses:

To apply the OR operator to part of a pattern, use parentheses to group the alternatives. For example, gr(e|a)y matches "grey" or "gray".
Multiple Alternatives:

You can have more than two alternatives by chaining multiple | operators. For example, red|green|blue matches "red", "green", or "blue".
Using with Other Components:

The OR operator can be combined with other regex components like anchors, character classes, and quantifiers. For example, ^a|b$ matches "a" at the start of a string or "b" at the end.

### Character Classes
Character classes in regular expressions are a set of characters enclosed within square brackets [ ], which allows you to specify a range of characters to match. Here are some key points and examples:

Basic Usage
Single Characters:

[abc]: Matches any one of the characters 'a', 'b', or 'c'.

Character Ranges:
[a-z]: Matches any lowercase letter from 'a' to 'z'.
[0-9]: Matches any digit from '0' to '9'.

Negation
Negated Character Classes:
[^abc]: Matches any character except 'a', 'b', or 'c'.
[^0-9]: Matches any character that is not a digit.

Combining Character Classes
Multiple Ranges:
[a-zA-Z]: Matches any uppercase or lowercase letter.
[0-9a-fA-F]: Matches any hexadecimal digit.
Predefined Character Classes
Common Shorthand Notations:
\d: Matches any digit (equivalent to [0-9]).
\D: Matches any non-digit (equivalent to [^0-9]).
\w: Matches any word character (alphanumeric plus underscore, equivalent to [a-zA-Z0-9_]).
\W: Matches any non-word character (equivalent to [^a-zA-Z0-9_]).
\s: Matches any whitespace character (spaces, tabs, line breaks).
\S: Matches any non-whitespace character.

### Flags
Flags in regular expressions are optional parameters that change the way a pattern is interpreted. They can be used to modify the behavior of the regex engine, making it more flexible and powerful. Here are some commonly used flags:

Common Flags
Case Insensitive (i):

Makes the regex match letters in a case-insensitive manner.
Example: /hello/i matches "hello", "Hello", "HELLO", etc.
Global (g):

Searches for all matches in the input string, not just the first one.
Example: /hello/g finds all occurrences of "hello" in the string.
Multiline (m):

Changes the behavior of ^ and $ to match the start and end of each line within a string, rather than the start and end of the entire string.
Example: /^hello/m matches "hello" at the start of each line.
Dot All (s):

Allows the dot . to match newline characters (\n).
Example: /a.b/s matches "a\nb" as well as "a b".
Unicode (u):

Enables full Unicode matching, allowing for the use of Unicode code points.
Example: /\u{1F600}/u matches the Unicode character "😀".
Sticky (y):

Matches the regular expression at the exact position in the string where it was last matched (sticky matching).
Example: /hello/y will match "hello" only if it is found exactly at the current position in the string.

### Grouping and Capturing
Grouping and capturing in regular expressions allow you to treat multiple characters as a single unit and extract parts of the matched text. Here are key concepts and examples:

Grouping
Basic Grouping:

Parentheses () are used to group part of a regex pattern.
Example: (abc) matches the exact sequence "abc".
Non-Capturing Groups:

Use (?:...) to group without capturing.
Example: (?:abc) matches "abc" but does not capture it for back-references.
Capturing
Capturing Groups:

Parentheses () not only group but also capture the matched text for use later.
Example: (abc) captures "abc" for back-references.
Back-References:

Refer to captured groups using \1, \2, etc., where the number corresponds to the position of the capturing group.
Example: (\w)\1 matches any character followed by itself, like "aa" or "bb".
Named Capturing Groups:

Use (?<name>...) to create a named capturing group.
Example: (?<digit>\d) captures a digit and names it "digit". You can reference it later with \k<name>.

### Bracket Expressions
Bracket expressions, also known as character classes, are used in regular expressions to specify a set of characters to match. They are enclosed within square brackets [ ] and can include individual characters, ranges, and combinations. Here are the key concepts and examples:

Basic Usage
Individual Characters:

[abc]: Matches any one of the characters 'a', 'b', or 'c'.
Character Ranges:

[a-z]: Matches any lowercase letter from 'a' to 'z'.
[A-Z]: Matches any uppercase letter from 'A' to 'Z'.
[0-9]: Matches any digit from '0' to '9'.
Negation
Negated Character Classes:
[^abc]: Matches any character except 'a', 'b', or 'c'.
[^0-9]: Matches any character that is not a digit.
Combining Character Classes
Multiple Ranges and Characters:
[a-zA-Z0-9]: Matches any uppercase or lowercase letter or digit.
[aeiou0-9]: Matches any vowel or digit.
Special Characters Inside Brackets
Literal Hyphen:

To include a hyphen -, place it at the beginning or end of the character class or escape it with a backslash.
Example: [-a-z] or [a-z-] or [a\-z] matches a hyphen or any lowercase letter.
Literal Brackets and Backslashes:

To include a literal closing bracket ], place it at the beginning or escape it with a backslash.
Example: []a-z] or [a\-z] matches ']' or any lowercase letter.
To include a backslash, escape it with another backslash \\.
Example: [\\] matches a backslash.

### Greedy and Lazy Match

In regular expressions, quantifiers can be greedy or lazy, determining how much text they match. Understanding the difference between greedy and lazy matching helps in controlling the behavior of your regex patterns.

Greedy Matching
Greedy quantifiers match as much text as possible. They try to match the longest possible string that satisfies the regex.

Common Greedy Quantifiers
* (zero or more times):

Example: a* matches "a", "aa", "aaa", and so on.
Pattern: a.*b
Text: "acb aabc aaab"
Match: "acb aabc aaab" (matches the entire string)
+ (one or more times):

Example: a+ matches "a", "aa", "aaa", and so on.
Pattern: a.+b
Text: "acb aabc aaab"
Match: "acb aabc aaab" (matches the entire string)
? (zero or one time):

Example: a? matches "" (empty string) or "a".
Pattern: a.?b
Text: "acb aabc aaab"
Match: "acb" (matches up to the first "b")
{n,m} (between n and m times):

Example: a{2,4} matches "aa", "aaa", or "aaaa".
Pattern: a.{2,4}b
Text: "acb aabc aaab"
Match: "aabc" (matches "aabc" in the text)
Lazy Matching
Lazy quantifiers match as little text as possible. They try to match the shortest possible string that satisfies the regex.

Common Lazy Quantifiers
*? (zero or more times):

Example: a*? matches "", "a", "aa", "aaa", and so on.
Pattern: a.*?b
Text: "acb aabc aaab"
Match: "acb" (matches up to the first "b")
+? (one or more times):

Example: a+? matches "a", "aa", "aaa", and so on.
Pattern: a.+?b
Text: "acb aabc aaab"
Match: "acb" (matches up to the first "b")
?? (zero or one time):

Example: a?? matches "" (empty string) or "a".
Pattern: a.??b
Text: "acb aabc aaab"
Match: "acb" (matches up to the first "b")
{n,m}? (between n and m times):

Example: a{2,4}? matches "aa", "aaa", or "aaaa".
Pattern: a.{2,4}?b
Text: "acb aabc aaab"
Match: "aabc" (matches "aabc" in the text)


### Boundaries
Boundaries in regular expressions are special constructs that allow you to specify positions within a string rather than matching specific characters. They help in defining where a pattern should match in the text. Here are the main types of boundaries:

Word Boundaries
Word Boundary (\b):

Matches the position between a word character (alphanumeric or underscore) and a non-word character.
Example: \bword\b matches "word" in "word boundary" but not in "swordfish".
Pattern: \bhello\b
Text: "hello there" or "say hello"
Match: "hello" (matches "hello" as a whole word)
Non-Word Boundary (\B):

Matches the position where there is no word boundary.
Example: \Bword\B matches "word" in "swordfish" but not in "word boundary".
Pattern: \Bword\B
Text: "swordfish" or "password"
Match: "word" (matches "word" within a larger word)
Line Boundaries
Start of Line (^):

Matches the position at the beginning of a line.
Example: ^hello matches "hello" only if it is at the start of a line.
Pattern: ^start
Text: "start the day" or "restart"
Match: "start" (matches "start" at the beginning of the line)
End of Line ($):

Matches the position at the end of a line.
Example: world$ matches "world" only if it is at the end of a line.
Pattern: end$
Text: "the end" or "ending"
Match: "end" (matches "end" at the end of the line)

### Back-references
Back-references in regular expressions allow you to refer to previously captured groups within the same pattern. They are useful for matching repeated or mirrored patterns within a string. Here are the key concepts and examples:

Basic Syntax
Basic Back-Reference:

\1, \2, etc., refer to the first, second, etc., capturing groups.
Example: (abc)\1 matches "abcabc".
Named Back-Reference:

\k<name> refers to a named capturing group.
Example: (?<word>\w+)\s+\k<word> matches a repeated word separated by spaces.

### Look-ahead and Look-behind
Look-ahead and look-behind are types of zero-width assertions in regular expressions that allow you to match a pattern only if it is (or isn't) followed or preceded by another pattern. They don't consume characters in the string but assert whether a match is possible or not based on the surrounding text.

Look-ahead
Look-ahead assertions check for a pattern ahead of the current position in the string without including it in the match.

Positive Look-ahead ((?=...)):

Asserts that what follows the current position matches the pattern inside the parentheses.
Example: foo(?=bar) matches "foo" only if it is followed by "bar".
Negative Look-ahead ((?!...)):

Asserts that what follows the current position does not match the pattern inside the parentheses.
Example: foo(?!bar) matches "foo" only if it is not followed by "bar".
Look-behind
Look-behind assertions check for a pattern behind the current position in the string without including it in the match.

Positive Look-behind ((?<=...)):

Asserts that what precedes the current position matches the pattern inside the parentheses.
Example: (?<=foo)bar matches "bar" only if it is preceded by "foo".
Negative Look-behind ((?<!...)):

Asserts that what precedes the current position does not match the pattern inside the parentheses.
Example: (?<!foo)bar matches "bar" only if it is not preceded by "foo".

## Author

Florida-based developer who is currently in the process of sharpening his developmental skills and future hopes of finding a job with them in the street or starting his own LLC for web development.
https://github.com/Matt-Carpenter-12
