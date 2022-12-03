# Yara (TryHackMe)
 
    Link : https://tryhackme.com/room/yara
    Data : 22/7/2022
    Author : [ParotRootHacker](https://tryhackme.com/p/ParotRootHacker)


### Task 1  : Introduction
*   Read the Information (No Answer Needed)



### Task 2 : What is Yara?

* What is the name of the base-16 numbering system that Yara can  detect?


> hex

*Explanation* : 
    With such a fitting quote, Yara can identify information based on both binary and textual patterns, such as hexadecimal and strings contained within a file.


*  Would the text "Enter your Name" be a string in an application? (Yay/Nay)


> yay

*Explanation* : 
    Malware, just like our "Hello World" application, uses strings to store textual data. Here are a few examples of the data that various malware types store within strings:



### Task 3 : Installing Yara (Ubuntu/Debian & Windows)
*   Read the Information (No Answer Needed)



### Task 4 : Deploy
*   Read the Information (No Answer Needed)



### Task 5 : Introduction to Yara Rules
*   Read the Information (No Answer Needed)



### Task 6 : Expanding on Yara Rules
*   Read the Information (No Answer Needed)




### Task 7 :  Yara Modules
*   Read the Information (No Answer Needed)



### Task 8 :  Other tools and Yara
*   Read the Information (No Answer Needed)



### Task 9 : What is Yara?

* Scan file 1. Does Loki detect this file as suspicious/malicious or benign?


> suspicious

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd tools/Loki/
cmnatic@thm-yara:~/tools/Loki$ python loki.py -p ../../suspicious-files/file1/
" Output : 
[NOTICE] Results: 0 alerts, 1 warnings, 7 notices
[RESULT] Suspicious objects detected! <======== LOOK HERE
[RESULT] Loki recommends a deeper analysis of the suspicious objects.
[INFO] Please report false positives via https://github.com/Neo23x0/signature-base
[NOTICE] Finished LOKI Scan SYSTEM: thm-yara TIME: 20220722T04:46:59Z"
```



* What Yara rule did it match on?


> webshell_metaslsoft

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd tools/Loki/
cmnatic@thm-yara:~/tools/Loki$ python loki.py -p ../../suspicious-files/file1/
" Output : 
FILE: ../../suspicious-files/file1/ind3x.php SCORE: 70 TYPE: PHP SIZE: 80992 
FIRST_BYTES: 3c3f7068700a2f2a0a09623337346b20322e320a / <?php/*b374k 2.2 
MD5: 1606bdac2cb613bf0b8a22690364fbc5 
SHA1: 9383ed4ee7df17193f7a034c3190ecabc9000f9f 
SHA256: 5479f8cd1375364770df36e5a18262480a8f9d311e8eedb2c2390ecb233852ad CREATED: Mon Nov  9 15:15:32 2020 MODIFIED: Mon Nov  9 13:06:56 2020 ACCESSED: Fri Jul 22 04:18:51 2022 
REASON_1: Yara Rule MATCH: webshell_metaslsoft SUBSCORE: 70 <===== LOOK HERE
"

```


* What does Loki classify this file as?


> Web Shell

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd tools/Loki/
cmnatic@thm-yara:~/tools/Loki$ python loki.py -p ../../suspicious-files/file1/
" Output : 
REASON_1: Yara Rule MATCH: webshell_metaslsoft SUBSCORE: 70 
DESCRIPTION: Web Shell - file metaslsoft.php <==== LOOK HERE 
"

```


* Based on the output, what string within the Yara rule did it match on?


> Str1

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd tools/Loki/
cmnatic@thm-yara:~/tools/Loki$ python loki.py -p ../../suspicious-files/file1/
" Output : 
DESCRIPTION: Web Shell - file metaslsoft.php 
MATCHES: Str1: $buff .= <=== LOOK HERE 
"

```



* What is the name and version of this hack tool?


> b374k 2.2

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd tools/Loki/
cmnatic@thm-yara:~/tools/Loki$ python loki.py -p ../../suspicious-files/file1/
" Output : 
FIRST_BYTES: 3c3f7068700a2f2a0a09623337346b20322e320a / <?php/*b374k 2.2 <==== LOOK HERE 
MD5: 1606bdac2cb613bf0b8a22690364fbc5 
"

```

* Inspect the actual Yara file that flagged file 1. Within this rule, how many strings are there to flag this file?


> 1

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd tools/Loki/
cmnatic@thm-yara:~/tools/Loki$ python loki.py -p ../../suspicious-files/file1/
" Output : 
DESCRIPTION: Web Shell - file metaslsoft.php REF: - 
MATCHES: Str1: $buff . <===== LOOK HERE 
"

```

*  Scan file 2. Does Loki detect this file as suspicious/malicious or benign?


> benign

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd tools/Loki/
cmnatic@thm-yara:~/tools/Loki$ python loki.py -p ../../suspicious-files/file2/
" Output : 
[INFO] Scanning ../../suspicious-files/file2/ ...  
[NOTICE] Results: 0 alerts, 0 warnings, 7 notices
[RESULT] SYSTEM SEEMS TO BE CLEAN. <== LOOK HERE BENIGN MEANS CLEAN 
"

```

 
*    Inspect file 2. What is the name and version of this web shell?


> b374k 3.2.3

*Explanation* : 
```bash
cmnatic@thm-yara:~$ cd suspicious-files/file2/
cmnatic@thm-yara:~/tools/Loki$ lesss 1ndex.php
" Output : 
<?php
/*
        b374k shell 3.2.3 <==== LOOK HERE 
        Jayalah Indonesiaku
        (c)2014
        https://github.com/b374k/b374k

*/

"

```

 To be Continued....
