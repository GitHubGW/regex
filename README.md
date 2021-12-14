# Regex

### Groups and ranges

| Character | 뜻                                          |
| --------- | ------------------------------------------- |
| `\|`      | 또는                                        |
| `()`      | 그룹을 지음                                 |
| `[]`      | 괄호 안의 문자셋을 포함하는 모든 것         |
| `[^]`     | 괄호 안의 문자셋을 포함하지 않는 모든 것    |
| `(?:)`    | 문자열을 찾지만 해당 그룹을 기억하지는 않음 |

### Quantifiers

| Character   | 뜻                   |
| ----------- | -------------------- |
| `?`         | 없거나 있거나        |
| `*`         | 없거나 있거나 많거나 |
| `+`         | 하나 또는 하나이상   |
| `{n}`       | 앞의 문자를 n번 반복 |
| `{min}`     | 최소                 |
| `{min,max}` | 최소 ~ 최대까지      |

### Boundary-type

| Character | 뜻               |
| --------- | ---------------- |
| `\b`      | 단어 경계        |
| `\B`      | 단어 경계가 아님 |
| `^`       | 문장의 시작      |
| `$`       | 문장의 끝        |

### Character classes

| Character | 뜻                              |
| --------- | ------------------------------- |
| `\`       | 특수 문자가 아닌 문자           |
| `.`       | 줄 바꿈 문자를 제외한 모든 문자 |
| `\d`      | 모든 숫자                       |
| `\D`      | 모든 숫자를 제외한 것           |
| `\w`      | 모든 문자                       |
| `\W`      | 모든 문자를 제외한 것           |
| `\s`      | 모든 공백                       |
| `\S`      | 모든 공백을 제외한 것           |

### Regex sites

- https://www.regexpal.com
- https://regexr.com
- https://regexone.com

### Regex examples

```ts
// \w+
Match	abcdefg
Match	abcde
Match	abc

// \d+
Match	abc123xyz
Match	define "123"
Match	var g = 123;

// [a-zA-Z0-9?=+]+\.
Match	cat.
Match	896.
Match	?=+.
Skip	abc1

// [c,m,f]an
Match	can
Match	man
Match	fan
Skip	dan
Skip	ran
Skip	pan

// [h,d]og
Match	hog
Match	dog
Skip	bog

// [A-Z]\w+
Match	Ana
Match	Bob
Match	Cpc
Skip	aax
Skip	bby
Skip	ccz

// waz{3,5}up
Match	wazzzzzup
Match	wazzzup
Skip	wazup

// a[a-z]+
Match	aaaabcc
Match	aabbbbc
Match	aacc
Skip	a

// [0-9]+ files? found\?
Match	1 file found?
Match	2 files found?
Match	24 files found?
Skip	No files found.

// \s
Match	1.   abc
Match	2.	    abc
Match	3.         abc
Skip	4.abc

// ^Mission: successful
Match	Mission: successful
Skip	Last Mission: unsuccessful
Skip	Next Mission: successful upon capture of target

// ^(file_[a-zA-Z0-9_]+) or ^(file.+)\.pdf$
Capture	file_record_transcript.pdf	file_record_transcript
Capture	file_07241999.pdf	          file_07241999

// (\w+ (\d+))
Capture	Jan 1987	Jan 1987 1987
Capture	May 1969	May 1969 1969
Capture	Aug 2011	Aug 2011 2011

// (\d+)x(\d+)
Capture	1280x720	1280 720
Capture	1920x1600	1920 1600
Capture	1024x768	1024 768

// I love (cats|dogs)
Match	I love cats
Match	I love dogs
Skip	I love logs
Skip	I love cogs

// \w+.+ or .*
Match	The quick brown fox jumps over the lazy dog.
Match	There were 614 instances of students getting 90.0% or above.
Match	The FCC had to censor the network for saying &$#*@!.
```
