## Page Object Model

The image below shows the poll page of the [Simba Organizer](https://github.com/barais/doodlestudent/) application discussed in classes.

![Simba Organizer Poll page](simba-poll-page.png)

Write in this document the interface of a page object class for this page.

## Answer

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;

public class PollPage {
    protected WebDriver driver;
    By name = By.id("nom");
    By email = By.id("mail");
    By icsFlowAccessibleButton = By.className("p-inputswitch-slider");
    By calendarView = By.xpath("//div[i[contains(text(), 'Vue Calendrier')]]");
    By calendarViewDateOptions = By.xpath("//div[@class='fc-event-time']");
    By tableView = By.xpath("//div[i[contains(text(), 'Vue Tableau')]]");
    By tableViewDateOptions = By.xpath("(//div[@class='p-checkbox-box'])[1]");
    By submitButton = By.xpath("//span[contains(text(), 'Soumettre voeux')]");
    By pollCommentAuthor = By.id("comment");
    By pollComment = By.id("commentdesc");
    
    public PollPage(WebDriver driver){
        this.driver = driver;
		if (!driver.getTitle().equals("Sign In Page")) {
			throw new IllegalStateException("This is not Sign In Page," +
				" current page is: " + driver.getCurrentUrl());
		}
    }
	
    public PollPage validPoll(String userName, String password) {
		driver.findElement(name).sendKeys(userName);
		driver.findElement(email).sendKeys(password);
		driver.findElement(icsFlowAccessibleButton).click();
		driver.findElement(calendarView).click();
		driver.findElement(calendarViewDateOptions).click();
		driver.findElement(tableView).click();
		driver.findElement(tableViewDateOptions).click();
		driver.findElement(submitButton).click();
		driver.findElement(pollCommentAuthor).sendKeys(userName);
		driver.findElement(pollComment).sendKeys(password);
		return this;
	}
}

```


