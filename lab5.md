# Student Post
Hi TA, when I run my grading script for the code with the correct implementation for merge and filter I am getting a score of 1/2 instead of a score of 2/2. Please help me. I think my bash script looks correct, it might be something wrong with the tests I created.
![Image](lab5-1.png)
# TA Response
Could you please include the output of when you run the test in your script. Also send me a picture of your tests.
# Student Response
Here is the output of the test:
![Image](lab5-2.png)
Here is the code for my tests:
```
import static org.junit.Assert.*;
import org.junit.*;
import java.util.Arrays;
import java.util.List;

class IsMoon implements StringChecker {
  public boolean checkString(String s) {
    return s.equalsIgnoreCase("moon");
  }
}

public class TestListExamples {
  @Test(timeout = 500)
  public void testMergeRightEnd() {
    List<String> left = Arrays.asList("a", "b", "c", "d");
    List<String> temp = left;
    temp.remove("d");
    List<String> right = temp; 
    List<String> merged = ListExamples.merge(left, right);
   List<String> expected = Arrays.asList("a", "a", "b", "b","c","c", "d");
    assertEquals(expected, merged);
  }

  @Test(timeout = 500)
  public void testFilter() {
    List<String> initial = Arrays.asList("a", "b", "moon", "c");
    List<String> actual = ListExamples.filter(initial, new IsMoon());
    List<String> expected = Arrays.asList("moon");
    assertEquals(expected, actual);
  }

}
```
# TA Response
So from the output we can see that the error is from your ```testMergeRightEnd``` method. It seems like you were trying to create two lists where left had the values ```("a", "b", "c", "d")``` and right had the values ```("a", "b", "c")```. However, when you create the variable ```temp``` it still refers to the saem left object so when you ```remove("d")``` it gets rid of ```d``` from the left list so ```left``` is now ```("a", "b", "c")``` and when you assign ```right``` to ```temp```, ```right``` is ```("a", "b", "c")```. To fix this just assign right to ```Arrays.asList("a", "b", "c");```.
