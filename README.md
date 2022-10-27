# Summary of REGEX. (Regular Expression)

[Source](https://regexone.com/)
| Pattern | Notes |
|---------|-------|
| abc… |	Letters |
| 123… |	Digits |
| \d |	Any Digit |
| \D |	Any Non-digit character |
| . |	Any Character |
| `\`. |	Period |
| [abc] |	Only a, b, or c |
| [^abc] |	Not a, b, nor c |
| [a-z] |	Characters a to z |
| [0-9] |	Numbers 0 to 9 |
| \w |	Any Alphanumeric character |
| \W |	Any Non-alphanumeric character |
| {m} |	m Repetitions |
| {m,n} |	m to n Repetitions |
| * |	Zero or more repetitions |
| + |	One or more repetitions |
| ? |	Optional character |
| \s |	Any Whitespace |
| \S |	Any Non-whitespace character |
| ^…$ |	Starts and ends |
| (…)	| Capture Group |
| (a(bc)) |	Capture Sub-group |
| (.*) |	Capture all |
| (abc|def) |	Matches abc or def |


## Some Examples.


----------------------------------------------------
1) Matching Characters . -> abc
----------------------------------------------------

```
Match	: abcdefg ✅
Match	: abcde	  ✅
Match	: abc     ✅

Pattern  : abc 
Pattern2 : \D\D\D    // Checks three non-digit character 

// // Explanation : Checks if there is `abc` in string in any position.
              \D => any non digit character.
```

----------------------------------------------------
2) Matching Digits. -> 123s
----------------------------------------------------
```
Match :	abc123xyz	    ✅
Match :	define "123"	✅
Match	: var g = 123   ✅

Pattern  : 123
Pattern2 : \d\d\d         // Checks three digit together


//  Explanation : Checks if there is `123` in string in any position.
//              \d => any digit character.
```
----------------------------------------------------
3) Matching with WildCard. ---> The Dot `.`
----------------------------------------------------
```
Match :	cat.	    ✅
Match :	896.	    ✅
Match :	?=+.	    ✅
Skip : abc1       ❌

Pattern : .../.

// Explanation : .  => wildcard, i.e can match any single character
//              \. => using period in Regex -> '.'
```
----------------------------------------------------
4) Matching Characters. [abc] || [ABC] || [123]
----------------------------------------------------
```
Match :	can	 ✅
Match :	man	 ✅
Match :	fan	 ✅
Skip :	dan  ❌
Skip :	ran  ❌ 
Skip :	pan  ❌

Pattern   : [cmf]an
Pattern2  : [^drp]an

// Explanation : [abc] will only match a single a,b,c and nothing else.
//               [^abc] will match a single character that isn't a,b,c.
```
----------------------------------------------------
5) Excluding Characters.
----------------------------------------------------
```
Match :	hog   ✅
Match :	dog   ✅
Skip :	bog   ❌

Pattern  : [^b]og
Pattern2 : [hd]og

// Explanation : [^b] matches a single character that isnt b. 
```
----------------------------------------------------
6) Character Ranges. [a-z]|| [A-Z] || [a-zA-Z0-9_] 
----------------------------------------------------
```
Match :	Ana	  ✅
Match :	Bob	  ✅
Match :	Cpc 	✅
Skip :	aax   ❌	
Skip :	bby   ❌	
Skip :	ccz   ❌

Pattern   :  [A-C][n-p][a-c]
Pattern2  :  [^a-c][n-p][a-c]
Pattern3  :  [A-C][^a-c][a-c]
Pattern4  :  [A-C][n-p][^x-z]

Explanation : Three characters, three ranges. 

```
----------------------------------------------------
7) Matching Repeated Characters ---> REPETITION {}
----------------------------------------------------
```
Match :	wazzzzzup ✅
Match :	wazzzup ✅
Skip :	wazup ❌

Pattern : waz{3,5}up    // better and precise
Pattern2 : z{3,5}       // barebone and vague . but works

<!-- 
Explanation : 
- z{3,5} means pattern will match z for no more than 5 and no less than 3 times.

- Extra : repetition can be used like :
    1) w{3}       -> three w's
    2) a{1,3}     -> `a` character no more than 3 times, but no less than once
    3) [wxy]{5}   -> five characters, each of which can be a w, x, or y
    4) [wxy]{2,6} -> between two and six of character,each of which can be a w, x, or y
    5) .{2,6}     -> between two and six of any character
 -->

```
----------------------------------------------------
8) Matching Repeated Characters ---> Mr. Kleene, Mr. Kleene
----------------------------------------------------
```
Match :	aaaabcc ✅
Match :	aabbbbc ✅
Match :	aacc ✅
Skip :	a ❌

Pattern   : a+b*c+              // one or more a , zero or more b, one or more c
Pattern2  : aa+b*c+             //better more clear way
Pattern3  : a{2,4}b{0,4}c{1,2}  // repetition using {}

<!--
Explanation :
 * => zero or more repetition
 + => one or more repetition           
-->
```
----------------------------------------------------
9)  Matching Optional Characters  --> Optional Characters. `?`
----------------------------------------------------
```
Match :	1 file found?   ✅
Match :	2 files found?	✅
Match :	24 files found?	✅
Skip :	No files found. ❌

Pattern   : [0-9]+ files? found\?     //Same as pattern2 \d = [0-9]
Pattern2  : \d+ files? found\?    

<!-- 
Explanation : 
- ? = optional 
- ab?c => match either the strings "abc" or "ac" because the b is considered optional. 
-->
```
----------------------------------------------------
10) Matching WhiteSpaces. ---> ALl the white Spaces.  (␣)
----------------------------------------------------
```
Match	1.   abc          ✅
Match	2.	abc           ✅
Match	3.           abc  ✅
Skip	4.abc             ❌

Pattern : \d\.\s+abc    \\ a digit (\d), a period (\.), a whitespace(\s)(one or more , +) and `abc`
 
<!--  
 Explanation : 
 \s => will match to all whitespaces, which includes (␣) , \t (tab), \ (newline) and \r (carriage return) 
-->
```

----------------------------------------------------
11) Matching Lines ----> Starting and Ending of **LINE** (^.......$)
----------------------------------------------------
```
Match :	Mission: successful                               ✅  
Skip  :	Last Mission: unsuccessful                        ❌
Skip  :	Next Mission: successful upon capture of target   ❌

Pattern : ^Mission: successful$ 

<!-- 
Explanation: 
- ^ (hat sign)    =>  starting of line
- $ (dollar sign) =>  ending of line
-->
```
----------------------------------------------------
12) Matching Groups. (matching and `extract`ing information using `(` and `)`)
----------------------------------------------------
 | Task |	Text |	Capture Groups |	 
 |---------|----------|------------|
 | `Capture` |	file_record_transcript.pdf |	`file_record_transcript` |
 | `Capture` |	file_07241999.pdf |	`file_07241999` |
 | Skip |	testfile_fake.pdf.tmp |
```
Pattern : ^(file.+)\.pdf$    // extacts filename starting with `file` + something and ending with `.pdf`

Explanation : 
- ^(IMG\d+\.png)$ => capture and extract the full filename of all png images.
- ^(IMG\d+)\.png$ => capture all filename without extensions.

```

----------------------------------------------------
13) Matching Nested Groups. -> extract using nested groups ie `(...(...))`
----------------------------------------------------

 | Task |	Text |	Capture Groups |	 
 |---------|----------|------------|
 | `Capture` |	Jan 1987 |	`Jan 1987` & `1987` |
 | `Capture` |	May 1969 |	`May 1969` & `1969` |
 | Skip |	Aug 2011 |  `Aug 2011` & `2011`  |

```
Pattern  : ([A-Z]\D{2}\s(\d{4}))   // ❌`RISKY` 3 non character with first capital letter, one whitespace, 4 digits.
Pattern2 : (\w+ (\d+)) // ✅ Better, one or more Any alphanumeric value, one or more digit.    

<!-- 
Explanation : 
 (...(..)) -> nesting Capture Group returns multiple captures. Outer capture then inner capture. 
-->

```
----------------------------------------------------
14) Matching Nested Groups
----------------------------------------------------

 | Task |	Text |	Capture Groups |	 
 |---------|----------|------------|
 | `Capture` |	1280x720  |	`1280` & `720` |
 | `Capture` |	1920x1600 |	`1920` & `1600` |
 | `Capture` |	1024x768  | `1024` & `768`  |

```
Pattern : (\d+)x(\d+) // one or more digit, one `x`, and one or more digit


```


----------------------------------------------------
15) Matching Conditional Text (abc|def) ==> | = logical OR, aka the pipe
----------------------------------------------------
```
Match : I love cats   ✅
Match : I love dogs   ✅
Skip  : I love logs   ❌
Skip  : I love cogs   ❌

Pattern : I love (cats|dogs)

<!-- 
Explanation : 
"Buy more (milk|bread|juice)" = match only the strings Buy more milk, Buy more bread, or Buy more juice.
-->

```

----------------------------------------------------
16) Other Special Characters.===> boundry `\b` ,
----------------------------------------------------
```
Match :	The quick brown fox jumps over the lazy dog.	To be completed ✅
Match :	There were 614 instances of students getting 90.0% or above.	To be completed ✅
Match :	The FCC had to censor the network for saying &$#*@!. ✅

Pattern : .*      //lol

```
