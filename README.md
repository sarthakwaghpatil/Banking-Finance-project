# Banking-Finance-project
..
package com.Banking_Test.Test;
import java.io.File;
import java.io.IOException;
import java.util.concurrent.TimeUnit;
import org.aspectj.util.FileUtil;
import org.openqa.selenium.By;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.chrome.ChromeOptions;

public class App 
{
    public static void main( String[] args ) throws InterruptedException, IOException
    {
   //  System.setProperty("webdriver.chrome.driver","C:\\Users\\dell\\Desktop\\chromedriver_win32\\chromedriver.exe");
   //   System.setProperty("webdriver.chrome.driver","/home/ubuntu/chromedriver");
        System.setProperty("webdriver.chrome.driver","/usr/bin/chromedriver");
        
        ChromeOptions chromeOptions = new ChromeOptions();
        chromeOptions.addArguments("--headless");
        chromeOptions.addArguments("--no-sandbox");
        chromeOptions.addArguments("--disable-dev-shm-usage");
        WebDriver driver = new ChromeDriver(chromeOptions);
        
     // driver.get("http://localhost:8081/contact.html");
        driver.get("http://3.80.46.192:8084/contact.html");
        
        driver.manage().timeouts().implicitlyWait(5,TimeUnit.SECONDS);
        driver.findElement(By.id("Name")).sendKeys("Vaibhav Mankar");
        driver.findElement(By.id("Phone Number")).sendKeys("8888883101");
        driver.findElement(By.id("Email")).sendKeys("Vaibhav3101mankar");
        driver.findElement(By.id("Message")).sendKeys("Welcome to Devops");
        driver.findElement(By.id("message")).click();
        
        String message = driver.findElement(By.id("message")).getText();
        if(message.equals("Email Sent")) {
        	System.out.println("Script executed Successfully");
        	
        }
        else {
        	System.out.println("script failed");        	
        }
       System.out.println("Taking Screenshot as proof");
        //take the screenshot of the testcases//
         TakesScreenshot scrShot = (TakesScreenshot)driver;
         File screenShot =scrShot.getScreenshotAs(OutputType.FILE);
         
         File destFile = new File("//home//ubuntu//screenshot.png");
         
         FileUtil.copyFile(screenShot, destFile);
         
         Thread.sleep(3000);
       
        driver.quit();
    }
}
