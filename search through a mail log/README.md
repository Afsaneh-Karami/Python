## Extracting data from a text file
This code read through 'mail log.txt' file and extracting some information from it. 
It build a histogram to categorizes each mail message by which day of the week the commit was done, and how many messages have come from each email address.
The order of functions used in this code:
* Make two dictionary, counts for saving the weekdays and itration of it, and emails for address email and its iteration.
* using the startswith('From') 
