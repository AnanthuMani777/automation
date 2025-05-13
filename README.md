package gurutelecom;

import java.io.File;
import java.io.IOException;

import org.apache.commons.io.FileUtils;
import org.openqa.selenium.By;
import org.openqa.selenium.OutputType;
import org.openqa.selenium.TakesScreenshot;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.annotations.BeforeSuite;
import org.testng.annotations.Test;

public class finalProject
{
	WebDriver driver;
	@BeforeSuite
	public void login() throws InterruptedException  
	{
		System.setProperty("webdriver.chrome.driver","C:\\Users\\hp\\OneDrive\\Desktop\\selenium drivers\\chromedriver-win32\\chromedriver.exe");
		driver=new ChromeDriver();
	}
	@Test(priority=0)
	public void open() throws InterruptedException
	{
	     driver.get("https://demo.guru99.com/telecom/index.html");
	     driver.manage().window().maximize();
	     Thread.sleep(2000);
	}
	@Test(priority=1)
	public void addCustomer() throws InterruptedException, IOException
	{
		 driver.findElement(By.xpath("//*[@id=\"one\"]/div/div[1]/div[1]/h3/a")).click();
		   driver.findElement(By.xpath("//*[@id=\"main\"]/div/form/div/div[1]/label")).click();
		   driver.findElement(By.id("fname")).sendKeys("Swaraj");
		   driver.findElement(By.id("lname")).sendKeys("Suresh");
		   driver.findElement(By.id("email")).sendKeys("swarajsuresh123@gmail.com");
		   Thread.sleep(2000);
		   driver.findElement(By.name("addr")).sendKeys("Purathuparambil House");
		   driver.findElement(By.id("telephoneno")).sendKeys("8897766899");
		   driver.findElement(By.xpath("//*[@id=\"main\"]/div/form/div/div[9]/ul/li[1]/input")).click();
		     driver.findElement(By.xpath("//*[@id=\"main\"]/div/div/ul/li/a")).click();
}
	@Test(priority=2)
	public void customerTariff() throws InterruptedException, IOException
	{
   driver.findElement(By.xpath("//*[@id=\"one\"]/div/div[1]/div[2]/h3/a")).click();
   driver.findElement(By.xpath("//*[@id=\"customer_id\"]")).sendKeys("434791");
   driver.findElement(By.xpath("//*[@id=\"main\"]/div/form/div/div[6]/input")).click();
	}
	@Test(priority=3)
	public void tariffPlan() throws InterruptedException
	{
   driver.findElement(By.xpath("//*[@id=\"header\"]/nav/a[1]")).click();
   Thread.sleep(2000);
   driver.findElement(By.xpath("//*[@id=\"menu\"]/ul/li[3]/a")).click();
   Thread.sleep(2000);
   driver.findElement(By.xpath("//*[@id=\"rental1\"]")).sendKeys("1");
   driver.findElement(By.id("local_minutes")).sendKeys("60");
   driver.findElement(By.id("inter_minutes")).sendKeys("30");
   driver.findElement(By.id("sms_pack")).sendKeys("100");
   driver.findElement(By.id("minutes_charges")).sendKeys("1");
   driver.findElement(By.id("inter_charges")).sendKeys("10");
   driver.findElement(By.id("sms_charges")).sendKeys("1");
   Thread.sleep(2000);
   driver.findElement(By.xpath("//*[@id=\"main\"]/div/form/div/div[36]/ul/li[1]/input")).click();
   Thread.sleep(2000);
   driver.findElement(By.xpath("//*[@id=\"main\"]/div/ul/li/a")).click();
   Thread.sleep(2000);
	}
	@Test(priority=4)
	public void payBilling() throws IOException, InterruptedException
	{
  driver.findElement(By.xpath("//*[@id=\"one\"]/div/div[3]/div[2]/h3/a")).click();
  Thread.sleep(2000);
  driver.findElement(By.xpath("//*[@id=\"customer_id\"]")).sendKeys("434791");
  driver.findElement(By.xpath("//*[@id=\"main\"]/div/form/div/div[6]/input")).click();
  File file1=((TakesScreenshot)driver).getScreenshotAs(OutputType.FILE);
	FileUtils.copyFile(file1,new File("C:\\Users\\hp\\OneDrive\\Pictures\\Screenshots\\bill.png"));
System.out.println("screenshot sucessfully saved");
driver.close();
	}
}
