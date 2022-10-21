# Regex tutorial

Hello as a student of this bootcamp I was given the task to explain what a Regex is. A Regex is actually commonly known as a Regular Expression (Regex or regexp for short), and  are extremely useful in extracting information from any text by searching for one or more matches of a specific search pattern. That means it uses a specific sequence of ASCII or unicode characters to find specific matches in a text. To simplify a regular expression is a group of characters or symbols which is used to find a specific pattern in a text.

A regular expression is a pattern that is matched against a subject string from left to right. Regular expressions are used to replace text within a string, validate forms, extract a substring from a string based on a pattern match, and so much more. Fields of application range from validation to parsing/replacing strings, passing through translating data to other formats and web scraping. One of the most interesting features is that once you’ve learned the syntax, you can actually use this tool in almost all programming languages.

## Summary

One of the many Regex's availabe is the one used to validate emails. Regex provides the ability to validate the structure of an email address. It can be handled with one or two lines of code and can easily be tweaked to handle a wide variation of different parameters. One thing to keep in mind is that it can only check the structure of an email address. There is no way, using regex by itself to verify if the person is using a legitimate address. It cannot check records to ensure that the address being provided is a legitimate address. In other words, someone can easily construct any string of characters that fits the rules and pass through this validation, and it is not possible to check whether the address provided is actually real.

Email addresses generally take a fairly standard structure (e.g. xxx@xxxxxx.xxx). There are, however, a wide range of other limitations. A basic email regex is built into HTML5, and uses the following expression:
* Matching an Email: /^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
What this does is it looks for any combination of A-Z (both upper and lowercase) and numbers, and allowing a few specific special characters, including:
* ! # $ % & ' * + - / = ? ^ _ ` { |
this website explains the concepts in more depth: https://www.oreilly.com/library/view/regular-expressions-cookbook/9781449327453/ch04s01.html

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components
Email Regex in python:
regex = '^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$'
def check(email):  
    if(re.search(regex,email)):  
        print("Valid Email")  
    else:  
        print("Invalid Email")  

Email Regex in PHP:
if(filter_var($email, FILTER_VALIDATE_EMAIL)) {
     echo ‘this email address is valid’;
}

PHP2:
'$email = "abc123@example.com"; 
$regex = '/^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/'; 
if (preg_match($regex, $email)) {
 echo $email . " is valid.";
}' 

Email Regex in JavaScript:
function ValidateEmail(inputText)
{
	var mailformat = /^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/
	if(inputText.value.match(mailformat))
	{
		alert("This is not a valid email address");
		return false;
		}
}

Email Regex in Ruby:
URI::MailTo::EMAIL_REGEXP

Ruby2:
VALID_EMAIL_REGEX = /\A([\w+\-].?)+@[a-z\d\-]+(\.[a-z]+)*\.[a-z]+\z/i

Email Regex in Go (Golang):
package main
import (
	"fmt"
	"regexp"
)
var emailRegex = regexp.MustCompile("^[a-zA-Z0-9.!#$%&'*+\\/=?^_`{|}~-]+@[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?(?:\\.[a-zA-Z0-9](?:[a-zA-Z0-9-]{0,61}[a-zA-Z0-9])?)*$")

func main() {
	e := "test@testing.com"
	if isEmailValid(e) {
		fmt.Println(e + " is a valid email")
	}
	if !isEmailValid("just text") {
		fmt.Println("not a valid email")
	}
}
func isEmailValid(e string) bool {
	if len(e) < 3 && len(e) > 254 {
		return false
	}
	return emailRegex.MatchString(e)
}

Email Regex in Java:
public static final Pattern VALID_EMAIL_ADDRESS_REGEX = 
    Pattern.compile("^[A-Z0-9._%+-]+@[A-Z0-9.-]+\\.[A-Z]{2,6}$", Pattern.CASE_INSENSITIVE);

public static boolean validate(String emailStr) {
        Matcher matcher = VALID_EMAIL_ADDRESS_REGEX.matcher(emailStr);
        return matcher.find();
}

Email Regex in JQuery:
var userinput = $(this).val();
var pattern = /^\b[A-Z0-9._%-]+@[A-Z0-9.-]+\.[A-Z]{2,4}\b$/i

if(!pattern.test(userinput))
{
  alert('not a valid e-mail address');
}​


### Anchors
* The caret ( ^ ) symbol: 
    Setting position for match :tells the computer that the match must start at the beginning of the string or line.
* The dollar ( $ ) symbol:
    It tells the computer that the match must occur at the end of the string or before \n at the end of the line or string.

### Quantifiers
* Repeaters : * , + and { } :
    These symbols act as repeaters and tell the computer that the preceding character is to be used for more than just one time.
* The asterisk symbol ( * ):
    It tells the computer to match the preceding character (or set of characters) for 0 or more times (upto infinite).
* The Plus symbol ( + ):
    It tells the computer to repeat the preceding character (or set of characters) for atleast one or more times(upto infinite).
* The curly braces {…}:
    It tells the computer to repeat the preceding character (or set of characters) for as many times as the value inside this bracket.
### Grouping Constructs
* Grouping Characters ( ):
    A set of different symbols of a regular expression can be grouped together to act as a single unit and behave as a block, for this, you need to wrap the regular expression in the parenthesis( ).
* Vertical Bar ( | ) :
    Matches any one element separated by the vertical bar (|) character.
* \number :
    Backreference: allows a previously matched sub-expression(expression captured or enclosed within circular brackets ) to be identified subsequently in the same regular expression. \n means that group enclosed within the n-th bracket will be repeated at current position.

### Bracket Expressions
* [set_of_characters] – Matches any single character in set_of_characters. By default, the match is case-sensitive.
* [^set_of_characters] – Negation: Matches any single character that is not in set_of_characters. By default,  the match is case sensitive.
* [first-last] – Character range: Matches any single character in the range from first to last.
### Character Classes
* Character Classes
    A character class matches any one of a set of characters. It is used to match the most basic element of a language like a letter, a digit, space, a symbol etc.
    /s : matches any whitespace characters such as space and tab
    /S : matches any non-whitespace characters
    /d : matches any digit character
    /D : matches any non-digit characters
    /w : matches any word character (basically alpha-numeric)
    /W : matches any non-word character
    /b : matches any word boundary (this would include spaces, dashes, commas, semi-colons, etc)
### The OR Operator
* Optional character – ( ? ):
    This symbol tells the computer that the preceding character may or may not be present in the string to be matched.
### Flags
* Wildcard – ( . ):
    The dot symbol can take place of any other symbol, that is why it is called the wildcard character.
### Character Escapes
The Escape Symbol : \
If you want to match for the actual ‘+’, ‘.’ etc characters, add a backslash( \ ) before that character. This will tell the computer to treat the following character as a search character and consider it for matching pattern.
Comment : (?# comment) –
Inline comment: The comment ends at the first closing parenthesis.
* '#' [to end of line] : X-mode comment. The comment starts at an unescaped # and continues to the end of the line.
## Author

Hi my name is Bryce Oparah and I hope this guide helps you understand regex a bit better.
GitHub: https://github.com/BryceOph
