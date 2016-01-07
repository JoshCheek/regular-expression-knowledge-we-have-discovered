# Knowledge we have discovered about regular expressions:

## Methods
* `=~`
  Gives the index of the first match
* `[]`
  return the first match
* `gsub`
  "Find and replace", takes two arguments of either strings or regex and replaces all occurences of the first arg with the second arg
* `split`
  Splits a string based on the regex, and returns an array of each side of the split as a separate entry in the array
* `scan`
  Returns an array of matches

## Things that can be in a regular expression
* `/P/` A character, anywhere in the string
* `/PM/` Two characters next to each other
* `/M+/` One or more of its target
* `/M*/` Zero or more of its target
* `/./` match any character

## Still unknown
* `[abc]`	A single character of: a, b, or c
* `[^abc]`	Any single character except: a, b, or c
* `[a-z]`	Any single character in the range a-z
* `[a-zA-Z]`	Any single character in the range a-z or A-Z
* `^`	Start of line: lets you find just a new line or a pattern at the beginning of a new line
* `$`	End of line:  lets you find just a end of a line or a pattern at the end of a line
* `\A`	Start of string
* `\z`	End of string
* `\s`	Any whitespace character
* `\S`	Any non-whitespace character
* `\d`	Any digit
* `\D`	Any non-digit
* `\w`	Any word character (letter, number, underscore): `"WORD!".scan(\w) => ["WORD"]`
* `\W`	Any non-word character: `"WORD!".scan(\W) => ["!"]`
* `\b`	Any word boundary
* `(...)`	Capture everything enclosed
* `(a|b)`	a or b
* `a?`	Zero or one of a
* `a*`	Zero or more of a
* `a+`	One or more of a
* `a{3}`	Exactly 3 of a
* `a{3,}`	3 or more of a 
* `a{3,6}`	Between 3 and 6 of a  ``"hellllo worllllld!".scan(l{3,6}) => ["llll", "lllll"]``  If there are more than the max, the regex grabs the maximum, leaving behind the remainder of the characters as such: `"777777777".scan(7{3-6}) => ["777777", "777"]`

## Open questions:

* does case matter? YES! Use `i` after the method as such: `"hi HI".scan(/hi/i) => ["hi", "HI"]`
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
