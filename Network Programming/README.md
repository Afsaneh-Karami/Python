## Extracting data from a web page using the Hypertext Transfer Protocol (HTTP)
This code asking user enters an properly URL and reading data from the web, also counts the number of characters it has received and stops displaying any text after it has shown 400 characters. 
There is built-in support in Python called socket which makes it very easy to make network connections and retrieve data over those sockets in a Python program. you can see a socket connection at below:
![Capture](https://user-images.githubusercontent.com/78735911/142168312-f65de815-798a-4b68-92cf-99625d2ba78a.PNG)</br>
First the program makes a connection to port 80 on the server. Since our program is playing the role of the “web browser”, the HTTP protocol says we must send the GET command followed by a blank line.</br>
The order of functions used in this code:
1. Definition of socket:
* mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
2. Asking the user to enter the URL (for example http://data.pr4e.org/romeo.txt) 
* cmd1=input('please enter your URL')
One of the requirements for using the HTTP protocol is the need to send and receive data as bytes objects, instead of strings. In the preceding example, the encode() and decode() methods convert strings into bytes objects and back again.

This code read through 'mail log.txt' file and extracting some information from it. 
It build a histogram to categorizes each mail message by which day of the week and the hour that commit was done, and how many messages have come from each email address. Also, it convert all the text to lower case and only count the letters a-z (not counting spaces, digits, punctuation, or anything other than the letters a-z), and prints the letters in decreasing order of frequency.
The order of functions used in this code:
* Make three dictionary, counts for saving the weekdays and itration of it, and emails for email address and its iteration, and the hour for the delivering time and its iteration.
* look for lines that start with “From”, then look for the third word (which is the day of the email) and keep a running count of each of the days of the week. An example of a line that starts with From is 'From stephen.marquard@uct.ac.za Sat Jan  5 09:14:16 2008'
  * counts[word]=counts.get(word,0)+1
* look for lines that start with “From”, then look for the second word (which is the address email) and keep a running count of email address.
  * emails[word]=emails.get(word,0)+1
* look for lines that start with “From”, look for the five word (which is the hour), then split it with ':', and choose the first item.
  * hour[word1]=hour.get(word1,0)+1
* print three dictionary datasets.
* Use a for loop to figure out who has the most messages in the file and then print the result.
* Reads every line of the text, and splits it into its words. Then based on the length of each word, counts letters and make a dictionary of letters and their frequency. Sorting the dictionary print the result.
