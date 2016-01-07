# Knowledge we have discovered about regular expressions:

## Methods
* `=~`
  Returns the index of the first match
* `[]` return the first match
* `gsub` Takes a regex expression, and a second argument. Replaces all instances of the target (first argument) with the second argument.

  ```ruby
  a = "Hello, its me!"

  a.gsub(/e/, "pizza") #=> "Hpizzallo, it's mpizza!"
  a.gsub(/l/, "pizza") #=> "Hepizzapizzao, it's me!"
  ```
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
* `/M?/` Zero or one of its target

  ```ruby
  "b ba baa baaa baaaaa".scan(/ba?/) # => ["b", "ba", "ba", "ba", "ba"]
  ```

  vs.

  ```ruby
  "b ba baa baaa baaaaa".scan(/ba*/) # => ["b", "ba", "baa", "baaa", "baaaaa"]
  ```
* `/./` match any character
* `/^M/` matches its target if target exists at the beginning of a line in a string

  ```ruby
  str = "Regexes are badass.\nI wonder if strings are jealous?\nRegexes are king."
  str.scan(/^Regexes/) # => ["Regexes", "Regexes"]
  ```
* `/^M/` matches its target if target exists at the beginning of a line in a string
* `a{3,}`	3 or more of 'a' so in 'haaapppy go lucky bunny rabbit' this will select 'aaa', but in 'haaaapppy go lucky bunny rabbit' you will get 'aaaa'. you can change this number to select whatever you want, however if you use 1 as in => a{1,} this will select every combination of 'a' so 'happpy go lucky bunny raaaabbit1' => 'a','aaaa'
* `\z`	Matches targets (".." in example) starting from the end of the string and working backwards from there.

  ```ruby
  "Joshua Mejia [7:58 PM]"[(/..\z/]) => "M]"
  ```

  vs.

  ```ruby
  "Joshua Mejia [7:58 PM]"[(/...\z/]) => "PM]"
  ```
* `\s`	Any whitespace character If using scan, will identify the character before or after.  For example, string = "whatup yo". If you enter this: string.scan(/p\s/), you will get ["p "]. Does not account for more than one empty space.
* `\W`	Any non-word character: Finds spaces, commas, colons, etc - things that wouldn't be part of a word. This does find apostraphe's also, so look out for contractions!
* `(...)`	Capture an item in the string and then use `.` to represent any place your want around the string
* `\w`	Any word character (letter, number, underscore)

  ```ruby
  "Joshua Mejia [7:58 PM]".scan(/\W/) => [" ", " ", "[", ":", " ", "]"]
  ```

  ```ruby
  "Joshua Mejia [7:58 PM]".scan(/.\W/) => ["a ", "a ", "7:", "8 ", "M]"]
  ```
* `\b`	Any word boundary
* `()` group items together. Ruby will also "capture" what gets matched
  and let you access it with `$1`, `$2`, ...

  ```ruby
  "HTTP/1.1 200 OK"[/(\S+) (\S+) (.+)/]  # => "HTTP/1.1 200 OK"
  $1                                     # => "HTTP/1.1"
  $2                                     # => "200"
  $3                                     # => "OK"
  ```

* `a{3,6}`	Between 3 and 6 of a

  ```ruby
  "hellllo worllllld!".scan(l{3,6}) => ["llll", "lllll"]
  ```

  If there are more than the max, the regex grabs the maximum, leaving behind the remainder of the characters as such:

  ```ruby
  "777777777".scan(7{3-6}) => ["777777", "777"]
  ```

## Still unknown

* `[abc]`	A single character of: a, b, or c
* `[^abc]`	Any single character except: a, b, or c
* `[a-z]`	Any single character in the range a-z
* `[a-zA-Z]`	Any single character in the range a-z or A-Z
* `^`	Start of line
* `$`	End of line
* `\A`	Start of string
* `\S`	Any non-whitespace character
* `\d`	Any digit ```str.scan(/\d/)``` found only the digits 0-9 in the string
* `\D`	Any non-digit ```str.scan(/\D/)``` found only the nondigits a-z in the string
* `(a|b)`	a or b
* `a?`	Zero or one of a
* `a*`	Zero or more of a
* `a+`	One or more of a
* `a{3}`	Exactly 3 of a
* `a{3,}`	3 or more of a
