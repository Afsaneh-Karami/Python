# Extracting data from a web page using the Hypertext Transfer Protocol (HTTP) and urllib library

### Using Hypertext Transfer Protocol: (GOTO [Read web page over HTTP link](https://github.com/Afsaneh-Karami/Python/blob/main/Network%20Programming/Read%20web%20page%20over%20HTTP)) </br>
This code asks the user to enter a proper URL and receives data from the web url, also counts the number of characters that it has received, and stops displaying any text after it has shown 400 characters. There is built-in support in Python called socket which makes it very easy to make network connections and retrieve data over those sockets in a Python program. 
<!---you can see a socket connection below:
![Capture](https://user-images.githubusercontent.com/78735911/142168312-f65de815-798a-4b68-92cf-99625d2ba78a.PNG)</br> --->

First, the program makes a connection to the port 80 on the server. Since the program is playing the role of the “web browser”, it must use the HTTP protocol and send the GET command followed by a blank line.</br>
The order of functions used in this code:
1. Definition of socket:
* mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)</br>
2. Asking the user to enter the URL (for example http://data.pr4e.org/romeo.txt) 
* cmd1=input('please enter your URL') </br>
* Use try and except method to inform the user if enter a false URL.</br></br>
3. Use split('/') to break the URL into its component parts so you can extract the host name for the socket connect call
* cmd2=cmd1.split('/')</br>
 mysock.connect((cmd2[2], 80))</br>
 cmd = ('GET '+cmd1+ ' HTTP/1.0\r\n\r\n').encode()
 mysock.send(cmd)
 * One of the requirements for using the HTTP protocol is the need to send and receive data as bytes objects, instead of strings. In the preceding example, the encode() and decode() methods convert strings into bytes objects and back again.</br></br>
 4. Receiving the data character by character and printing them until the 400 letter.
* while True:</br>
        data = mysock.recv(1)</br>
        if len(data) <= 0:</br>
            break</br>
        cout=cout+len(data)</br>
        b=(data.decode())</br>
        if cout<=400:</br>
          print(b, end='') </br></br>
5. Closing the socket
* mysock.close()</br>
### Using urllib library to retrieve web pages: (GOTO [Read web pages with urllib link](https://github.com/Afsaneh-Karami/Python/blob/main/Network%20Programming/Read%20web%20pages%20with%20urllib)) </br>
While we can manually send and receive data over HTTP using the socket library, there is a much simpler way to do this in Python by using the urllib library.
Using urllib, we can treat a web page much like a file. We just indicate the desired web page to retrieve data and urllib handles all of the HTTP protocol and header details. When the web page has been opened with urllib.urlopen, we treat it like a file and read through it using a for loop. </br>
This code uses urllib library to retrieve the document from a URL ("https://en.wikipedia.org/wiki/Artificial_intelligence"). Then displaying up to 90 characters, counting the overall number of characters in the document, and counting the paragraph (p) tags of the document.</br>
The order of functions used in this code:</br></br>
1. Import the required package
* import urllib.request </br>
* from bs4 import BeautifulSoup
* import ssl </br>
2. Open the desired URL
* fhand=urllib.request.urlopen('https://en.wikipedia.org/wiki/Artificial_intelligence')</br>
3. Use a for loop to count the number of characters, print untill the 90 the character.</br></br>
4. Use the BeautifulSoup library to count paragraph (p) tags from the retrieved HTML document.
*  BeautifulSoup use to extract the href attributes from the anchor (a) tags.
*  Ignore SSL certificate errors by the following code:
*  ctx = ssl.create_default_context()  </br>
ctx.check_hostname = False  </br>
ctx.verify_mode = ssl.CERT_NONE  </br>
* Retrieve all of the paragraph tags</br>
  soup=BeautifulSoup(fhand, 'html.parser')</br>
  tags=soup('p')</br>








