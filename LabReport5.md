# Lab Report 5 

## Part 1 

1. Issue with Lab Report 4
> I am trying to do lab 4, but I am having issues with figuring out what is wrong with passing my tests, I tried to fix the issue in `ExamplesList` but I can't seem to do anything in vim.
[!Image](Lab5Bash.png)
[!Image](Lab5ExampleList.png)

> The command that I had used was `vim ExampleList`. 

2. 
> The problem is, is that you are using vim on the wrong directory. The confusion is that you are using `vim ExamplesList`, instead try `vim ExamplesList.java` which should then vim you into the right directory. Once you get that figured out, the bug in ExamplesList.java that causes the failed tests, has something to do with how things are stored in indexes. 

3.
[!Image](Lab5Result.png)


>The issue was that the student was experiencing was that he didn't know how to access the right directory, giving them the right feedback resulted in them going into the right directory using vim.
>The actual bug in the code that fails the tests is in `ExamplesList.java` which has an issue with the index in the second while loop. Instead of it being `index2 += 1` it was `index1 += 1`

4. 

a. 
/home/linux/ieng6/oce/8h/kyugay/lab7
  ListExamples.class  ListExamples.java  ListExamplesTests.class  ListExamplesTests.java  StringChecker.class  lib  test.sh

b. 
> `ListExamples.java`
```
import java.util.ArrayList;
import java.util.List;

interface StringChecker { boolean checkString(String s); }

class ListExamples {

  // Returns a new list that has all the elements of the input list for which
  // the StringChecker returns true, and not the elements that return false, in
  // the same order they appeared in the input list;
  static List<String> filter(List<String> list, StringChecker sc) {
    List<String> result = new ArrayList<>();
    for(String s: list) {
      if(sc.checkString(s)) {
        result.add(0, s);
      }
    }
    return result;
  }


  // Takes two sorted list of strings (so "a" appears before "b" and so on),
  // and return a new list that has all the strings in both list in sorted order.
  static List<String> merge(List<String> list1, List<String> list2) {
    List<String> result = new ArrayList<>();
    int index1 = 0, index2 = 0;
    while(index1 < list1.size() && index2 < list2.size()) {
      if(list1.get(index1).compareTo(list2.get(index2)) < 0) {
        result.add(list1.get(index1));
        index1 += 1;
      }
      else {
        result.add(list2.get(index2));
        index2 += 1;
      }
    }
    while(index1 < list1.size()) {
      result.add(list1.get(index1));
      index1 += 1;
    }
    while(index2 < list2.size()) {
      result.add(list2.get(index2));
      index1 += 1;
    }
    return result;
  }


}
```

> `test.sh` 
```
javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java
java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests
```

c. `bash test.sh` which is what triggers the bug, the actual bug is in the ExampleList.java file. 

d. To fix the bug the student needed to vim into the right directory( which was the students issue) and change `index1 += 1` into `index2 += 1` in the code, in the second while loop. 





    

