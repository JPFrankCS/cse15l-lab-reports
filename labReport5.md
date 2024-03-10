# Debugging and Reflecting
#### Debugging

1.The original post from a student with a screenshot showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is. (Don't actually make the post! Just write the content that would go in such a post)
2.A response from a TA asking a leading question or suggesting a command to try (To be clear, you are mimicking a TA here.)
3.Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.
At the end, all the information needed about the setup including:
-The file & directory structure needed
-The contents of each file before fixing the bug
-The full command line (or lines) you ran to trigger the bug
-A description of what to edit to fix the bug

Lets discuss debugging! Lets examine a hypothetical online interaction between a TA and a student as the student asks for help debugging their program. Lets look at an example student of a grading script, meant to grade student submitted code. The student's original code in their `grade.sh` file is below:
```
rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission 2> clone-output.txt
echo 'Finished cloning'

if [[ -f student-submission/ListExamples.java ]] 
then
    cp student-submission/ListExamples.java grading-area/
    cp TestListExamples.java grading-area/
else
    echo "Missing student-submission/ListExamples.java, did you forget the file or misname it? Score: 0"
    exit 1
fi

cd grading-area

CPATH='.;../lib/hamcrest-core-1.3.jar;../lib/junit-4.13.2.jar'
javac -cp $CPATH *.java 

if [[ $? -ne 0 ]] #if exit code != 0
then
    echo "The program failed to compile, see compile error above. Score: 0"
    exit 1
fi

echo "Finished Compiling"

java -cp $CPATH org.junit.runner.JUnitCore TestListExamples >junit-output.txt

testCheck=$(cat junit-output.txt | tail -n 2 | awk -F'[, ]' '{print $1}')

if [[ $testCheck = "OK" ]]
then
    tests=$(cat junit-output.txt | tail -n 2 | awk -F'[, ]' '{print $2}' | cut -b 2)
    echo "You Passed All Tests! That is a score of 100%!"
    exit 1
fi
tests=$(cat junit-output.txt | tail -n 2 | awk -F'[, ]' '{print $3}')
failures=$(cat junit-output.txt | tail -n 2 | head -n 1 | awk -F'[, ]' '{print $7}')
successes=$((tests-failures))

percent=$((100*successes/tests))
echo "You Passed $successes / $tests Tests! That is a score of $percent%!"
```
Their file structure after running the code looks like this:
```
list-examples-grader/
|--grading-area/
|  |--ListExamples.java
|  |--TestListExamples.java
|--lib/
|  |--hamcrest-core-1.3.jar
|  |--junit-4.13.2.jar
|--student-submission/
|  |--ListExamples.java
|--GradeServer.java
|--Server.java
|--TestListExamples.java
|--clone-output.txt
|--grade.sh
```
Here is the student's post asking for help:
> HELPPP
Here is the TA's response:
> You needa do this!

Reading the TA's response, the student may try something like seen below, ____
<<Screenshot>>>>>
The student now sees the bug is ___

---
#### Reflecting
I really enjoyed building the autograder in the last lab. It was really cool to be able to take a deeper dive into how the system could be improved for users. An interesting thing I learned was the `OSTYPE` varaible and how it can be used to determine the user's operating system when writing scripts that are dependant on that operating system. I also appreciated learning about `if` statements in `bash`. I feel like they really opened up the language for me as far as its applications and ways I could imagine using it.
