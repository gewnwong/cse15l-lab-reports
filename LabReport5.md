# Lab Report 5 

## Writing the grading script from Lab 6 and showing it working

---

## Writing ```grade.sh```

---

Since my group did lab 6 by writing ```grade.sh``` together on one of my partners' computer, I thought it would be helpful to code it myself. During lab, my group also opted for only pass/fail output instead of exactly how many tests passed out of how many ran, so I made ```grade.sh``` include fractional results indicating partial credit.

Here is my code for ```grade.sh```:

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
      echo $TOTAL
      SECOND_DIGIT=${TOTAL:1:1}
      if [[ $SECOND_DIGIT = "," ]]
      then
          TOTAL=${RESULT:11:1}
      fi

      FAILED=${RESULT:25:2}
      echo $FAILED
      SECOND_DIGIT=${FAILED:1:1}
      if [[ $SECOND_DIGIT = " " ]]
      then 
          FAILED=${RESULT:25:1}
      fi

      echo "JUnit output was:"
      cat junit-output.txt
      echo ""
      echo "Score: $(($TOTAL - $FAILED))/$TOTAL"
  fi



For lab 6 (about creating a grading script), finish the grading script and take screenshots that demonstrate it working on several files.
