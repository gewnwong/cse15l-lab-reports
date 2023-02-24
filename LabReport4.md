# Lab Report 4

---

## 1. (Setup) Delete any existing forks of the repository you have on your account
<img width="831" alt="Screenshot 2023-02-23 at 3 26 29 PM" src="https://user-images.githubusercontent.com/122576781/221054340-687d2fab-900b-4d5a-9ece-72fcfa70f086.png">

Keys pressed: ```rm -r lab7<enter>```, ```yes```,```yes```,```yes```,```yes```,```yes```

I typed in the command to delete ```lab7``` and then had to agree to delete all the files within the directory. 

<img width="447" alt="Screenshot 2023-02-23 at 3 31 08 PM" src="https://user-images.githubusercontent.com/122576781/221054999-c729fe64-76d0-4069-8d92-7fd90ed395ee.png">

Keys pressed: ```gewnwong/lab7<enter>```

I had to agree to delete the repository from my Github account. 

## 2. (Setup) Fork the repository

![Screenshot 2023-02-23 at 5 59 16 PM](https://user-images.githubusercontent.com/122576781/221073571-f4864c39-5590-4973-b0e7-922a362d211f.png)

I forked the repository to my Github account under the name "lab7" to set up. 

## 3. The real deal: Start the timer!

## 4. Log into ieng6

<img width="698" alt="Screenshot 2023-02-23 at 6 07 00 PM" src="https://user-images.githubusercontent.com/122576781/221074378-c1df8d8b-bbd8-41b1-84ef-82eefd5338c2.png">

Keys pressed: ```ssh cs15lwi23auq@ieng6.ucsd.edu<enter>```

I connected to the remote server using my account.

## 5. Clone your fork of the repository from your Github account

<img width="697" alt="Screenshot 2023-02-23 at 6 11 53 PM" src="https://user-images.githubusercontent.com/122576781/221074972-1c39ca8e-b6c7-40d7-a197-b173ba8cc891.png">

Keys pressed: ```git clone <Ctrl-V><enter>```

Since I'd previously copied the ```SSH``` clone URL from the forked repository, I typed in the command to clone the repository and pasted the URL (``` git@github.com:gewnwong/lab7.git```) right after it.

## 6. Run the tests, demonstrating that they fail

<img width="703" alt="Screenshot 2023-02-23 at 6 49 28 PM" src="https://user-images.githubusercontent.com/122576781/221079897-3b56188e-407f-43e2-aa35-0abc35da49e8.png">

Keys pressed: ```cd lab7<enter>```, ```<Ctrl-C><Ctrl-V><enter>```, ```<Ctrl-C><Ctrl-V> Li<tab>Tests<enter>```

I first changed the working directory to ```lab7``` so I could then compile, run, and work on the files within that directory. I then copied the command to compile the files (```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java```) from elsewhere and pasted it on the command line. To run the tests and demonstrate that they fail, I copied the command to run the tester (```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore```) from elsewhere, pasted it on the command line, and added the file after it that I wanted to be run. The ```<tab>``` after the ```Li``` autocompleted to ```ListExamples``` and then I added ```Tests```.

## 7. Edit the code file to fix the failing test

<img width="412" alt="Screenshot 2023-02-23 at 6 37 07 PM" src="https://user-images.githubusercontent.com/122576781/221078269-d942bbe5-1955-4aeb-8444-74adcee3fd45.png">

<img width="697" alt="Screenshot 2023-02-23 at 6 37 44 PM" src="https://user-images.githubusercontent.com/122576781/221078339-0da65ee9-d992-4aa9-87c6-b5e90ade10ef.png">

Keys pressed: ```nano Li<tab>.j<tab><enter>```, ```<Ctrl-W>< 0<enter>```, ```<right>=```, ```<down><down><down><down><down><down><down><down><down><down><down><down><down><down><down><left><left><left><left><left><left><backspace>2```, ```<Ctrl-O><enter>```, ```<Ctrl-X>```

I used the command ```nano``` to open an editor of the file ```ListExamples.java``` that was filled in with the help of autocomplete. To get the cursor to where the first bug was located, I used ```<Ctrl-W>``` to search and go to where ```< 0``` was. I then used the right arrow key to get to the spot in front of the ```<```, where I then added an equal sign to make the code there correct. Once again, I used the arrow keys to get to the second bug, hten changed the line ```index1 +=1;``` to ```index2 += 1;``` to be correct. To save this file, I used ```<Ctrl-O>```, and to exit, I used ```Ctrl-X```.

## 8. Run the tests, demonstrating that they now succeed

<img width="699" alt="Screenshot 2023-02-23 at 6 51 15 PM" src="https://user-images.githubusercontent.com/122576781/221080141-1c9c0548-9c07-4e19-91e5-203c85d485bd.png">

Keys pressed: ```<up><up><up><enter>```, ```<up><up><up><enter>```

The ```javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java``` command was 3 up in the search history, so I used the up arrow to access it. Then the ```java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests``` command to run the compiled tester was 3 up in the search history, so I accessed and ran it in the same way.

## 9. Commit and push the resulting change to your Github account 

<img width="706" alt="Screenshot 2023-02-23 at 6 55 28 PM" src="https://user-images.githubusercontent.com/122576781/221080688-3c727347-890c-434f-9b70-f2ee1024972c.png">

![Screenshot 2023-02-23 at 6 55 49 PM](https://user-images.githubusercontent.com/122576781/221080766-2033c2a3-8260-42cf-a19a-dada8bf712ce.png)


Keys pressed: ```git add L<tab>.j<tab><enter>```, ```git commit -m "yAy"```, ```git push```

I added ```ListExamples.java``` to git using autofilled results, then committed and pushed. The commit message showed up on my Github, showing that these steps worked.
