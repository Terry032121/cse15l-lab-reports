# CSE15l-labReport5-Terry
## Part 1
### The original post from student 
**Name:** Poliz Hallpe <br>
**Tittle:** Strange Output<br>
**Description:** <br>
Hi, all. I'am working on our grader assignment but there when I was testing `https://github.com/ucsd-cse15l-f22/list-methods-nested` this, the terminal says it can't find the file I wanted to test for. This really bothers me because all my other testcases was passed perfectly and all the files were found. This is the fisrt time I am encountering this kind of situation. I am wondering that the file can't be found because the student submitted the file with wrong name or the the acutal file is hidden somewhere??

<img width="909" alt="截屏2024-03-12 下午4 37 51" src="https://github.com/Terry032121/cse15l-lab-reports/assets/133158645/3fbb9740-b9fb-42bb-b3ac-02759b2548da">

### Response from TA
Hi there, you are definitely on the right track. There can be two scenarios when you can't find the submitted file. One is the student have the wrong file name, the second one is the the file can be hidden under other directories which this really happens a lot in real life. I would suggest you to find some way to find all the files/directory of what students submitted.

### Information the student got
<img width="1025" alt="截屏2024-03-12 下午4 45 40" src="https://github.com/Terry032121/cse15l-lab-reports/assets/133158645/14988d92-cad0-42b1-9160-fdf8671df6af"> 
The bug was the student didn't find recursively for the file. The given test is a scenario where the file we want to test is under a nested directory. 

### All the information
#### file & directory structure
list-example-grader/<br>
  - grading-area/<br>
    - libs/<br>
      - hamcrest-core-1.3.jar<br>
      - junit-4.13.2.jar<br>
    - isMoon.class<br>
    - ListExamples.java <br>
    - ListExamples.class <br>
    - StringChecker.class <br>
    - TestListExamples.class <br>
    - TestListExamples.java <br>
  - libs/<br>
      - hamcrest-core-1.3.jar<br>
      - junit-4.13.2.jar<br>
  - student-submission/
    - pa1/
      - ListExamples.java
  - grade.sh
  - TestListExamples.java
#### The contents of file before fixing the bug
``` bash
CPATH='.:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar'

rm -rf student-submission
rm -rf grading-area

mkdir grading-area

git clone $1 student-submission
echo 'Finished cloning'

find_list_examples() {
    for file in $(find -r student-submission -name 'ListExamples.java'); do
        cp "$file" grading-area/
        echo "No Error: ListExamples.java found in the student submission."
        return
    done
    echo "Error: ListExamples.java not found in the student submission."
    exit 1
}

if [ ! -f "student-submission/ListExamples.java" ]; then
    echo "Error: ListExamples.java not found in the student submission."
    exit 1
fi

echo "No Error: ListExamples.java found in the student submission."

cp -r lib grading-area/
cp student-submission/ListExamples.java grading-area/
cp TestListExamples.java grading-area/

cd grading-area
javac -cp $CPATH TestListExamples.java ListExamples.java
if [ $? -ne 0 ]; then
    echo "Error: Compilation failed."
    exit 1
fi

echo "No Error: Compilation successful."


java -cp $CPATH org.junit.runner.JUnitCore TestListExamples  
```

#### The full command line ran to trigger the bug
`list-examples-grader % bash grade.sh https://github.com/ucsd-cse15l-f22/list-methods-nested`

#### A description of what to edit to fix the bug
To fix the bug, we need to find recursively under the directory student submission.<br>
we add this to find: <br>
```bash
find_list_examples() {
    local file_path
    file_path=$(find student-submission -type f -name "ListExamples.java" | head -n 1)
    echo "$file_path"
}

LIST_EXAMPLES=$(find_list_examples)
if [ -z "$LIST_EXAMPLES" ]; then
    echo "Error: ListExamples.java not found in the student submission."
    exit 1
fi
```
And then we update the classpath to for running the test:
```bash
java -cp $CPATH org.junit.runner.JUnitCore TestListExamples



        echo "No Error: ListExamples.java found in the student submission."
        return
    done
    echo "Error: ListExamples.java not found in the student submission."
    exit 1
}
if [ ! -f "student-submission/ListExamples.java" ]; then
    echo "Error: ListExamples.java not found in the student submission."
    exit 1
fi

echo "No Error: ListExamples.java found in the student submission."

cp -r lib grading-area/
cp student-submission/ListExamples.java grading-area/
cp TestListExamples.java grading-area/

cd grading-area
javac -cp $CPATH TestListExamples.java ListExamples.java
if [ $? -ne 0 ]; then
    echo "Error: Compilation failed."
    exit 1
fi

echo "No Error: Compilation successful."


java -cp $CPATH org.junit.runner.JUnitCore TestListExamples
```

## Part2
I think the coolest thing I learnt is how to communicate regarding coding professionally. Before attending this class all know is copy ,paste and send, but now I know how to  `git add` and pull requests etc. I think this will help my future career a lot. 
