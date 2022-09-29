# Week 1 Lab Report

- Installing VScode

![Image](https://matttam2002.github.io/cse15l-lab-reports/screenshot%20for%20cs15L%20week0.png)

- Remotely Connecting
Here is my output in VS-code

![Image](https://matttam2002.github.io/cse15l-lab-reports/Screenshot.1.png)

- Trying Some Commands

![Image](https://matttam2002.github.io/cse15l-lab-reports/screenshot.2.png)

![Image](https://matttam2002.github.io/cse15l-lab-reports/Screenshot.3.png)


- Moving Files with scp

[cs15lfa22im@ieng6-203]:~:51$ javac WhereAmI.java 

[cs15lfa22im@ieng6-203]:~:53$ java WhereAmI

Linux

cs15lfa22im

/home/linux/ieng6/cs15lfa22/cs15lfa22im

/home/linux/ieng6/cs15lfa22/cs15lfa22im

- Setting an SSH Key

PS C:\Users\85295\Desktop\cs15L> ssh cs15lfa22im@ieng6.ucsd.edu

Last login: Wed Sep 28 16:04:50 2022 from 100.81.35.42

Hello cs15lfa22im, you are currently logged into ieng6-203.ucsd.edu
 
You are using 0% CPU on this system
 
Cluster Status 

Hostname     Time    #Users  Load  Averages  

ieng6-201   21:25:01   10  0.00,  0.02,  0.05

ieng6-202   21:25:01   5   0.03,  0.04,  0.05

ieng6-203   21:25:01   16  0.07,  0.06,  0.05

- Optimizing Remote Running

PS C:\Users\85295\Desktop\cs15L> scp WhereAmI.java cs15lfa22im@ieng6.ucsd.edu:~/
WhereAmI.java                                                                                                                      100%  346    12.1KB/s   00:00    
PS C:\Users\85295\Desktop\cs15L> ssh cs15lfa22im@ieng6.ucsd.edu "ls"   

WhereAmI.class

WhereAmI.java

hello.txt

perl5

PS C:\Users\85295\Desktop\cs15L> ssh cs15lfa22im@ieng6.ucsd.edu 

Last login: Wed Sep 28 21:34:46 2022 from cpe-75-80-53-45.san.res.rr.com

Hello cs15lfa22im, you are currently logged into ieng6-203.ucsd.edu

You are using 0% CPU on this system

Cluster Status 

Hostname     Time    #Users  Load  Averages  

ieng6-201   21:35:01   10  0.24,  0.07,  0.06

ieng6-202   21:35:01   9   0.00,  0.03,  0.05

ieng6-203   21:35:01   12  0.00,  0.01,  0.05
 
Wed Sep 28, 2022  9:39pm - Prepping cs15lfa22

[cs15lfa22im@ieng6-203]:~:65$ javac WhereAmI.java

[cs15lfa22im@ieng6-203]:~:66$ java WhereAmI 

Linux

cs15lfa22im

/home/linux/ieng6/cs15lfa22/cs15lfa22im

/home/linux/ieng6/cs15lfa22/cs15lfa22im

test

(I made a edit to the local file , WhereAmI.java, which I print one more line of a string “test”) 




