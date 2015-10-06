# Small-Selenium-Project

import java.util.List;
import java.util.Random;

import org.openqa.selenium.By;
import org.openqa.selenium.Keys;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.firefox.FirefoxDriver;
import org.openqa.selenium.interactions.Actions;

public class your_store {

	public static void main(String[] args) {
		
		//Open browser and go to http://demo.opencart.com
		WebDriver driver=new FirefoxDriver();
		
		//Max browser
		driver.manage().window().maximize();
		
		//Go to: http://demo.opencart.com
		driver.get("http://demo.opencart.com"); 
		
		//Clicking on "$ Currency" button
		WebElement currency = driver.findElement(By.xpath("//button[@class='btn btn-link dropdown-toggle']"));
		currency.click();
		
		//Change currency from USD to GBP
		WebElement gbp = driver.findElement(By.name("GBP"));
		gbp.click();
		
		//Fill in field search with value iPod
		WebElement search = driver.findElement(By.name("search"));
		search.sendKeys("iPod");
		
		//Clicking on search
		WebElement search1 = driver.findElement(By.xpath("//*[@id='search']/span/button"));
		search1.click();
		
		//Add all products to product comparison
		List<WebElement> list = driver.findElements(By.xpath("//button[@data-original-title='Compare this Product']"));
		for(int i=0; i<=list.size()-1; i++){
			list.get(i).click();
		}
		//Go to product comparison
		WebElement product_comparison = driver.findElement(By.xpath("//a[@href='http://demo.opencart.com/index.php?route=product/compare']"));
		product_comparison.click();
		
		//Finding and removing products that are Out of Stock - it's just removing one particular product (that is already 'Out of Stock').
		//I had idea how to remove all Out of Stock products, but I had issue, we can discuss about it, then I will explain my point of view
		WebElement OutOfStock = driver.findElement(By.xpath("//*[@id='content']/table/tbody[2]/tr/td[2]/a"));
		OutOfStock.click();
		
		//Add a random product to shopping cart
		List<WebElement> list_random = driver.findElements(By.xpath("//input[@value='Add to Cart']"));
		int iCnt = list_random.size()-1;
		Random num = new Random();
		int iSelect = num.nextInt(iCnt+1);
		list_random.get(iSelect).click();
		
		//Go to Shopping Cart
		WebElement shopping_cart = driver.findElement(By.xpath("//a[@href='http://demo.opencart.com/index.php?route=checkout/cart']"));
		shopping_cart.click();
			
		//Check if price of a product is equal to total price for 1 product:
		WebElement price_total= driver.findElement(By.xpath("//*[@id='content']/form/div/table/tbody/tr/td[6]"));
		WebElement price = driver.findElement(By.xpath("//*[@id='content']/form/div/table/tbody/tr/td[5]"));
		if (price_total.getText().equals(price.getText())){
			System.out.print("Total Price is equal to price of a product;");
		}
		else {
			System.out.print("Prices are not equal;");
		}
		
		//Set quantity for 2
		WebElement Quantity=driver.findElement(By.xpath("//input[@class='form-control']"));
		Quantity.clear();
		Quantity.sendKeys("2");
				
		//Submit quantity
		WebElement Quantity_submit=driver.findElement(By.xpath("//button[@data-original-title='Update']"));
		Quantity_submit.click();
		
		

	}}


