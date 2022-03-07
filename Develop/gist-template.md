# Regex Tutorial

Welcome to the regex tutorial!

Here you will learn a basic understanding of some of the many regexs out there. You'll learn about Anchors, Flags, Character Classes, and several others. You'll also have access to further in depth explanations through other websites in some of these tutorials. I hope you find the information below useful!

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

Group capturing is one of if not the most common regex in Javascript. There are several different types of groups and captures, there will be a link added at the end of this section that lists each of them. Rather than going over one or two of them, we'll learn the general purpose of them. 

Essentially, capturing groups allows us to do two things: get a part of the match as a separate item in a result array, and applies the captured group as a whole if we use a quantifier after it. It's very simple but it makes a world of a difference for our regexs. 

There's not much else to cover, so as promised, explore this link to learn more about the different group capture methods: https://www.regular-expressions.info/refcapture.html

### Bracket Expressions

Bracket Expressions, an expression that uses the square brackets "[]", matches a specific set of single characters, and can match specific sets of multi-character elements. Using a bracket expression can really narrow our search. Say we want our regex to only find words that begin in "a, b, c". We would use [abc] our formula to tell it to only search for those character elements. But what if we want to exclude some words? We would write our brackets like [^abc]. But wouldn't that just tell our formula the same thing since we're using the carrot anchor? A keen eye, but in this case we are actually telling our formula to exclude those words. 

### Greedy and Lazy Match

It's probably strange to hear such negative descriptions being applied to a regex, but these are simply blunt descriptors of how their algorithms operate. The difference between a greedy match and a lazy match isn't stark, but it is noticable. 

For instance, when using a greedy match, the algorithm will try to repeat it's formula as many times as possible until it finds all the matches. Think of it as playing Monopoly, the greedy match wants the entire street of orange and magenta, so it will run the board as many times as it can until it as that entire street. 

A lazy match, however, only runs the minimal number times to find a match. It will only repeat itself until it's found a match, repeating a few times as necessary. Using our Monopoly reference again, the lazy match only wants the green properties. So, being more conservative in their moves, they will go around the board so many times until it has the green properties. 

For more info, visit this sight: https://javascript.info/regexp-greedy-and-lazy#greedy-search

### Boundaries

Remember back in the first tutorial how we learned about ^ and $ anchors? Well those only work if we're narrowing our search by a first or last letter. What if our search needs be narrowed down even more, say by an entire word? That's what boundaries are for. Boundaries, "\b", are our third anchor and it's what we use when we want our algorithm to match a "word-character." 

Say we have a list of Dragon Ball Z characters and we just want our algorithm to match the word-character with "Goku." Well in our algorithm, we would use the boundary: 

    \bGoku\b

That is a basic form of how we would use a boundary. For a more in depth look, visit this link: https://www.regular-expressions.info/wordboundaries.html

### Back-references

Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag. Here’s how: 

    <([A-Z][A-Z0-9]*)\b[^>]*>.*?</\1>

This regex contains only one pair of parentheses, which capture the string matched by [A-Z][A-Z0-9]*. This is the opening HTML tag. (Since HTML tags are case insensitive, this regex requires case insensitive matching.) The backreference \1 (backslash one) references the first capturing group. \1 matches the exact same text that was matched by the first capturing group. The / before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.

To figure out the number of a particular backreference, scan the regular expression from left to right. Count the opening parentheses of all the numbered capturing groups. The first parenthesis starts backreference number one, the second number two, etc. Skip parentheses that are part of other syntax such as non-capturing groups. This means that non-capturing parentheses have another benefit: you can insert them into a regular expression without changing the numbers assigned to the backreferences. This can be very useful when modifying a complex regular expression.

You can reuse the same backreference more than once. ([a-c])x\1x\1 matches axaxa, bxbxb and cxcxc.

Most regex flavors support up to 99 capturing groups and double-digit backreferences. So \99 is a valid backreference if your regex has 99 capturing groups.

### Look-ahead and Look-behind

Lookahead and lookbehind, collectively called “lookaround”, are zero-length assertions just like the start and end of line, and start and end of word anchors explained earlier in this tutorial. The difference is that lookaround actually matches characters, but then gives up the match, returning only the result: match or no match. That is why they are called “assertions”. They do not consume characters in the string, but only assert whether a match is possible or not. Lookaround allows you to create regular expressions that are impossible to create without them, or that would get very longwinded without them.

## Author

Github: https://github.com/CJThom98

Cory Thompson (CJThom98) is very new to the coding scene. He's only been coding for a few months now and, while he hopes to find more confidence in his work, anticipates that he will improve someday. He a natural enjoyer of history, video games, anime, and comic conventions. He hopes to someday be a team member in a web development division, and have a place of his own one day. 
