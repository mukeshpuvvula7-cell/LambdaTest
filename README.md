# LambdaTest
hear is the test report of lambdatest certification in selenium with java 
package LambdaTest_Project;

import org.openqa.selenium.By;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Actions;

public class Slider_Demo implements all_in_demo {

    public static void main(String[] args) throws InterruptedException {

        ChromeDriver driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get(slide_url);   // this will come from your interface (all_in_demo)


        // Accessing the slider (Default value = 15)
        WebElement slider = driver.findElement(slider_locator);

        // Access the displayed value area
        WebElement slider_value = driver.findElement(slider_value_box);

        Actions act = new Actions(driver);

        // Move slider until it becomes 95
        while (!slider_value.getText().equals("95")) {
            act.dragAndDropBy(slider, 5, 0).perform();
            Thread.sleep(100);
        }

        // Validation
        String expectedValue = "95";
        String actualValue = slider_value.getText();

        if (actualValue.equals(expectedValue)) {
            System.out.println("PASS: Slider moved to → " + actualValue);
        } else {
            System.out.println("FAIL: Expected → " + expectedValue + " | Actual → " + actualValue);
        }

        driver.quit();
    }
}
