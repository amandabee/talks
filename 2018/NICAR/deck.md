## Back of the Napkin RegEx

I teach data reporting at UC Berkeley and am working on some yet-to-be-unveiled investigative data projects. This is almost entirely a wholesale repeat of a workshop I lead in 2014 -- Regular expressions don't change that much.

TK: Chrys Wu and Kennedy

If I'm being honest my heart is still at CUNY.
--v--

## So ..okay. Regular Expressions.

Regular expressions are statements that you make in a pattern matching language.

I can search for all the instances of "regular expressions" and replace them with "regex" without doing anything fancy. But if I want to find all the isntances of "Jim" and "Jimmy" and change them to "James", I need something a little more complex.

Two terms you're going to hear: "strings" just means a bunch of characters strung together. Letters are characters, numbers are characters. Curly braces and plus signs are characters.

### RegEx

It will shock you to learn that Wikipedia has an extensive and thorough history of [regular expressions](http://en.wikipedia.org/wiki/Regular_expression).

The first awesome thing about regular expressions is that they're not actually regular. When you start getting fancy you'll start to discover that applications can vary subtly in their implementation.


### Get Started

We're going to use two tools:

[Rubular](http://rubular.com/) and [RegEx 101](http://regex101.com/) to work through our puzzles today.

I like to start with a manageable block of text, one where you can *see* what you're up against just fine.

    NAME: Sean Burnett POS: RP AGE: 30 WT: 200 BORN: Dunedin, FL SALARY: 2350000
    NAME: Tyler Clippard POS: RP AGE: 27 WT: 200 BORN: Lexington, KY SALARY: 1650000
    NAME: Ross Detwiler-Smith POS: SP AGE: 26 WT: 174 BORN: St. Louis, MO SALARY: 485000
    NAME: Christian Garcia POS: RP AGE: 27 WT: 215 BORN: Miami, FL SALARY: N/A
    NAME: Gio Gonzalez POS: SP AGE: 27 WT: 205 BORN: Hialeah, FL SALARY: 3335000
    NAME: Mike Gonzalez POS: RP AGE: 34 WT: 215 BORN: Robstown, TX SALARY: N/A
    NAME: Ryan P. Mattheus POS: RP AGE: 28 WT: 215 BORN: Sacramento, CA SALARY: 481000
    NAME: Craig Stammen POS: RP AGE: 28 WT: 200 BORN: Coldwater, OH SALARY: 485000
    NAME: Drew Storen POS: RP AGE: 25 WT: 180 BORN: Indianapolis, IN SALARY: 498750
    NAME: Jordan Q. Zimmermann POS: SP AGE: 26 WT: 218 BORN: Auburndale, WI SALARY: 2300000


That is player data from the Washington Nationals 2012 lineup that I stole from [Anthoney DeBarros](http://www.anthonydebarros.com/2012/10/09/excel-extract-text-find-mid-string/) who uses it to demonstrate some cool Excel functions, which will also work if you want to break this all up. I sometimes think it wouldn't kill me to get more current data, but I haven't yet. I did alter it subtly to make our challenge more fun.

Let's say, hypothetically, that I want to put this in a spreadsheet. And I want all the data in columns. I can't just use `text to columns` because there's no delimiter.

So I want us to start by walking through how we can turn that into something closer to...

    Sean Burnett, RP, 30, 200, Dunedin, FL, 2350000
    Tyler Clippard, RP, 27, 200, Lexington, KY, 1650000
    Ross Detwiler-Smith, SP, 26, 174, St. Louis, MO, 485000
    Christian Garcia, RP, 27, 215, Miami, FL, N/A
    Gio Gonzalez, SP, 27, 205, Hialeah, FL, 3335000
    Mike Gonzalez, RP, 34, 215, Robstown, TX, N/A
    Ryan P. Mattheus, RP, 28, 215, Sacramento, CA, 481000
    Craig Stammen, RP, 28, 200, Coldwater, OH, 485000
    Drew Storen, RP, 25, 180, Indianapolis, IN, 498750
    Jordan Q. Zimmermann, SP, 26, 218, Auburndale, WI, 2300000


Start with the name. We're going to walk through this together and you should sketch out on a napkin how you think we can solve each piece of the puzzle. <http://rubular.com/r/OCClBeRKQi>

    NAME: \w*        # Not a bad start.
    NAME: \w* \w*    # Better, but check out Jordan Q. Zimmerman, Ross Detwiler-Smith
    NAME: \w*[-\w. ]*\w* # Now we have everyone.

But we want to be able to make replacements, so we're going to start grouping the good stuff:

    NAME: (\w*[-\w. ]*\w*) POS:

    NAME: (\w*[-\w .]*\w*[ ]*) POS: ([A-Z][A-Z])
    NAME: (\w*[-\w .]*\w*[ ]*) POS: ([A-Z]{2})

    NAME: (\w*[-\w .]*\w*[ ]*) POS: ([A-Z]{2}) AGE: (\d\d) WT: (\d{3}) BORN: .* SALARY: (\d+|N\/A)

Unpack the SALARY "or" statement: \d* will match 0 or more and stop. We want 1 or more. This is why I like Rubular, it shows you your matches. <http://rubular.com/r/lmLv0Igsdo>

But now is a good time to take this over to [Regex101](http://regex101.com/) to see it all colorized http://regex101.com/r/vS5eT3



### More Challenges
Convert dates from 1/12/99 to 1999-12-01; find proper nouns and large currency amounts in a giant blob of text

## Tools
If you're already pretty good at regular expressions, check out the [Tuesday Challenge](http://callumacrae.github.io/regex-tuesday/) or [Hacker Rank's Challenges](https://www.hackerrank.com/categories/miscellaneous/regex).

The [RegEx Crosswords](http://regexcrossword.com/) are fun, if cryptic.

And if you just want an easier format:
http://regex101.com/ or

http://rubular.com/
