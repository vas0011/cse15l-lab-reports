# The original post from a student with a screenshot showing a symptom and a description of a guess at the bug/some sense of what the failure-inducing input is. (Don't actually make the post! Just write the content that would go in such a post)
Hi TA, when I run my grading script for the code with the correct implementation for merge and filter I am getting a score of 1/2 instead of a score of 2/2. Please help me. I think my bash script looks correct, it might be something wrong with the tests I created.
![Image](lab5-1.png)
# A response from a TA asking a leading question or suggesting a command to try (To be clear, you are mimicking a TA here.)
Could you please include the output of when you run the test in your script. Also send me a picture of your tests.
# Another screenshot/terminal output showing what information the student got from trying that, and a clear description of what the bug is.
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
# At the end, all the information needed about the setup including:
