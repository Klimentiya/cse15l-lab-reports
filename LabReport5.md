# Lab Report 5 

## Part 1 

1. Issue with Lab Report 4
> I am trying to do lab 4, but I am having issues with figuring out what is wrong with passing my tests, I tried to fix the issue in `ExamplesList` but I can't seem to do anything in vim.
[Image]()
[Image]()

> The command that I had used was `vim ExampleList`. 

2. 
> The problem is, is that you are using vim on the wrong directory. The confusion is that you are using `vim ExamplesList`, instead try `vim ExamplesList.java` which should then vim you into the right directory.

3.
[Image]()

>The bug that the student was experiencing was that he didn't know how to access the right directory, giving them the right feedback resulted in them going into the right directory using vim.

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
      // change index1 below to index2 to fix test
      index1 += 1;
    }
    return result;
  }


}
```

    

