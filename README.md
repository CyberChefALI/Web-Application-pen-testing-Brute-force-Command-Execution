# Web-Application-pen-testing-Command-Execution-DVWA


## OVERVIEW 

This lab is a hands-on exercise to learn how poorly secured websites can let attackers run unauthorized commands on the underlying server.

You will use a practice app (DVWA) to test exploits across four security levels—from completely unprotected (Low) to fully secure (Impossible).


## Prerequisites

* Ensure you have DVWA installed and running.
* Familiarize yourself with BurpSuite and the FoxyProxy extension for effective testing.


## STEP - 1  Setup Metasploit & DVWA



Before you can practice hacking techniques, you need to set up your environment. This involves launching DVWA (your vulnerable practice target) and preparing Metasploit (the industry-standard penetration testing toolkit used to exploit flaws and manage attacks).

<img width="1920" height="991" alt="meta  Running  - Oracle VirtualBox 28_10_2026 14_39_22" src="https://github.com/user-attachments/assets/01fadeff-4967-4780-bb33-7c150388f8bf" />
<img width="1920" height="1020" alt="meta  Running  - Oracle VirtualBox 28_10_2026 14_45_17" src="https://github.com/user-attachments/assets/4452909e-c17a-449e-9f2d-0cf17db161ae" />
<img width="1920" height="1020" alt="Metasploitable2 - Linux - Personal - Microsoft​ Edge 28_10_2026 14_49_47" src="https://github.com/user-attachments/assets/0d9bbef8-908c-4ab0-a88a-3e761c04c4b6" />


## STEP - 2 Launch DVWA on  Low-Level Command Injection

Objective: Identify and exploit a low-level command injection vulnerability.

<img width="1920" height="1020" alt="Damn Vulnerable Web App (DVWA) v1 0 7 __ Welcome and 1 more page - Personal - Microsoft​ Edge 28_10_2026 14_50_30" src="https://github.com/user-attachments/assets/f64147cb-374b-4ce6-b9b6-4c27e065de11" />
<img width="1920" height="1020" alt="Damn Vulnerable Web App (DVWA) v1 0 7 __ Welcome and 1 more page - Personal - Microsoft​ Edge 28_10_2026 14_50_53" src="https://github.com/user-attachments/assets/00978c3d-f8eb-4c95-8651-fed58f6634ba" />

A) Test a Valid IP Address:

Input http://192.168.1.104/ and submit the form.
Observe the response from the application.

<img width="1920" height="1020" alt="Damn Vulnerable Web App (DVWA) v1 0 7 __ Vulnerability_ Brute Force - Personal - Microsoft​ Edge 03_11_2026 10_43_34" src="https://github.com/user-attachments/assets/30617ac7-df58-403e-a496-3e201660a36d" />

B) Inject a Malicious Command:

Now, use the following payload:
192.168.1.104 ; whoami ; cat /etc/passwd

<img width="1920" height="1020" alt="Damn Vulnerable Web App (DVWA) v1 0 7 __ Vulnerability_ Brute Force - Personal - Microsoft​ Edge 03_11_2026 10_50_46" src="https://github.com/user-attachments/assets/0bc3bc07-3e33-4c90-a892-7d00ebaab42d" />

C) Review and Impact
What information was returned? Discuss the implications of this vulnerability.


## STEP - 2  Medium-Level Command Injection

A) Test a Valid IP Address:
Input http://192.168.1.104/ and submit the form.
Observe the response from the application.

B) Set the security level to medium
<img width="1920" height="1020" alt="Damn Vulnerable Web App (DVWA) v1 0 7 __ Vulnerability_ Brute Force - Personal - Microsoft​ Edge 03_11_2026 10_56_46" src="https://github.com/user-attachments/assets/94dafaaf-75e8-4657-86d4-b563dfeac902" />

C) Bypass Input Restrictions:

Use the following payload:
192.168.1.104 | whoami
Submit the form and observe the result.
<img width="1920" height="1020" alt="Damn Vulnerable Web App (DVWA) v1 0 7 __ Vulnerability_ Brute Force - Personal - Microsoft​ Edge 03_11_2026 11_01_17" src="https://github.com/user-attachments/assets/540d2632-c25d-4a84-91cd-8b0835b85d26" />

D) Review and Impact
How did you bypass the input restrictions? What does this say about the security of the application?


## STEP -3 High-Level Command Injection

A) Test a Valid IP Address:
Input http://192.168.1.104/ and submit the form.
Observe the response from the application.

B) Set the security level to HIGH
<img width="1920" height="1020" alt="Captures - File Explorer 03_11_2026 11_07_23" src="https://github.com/user-attachments/assets/e6e88f23-182c-4041-ac99-2d7002c4ceca" />

C) Bypass Input Restrictions:
Use a Different Payload:

Test the following command:
192.168.1.104 |whoami
Submit and check the response.
<img width="1920" height="1020" alt="Captures - File Explorer 03_11_2026 11_12_54" src="https://github.com/user-attachments/assets/1e93a719-a161-45f9-b71c-d03610b45224" />

D) Review and Impact
Did this command execute successfully? Explain why or why not, considering the input sanitization in place.


## LAB REPORT


Exercise 1 (Low Security):

What you saw: The server blindly ran whatever you typed without checking anything.

Why it matters: It proves that zero security lets anyone take over the app instantly.

Exercise 2 (Medium Security):

What you saw: The app tried to block certain words or characters, but you found a loophole to make it work anyway.

Why it matters: It shows that blocking a few "bad words" (blacklisting) isn't enough to stop a clever attacker.

Exercise 3 (High Security):

What you saw: The app used much tighter rules, forcing you to use advanced tricks or alternative commands to bypass them.

Why it matters: It proves that even strict filters can fail if the app is still trying to clean dirty input instead of avoiding system commands altogether.


## Conclusion

In this lab, you have learned about Command Injection vulnerabilities and how they can be exploited at different levels. Take note of the importance of input validation and sanitization to secure applications against such attacks.

