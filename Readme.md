# Knowledge we have discovered about regular expressions:

## Methods
* `=~`
  Returns the index of the first match
* `[]`
  return the first match
* `gsub`
  FIND ME
* `split`
  Splits string based on the character argumert provided (a.split(/<character(s)>/).
  Removes the arg character(s) from the string, returns an array of strings
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
* `^`	Start of line
* `$`	End of line
* `\A`	Start of string
* `\z`	End of string
* `\s`	Any whitespace character
* `\S`	Any non-whitespace character
* `\d`	Any digit ```str.scan(/\d/)``` found only the digits 0-9 in the string
* `\D`	Any non-digit ```str.scan(/\D/)``` found only the nondigits a-z in the string
* `\w`	Any word character (letter, number, underscore)
* `\W`	Any non-word character
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
