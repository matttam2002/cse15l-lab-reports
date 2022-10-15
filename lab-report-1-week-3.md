# Week 3 Lab Report

# Part 1
- Simple Search Engine
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList; 
class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> list = new ArrayList <String> () ;

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                list.add(parameters[1]);
            }
            return parameters[1]+ " added"; 
        }
        else if (url.getPath().contains("/search")){
            String[] parameters = url.getQuery().split("=");
            String result = ""; 
            if (parameters[0].equals("s")){
                for(int i=0; i<list.size(); i++){                   
                    if (list.get(i).contains(parameters[1])){
                        result = result +" " +list.get(i);
                    }
                }
            }
            return result;
        }
        else if ( url.getPath().equals("/")) {
            return ("Please add elements !"); 
        }
        else {
            return  "404 Not Found!"; 
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
- Using add

![Image](https://matttam2002.github.io/cse15l-lab-reports/lab3_2.png)
~ The method I use is call handleRequest(URI url) 

~ When the program run the method, it recognize the path of the url is add. And it split the argument by =. So the arguments value is 0 which is "s" and 1 which is "iphone". 

~ If I change the value, the program won't recognize which input should be added to the list. 

- showing the URL in the browser 
![Image](https://matttam2002.github.io/cse15l-lab-reports/lab_3_1.png)
~ The method I use is call handleRequest(URI url) 

~ When the program run the method, it recognize the path of the url is add. And it split the argument by =. So the arguments value is empty. 

~ If I change the value, the program won't pass all the if instruction, so it will return "404 Not Found!". 


- response on the page.

![Image](https://matttam2002.github.io/cse15l-lab-reports/lab3_5.png)

~ The method I use is call handleRequest(URI url) 

~ When the program run the method, it recognize the path of the url is search. And it split the argument by =. So the arguments value is 0 which is "s" and 1 which is "one". 

~ If I change the value, the program will end up not knowing which value should input to the loop which determine which element in list contain the input string. 

# Part 2

- First Bug 

~The Failure inducing input
```
 @Test 
	public void testReverseInPlace() {
    int[] input1 = { 3,4,5 };
    ArrayExamples.reverseInPlace(input1);
    System.out.println(Arrays.toString(input1));
    assertArrayEquals(new int[]{ 5,4,3 }, input1);
	}
```

~ The symptom
```
JUnit version 4.13.2
.[5, 4, 5]
E
Time: 0.011
There was 1 failure:
1) testReverseInPlace(ArrayTests)
arrays first differed at element [2]; expected:<3> but was:<5>
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace(ArrayTests.java:12)
        ... 30 trimmed
Caused by: java.lang.AssertionError: expected:<3> but was:<5>
        at org.junit.Assert.fail(Assert.java:89)
        at org.junit.Assert.failNotEquals(Assert.java:835)
        at org.junit.Assert.assertEquals(Assert.java:120)
        at org.junit.Assert.assertEquals(Assert.java:146)
        at org.junit.internal.ExactComparisonCriteria.assertElementsEqual(ExactComparisonCriteria.java:8)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:76)
        ... 36 more

FAILURES!!!
Tests run: 1,  Failures: 1

```
~ The bug 
```
static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
~ The input for the test is { 3,4,5 }. And the output is {5,4,5}, which not the expect output. In the bug, the loop run normally for the first 2 element in the array, but fail in the last element. In the loop, when i equal 0, it create {5,4,5}, which changing the arr[0] into 
arr[2]. And when i equal 1, it change the arr[1]into arr[1]. But when i equal 2, it change the arr[2] into arr[0]. It looks right, but notice that it is taking arr[2] of the previous arr = {5,4,5}. So it causes the failure output. 

- Second Bug 

~The Failure inducing input
```@Test
public void testListExamples() {
List<String> temp1= new ArrayList<String>(); 
temp1.add("a");
temp1.add("c");
List<String> temp2 = new ArrayList<String>(); 
temp2.add("b");
temp2.add("d");

List<String> expect = new ArrayList<String>(); 
expect.add("a");
expect.add("b");
expect.add("c");
expect.add("d");

System.out.println(ListExamples.merge(temp1, temp2));
assertEquals( expect, ListExamples.merge(temp1, temp2));
}
```
~ The symptom
```
Time: 8.538
There was 1 failure:
1) testListExamples(ListTests)
java.lang.OutOfMemoryError: Java heap space
        at java.base/java.util.Arrays.copyOf(Arrays.java:3512)
        at java.base/java.util.Arrays.copyOf(Arrays.java:3481)
        at java.base/java.util.ArrayList.grow(ArrayList.java:237)
        at java.base/java.util.ArrayList.grow(ArrayList.java:244)
        at java.base/java.util.ArrayList.add(ArrayList.java:454)
        at java.base/java.util.ArrayList.add(ArrayList.java:467)
        at ListExamples.merge(ListExamples.java:42)
        at ListTests.testListExamples(ListTests.java:23)
        at java.base/java.lang.invoke.LambdaForm$DMH/0x0000000800c12400.invokeVirtual(LambdaForm$DMH)
        at java.base/java.lang.invoke.LambdaForm$MH/0x0000000800c13000.invoke(LambdaForm$MH)
        at java.base/java.lang.invoke.Invokers$Holder.invokeExact_MT(Invokers$Holder)

FAILURES!!!
Tests run: 1,  Failures: 1
```
~ The bug 
```
 while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
```
~ The symptom and the bug is related because the sympton is "OutOfMemoryError: Java heap space" , which the loop is running infinitely. And by tracing the failure, I can tell the error is at ListExamples.java:42.And I find out in the while loop, it runs list2, and stop when index2 < list2.size. But in the loop, index1+=1, index2 will stay the same, which is 0. Therefore, the loop will go infinitely. 



