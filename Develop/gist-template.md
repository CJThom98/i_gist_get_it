# Title (replace with your title)

Introductory paragraph (replace this with your text)

## Summary

Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors

Anchors serve a special purpose in Javascript. Rather than matching specific characters, they identify the position of beginning and end characters. The carrot (^) is used to identify characters at the beginning and the dollar sign ($) is used to identify characters at the end. 

Take the following snippet of code for example:

    let str = 'JavaScript';
    console.log(/^J/.test(str));

If we were to input this code into a JS file and run it, the output will be "true" because our anchor, "/^J/", is looking to match text that starts with J. If our beginning anchor was "/^S", we would see an output of false because our word does not begin with S. 

The same principle applies with our $ except it looks for ending characters. Take this example:

    let str = 'JavaScript';
    console.log(/t$/.test(str));

If we were to input this into a JS file, it would return "true" because our ending anchor, "/$t/", is looking for text that matches with "t". Similar to our beginning anchor, if the letter were anything but "t", the output would return false because our only text ends in a lower case t. 

### Quantifiers

When we use a quantifier, we looking to match the number of instances of a character, group, or character class in a string. There are two main quantifiers, Exact and Range, and a few shorthands. In this tutorial, we'll learn about Exact and Range quanitifiers. 

The Exact quantifier is used when we are looking for a string with a specific number of instances. The common and simplist use of this quanitifer is the number you're looking for wrapped in curly brackets, {n}. Look at the following example to see this quantifier in action:

    let str = 'ECMAScript 2020';
    let re = /\d{4}/;

    let result = str.match(re);

    console.log(result);

Our quantifier is "/\d{4}/," we're telling our code that we looking four characters that we used as a date. Once implemented, the output should be: ["2020"]. Why did we write our quanitifer as "/\d{4}/"? Isn't that like telling our code we're looking for 4 separate dates? It might seem that way, but it's the same as writing the quanitifier as "/\d\d\d\d/." Meaning we looking for a string of characters that used in that form. 

The second quantifier used is the Range. This is used when we're not looking for a specific number of characters, but rather we're looking for matches that occuer "n" to "m" times. For instance, say we have a text with multiple numbers of various sizes and we want to match them all. We would use a Range to ensure we have each instance of those numbers. Take the following example:

    let str = 'The official name of ES11 is ES2020';
    let re = /\d{2,4}/g;

    let result = str.match(re);
    console.log(result);

Our quantifier, "/\d{2,4}/g," is looking for numbers with character instances between 2 and 4. Once implemented, our output should be: ["11", "2020"]. But what if we know the minimum of our range but not the maximum? Take a look at the next example: 

    let numbers = '+1-(408)-555-0105'.match(/\d{1,}/g);
    console.log(numbers);

Our quantifier, "/\d{1,}/g," is looking for every character instance of 1 and has no cap on the maximum. So, when we put this code into use, our quantifier should capture every number, resulting in: ["1", "408", "555", "0105"].

### OR Operator

An OR Operator is also known simply as Alteration. It is one of the simplest if not the easiest regex out there. All we need to distinguish this regex is the vertical line character, |. When would we use this regex? Say we need to find the langauages HTML, CSS, and Javascript. We would create our regex as so: "/html/css/java(script)?/." To see it in action, look at the following example: 

    let regexp = /html|css|java(script)?/gi;

    let str = "First HTML appeared, then CSS, then JavaScript";

    alert( str.match(regexp) );

Once implemented, the output should be: HTML, CSS, Javascript. 

### Character Classes

With a “character class”, also called “character set”, you can tell the regex engine to match only one out of several characters. Simply place the characters you want to match between square brackets. If you want to match an a or an e, use [ae]. You could use this in gr[ae]y to match either gray or grey. Very useful if you do not know whether the document you are searching through is written in American or British English.

A character class matches only a single character. gr[ae]y does not match graay, graey or any such thing. The order of the characters inside a character class does not matter. The results are identical.

### Flags

You've already seen the flags in the last few tutorials but you likely didn't realize it. Remember the "gi" at the end of the Alteration regex, or the "g" at the end of the quantifiers? Those are flags, there are six of them and they affect our search. 

i: This flag is telling our search that it's case-insensitive. Meaning there's no difference between A and a. 

g: We are looking for all matches with this flag, not just looking for the first match. 

m: This flag indicates multiline mode. Telling our search to look at every line for a match. 

s: Enables “dotall” mode, that allows a dot to match newline character.

u: Enables full Unicode support. The flag enables correct processing of surrogate pairs.

y: “Sticky” mode: searching at the exact position in the text. 

### Grouping and Capturing



### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
