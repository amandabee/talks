# RegEx Handout

## Text Block 1:
[2012 Nationals Lineup, Sort Of](https://gitorious.org/talks-and-teaching/talks/raw/a64f5d1e465fa1e35d418a7f76da74278682ea32:NICAR2014/regex/sample%20files/Sample%20Text%202012%20Nationals.txt) |
<http://rubular.com/r/NddU4mCdk0>   
**Search String:**
`NAME: ([-\.\w ]*)POS: ([A-Z]{2}) AGE: (\d+) WT: (\d+) BORN: ([\w. ]+), ([A-Z]{2}) SALARY: (\d+|N\/A)`  

## Text Block 2:
[A Bunch of Random Phone Numbers](https://gitorious.org/talks-and-teaching/talks/raw/a64f5d1e465fa1e35d418a7f76da74278682ea32:NICAR2014/regex/sample%20files/Sample%20Text%20Phone%20Numbers.txt) | <http://regex101.com/r/mB1bF0>
**Search String**   
`([0-9]{3})[-. )\/]*([0-9]{3})\D*([0-9]{4})`  
**Better Search String**
`\(*([0-9]{3})\D*([0-9]{3})\D*([0-9]{4})`  
**Replace String**
`\(\1\) \2-\3`  


##Very Useful Links
<http://rubular.com/> and <http://regex101.com>

Zed Shaw's <http://regex.learncodethehardway.org/> Learn Regex The Hard Way will make you an expert  

Dan Nguyen is awesome. His book <https://leanpub.com/bastards-regexes>, The Bastards Book of Regular Expressions is probably also awesome.  

If you're already pretty good at regular expressions, check out the <http://callumacrae.github.io/regex-tuesday/> Tuesday Challenge or <https://www.hackerrank.com/categories/miscellaneous/regex> Hacker Rank's Challenges. The <http://regexcrossword.com> RegEx Crosswords are fun, if cryptic.  

<http://www.rexegg.com/regex-lookarounds.html> Lookaheads will make your brain hurt a little, but that doesn't mean they aren't worth understanding.

And if you have [LibreOffice](https://www.libreoffice.org/) you can have [the cheatsheet](/talks/2014/HacksHackers/napkin.odt)
