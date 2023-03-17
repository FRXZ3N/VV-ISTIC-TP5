## Find a bug

Clone the [Simba Organizer repository](https://github.com/selabs-ur1/doodle) and follow the instructions to run the application on your machine.

Find a bug in the application. 

With the help of Selenium and the Page Object Model desing pattern write a simple test that fails for this bug.

Optionally make a pull request to the project.

Include in this document the code of the test and, if you did it, the link to the pull request.

## Answer

In this application, you can click wherever you want in the workflow to go on the step you want. For example, you can go directly to the last step without going through the previous steps. This is a bug because the user should go through the steps in the right order.

```java
public class SimbaBugTest {

  @Test
  /**
   * This test checks if the user can go directly to the last step without going through the previous steps.
   */
  public void simbaBugTest() {
    HomePageSimba homePage = new HomePageSimba(driver);
    By step3Button = By.className(".p-steps-item:nth-child(3)");
    By linkToPoll = By.className("p.card-content").findElement(By.tagName("a")).getAttribute("href");
    driver.findElement(step3).click();
    assertThat(linkToPoll).isNotNull();
  }
}
```
With this test, we click on the third step of the workflow and we check if the link to the poll is not null. 
If the link is null, it means that the user can go directly to the last step without going through the previous steps.


