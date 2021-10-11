## Extracting data from a text file
This code read through 'mail log.txt' file and extracting some information from it. 
It build a histogram to categorizes each mail message by which day of the week the commit was done, and how many messages have come from each email address.
The order of functions used in this code:
* Make two dictionary, counts for saving the weekdays and itration of it, and emails for address email and its iteration.
* look for lines that start with “From”, then look for the third word (which is the day of the email) and keep a running count of each of the days of the week.
  * counts[word]=counts.get(word,0)+1
* look for lines that start with “From”, then look for the second word (which is the address email) and keep a running count of email address.
  * emails[word]=emails.get(word,0)+1
* print two dictionary datasets.
* Use a for loop to figure out who has the most messages in the file and then print the result.
