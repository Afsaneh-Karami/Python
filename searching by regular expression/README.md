## Extracting data from a text file by regular experssion
This code read through the 'mail log.txt' file and extracted some information from it by using the regular expressions library (re). Regular expressions are a programming language for searching and parsing strings. The power of the regular expressions comes when we add special characters to the search string that allow us to more precisely control which lines match the string. Adding these special characters to our regular expression allows us to do sophisticated matching and extraction while writing very little code. The order of functions used in this code:
1. First, search through each line of text, and find the domain name of emails.
* use findall() method to extract all of the substrings which have @ that look like an email address and extract the domain name of it.
* g=re.findall('@([^  \>;)]+)',line)
* use a counter to have the number of lines.<br />
2. Then search for numbers in the text and compute the average of the numbers and print out the average as an integer.
* g1=re.findall('[0-9]+',line)
* Use a for loop to get the whole of a number.
* Define a counter to have the number of digits.


