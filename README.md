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
(Burpsuite can be used to intercept packets)

<img src="blue-vuln2.gif">

## Green

Vulnerability #1: __________________

Description:

<img src="green-vuln1.gif">

Vulnerability #2: __________________

Description:

<img src="green-vuln2.gif">


## Red

Vulnerability #1: __________________

Description:

<img src="red-vuln1.gif">

Vulnerability #2: __________________

Description:

<img src="red-vuln2.gif">


## Notes

Describe any challenges encountered while doing the work

