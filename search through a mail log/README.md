## Extracting data from a text file
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
