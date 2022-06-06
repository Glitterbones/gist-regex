# Title  Title- Regular Expression (regex) for Matching a URL
--------------------------------------------------------------
A "Regex" (regular expression) is defined as a sequence of characters that defines a search pattern, 
           mainly for use in pattern matching with strings, or string matching, i.e. "find and replace"-like operations. 
Regular expressions can be helpful in a multitude of different ways including verifying email addresses or phone numbers 
and matching passwords. In this tutorial I will be taking a closer look at Matching a URL.

This tutorial explains how a specific regular expression, or regex, functions by breaking down each part or component i.e. 
#regex-components of the expression and describing what it does.


## Summary
--------------
Matching a URL: /^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
URL' will include the following components 

- http or https
    A URL must start with http or https in the address. 
    The difference between http and https is that 
          http is "No Data Encrytion implemented", where as
          https has an encryption component. 
- :// 
    will then follow either the hypertext transfer protocol. 
- www
    The synonym of www is "world wide web", comes after the http or https. 

- The next element in the url address is a "subdomain" which may vary in length between (2 and 256) characters. 
- File path 
- .com, .org, .edu etc...
    The final component will be the top level domain such as a .com, .org or .edu


## Table of Contents
---------------------------------------
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
-------------------------
To start, we must set the limits of the regex. Using /, we announce between these / are all of our parameters, we're to talking regex speak for now, interpret accordingly.

### Anchors
Once we have our starting and end points established, via / we'll use anchors to filter down the begining and ending portions of our URL. In the reference example snippet, the characters ^ and $ are our anchors.
The ^ can be found at the beginning of the regex and the $ at the end. 
By enveloping the regex between the two, this tells the search function to match exactly what is included in between them.

### Quantifiers
Quantifiers set the limits your regex matches, whether overall or in a specified section, and usually set minimum and maximum number of characters being searched for. 

Minimum quantifiers can be thought of as "at-leasters": * - At least 0 or more matches. That's right, at least 0 times. Search for it, accept how ever many times it finds it, and if it doesn't find it at all, that's ok too. + - At least 1 or more matches. As long as it matches at least 1 time, it can find as many as it wants after that.

We can also set our quantifiers manually using curly-brackets {} in 3 possible ways:
- { 1 } - A single number by itself sets the exact number of times it matches the pattern, in this case once, and only once. { 5 } would require exactly 5 matches.
- { 1, } - Adding a comma without a second number creates an at least scenario, at least one match, but more is ok, { 1, } would be the equivalent of +, whereas { 5, }, would increase the minimum to 5.
- { 1, 5 } - And now we have our minimum, maximum criteria. This is saying it should match the pattern at least once, but not more than 5 times. { 5, 10 } would set at least 5 matches, but no more than 10.

Seeing as * and + have minimum requirements, but not max, if searching for 0 or 1 match would otherwise require {}, but is a common requirement so ? can be used as a shortcut. ? is the equivalent of { 0, 1 } shortened for ease.

? can also be used after the above to make them "lazy", which will make them match as few occurrences as possible.

All these quantifiers are used after the criteria. For example:
^(https?:\/\/)? our starting criteria, as indicated with ^, is searching for https limiting results to when it appears 0 or 1 time while also searching for https:// also limited to 0 (to account for non-secure addresses) or 1 match.

### OR Operator
| symbolizes the OR or 'Alternate' operator which essentially performs a either match whatever's to the left or right of the '|'.

### Character Classes
The main character classes to consider in the above expression include the \d character class which looks for any digit, and the \w character class that looks for any alphanumeric character.

### Flags
/ delimits regular expressions and are commonly seen at the beginning and/or at the end and at times after anchors too. This is used to identify search criteria outside of the Flags to help mark the expression as global (g), insensitive (i) or multi-line (m).

### Grouping and Capturing
As patterns within a string search begin to get more complicated, Grouping Constructs becomes essential to partition regex using ( ) in order to match only a portion of the string at a time.

Note: In the HTML Example above - Multiple groups are bounded by parentheses like for example ?: is grouped to designate them as non-capturing - So long as ?: is not included regex will keep count of all 'capturing groups' bounded by ( ).

### Bracket Expressions
[ ] helps identify which portions of the expression can be any or all of the characters within the Bracket Expression

Note: In the URL Example above - the initial bracket expression, is looking for any digit, or any lower case character a-z, or any "." or "-" & in the last two brackets, any or all of those characters are been looked for.

### Greedy and Lazy Match
- The lazy mode of quantifiers is an opposite to the greedy mode. It means: “repeat minimal number of times”.
We can enable it by putting a question mark '?' after the quantifier, so that it becomes *? or +? or even ?? for '?'.
To make things clear: usually a question mark ? is a quantifier by itself (zero or one), but if added after another quantifier (or even itself) it gets another meaning – it switches the matching mode from greedy to lazy.
- Greedy will look for the longest possible string to consume, starting with the < , then looking for matching any character , excluding new lines. The + to repeat the proceeding as often as it can, and > is the end of the string.

### Boundaries
Bondaries are defines by the \b symbol at the begening and /b at the end. It is similar to the anchors ^ and $. 
Example if we wanted to return a match for Hello, the boundries should be set as followed ...\/bHello\b/ 

### Back-references
When matching characters in a group more than once, or for a repeat of a string, back-references may be used. 
For example to match a repeated words , you could use \w
Backreference Constructs allow reference to whatever was matched by previous code in the regex by using 'capturing groups'!
Note: \1 refers to the first capturing group ; \2 second ; \3 third and so on

### Look-ahead and Look-behind
To find occuring patterns that are next to each other look-ahead and look-behind can be used. 
Look-ahead, using ?=  is looking for a to follow to the left.
Look-behing using ?<= will look for a pattern to follow.

## Author
Ashley Lockhart 
U of U - Full Stack Development Course.

GitHub:https://github.com/Glitterbones
