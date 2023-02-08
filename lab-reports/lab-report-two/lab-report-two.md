# **CSE 15L Winter 2023 Lab Report 2**
### Eric Song, Wednesday B270 1 p.m.
### Part 1: StringServer

StringServer.java Code:
```
import java.io.IOException;
import java.net.URI;


/**
 * ServerString objects implement the handleRequest method; this lets it
 * respond to changes in the URL.
 */
class ServerString implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    
    private static final int INITIAL = 0;
    private static final int DEFAULT_END = 2;
    private static final int ADDED_STRING = 1;
    String overallMessage = "";
    boolean firstMessage = true;

    /**
     * Determines the different responses based on how the URL is changed in
     * the browser.
     * 
     * @param url the URL being processed
     */
    public String handleRequest(URI url) {
        if (url.getPath().equals("/add-message")) {
            String query = url.getQuery();
            //check for valid query
            try {
                if (query.substring(INITIAL, DEFAULT_END).equals("s=")) {
                    //valid query, add query string to overlal string
                    String message = query.split("=")[ADDED_STRING];
                    overallMessage += message + "\n";

                    //return overall string
                    return overallMessage;
                } else {
                    //invalid query
                    return "Invalid Query";
                }
            } catch (Exception E) {
                return "Invalid Query";
            }
        } else if (firstMessage == true) {
            firstMessage = false;
            return "Use Path /add-message?s=<string>";
        } else {
            return "Invalid URL\nCurrent Strings:\n" + overallMessage;
        }

    }
}

/**
 * Runs the StringServer.
 */
class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new ServerString());
    }
}
```
### /add-message demonstrations:
<br /> C:\Users\19255\Documents\GitHub\cse15l-lab-reports\lab-reports\lab-report-two>java StringServer 4000
<br /> Server Started! Visit http://localhost:4000 to visit.
#### Initial State (before any strings are added): http://localhost:4000/
<br /> <img src="labreporttwo_ss_1.png" alt="" title="first ss" width="302" height="30" />
#### Screenshot 1:
![image](https://user-images.githubusercontent.com/67176000/217477282-3e655db9-f940-49ba-91ee-5b874ddbd384.png)   

>The method being called in StringServer.java is `handleRequest`.  
>The relevant argument to this method is the `URI url`.  
>Values of Relevant Fields:  
>`url`: http://localhost:4000/add-message?s=this%20is%20the%20first%20message%20to%20be%20added --> url input  
>`overallMessage`: ""  --> changes to "this is the first message to be added\n"  
>`firstMessage`: false --> stays false  
>the overallMessage String changes because the query is adding a string; the firstMessage boolean is the same because it is no longer the firstMessage  
#### Screenshot 2:
![image](https://user-images.githubusercontent.com/67176000/217477529-99dddcab-53a2-4abb-98c1-dedb75a1a4c2.png)   

>The method being called in StringServer.java is `handleRequest`.  
>The relevant argument to this method is the `URI url`.  
>Values of Relevant Fields:  
>`url`: http://localhost:4000/add-message?s=this%20is%20the%20second%20message%20to%20be%20added! --> url input  
>`overallMessage`: ""  --> changes to "this is the first message to be added\nthis is the second message to be added!\n"  
>`firstMessage`: false --> stays false  
>the overallMessage String changes because the query is adding a string; the firstMessage boolean is the same because it is no longer the firstMessage

### Part 2: Bug Fixes for ArrayExamples.java  
**Failure-Inducing Inputs:**  
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    //successful input
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);

    int[] input2 = {1, 1};
    ArrayExamples.reverseInPlace(input2);
    assertArrayEquals(new int[]{ 1, 1 }, input2);

    int[] input3 = {1, 3, 5, 3, 1};
    ArrayExamples.reverseInPlace(input3);
    assertArrayEquals(new int[]{1, 3, 5, 3, 1}, input3);

    int[] input4 = {1, 2, 2, 1};
    ArrayExamples.reverseInPlace(input4);
    assertArrayEquals(new int[] {1, 2, 2, 1}, input4);

    //faiure-inducing input
    int[] input5 = {1, 2, 3, 4, 5};
    ArrayExamples.reverseInPlace(input5);
    assertArrayEquals(new int[] {5, 4, 3, 2, 1}, input5);

    int[] input6 = {1, 3, 5, 2};
    ArrayExamples.reverseInPlace(input6);
    assertArrayEquals(new int[] {2, 5, 3, 1}, input6);

    
  }


  @Test
  public void testReversed() {
    //successful input
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));

    //failure-inducing input
    int[] input2 = {1, 3, 5, 2};
    assertArrayEquals(new int[] {2, 5, 3, 1}, ArrayExamples.reversed(input2));
  }

  @Test
  public void testAverageWithoutLowest() {
    //successful input
    double[] input1 = {1, 2, 3, 4, 5, 6};
    assertEquals(4.0, 
        ArrayExamples.averageWithoutLowest(input1), 0.001);

    //failure-inducing
    double[] input2 = {1, 1, 2, 3, 4, 5, 6};
    assertEquals(4.0, 
        ArrayExamples.averageWithoutLowest(input2), 0.001);
    
  }
}
```
<br /> The above block of code contains the JUnit tests for ArrayExamples.java   

#### Symptoms for reverseInPlace  
![image](https://user-images.githubusercontent.com/67176000/217477955-25790c90-14d9-4b23-a706-1960d1e3f089.png)   
Based on the JUnit tests done on this method, it seems that it only works as intended when the input array is palindromic.  
This suggests that there is an error in how the array is being copied.  

#### Symptoms for reversed  
![image](https://user-images.githubusercontent.com/67176000/217478099-0d8f4543-e699-4ce6-b2ab-d71fbaae3e82.png)   
Based on the JUnit tests, it seems that the contents of the array being output are only 0s.  
This suggests that there is an error in copying the contents of one array to another.  

#### Symptoms for averageWithoutLowest  
![image](https://user-images.githubusercontent.com/67176000/217478250-524672e4-6abb-4a5e-bec3-1d9f760b46ba.png)   
Based on the JUnit test show above, there is an error in finding the average.  
The hand-calculated value is larger than the returned value; this suggests that perhaps there is an error in how the sum is divided.  

### Bug Fixes:  
reverseInPlace:  
*Before*
```  
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```  
*After*  
```  
  static void reverseInPlace(int[] arr) {
    //temporary array to hold reverse array
    int[] temp = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      temp[i] = arr[arr.length - i - 1];
    }
    //reassigning arr
    for (int j = 0; j < arr.length; j++) {
      arr[j] = temp[j];
    }
  }
  ```  
The before code is simplying assigning the front sections of the input array to the back sections of the input arr. This was producing the palindromic symptom. By deep copying arr in reverse order to temp and then recopying it back into arr, arr becomes reversed.  
  
  reversed:  
  *Before*  
  ```  
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = newArray[arr.length - i - 1];
    }
    return arr;
  }
  ```  
  *After*  
  ```  
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
  ```  
The before code was assigning arr to newArray instead of the other way around. Because newArray is a newly initialized integer array, all its contents were 0s. This turned arr into an array of 0s. Switching the order around deep copies arr in reverse order into the newArray. Then, newArray is returned instead of arr.  
  
  averageWithoutLowest:  
  *Before*
  ```  
  static double averageWithoutLowest(double[] arr) {
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
    }
    return sum / (arr.length - 1);
  }
  ```  
  *After*  
  ```  
  static double averageWithoutLowest(double[] arr) {
    int numRemoved = 0;
    if(arr.length < 2) { return 0.0; }
    double lowest = arr[0];
    for(double num: arr) {
      if(num < lowest) { lowest = num; }
    }
    double sum = 0;
    for(double num: arr) {
      if(num != lowest) { sum += num; }
      else {
        numRemoved++;
      }
    }
    return sum / (arr.length - numRemoved);
  }
  
  ```  
The before code was assuming that there would only be one instance of the lowest number. This assumption causes the symptom where the expected average is larger than the returned average. The fix keeps track of how many instances of the lower number there are. Then it accounts for that change in the operation calculating the average.
  
### Part 3: Reflection
From Week 2, I learned how to copy files from my end onto the remove server with the scp command (by using scp <file> cs15lwi23amv@ieng6.ucsd.edu:~/). I also learned how to use git clone (git clone <repo-url>) to clone repositories from Github onto my own computer or the remote server. From Week 3, I learned how to use JUnit to design test cases to figure out whether my code is performing how it should be or not. I didn't know that I could check for differences in arrays with assertArrayEquals. This helped me out a lot (especially since it was relevant to my PA assignment in CSE 12). 
  
  








