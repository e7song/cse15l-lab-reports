# CSE 15L Winter 2023 Lab Report #4   
### Eric Song, Wed. 1 p.m.    

#### Week 7 Lab Tasks
>1. Setup Delete any existing forks of the repository you have on your account
>2. Setup Fork the repository
>3. The real deal Start the timer!
>4. Log into ieng6
>5. Clone your fork of the repository from your Github account
>6. Run the tests, demonstrating that they fail
>7. Edit the code file to fix the failing test
>8. Run the tests, demonstrating that they now succeed
>9. Commit and push the resulting change to your Github account (you can pick any commit message!)   


### Step 1: Preparing for the Competition   
Before starting the competition, it's important to make sure that any existing forks (from previous attempts) are deleted.
To do so, click on the **Settings** button ⚙️.   

![image](https://user-images.githubusercontent.com/67176000/221398308-a059a567-408b-437c-b57c-f91f991e890e.png)   

Scroll to the bottom and proceed with the following steps.   

![image](https://user-images.githubusercontent.com/67176000/221398325-45d0fbf0-2b32-422c-908d-9d3ec15112bb.png)    

### Step 2: Setup   
Click on this [link](https://github.com/ucsd-cse15l-w23/lab7) to go to the required repository and then fork it.   
```
+-- lab7
|   +-- lib
|       +-- hamcrest-core-1.3.jar
|       +-- junit-4.13.2.jar
|   +-- ListExamples.java
|   +-- ListExamplesTests.java
```   
Once this repository is forked, you should have the above files.   

### Step 3: Start  
Use a time keeping device to keep track of how long it takes for you to do steps 4-9.   

### Step 4: Log into ieng6   
* Type `ssh cs15lwi23amv@ieng6.ucsd.edu` (exact login will vary based on user).   
![image](https://user-images.githubusercontent.com/67176000/221399392-b30ba543-5444-42a4-a823-ace39ebb9c97.png)   
If you are not automatically signed in, refer to the *Github and Login Command-Line Setup* section of [this page](https://ucsd-cse15l-w23.github.io/week/week7/).   

### Step 5: Clone your fork from Github
* Type `git clone git@github.com:e7song/lab7.git <enter>`.   

If this does not work, you may have forgotten to also remove ~/lab7/ from your remote directory.   
   
![image](https://user-images.githubusercontent.com/67176000/221401513-55e7cf7b-1d81-4ffc-a742-bf1f99f3054d.png)

* Immediately after, type `cd la <tab> <enter>`.   
![image](https://user-images.githubusercontent.com/67176000/221401541-2f11b6e0-dc15-4b75-8d0b-818a785d5841.png)   
The `<tab>` command autofills in lab7/, which saves time.   

### Step 6: Run the JUnit Tests
* Type `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java <enter>`.   
* Then `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests <enter>`.   
![image](https://user-images.githubusercontent.com/67176000/221401569-f254bed1-5070-4df3-b67a-dc29860d8ffb.png)   

### Step 7: Edit the code file to fix the failing test   
* Use `nano ListExamples.java <enter>` to enter into the ListExamples.java file.   
* Press `alt + /` to jump directly to the bottom of the file.   
![image](https://user-images.githubusercontent.com/67176000/221401758-ffa94b2e-0794-40ce-9b7e-e4191067fecf.png)   
* Then type `<up> <up> <up> <up> <up> <up> <left arrow> <left arrow> <left arrow> <left arrow><left arrow>` <br /> `<left arrow> <left arrow> <backspace> <2>`.   
This should replace `index1 += 1;` with `index2 +=1;`.   
* Press `ctrl + o` then `<enter> ctrl + x`.
![image](https://user-images.githubusercontent.com/67176000/221401795-a6c7ac6c-3d6c-46a2-a251-19b89c797116.png)
This should exit you out of nano.   
`alt + /` saves time by bringing you to the bottom of the file.   

### Step 8: Rerun the JUnit Tests   
* Press `<up arrow> <up arrow> <up arrow> <enter>` to bring yourself back to the compile command and run it.   
* Press `<up arrow> <up arrow> <up arrow> <enter>` tobring yourself back to the run command and run it.  
![image](https://user-images.githubusercontent.com/67176000/221401915-53684a37-0572-45b4-8689-cec8b2e0315c.png)   
Since these commands were already used, using the up arrow saves time on retyping the commands.   

### Step 9: Commit and Push the resulting change to Github    
Type `git commit -am "Resolved infinite loop error" && git push <enter>`   
![image](https://user-images.githubusercontent.com/67176000/221402121-c8bbf41e-632b-429c-80c9-befb1cd74908.png)   

This command allows me to git add, commit, and push in one line. This is one way to save some time.   















