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