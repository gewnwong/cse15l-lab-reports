# Lab Report 5 

## Writing the grading script from Lab 6 and showing it working

---

## Writing ```grade.sh```

---

Since my group did lab 6 by writing ```grade.sh``` together on one of my partners' computer, I thought it would be helpful to code it myself. During lab, my group also opted for only pass/fail output instead of exactly how many tests passed out of how many ran, so I made my ```grade.sh``` include fractional results indicating partial credit.

Here is my code for ```grade.sh```:

```java
CPATH=".:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar"

rm -rf student-submission
git clone $1 student-submission
echo "Finished cloning"

if [[ -f student-submission/ListExamples.java ]]
then
    echo "ListExamples.java found"
else
    echo "ListExamples.java not found"
    echo "Score: Invalid"
    exit 1
fi

cp student-submission/ListExamples.java ./

javac -cp $CPATH *.java &> compile.txt

# Check for if student-submission compiles
FAIL=`grep -c error: compile.txt`
if [[ $FAIL -ne 0 ]] 
then
    echo "Compile failed with output:"
    cat compile.txt
    echo "Compile of the student submission failed"
    echo "Score: Invalid"
    exit 1
else
    echo "Compile of the student submission succeeded"
fi

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples > junit-output.txt

# Check for FAILURES!!!
FAILURES=`grep -c FAILURES!!! junit-output.txt`

if [[ $FAILURES -eq 0 ]]
then 
    echo 'All tests passed'
    # Check for number of tests 
    RESULT=`grep "OK" junit-output.txt`
    TOTAL=${RESULT:4:2}
    SECOND_DIGIT=${TOTAL:1:1}
    if [[ $SECOND_DIGIT = ")" ]]
    then
        TOTAL=${RESULT:4:1}
    fi
    echo "Score: $TOTAL/$TOTAL"
else
    RESULT=`grep "Tests run:" junit-output.txt`

    TOTAL=${RESULT:11:2}
    SECOND_DIGIT=${TOTAL:1:1}
    if [[ $SECOND_DIGIT = "," ]]
    then
        TOTAL=${RESULT:11:1}
    fi

    FAILED=${RESULT:25:2}
    SECOND_DIGIT=${FAILED:1:1}
    if [[ $SECOND_DIGIT = " " ]]
    then 
        FAILED=${RESULT:25:1}
    fi

    echo "JUnit output was:"
    cat junit-output.txt
    echo "Score: $(($TOTAL - $FAILED))/$TOTAL"
fi
```

Issues/complications I ran into while writing ```grade.sh```:
- I had to look up what the ```-c``` option did. (It counts the number of lines with the specified string.)
- I forgot to include output for if the student submission fails to compile. (I also had to look back in the notes to recall that error output and normal output can be saved to a file using ```&>```.)
- I wasn't sure how to do arithmetic operations between what I saw as two strings, but, after some research, I learned that bash sees variables as integers or strings based on context. 
- I learned how to get a substring in bash, using the syntax ```${VAR:N:M}```. 

Not shown in ```grade.sh```, I added another test to the ```TestListExamples.java``` file to test the ```filter``` method in ```ListExamples.java``` as shown here:

```java
@Test(timeout = 500)
  public void testFilter() {
    List<String> s1 = Arrays.asList("a", "b", "c");
    List<String> s2 = Arrays.asList("d", "a");
    List<String> expect = Arrays.asList("a");
    List<String> result1 = ListExamples.filter(s1, new IsA());
    List<String> result2 = ListExamples.filter(s2, new IsA());
    assertEquals(expect, result1);
    assertEquals(expect, result2);
  }
```

# Output of my ```grade.sh```

---

I ran all the files given to test ```grade.sh``` in lab 6 on my ```grade.sh```.

Submission that times out for ```merge```:

![Screenshot 2023-03-10 at 12 56 13 PM](https://user-images.githubusercontent.com/122576781/224426610-e627a11c-acef-48ee-a284-ef6cc028c60a.png)

Submission that is correct for both ```merge``` and ```filter```:

![Screenshot 2023-03-10 at 2 28 02 PM](https://user-images.githubusercontent.com/122576781/224439993-0d8b1904-5a2f-48be-ae9d-bd0c6d74f38e.png)

Submission with a syntax error in ```ListExamples.java```:

![Screenshot 2023-03-10 at 2 29 02 PM](https://user-images.githubusercontent.com/122576781/224440105-dc184062-f58f-4365-976f-5fb7c894878b.png)

Submission with incorrect order of arguments for ```filter```:

![Screenshot 2023-03-10 at 2 30 17 PM](https://user-images.githubusercontent.com/122576781/224440293-f539cc7a-30ce-4210-930e-6f015c6c42c4.png)

Submission with incorrect file name:

![Screenshot 2023-03-10 at 2 31 09 PM](https://user-images.githubusercontent.com/122576781/224440430-b83bd6d0-c6d6-482e-b196-d18c254ec7ae.png)

Submission in a nested directory:

![Screenshot 2023-03-10 at 2 32 03 PM](https://user-images.githubusercontent.com/122576781/224440565-42c21e9d-adbd-4165-b512-5aab3aefebea.png)

"Challenge" submission (only merges one copy if duplicates occur between the left and right halves):

![Screenshot 2023-03-10 at 2 34 33 PM](https://user-images.githubusercontent.com/122576781/224440862-73f0ca72-0ae3-4c47-9cea-00ea5469da79.png)
