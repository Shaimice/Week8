# Project 8 - Pentesting Live Targets

Time spent: **14** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection (SQLI)
- Summary: Navigated to the Public Site and selected Find a Salesperson. Selected sales person and inserted the SQLI provided in the assignment hints (' OR SLEEP(5)=0--'). When initiated, the website with sleep for 5 seconds before it reloads/refreshes.

- GIT Walkthrough: ![](https://github.com/Shaimice/Week8/blob/master/SQLI.gif)

Vulnerability #2: Session Hijacking/Fixation
- Summary: Opened Chrome browser and Internet Explorer (IE) browser and navigated both to the Login page. Logged in with credentials on the IE browser and captured the PHPSESSIONID using the provided hacktools.  On the Chrome browser used the same hacktools to paste the PHPSESSIONID from IE to Chrome.  This allowed access to the site using the Chrome Browser without having to provide credentials.

- GIT Walkthrough: ![](https://github.com/Shaimice/Week8/blob/master/Fix.gif)

## Green

Vulnerability #1: User Enumeration
- Summary: Using login hint (jmonroe99) in the assignment instructions, attempted to login with an improvised password. An attempt was made with an authenticated Username and one that was not.  Results revealed a change in login feedback, verifying a valid username from the server.

- GIT Walkthrough: ![](https://github.com/Shaimice/Week8/blob/master/User.gif)

Vulnerability #2: Cross-Site Scripting (XSS)
- Summary: Navigated to the public site and selected Contact. Entered name and email into the requisite fields.  In the Feedback field, inserted the following script: <script>alert('Shayne found the XSS!');</script>).  Logged into the site and selected Feedback.  An alert is thrown identifying the XSS.

- GIT Walkthrough: ![](https://github.com/Shaimice/Week8/blob/master/XSS.gif)

## Red

Vulnerability #1: Insecure Direct Object Reference (IDOR)
- Summary: Captured the GET request in BURP and sent to intruder.  Initiated enumerated payload to discover Testy McTesterson (NOT PUBLIC UNTIL SEPT. 1), represented by if=10: https://35.202.226.35/red/public/salesperson.php?id=10 and Lazy Lazyman (FIRED FOR STEALING), represented by id=11: https://35.202.226.35/red/public/salesperson.php?id=11.

- GIT Walkthrough: ![](https://github.com/Shaimice/Week8/blob/master/IDOR.gif)

Vulnerability #2: Cross-Site Forgery Request (CSRF)
- Summary: Logged into the site and navigated to Salesperson.  Selected a Salesperson by clicking Edit.  Captured the POST request in BURP and modified the First name, Last name, telephone and email. Selected Go in BURP and then selected Back to Salespeople List hyperlink.  The Salespeople page now reflects the changes that were made.

- GIT Walkthrough: ![](https://github.com/Shaimice/Week8/blob/master/CSRF.gif)

## Bonus Objective 1 - Additional Information
- Operating System: Linux Ubuntu 16.04
- Web Application: Apache 2.4.18
- DBMS: MySQL Version 5.0.12

- GIT Walkthrough: ![](https://github.com/Shaimice/Week8/blob/master/SQLMAP.gif)

## Notes

I was attempting to complete Bonus Objective 2 (Optional) and while trying a few different XSS alternatives to solve the challenge.  Unfortunately, when I tried the redirect to another website using XSS, I am not able to get the server to escape out of executing the previous XSS scripts that were saved.  I was not able to get past the website redirect despite there being additional XSS scripts that I created in an attempt to capture cookies.
