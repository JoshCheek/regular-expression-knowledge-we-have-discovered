# Knowledge we have discovered about regular expressions:

## Methods
* `=~`
  Returns the index of the first match
* `[]` return the first match
* `gsub` Takes a regex expression, and a second argument. Replaces all instances of the target (first argument) with the second argument.
* `split`
  Splits string based on the character argumert provided (`a.split(/<character(s)>/`).
  Removes the arg character(s) from the string, returns an array of strings

  ```ruby
  a = "Hello, its me!"
  a.split           # =>  ["Hello,", "its", "me!"]
  a.split(/i/)      # =>  ["Hello, ", "ts me!"]
  a.split(/ll/)     # =>  ["He", "o, its me!"]
  a.split(/z/)      # =>  ["Hello, its me!"]
  ```

* `scan`
  Returns an array of matches

## Things that can be in a regular expression
* `/P/` A character, anywhere in the string
* `/PM/` Two characters next to each other
* `/M+/` One or more of its target
* `/M*/` Zero or more of its target
* `/./` match any character
* `/^M/` matches its target if target exists at the beginning of a line in a string

  ```ruby
  str = "Regexes are badass.\nI wonder if strings are jealous?\nRegexes are king."
  str.scan(/^Regexes/) # => ["Regexes", "Regexes"]
  ```
* `/^M/` matches its target if target exists at the beginning of a line in a string
* `a{3,}`	3 or more of 'a' so in 'haaapppy go lucky bunny rabbit' this will select 'aaa', but in 'haaaapppy go lucky bunny rabbit' you will get 'aaaa'. you can change this number to select whatever you want, however if you use 1 as in => a{1,} this will select every combination of 'a' so 'happpy go lucky bunny raaaabbit1' => 'a','aaaa' 

## Still unknown
* `[abc]`	A single character of: a, b, or c
* `[^abc]`	Any single character except: a, b, or c
* `[a-z]`	all instances of lowercase letters; Brackets are required ``` "abc".scan(/[a-z]/) #=> ["a", "b", "c"] ```
* `[a-zA-Z]`	Any single character in the range a-z or A-Z
* `^`	Start of line
* `$`	End of line
* `\A`	Start of string
* `\z`	Matches targets (".." in example) starting from the end of the string and working backwards from there.
*     EXAMPLE: "Joshua Mejia [7:58 PM]"[(/..\z/]) => "M]" vs. "Joshua Mejia [7:58 PM]"[(/...\z/]) => "PM]"
* `\s`	Any whitespace character
* `\S`	Any non-whitespace character
* `\d`	Any digit ```str.scan(/\d/)``` found only the digits 0-9 in the string
* `\D`	Any non-digit ```str.scan(/\D/)``` found only the nondigits a-z in the string
* `\w`	Any word character (letter, number, underscore)
* `\W`	Any non-word character: Finds spaces, commas, colons, etc - things that wouldn't be part of a word. This does find apostraphe's also, so look out for contractions!
*     EXAMPLE: ```ruby
*           "Joshua Mejia [7:58 PM]".scan(/\W/) => [" ", " ", "[", ":", " ", "]"]
*           ```
*           ```ruby
*              "Joshua Mejia [7:58 PM]".scan(/.\W/) => ["a ", "a ", "7:", "8 ", "M]"]
*              ```
*
* `\b`	Any word boundary
* `(...)`	Capture everything enclosed
* `(a|b)`	a or b
* `a?`	Zero or one of a
* `a*`	Zero or more of a
* `a+`	One or more of a
* `a{3}`	Exactly 3 of a
* `a{3,}`	3 or more of a
* `a{3,6}`	Between 3 and 6 of a

## Open questions:

* does case matter?
* can we get rid of the plus in scan?


__END__
$ curl -i google.com
HTTP/1.1 301 Moved Permanently
Location: http://www.google.com/
Content-Type: text/html; charset=UTF-8
Date: Thu, 07 Jan 2016 16:49:09 GMT
Expires: Sat, 06 Feb 2016 16:49:09 GMT
Cache-Control: public, max-age=2592000
Server: gws
Content-Length: 219
X-XSS-Protection: 1; mode=block
X-Frame-Options: SAMEORIGIN

<HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="http://www.google.com/">here</A>.
</BODY></HTML>
