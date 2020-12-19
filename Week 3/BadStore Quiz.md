# BadStore Quiz
##### 1. One of the BadStore pages has a hidden form field that establishes a new user's privilege level. What is the name of this field?

***role***

##### 2. How many items for purchase are in BadStore's database? Use SQL injection on the quick search form field to find out.

***16 ***

#####  3. Which of the following operations are suppliers permitted to do? Use SQL injection to bypass authentication, or find a way to create an account as a supplier.

 - ***View existing price list***
 - Cancel contract
 - ***Upload price list***
 - Submit monthly bill payment
 - Download an activity report

 'OR 1=1 OR'

##### 4. Log in as joe@supplier.com --- this is possible in a variety of ways, including SQL injection. Then look at his previous orders and answer the question: What credit card number did he use to make a purchase of $46.95? Multiple answers are possible, but we will accept all of them.

***5500000000000004***

##### 5. Get administrator privileges and then use the admin action to look at the user database. There are two users whose emails have the form XXX@whole.biz; what is the XXX portion of either of the two users? For example, if one of the users is jackie@whole.biz, the right answer is jackie. (The answer is case-sensitive.)

 ***fred***

##### 6. BadStore uses cookies to implement a session key, once you've authenticated, and for tracking the contents of the cart, once you've added something to it. You can figure out the cookies in use by BadStore in various ways. One way is to do an XSS attack on the guest book. Get the guest book to run the code <script>alert(document.cookie)</script> and it will tell you the current cookies. (Be sure you have popups enabled on your browser or this won't work.) Alternatively, you can examine the cookies directly using Firefox developer tools. Recall that cookies are pairs key=value. What is the key of the session cookie?

***SSOid***

##### 7 the key of the cookie used for the cart?

 ***CartID***

##### 8. BadStore's session cookie format is poorly designed because it is uses a predictable structure. In particular, it is an encoded string (with a URL-encoded newline at the end) of the form XXX:YYY:ZZZ:U. What are the XXX, YYY, and ZZZ portions of this string?

 - ***e-mail address***
 - expiration timeout
 - ***MD5 hash of password***
 - the number of fail login attempts
 - ***full name***
 - SHA1 hash of password
 - ***role***
 - integer that counts the number of times ever logged in
 
 ##### 9. BadStore's cart cookie is also an encoded string with a predictable structure XXX:YYY:... etc., and it probably contains information it shouldn't. Which field of the decoded string could an attacker change to give himself a discount on an item's price?

***3***