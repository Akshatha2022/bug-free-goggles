# Regex Tutorial: Telephone

Regular expressions (Regex) are a way of describing patterns in a string of data, which allows you to search for strings, like email addresses,passwords, or phone numbers that match a pattern.



## Summary

Regular expressions are patterns that allow you to describe, match, or parse text. In this tutorial we will be learning about matching a phone number to a pattern like this `###-###-#### (where # represents a number)`.

conventionally we can use a small function to find if a supplied string matches a pattern or not like below in JavaScript by looping through the numbers and matching against the case and making a decison.
```
function isPatternMatch(input) {
  if (typeof input !== 'string' || input.length !== 12) {
    return false;
  }
  for (let i = 0; i < input.length; i++) {
    let c = input[i];
    switch (i) {
      case 0:
      case 1:
      case 2:
      case 4:
      case 5:
      case 6:
      case 8:
      case 9:
      case 10:
      case 11:
        if (c < 0 || c > 9) return false;
        break;
      case 3:
      case 7:
        if (c !== '-') return false;
        break;
    }
  }
  return true;
}
```
Alternatively, this can be simplified and written with regex as below in one line to match against the input and return a boolean back.

```
function isPatternMatch(input) {
  return /^\d{3}-\d{3}-\d{4}$/.test(input);
}
```

## Table of Contents

- [Anchors](#anchors)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Greedy Match](#greedy-match)
- [Boundaries](#boundaries)

## Regex Components

### Anchors

Anchors are metacharacters that match the start and end of a line of text being matched.The two characters used are `^` and `$`.

1. `^` matches the start of a line and anchors a literal at the beginning of that line. For example:
    ```
    const regexPattern1 = /^cat/;
    console.log(regexPattern1.test('cat and mouse')); // Output: true
    console.log(regexPattern1.test('The cat and mouse')); // Output: false because the line does not start with cat
    // Without the ^ in the pattern, the output will return true
    // because we did not assert a boundary.
    const regexPattern2 = /cat/;
    console.log(regexPattern2.test('The cat and mouse')); // Output: true   
    ```
1. `$` matches the end of a line and anchors a literal at the end of that line. For example:
    ```
    const regexPattern = /cat$/;
    console.log(regexPattern.test('The mouse and the cat')); // Output: true
    console.log(regexPattern.test('The cat and mouse')); // Output: false
   ```

### Grouping Constructs

Our grouping constructs are simply binding our statements together so that we can achieve a more unique match. The operator `-` help us achieve this.


### Character Classes

A character class is used to match any one of several characters in a particular position. To denote a character class, you use square brackets `[]` and then list the characters you want to match inside the brackets.

```
// Find and match a word with two alternative spellings

const regexPattern = /fl[ow]er/;

console.log(regexPattern.test('flower')); // Output: true

// The regex pattern interprets as:  find a followed by m, then b,
// then i, then either e or a, then n, then c, and then e.
```

### Flags

Flags or modifiers are characters that enable advanced search features including case-insensitive and global searching. You can use them individually or collectively. Some commonly used ones are:

1. `g` is used for global search which means the search will not return after the first match.
1. `i` is used for case-insensitive search meaning that a match can occur regardless of the casing.
1. `m` is used for multiline search.
1. `u` is used for Unicode search.

### Greedy Match

All quantifiers by default are greedy. This means that they will try to match all possible characters. To remove this default state and make them non-greedy, you append a `?`

### Boundaries

Boundaries are metacharacters that match the start and end position of a string, a sequence of alphanumeric characters. In our pattern we use `\d`
1. `\d` matches any decimal digit and is shorthand for [0-9].
1. `\D` matches any non-digit and is the same as [^0-9.]


## Author
Akshatha Krishnamurthy
[GitHub](https://github.com/Akshatha2022)
[Portfolio](https://akshatha2022.github.io/02ChallengeCSS/)