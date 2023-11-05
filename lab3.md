**Lab 3**
---
Part 1  
A failure-inducing input for the buggy program, as a JUnit test and any associated code (write it as a code block in Markdown)  
```
  @Test
  public void testReverseInPlace2() {
    int[] input1 = {1,2,3};
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3,2,1}, input1);
  }
```
