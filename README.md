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

Pattern : abc 
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

Pattern : 123
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

Pattern : [cmf]an
Pattern2 : [^drp]an

// Explanation : [abc] will only match a single a,b,c and nothing else.
//               [^abc] will match match a single character that isn't a,b,c.
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

Pattern :  [A-C][n-p][a-c]
Pattern2 :  [^a-c][n-p][a-c]
Pattern3 :  [A-C][^a-c][a-c]
Pattern4 :  [A-C][n-p][^x-z]

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
    1) w{3}     -> three w's
    2) a{1,3}   -> `a` character no more than 3 times, but no less than once
    3) [wxy]{5} -> five characters, each of which can be a w, x, or y
    4) [wxy]{2,6} -> between two and six of character,each of which can be a w, x, or y
    5) .{2,6}   -> between two and six of any character
 -->

```
----------------------------------------------------
8) Matching Repeated Characters ---> Mr. Kleene, Mr. Kleene
----------------------------------------------------
```


```
----------------------------------------------------

----------------------------------------------------

