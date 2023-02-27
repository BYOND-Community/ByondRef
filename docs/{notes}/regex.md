

 Regular expressions
---------------------




**See also:** 


[regex datum](#/regex) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 

[replacetext proc](#/proc/replacetext) 

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 








**See also:** 

**See also:**

[regex datum](#/regex) 

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 

[replacetext proc](#/proc/replacetext) 

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 






[regex datum](#/regex)

[regex proc](#/proc/regex) 

[findtext proc](#/proc/findtext) 

[replacetext proc](#/proc/replacetext) 

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 





[regex proc](#/proc/regex)

[findtext proc](#/proc/findtext) 

[replacetext proc](#/proc/replacetext) 

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 




[findtext proc](#/proc/findtext)

[replacetext proc](#/proc/replacetext) 

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 



[replacetext proc](#/proc/replacetext)

[splittext proc](#/proc/splittext) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 


[splittext proc](#/proc/splittext)

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE) 

[REGEX\_QUOTE proc](#/proc/REGEX_QUOTE)

 Regular expressions are patterns that can be searched for within a text
string, instead of searching for an exact match to a known piece of text.
They are much more versatile for find and replace operations, and therefore
useful for parsing, filtering, etc.




 Some example regular expressions are:





| 
 Pattern
  | 
 Code
  | 
 Meaning
  |
| --- | --- | --- |
| 
 B.\*D
  | 
 regex("B.\*D")
  | 
 Find
 
 B
 
 , followed by any number of characters (including none), followed by a
 
 D
 
 .
  |
| 
 [0-3]
  | 
 regex(@"[0-3]")
  | 
 Find any digit from 0 to 3
  |
| 
 foo|bar
  | 
 regex("foo|bar","i")
  | 
 Find
 
 foo
 
 or
 
 bar
 
 , case-insensitive
  |
| 
 \d+
  | 
 regex(@"\d+","g")
  | 
 Find all sequences of digits
  |


| 
 Pattern
  | 
 Code
  | 
 Meaning
  |

 
 Pattern
 |
 
 Code
 |
 
 Meaning
 |
| 
 B.\*D
  | 
 regex("B.\*D")
  | 
 Find
 
 B
 
 , followed by any number of characters (including none), followed by a
 
 D
 
 .
  |

 
 B.\*D
 |
 
 regex("B.\*D")
 |
 
 Find
 
 B
 
 , followed by any number of characters (including none), followed by a
 
 D
 
 .
 |

 B


 D

| 
 [0-3]
  | 
 regex(@"[0-3]")
  | 
 Find any digit from 0 to 3
  |

 
 [0-3]
 |
 
 regex(@"[0-3]")
 |
 
 Find any digit from 0 to 3
 |
| 
 foo|bar
  | 
 regex("foo|bar","i")
  | 
 Find
 
 foo
 
 or
 
 bar
 
 , case-insensitive
  |

 
 foo|bar
 |
 
 regex("foo|bar","i")
 |
 
 Find
 
 foo
 
 or
 
 bar
 
 , case-insensitive
 |

 foo


 bar

| 
 \d+
  | 
 regex(@"\d+","g")
  | 
 Find all sequences of digits
  |

 
 \d+
 |
 
 regex(@"\d+","g")
 |
 
 Find all sequences of digits
 |

 These are some of the patterns you can use. If you want to use any of the
operators as an actual character, it must be escaped with a backslash.




 It is highly recommended that you use
 [raw strings](#/DM/text) 
 like
 `@"..."` 
 for your regular expression patterns, because with a
regular DM string you have to escape all backslash
 `\` 
 and open
bracket
 `[` 
 characters, which will make your regular expression
much harder for you to read. It's easier to write
 `@"[\d]\n"` 
 than
 `"\[\\d]\\n"` 
 .



[raw strings](#/DM/text)
`@"..."`
`\`
`[`
`@"[\d]\n"`
`"\[\\d]\\n"`


| 
 Pattern
  | 
 Matches
  |
| --- | --- |
| *a* 
 |
 *b*  | *a* 
 or
 *b*  |
| 
 .
  | 
 Any character (except a line break)
  |
| 
 ^
  | 
 Beginning of text; or line if
 
 m
 
 flag is used
  |
| 
 $
  | 
 End of text; or line if
 
 m
 
 flag is used
  |
| 
 \A
  | 
 Beginning of text
  |
| 
 \Z
  | 
 End of text
  |
| 
 [
 *chars* 
 ]
  | 
 Any character between the brackets. Ranges can be specified with a hyphen, like 0-9. Character classes like
 
 \d
 
 and
 
 \s
 
 can also be used (see below).
  |
| 
 [^
 *chars* 
 ]
  | 
 Any character NOT matching the ones between the brackets.
  |
| 
 \b
  | 
 Word break
  |
| 
 \B
  | 
 Word non-break
  |
| 
 (
 *pattern* 
 )
  | 
 Capturing group: the pattern must match, and its contents will be captured in the group list.
  |
| 
 (?:
 *pattern* 
 )
  | 
 Non-capturing group: Match the pattern, but do not capture its contents.
  |
| 
 \1
 *through* 
 \9
  | 
 Backreference;
 
 \
 *N* 

 is whatever was captured in the
 *N* 
 th capturing group.
  |
| 
 Modifiers
  |
| 
 Modifiers are "greedy" by default, looking for the longest match possible. When following a word, they only apply to the last character.
  |
| *a* 
 \*
  | 
 Match
 *a* 
 zero or more times
  |
| *a* 
 +
  | 
 Match
 *a* 
 one or more times
  |
| *a* 
 ?
  | 
 Match
 *a* 
 zero or one time
  |
| *a* 
 {
 *n* 
 }
  | 
 Match
 *a* 
 , exactly
 *n* 
 times
  |
| *a* 
 {
 *n* 
 ,}
  | 
 Match
 *a* 
 ,
 *n* 
 or more times
  |
| *a* 
 {
 *n* 
 ,
 *m* 
 }
  | 
 Match
 *a* 
 ,
 *n* 
 to
 *m* 
 times
  |
| *modifier* 
 ?
  | 
 Make the previous modifier non-greedy (match as little as possible)
  |
| 
 Escape codes and character classes
  |
| 
 \x
 *NN*  | 
 Escape code for a single character, where
 *NN* 
 is its hexadecimal ASCII value
  |
| 
 \u
 *NNNN*  | 
 Escape code for a single 16-bit Unicode character, where
 *NNNN* 
 is its hexadecimal value
  |
| 
 \U
 *NNNNNN*  | 
 Escape code for a single 21-bit Unicode character, where
 *NNNNNN* 
 is its hexadecimal value
  |
| 
 \d
  | 
 Any digit 0 through 9
  |
| 
 \D
  | 
 Any character except a digit or line break
  |
| 
 \l
  | 
 Any letter A through Z, case-insensitive
  |
| 
 \L
  | 
 Any character except a letter or line break
  |
| 
 \w
  | 
 Any identifier character: digits, letters, or underscore
  |
| 
 \W
  | 
 Any character except an identifier character or line break
  |
| 
 \s
  | 
 Any space character
  |
| 
 \S
  | 
 Any character except a space or line break
  |
| 
 Assertions
  |
| 
 (?=
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern to come next, but don't include it in the match
  |
| 
 (?!
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern NOT to come next
  |
| 
 (?<=
 *pattern* 
 )
  | 
 Look-behind: Require this pattern to come before, but don't include it in the match (must be a fixed byte length)
  |
| 
 (?<!
 *pattern* 
 )
  | 
 Look-behind: Require this pattern NOT to come before (must be a fixed byte length)
  |


| 
 Pattern
  | 
 Matches
  |

 
 Pattern
 |
 
 Matches
 |
| *a* 
 |
 *b*  | *a* 
 or
 *b*  |

 *a* 
 |
 *b*  |
*a*
*b*
 *a* 
 or
 *b*  |
*a*
*b*
| 
 .
  | 
 Any character (except a line break)
  |

 
 .
 |
 
 Any character (except a line break)
 |
| 
 ^
  | 
 Beginning of text; or line if
 
 m
 
 flag is used
  |

 
 ^
 |
 
 Beginning of text; or line if
 
 m
 
 flag is used
 |

 m

| 
 $
  | 
 End of text; or line if
 
 m
 
 flag is used
  |

 
 $
 |
 
 End of text; or line if
 
 m
 
 flag is used
 |

 m

| 
 \A
  | 
 Beginning of text
  |

 
 \A
 |
 
 Beginning of text
 |
| 
 \Z
  | 
 End of text
  |

 
 \Z
 |
 
 End of text
 |
| 
 [
 *chars* 
 ]
  | 
 Any character between the brackets. Ranges can be specified with a hyphen, like 0-9. Character classes like
 
 \d
 
 and
 
 \s
 
 can also be used (see below).
  |

 
 [
 *chars* 
 ]
 |
*chars*
 
 Any character between the brackets. Ranges can be specified with a hyphen, like 0-9. Character classes like
 
 \d
 
 and
 
 \s
 
 can also be used (see below).
 |

 \d


 \s

| 
 [^
 *chars* 
 ]
  | 
 Any character NOT matching the ones between the brackets.
  |

 
 [^
 *chars* 
 ]
 |
*chars*
 
 Any character NOT matching the ones between the brackets.
 |
| 
 \b
  | 
 Word break
  |

 
 \b
 |
 
 Word break
 |
| 
 \B
  | 
 Word non-break
  |

 
 \B
 |
 
 Word non-break
 |
| 
 (
 *pattern* 
 )
  | 
 Capturing group: the pattern must match, and its contents will be captured in the group list.
  |

 
 (
 *pattern* 
 )
 |
*pattern*
 
 Capturing group: the pattern must match, and its contents will be captured in the group list.
 |
| 
 (?:
 *pattern* 
 )
  | 
 Non-capturing group: Match the pattern, but do not capture its contents.
  |

 
 (?:
 *pattern* 
 )
 |
*pattern*
 
 Non-capturing group: Match the pattern, but do not capture its contents.
 |
| 
 \1
 *through* 
 \9
  | 
 Backreference;
 
 \
 *N* 

 is whatever was captured in the
 *N* 
 th capturing group.
  |

 
 \1
 *through* 
 \9
 |
*through*
 
 Backreference;
 
 \
 *N* 

 is whatever was captured in the
 *N* 
 th capturing group.
 |

 \
 *N* 

*N*
*N*
| 
 Modifiers
  |

 
 Modifiers
 |
| 
 Modifiers are "greedy" by default, looking for the longest match possible. When following a word, they only apply to the last character.
  |

 
 Modifiers are "greedy" by default, looking for the longest match possible. When following a word, they only apply to the last character.
 |
| *a* 
 \*
  | 
 Match
 *a* 
 zero or more times
  |

 *a* 
 \*
 |
*a*
 
 Match
 *a* 
 zero or more times
 |
*a*
| *a* 
 +
  | 
 Match
 *a* 
 one or more times
  |

 *a* 
 +
 |
*a*
 
 Match
 *a* 
 one or more times
 |
*a*
| *a* 
 ?
  | 
 Match
 *a* 
 zero or one time
  |

 *a* 
 ?
 |
*a*
 
 Match
 *a* 
 zero or one time
 |
*a*
| *a* 
 {
 *n* 
 }
  | 
 Match
 *a* 
 , exactly
 *n* 
 times
  |

 *a* 
 {
 *n* 
 }
 |
*a*
*n*
 
 Match
 *a* 
 , exactly
 *n* 
 times
 |
*a*
*n*
| *a* 
 {
 *n* 
 ,}
  | 
 Match
 *a* 
 ,
 *n* 
 or more times
  |

 *a* 
 {
 *n* 
 ,}
 |
*a*
*n*
 
 Match
 *a* 
 ,
 *n* 
 or more times
 |
*a*
*n*
| *a* 
 {
 *n* 
 ,
 *m* 
 }
  | 
 Match
 *a* 
 ,
 *n* 
 to
 *m* 
 times
  |

 *a* 
 {
 *n* 
 ,
 *m* 
 }
 |
*a*
*n*
*m*
 
 Match
 *a* 
 ,
 *n* 
 to
 *m* 
 times
 |
*a*
*n*
*m*
| *modifier* 
 ?
  | 
 Make the previous modifier non-greedy (match as little as possible)
  |

 *modifier* 
 ?
 |
*modifier*
 
 Make the previous modifier non-greedy (match as little as possible)
 |
| 
 Escape codes and character classes
  |

 
 Escape codes and character classes
 |
| 
 \x
 *NN*  | 
 Escape code for a single character, where
 *NN* 
 is its hexadecimal ASCII value
  |

 
 \x
 *NN*  |
*NN*
 
 Escape code for a single character, where
 *NN* 
 is its hexadecimal ASCII value
 |
*NN*
| 
 \u
 *NNNN*  | 
 Escape code for a single 16-bit Unicode character, where
 *NNNN* 
 is its hexadecimal value
  |

 
 \u
 *NNNN*  |
*NNNN*
 
 Escape code for a single 16-bit Unicode character, where
 *NNNN* 
 is its hexadecimal value
 |
*NNNN*
| 
 \U
 *NNNNNN*  | 
 Escape code for a single 21-bit Unicode character, where
 *NNNNNN* 
 is its hexadecimal value
  |

 
 \U
 *NNNNNN*  |
*NNNNNN*
 
 Escape code for a single 21-bit Unicode character, where
 *NNNNNN* 
 is its hexadecimal value
 |
*NNNNNN*
| 
 \d
  | 
 Any digit 0 through 9
  |

 
 \d
 |
 
 Any digit 0 through 9
 |
| 
 \D
  | 
 Any character except a digit or line break
  |

 
 \D
 |
 
 Any character except a digit or line break
 |
| 
 \l
  | 
 Any letter A through Z, case-insensitive
  |

 
 \l
 |
 
 Any letter A through Z, case-insensitive
 |
| 
 \L
  | 
 Any character except a letter or line break
  |

 
 \L
 |
 
 Any character except a letter or line break
 |
| 
 \w
  | 
 Any identifier character: digits, letters, or underscore
  |

 
 \w
 |
 
 Any identifier character: digits, letters, or underscore
 |
| 
 \W
  | 
 Any character except an identifier character or line break
  |

 
 \W
 |
 
 Any character except an identifier character or line break
 |
| 
 \s
  | 
 Any space character
  |

 
 \s
 |
 
 Any space character
 |
| 
 \S
  | 
 Any character except a space or line break
  |

 
 \S
 |
 
 Any character except a space or line break
 |
| 
 Assertions
  |

 
 Assertions
 |
| 
 (?=
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern to come next, but don't include it in the match
  |

 
 (?=
 *pattern* 
 )
 |
*pattern*
 
 Look-ahead: Require this pattern to come next, but don't include it in the match
 |
| 
 (?!
 *pattern* 
 )
  | 
 Look-ahead: Require this pattern NOT to come next
  |

 
 (?!
 *pattern* 
 )
 |
*pattern*
 
 Look-ahead: Require this pattern NOT to come next
 |
| 
 (?<=
 *pattern* 
 )
  | 
 Look-behind: Require this pattern to come before, but don't include it in the match (must be a fixed byte length)
  |

 
 (?<=
 *pattern* 
 )
 |
*pattern*
 
 Look-behind: Require this pattern to come before, but don't include it in the match (must be a fixed byte length)
 |
| 
 (?<!
 *pattern* 
 )
  | 
 Look-behind: Require this pattern NOT to come before (must be a fixed byte length)
  |

 
 (?<!
 *pattern* 
 )
 |
*pattern*
 
 Look-behind: Require this pattern NOT to come before (must be a fixed byte length)
 |

 The optional flags can be any combination of these:





| 
 Flag
  | 
 Meaning
  |
| --- | --- |
| 
 i
  | 
 Case-insensitive matching
  |
| 
 g
  | 
 Global: In Find() subsequent calls will start where this left off, and in Replace() all matches are replaced.
  |
| 
 m
  | 
 Multi-line: ^ and $ refer to the beginning and end of a line, respectively.
  |


| 
 Flag
  | 
 Meaning
  |

 
 Flag
 |
 
 Meaning
 |
| 
 i
  | 
 Case-insensitive matching
  |

 
 i
 |
 
 Case-insensitive matching
 |
| 
 g
  | 
 Global: In Find() subsequent calls will start where this left off, and in Replace() all matches are replaced.
  |

 
 g
 |
 
 Global: In Find() subsequent calls will start where this left off, and in Replace() all matches are replaced.
 |
| 
 m
  | 
 Multi-line: ^ and $ refer to the beginning and end of a line, respectively.
  |

 
 m
 |
 
 Multi-line: ^ and $ refer to the beginning and end of a line, respectively.
 |

 After calling
 
 Find()
 
 on a
 
 /regex
 
 datum, the datum's
 
 group
 
 var will contain a list—if applicable—of any
sub-patterns found with the
 
 ()
 
 parentheses operator. For instance,
searching the string
 
 "123"
 
 for
 
 1(\d)(\d)
 
 will match
 
 "123"
 
 , and the
 
 group
 
 var will be
 
 list("2","3")
 
 .
Groups can also be used in replacement expressions; see the
 [Replace() proc](#/regex/proc/Replace) 
 for more details.




 Find()


 /regex


 group


 ()


 "123"


 1(\d)(\d)


 "123"


 group


 list("2","3")

[Replace() proc](#/regex/proc/Replace)


---


