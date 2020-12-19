


# Week 3 quiz

##### 1. What is one difference between an HTTP GET and an HTTP POST request?

 - Only GET requests use the REFERER header
 - ***Only POST requests may include parameter data in the request body***
 - Only GET requests are subject to the same-origin policy
 - Only POST requests can encode parameters in the URL

##### 2. Which of the following is true about static and dynamic web content?

 - Static pages may include PHP programs, which execute at the browser
 - ***The server often produces dynamic content based on the contents of
   the database***
 - Static content may be re-generated with each request
 - Javascript programs embedded in HTML pages are run server-side to
   produce dynamic content

##### 3. SQL injection exploits a bug in what interaction of a web application?

 - Client to server
 - Network to server
 - Server to client
 - ***Server to database***

#####  4. SQL injection often allows an attacker to do which of the following?

 - Overrun a buffer to smash the stack
 - All of the above
 - Cause memory to be used after it's freed
 - ***Access information he shouldn't***

##### 5. If you had to summarize the key (most specific) programming failure with SQL injection, it would be:

 - ***Confusing data with code***
 - Bypassing authentication
 - Trusting without verifying
 - Circumventing the same origin policy

##### 6. What is escaping an example of?

 - Blacklisting
 - ***Sanitization***
 - Checking
 - Whitelisting
 
##### 7. Suppose a web application implements authentication by constructing an SQL query from HTML from data using PHP's prepared statements. What would happen if an attacker entered FRANK' OR 1=1; -- in the web form's user field?
 - The text will modify the structure of the SQL query and possibly
   bypass authentication
 - The text will be confused as the password and authentication will
   probably fail
 - The text will corrupt the query structure and the database will view
   it as a syntax error
 - ***The application will try to authenticate a user whose name is FRANK'
   OR 1=1; --***

##### 8. Why is it undesirable to implement session identifiers using (only) hidden form fields?

 - Such fields cannot include timeout information
 - Such fields cannot contain binary data
 - These fields are easily modified by the user
 - ***The session ID is forgotten when the browser window is closed***
 
 ##### 9. Suppose a browser submits a GET request to URL http://www.mybank.com/accountinfo on 20 February 2015. Which of the following cookies, if already stored at the browser, would be sent with the request?
 - lang=us-english; expires=Sat, 1-Aug-2015; path=/accountinfo/;
   domain=.fidelity.com
 - editon=us; expires=Thu, 19-Feb-2015; path=/accountinfo/prefs;
   domain=.mybank.com
 - edition=us; expires=Wed, 18-Feb-2015; path=/; domain=.mybank.com
 - ***sessid=ABCDEFG; expires=Sat, 21-Feb-2015; path=/; domain=.mybank.com***

##### 10. Which of the following are ways that session cookies could be stolen or forged?

 - Stealing it from the password database
 - ***Predicting the cookie's structure and reconstructing it***
 - ***Reading a cookie from an unencrypted web request***
 - ***Compromising the browser or server***
 
 ##### 11. Which of the following are ways to reduce the impact of a stolen cookies?
 - Prevent cookies from entering the DNS cache
 - ***Giving each cookie a timeout***
 - ***Changing a user's cookie from session to session***
 - ***Associate the cookie with the client�s IP address***
 
 ##### 12. How can the REFERER field be used to defend against CSRF attacks?
 - ***It can be used to ensure that sensitive requests are (only) initiated
   by interaction with a site's own pages***
 - It ensures that requests only come from authenticated users
 - It can't be used reliably because it only works for dynamic content
 - It can be used to check that a Javascript program is from the proper
   origin
 
 ##### 13. <script></script>tags in HTML pages most often identify programs written in what language?
 - PHP
 - C
 - Java
 - ***Javascript***
 
 ##### 14. The browser implements security for Javascript programs for what reason?
 - ***Such programs may access browser-controlled resources, which include
   potentially sensitive data in HTML documents and cookies***
 - It doesn't -- these programs are only used to render dynamic content
   but are otherwise not security-relevant
 - Such programs could deny service by running forever
 - It doesn't -- Javascript programs run at the server so the browser
   can ignore them
 
 ##### 15. XSS subverts what policy?
 - Whitelisting
 - ***Same Origin***
 - Availability
 - Secure defaults
 
 ##### 16. What is the difference between stored (or persistent) XSS and reflected XSS?
 - ***Stored XSS works by injecting code in a site's served content, while
   reflected XSS injects code in a URL***
 - Stored XSS works on database queries while reflected XSS works on
   cookies, which are received from and reflected back to the server
 - Stored XSS embeds Javascript in an a URL, while reflected XSS embeds
   it in a mirrored site
 - Stored XSS is amenable to blacklisting but reflected XSS is not
