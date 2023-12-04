**Lab Report 5**
---  
**Part 1**  
Step 1: Student Post   
I am running into an error when I attempt to run the lab 7 program. In the screenshot below, I noticed that the program timed out. I think this means that there is a bug in a loop that causes it to never end. Without the `(timeout = 500)`, the code would never finish executing. The error says the problem is somewhere in line 28, so I think it has to do with the if statement in the merge method. 
Below is a snippit of the my code and the error I am receiving.  
<img width="784" alt="Screenshot 2023-12-03 at 5 26 39 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/abdb8db3-6bb2-476f-9263-1e82e969b0f2">
<img width="904" alt="Screenshot 2023-12-03 at 5 30 14 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/63a926f8-97c6-41e9-953c-428380244f74">  
  
Step 2: TA Response  
It seems you are on the right track. We know that the `merge` method is meant to "merge" the two sorted list. As we can see, in the first `while` loop, there is an `if` statement, it properly add's elements from `list1` to `result` when `list1.get(index1).compareTo(list2.get(index2)) < 0` is true. 
What happens when that statement is false? Do elements from `list2` get added to `results`? 
Take a look at the `while loops` conditional statement as well. `index1 < list1.size() && index2 < list2.size()` means that the `while` loop will continue until `index1` is greater than `list1.size()` AND `index2` is greater than `list2.size()`.
We can see that `index1` changes when we add elements from `list1` to `results`, what about `index2`?  
  
Step 3: Student Response  
<img width="879" alt="Screenshot 2023-12-03 at 5 54 17 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/02d83b7a-b924-4f27-8d4a-2cd70c045ffe">  
<img width="375" alt="Screenshot 2023-12-03 at 5 54 38 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/394bf126-086b-418b-a292-cd162bf9795e">  
The bug that caused the loop to iterate non-stop was that `index2`'s value never changed. So it was always less than  `list2.size()`. After fixing this, there was another error 
regarding `results`. With the help of the TA's response, I notied that the code was only adding elements from `list1` and not `list2`, so `results` only contained elements from `list1`.
To fix this issue, the `if` statement in the first `while` loop needed an `else` statement where if the current element in `list1` is not less than the current element `list2`, it adds the `list2` element to 
`results` and increments `index2` by 1.  
  
Step 4:  
* The file & directory structure needed:  
  <img width="201" alt="Screenshot 2023-12-03 at 6 07 33 PM" src="https://github.com/ivannchenn/cse15l-lab-reports/assets/146862312/c8a58ada-bc1a-4097-b80d-0ffac9585e3b">  
* The contents of each file before fixing the bug:  
  `ListExamples.java`  
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
            result.add(s);
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
    
        }
        while(index1 < list1.size()) {
          result.add(list1.get(index1));
          index1 += 1;
        }
        while(index2 < list2.size()) {
          result.add(list2.get(index2));
          index2 += 1;
        }
        return result;
      }
    
    
    }
  ```
  `ListExamplesTest.java`
  ```
  import static org.junit.Assert.*;
  import org.junit.*;
  import java.util.*;
  import java.util.ArrayList;
  
  
  public class ListExamplesTests {
  	@Test(timeout = 500)
  	public void testMerge1() {
      		List<String> l1 = new ArrayList<String>(Arrays.asList("x", "y"));
  		List<String> l2 = new ArrayList<String>(Arrays.asList("a", "b"));
  		assertArrayEquals(new String[]{ "a", "b", "x", "y"}, ListExamples.merge(l1, l2).toArray());
  	}
  	
  	@Test(timeout = 500)
          public void testMerge2() {
  		List<String> l1 = new ArrayList<String>(Arrays.asList("a", "b", "c"));
  		List<String> l2 = new ArrayList<String>(Arrays.asList("c", "d", "e"));
  		assertArrayEquals(new String[]{ "a", "b", "c", "c", "d", "e" }, ListExamples.merge(l1, l2).toArray());
          }
  
  }
  ```
    
* The full command line (or lines) you ran to trigger the bug:  
  `bash test.sh`
  
* A description of what to edit to fix the bug:  
  The first `while` loop kept looping because the conditions weren't met to end the loop. `index1` was being incremented by 1, but there was no code to increment `index2`.
  It also properly added each element of `list1` to `results`, but there wasn't anything to add elements of `list2` to `results`. So if we only implemented incrementing `index2`,
  there would still be an error resulting in the wrong sorted list because it didn't contain anything from `list2`. To fix this, the `if` statement in the first `while` loop required an `else`
  statement, where if the current element in `list1` is not less than the current element `list2`, it adds the `list2` element to `results` and increments `index2` by 1.
  
**Part 2: Reflection**  
Something that I found was really interesting this half of the quarter was learning about the things we can do straight from the command line. Being able to commit and push
from the command line made it really easy to make changes instead of uploading the updated files to github each time. It was also interesting to learn about vim and the different commands to 
help us edit files.

