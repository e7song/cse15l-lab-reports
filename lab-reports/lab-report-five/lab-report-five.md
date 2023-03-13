# CSE 15L Winter 2023 Lab Report #5   
### Eric Song, Wed. 1 p.m.   
## **Week 7- CSE Labs "Done Quick"**   

### **Introduction**   
Lab 7 was my favorite lab because it was fun experimenting with how I could make process of running each step smoother and faster. 
This would include using techniques such as the pressing up/down arrow to navigate previously used commands and various other shortcuts.   

### **Previous Process**      
```
+-- lab7
|   +-- lib
|       +-- hamcrest-core-1.3.jar
|       +-- junit-4.13.2.jar
|   +-- ListExamples.java
|   +-- ListExamplesTests.java
```   
To clone the repository, I would use `git clone git@github.com:e7song/lab7.git <enter>`.   

For compiling and running the code, I would use   
`javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter>` and    
`java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>`.  

To fix the error, I would use `nano ListExamples.java <enter>`.   

Finally, to push and commit to github, I would use `git commit -am "Resolved infinite loop error" && git push <enter>`.   
Although I managed to cut my time down to about one minute, this challenge could have been completed much faster with a script.   

### **New Process**   
Using what I've learned, I made a script that would do every step in the challenge (aside from the manual ones like forking the repository and deleting it).  

#### Setup   

![image](https://user-images.githubusercontent.com/67176000/224747765-2c289c23-118b-4e1d-8ee6-1155f33245ca.png)   

First I created a script and used `scp` to copy it onto my remote account.   

![image](https://user-images.githubusercontent.com/67176000/224762773-41c7f29a-7b18-4917-8b16-7295297b1d53.png)   

The first few lines will clone the repository and then change my directory so I am in the correct spot to start running and editing files.   

![image](https://user-images.githubusercontent.com/67176000/224763592-317baedf-b5fc-46c6-8afd-089a6c3eed27.png)   

![image](https://user-images.githubusercontent.com/67176000/224763712-e09bcd00-d0dc-432e-a36f-d414c726631a.png)   

Next, I compile and run the code.   

![image](https://user-images.githubusercontent.com/67176000/224763856-853748a1-c5b8-487f-9c76-116c8ad1ef6c.png)   

Then, I edit the code using `sed`.   

![image](https://user-images.githubusercontent.com/67176000/224764817-6c2e9c14-b0df-4593-b1a0-4684d3ccf106.png)   

This way, I can cut out the use of `nano` and directly change the file. I compile and run the code again.     

![image](https://user-images.githubusercontent.com/67176000/224764973-c791334b-e056-484c-858c-4ed79ada9b9a.png)   

This time, there aren't any errors.   

![image](https://user-images.githubusercontent.com/67176000/224765124-ff372e58-df72-4822-a41f-01c6aab824d8.png)   

I commit and push the code.   

![image](https://user-images.githubusercontent.com/67176000/224765350-a965ac54-fd05-4ccd-b04e-2ed3beada535.png)   

![image](https://user-images.githubusercontent.com/67176000/224765307-529b0647-8dea-4705-9415-497f0d711dc5.png)   

When I check the repository, the updates are reflected!   

![image](https://user-images.githubusercontent.com/67176000/224765954-f4e27924-4c2f-4b74-acc0-c63a5d097d61.png)   

![image](https://user-images.githubusercontent.com/67176000/224766227-b97cff70-75f1-4685-930f-d225bab7519c.png)   

My script basically just runs the same thing I ran in lab, just bundled neatly into one place. However, there is a key difference.   
I used `sed` instead of `nano` to edit my code.   

### **Explanation**   
```
sed -i '43d' ListExamples.java
sed -i '42d' ListExamples.java
```   
These first two lines of code delete line 43 and line 42.   
```
sed -i '41 a\
      result.add(list2.get(index2));' ListExamples.java
sed -i '42 a\
      index2 += 1;' ListExamples.java
```   
Then, the next two `sed` commands add two lines of code.   
The `a/` means to add in the given line after the specified line number.   

Overall, using `sed` greatly increased the speed at which I could fix the code.   



















