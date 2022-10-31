# Week 4 Lab Report 

# Find

1. 
```
[cs15lfa22im@ieng6-202]:technical:231$ find -size +100k
./911report/chapter-1.txt
./911report/chapter-12.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-3.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./biomed/1471-2105-3-2.txt
```
For "find -size" , it find the files in technical that it's size is greater than 100kb. 

2. 
``` 
[cs15lfa22im@ieng6-202]:technical:232$ find -type d
.
./911report
./biomed
```
For "find -type d" , it finds which files is directory type. 

3. 
``` 
[cs15lfa22im@ieng6-202]:technical:233$ find -empty
./biomed/gb-2002-3-12-research0075.txt
```
For "find -empty", it finds file that are empty . 

# Less 

1. 
``` 
[cs15lfa22im@ieng6-202]:technical:239$ less -p "Boston" ./911report/chapter-1.txt
```
![Image](https://matttam2002.github.io/cse15l-lab-reports/Screenshot%20lab4_1.png)

For "less -p", it searches the world "boston" in the file ./911report/chapter-1.txt and highlight the word "boston" when printing out the content. 

2. 
``` 
[cs15lfa22im@ieng6-202]:technical:241$ less -N ./911report/chapter-1.txt
```
![Image](https://matttam2002.github.io/cse15l-lab-reports/Screenshot%20lab4_2.png)

For "less -N", it provide the line number when printing out the content.

3.

```
[cs15lfa22im@ieng6-202]:technical:250$ [cs15lfa22im@ieng6-202]:technical:250$ less +10 ./911report/chapter-1.txt
```
![Image](https://matttam2002.github.io/cse15l-lab-reports/Screenshot%20lab4_3%20.png)

For "less +10", it print out the content start from line 10. 

# Grep 

1. 
``` 
[cs15lfa22im@ieng6-202]:technical:210$ grep -c "Boston" 911report/*.txt
911report/chapter-1.txt:36
911report/chapter-10.txt:0
911report/chapter-11.txt:0
911report/chapter-12.txt:0
911report/chapter-13.1.txt:0
911report/chapter-13.2.txt:24
911report/chapter-13.3.txt:0
911report/chapter-13.4.txt:1
911report/chapter-13.5.txt:2
911report/chapter-2.txt:1
911report/chapter-3.txt:0
911report/chapter-5.txt:0
911report/chapter-6.txt:4
911report/chapter-7.txt:6
911report/chapter-8.txt:1
911report/chapter-9.txt:0
911report/preface.txt:0
```
For "grep -c", it searches all the files in the directory 911report, and find each files and count many times does "Boston" appear. 

2. 
```
[cs15lfa22im@ieng6-202]:technical:213$ grep -v "a" 911report/chapter-1.txt

"WE HAVE SOME PLANES"

INSIDE THE FOUR FLIGHTS

```
For "grep -v", it print out all the lines that doesn't contain "a" in 911report/chapter-1.txt file.

3.

```
[cs15lfa22im@ieng6-202]:technical:216$ grep ^B 911report/chapter-1.txt

Boarding the Flights
```


For "grep ^B", it print out all the lines that start with the character B.
