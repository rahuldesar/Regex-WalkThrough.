# Summary of REGEX. (Regular Expression) in JS vs All

Source 1 : [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)

**Regular expressions** are patterns used to match character combinations in strings. In JavaScript, regular expressions are also `objects`.

1. Creating a Regular Expression in JS. ( only JS ❓)
  
  - Using a regular expression literal. i.e pattern enclosed between slashes.
    ```
    const re = /ab+c/   //Enclosed within `/` `/`
    ```

  - Using a constructor function of `RegExp` object.
    ```
    const re = new RegExp('ab+c');
    ```




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
