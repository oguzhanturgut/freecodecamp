#Introduction to the Regular Expression Challenges
Regular expressions are special strings that represent a search pattern. Also known as "regex" or "regexp", they help programmers match, search, and replace text. Regular expressions can appear cryptic because a few characters have special meaning. The goal is to combine the symbols and text into a pattern that matches what you want, but only what you want. This section will cover the characters, a few shortcuts, and the common uses for writing regular expressions.

***

###Using the Test Method
Regular expressions are used in programming languages to match parts of strings. You create patterns to help you do that matching.

If you want to find the word "the" in the string "The dog chased the cat", you could use the following regular expression: /the/. Notice that quote marks are not required within the regular expression.

JavaScript has multiple ways to use regexes. One way to test a regex is using the `.test()` method. The .test() method takes the regex, applies it to a string (which is placed inside the parentheses), and returns true or false if your pattern finds something or not.

    let testStr = "freeCodeCamp";
    let testRegex = /Code/;
    testRegex.test(testStr);
    // Returns true
Apply the regex myRegex on the string myString using the `.test()` method.

    let myString = "Hello, World!";
    let myRegex = /Hello/;
    let result = myRegex.test(myString); // Change this line

***

###Match Literal Strings
In the last challenge, you searched for the word "Hello" using the regular expression `/Hello/`. That regex searched for a literal match of the string "Hello". Here's another example searching for a literal match of the string "Kevin":

    let testStr = "Hello, my name is Kevin.";
    let testRegex = /Kevin/;
    testRegex.test(testStr);
    // Returns true
Any other forms of "Kevin" will not match. For example, the regex `/Kevin/` will not match "kevin" or "KEVIN".

    let wrongRegex = /kevin/;
    wrongRegex.test(testStr);
    // Returns false
A future challenge will show how to match those other forms as well.

Complete the regex waldoRegex to find "Waldo" in the string waldoIsHiding with a literal match.

    let waldoIsHiding = "Somewhere Waldo is hiding in this text.";
    let waldoRegex = /Waldo/; // Change this line
    let result = waldoRegex.test(waldoIsHiding);

***

###Match a Literal String with Different Possibilities
Using regexes like `/coding/`, you can look for the pattern "coding" in another string.

This is powerful to search single strings, but it's limited to only one pattern. You can search for multiple patterns using the `alternation` or `OR` operator: `|`.

This operator matches patterns either before or after it. For example, if you wanted to match "yes" or "no", the regex you want is `/yes|no/`.

You can also search for more than just two patterns. You can do this by adding more patterns with more OR operators separating them, like `/yes|no|maybe/`.

Complete the regex petRegex to match the pets "dog", "cat", "bird", or "fish".

    let petString = "James has a pet cat.";
    let petRegex = /dog|cat|bird|fish/; // Change this line
    let result = petRegex.test(petString);

***

###Ignore Case While Matching
Up until now, you've looked at regexes to do literal matches of strings. But sometimes, you might want to also match case differences.

Case (or sometimes letter case) is the difference between uppercase letters and lowercase letters. Examples of uppercase are "A", "B", and "C". Examples of lowercase are "a", "b", and "c".

You can match both cases using what is called a flag. There are other flags but here you'll focus on the flag that ignores case - the i flag. You can use it by appending it to the regex. An example of using this flag is /ignorecase/i. This regex can match the strings "ignorecase", "igNoreCase", and "IgnoreCase".

Write a regex fccRegex to match "freeCodeCamp", no matter its case. Your regex should not match any abbreviations or variations with spaces.

    let myString = "freeCodeCamp";
    let fccRegex = /freecodecamp/i; // Change this line
    let result = fccRegex.test(myString);

***

###Extract Matches
So far, you have only been checking if a pattern exists or not within a string. You can also extract the actual matches you found with the `.match()` method.

To use the `.match()` method, apply the method on a string and pass in the regex inside the parentheses.

Here's an example:

    "Hello, World!".match(/Hello/);
    // Returns ["Hello"]
    let ourStr = "Regular expressions";
    let ourRegex = /expressions/;
    ourStr.match(ourRegex);
    // Returns ["expressions"]
Note that the `.match` syntax is the "opposite" of the `.test` method you have been using thus far:

    'string'.match(/regex/);
    /regex/.test('string');
Apply the `.match()` method to extract the word coding.

    let extractStr = "Extract the word 'coding' from this string.";
    let codingRegex = /coding/; // Change this line
    let result = extractStr.match(codingRegex); // Change this line

***

###Find More Than the First Match
So far, you have only been able to extract or search a pattern once.

    let testStr = "Repeat, Repeat, Repeat";
    let ourRegex = /Repeat/;
    testStr.match(ourRegex);
    // Returns ["Repeat"]
To search or extract a pattern more than once, you can use the `g` flag.

    let repeatRegex = /Repeat/g;
    testStr.match(repeatRegex);
    // Returns ["Repeat", "Repeat", "Repeat"]
Using the regex starRegex, find and extract both "Twinkle" words from the string twinkleStar.

Note
You can have multiple flags on your regex like `/search/gi`

    let twinkleStar = "Twinkle, twinkle, little star";
    let starRegex = /twinkle/gi; // Change this line
    let result = twinkleStar.match(starRegex); // Change this line

***

###Match Anything with Wildcard Period
Sometimes you won't (or don't need to) know the exact characters in your patterns. Thinking of all words that match, say, a misspelling would take a long time. Luckily, you can save time using the wildcard character: .

The wildcard character . will match any one character. The wildcard is also called dot and period. You can use the wildcard character just like any other character in the regex. For example, if you wanted to match "hug", "huh", "hut", and "hum", you can use the regex `/hu./` to match all four words.

    let humStr = "I'll hum a song";
    let hugStr = "Bear hug";
    let huRegex = /hu./;
    huRegex.test(humStr); // Returns true
    huRegex.test(hugStr); // Returns true
Complete the regex unRegex so that it matches the strings "run", "sun", "fun", "pun", "nun", and "bun". Your regex should use the wildcard character.

    let exampleStr = "Let's have fun with regular expressions!";
    let unRegex = /.un/; // Change this line
    let result = unRegex.test(exampleStr);

***

###Match Single Character with Multiple Possibilities
You learned how to match literal patterns `(/literal/)` and wildcard character `(/./)`. Those are the extremes of regular expressions, where one finds exact matches and the other matches everything. There are options that are a balance between the two extremes.

You can search for a literal pattern with some flexibility with character classes. Character classes allow you to define a group of characters you wish to match by placing them inside square `([ and ])` brackets.

For example, you want to match "bag", "big", and "bug" but not "bog". You can create the regex `/b[aiu]g/` to do this. The `[aiu]` is the character class that will only match the characters "a", "i", or "u".

    let bigStr = "big";
    let bagStr = "bag";
    let bugStr = "bug";
    let bogStr = "bog";
    let bgRegex = /b[aiu]g/;
    bigStr.match(bgRegex); // Returns ["big"]
    bagStr.match(bgRegex); // Returns ["bag"]
    bugStr.match(bgRegex); // Returns ["bug"]
    bogStr.match(bgRegex); // Returns null
Use a character class with vowels (a, e, i, o, u) in your regex vowelRegex to find all the vowels in the string quoteSample.

Note
Be sure to match both upper- and lowercase vowels.

    let quoteSample = "Beware of bugs in the above code; I have only proved it correct, not tried it.";
    let vowelRegex = /[aeiou]/gi; // Change this line
    let result = quoteSample.match(vowelRegex); // Change this line


***

###Match Letters of the Alphabet
You saw how you can use character sets to specify a group of characters to match, but that's a lot of typing when you need to match a large range of characters (for example, every letter in the alphabet). Fortunately, there is a built-in feature that makes this short and simple.

Inside a character set, you can define a range of characters to match using a hyphen character: -.

For example, to match lowercase letters a through e you would use `[a-e]`.

    let catStr = "cat";
    let batStr = "bat";
    let matStr = "mat";
    let bgRegex = /[a-e]at/;
    catStr.match(bgRegex); // Returns ["cat"]
    batStr.match(bgRegex); // Returns ["bat"]
    matStr.match(bgRegex); // Returns null
Match all the letters in the string quoteSample.

Note
Be sure to match both upper- and lowercase letters.

    let quoteSample = "The quick brown fox jumps over the lazy dog.";
    let alphabetRegex = /[a-z]/gi; // Change this line
    let result = quoteSample.match(alphabetRegex); // Change this line

***

###Match Numbers and Letters of the Alphabet
Using the hyphen `(-)` to match a range of characters is not limited to letters. It also works to match a range of numbers.

For example, `/[0-5]/` matches any number between 0 and 5, including the 0 and 5.

Also, it is possible to combine a range of letters and numbers in a single character set.

    let jennyStr = "Jenny8675309";
    let myRegex = /[a-z0-9]/ig;
    // matches all letters and numbers in jennyStr
    jennyStr.match(myRegex);
Create a single regex that matches a range of letters between h and s, and a range of numbers between 2 and 6. Remember to include the appropriate flags in the regex.

    let quoteSample = "Blueberry 3.141592653s are delicious.";
    let myRegex = /[h-s2-6]/gi; // Change this line
    let result = quoteSample.match(myRegex); // Change this line

***

###Match Single Characters Not Specified
So far, you have created a set of characters that you want to match, but you could also create a set of characters that you do not want to match. These types of character sets are called negated character sets.

To create a negated character set, you place a caret character `(^)` after the opening bracket and before the characters you do not want to match.

For example, `/[^aeiou]/gi` matches all characters that are not a vowel. Note that characters like ., !, [, @, / and white space are matched - the negated vowel character set only excludes the vowel characters.

Create a single regex that matches all characters that are not a number or a vowel. Remember to include the appropriate flags in the regex.

    let quoteSample = "3 blind mice.";
    let myRegex = /[^0-9aeiou]/gi; // Change this line
    let result = quoteSample.match(myRegex); // Change this line

***

