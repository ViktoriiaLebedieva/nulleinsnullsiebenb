package Headless.Test;

import org.junit.*;

import static org.junit.Assert.*;

import org.openqa.selenium.*;
import org.openqa.selenium.htmlunit.HtmlUnitDriver;
import org.openqa.selenium.support.ui.Select;


public class nulleinsnullsiebenb {
	  private HtmlUnitDriver driver;
	  private String baseUrl;
	  private boolean acceptNextAlert = true;
	  private StringBuffer verificationErrors = new StringBuffer();
	  SelectBrowser bv = new SelectBrowser();
	  InitializeShop is = new InitializeShop();
	  Search search = new Search();
	  GoToCart gc = new GoToCart();
	  Login login = new Login();
	  BillFormula bf = new BillFormula();
  @Before
	  public void setUp() throws Exception {
	  	  baseUrl ="http://klstage.kikaleiner.at/webapp/wcs/stores/servlet/AjaxStoreLocatorDisplayView?langId=-3&storeId=10151";
	  	  driver = new HtmlUnitDriver(bv.getBrowserVersion());
	  	  is.intializeDriver(driver);
	  }
  @Test
  public void test0107bDurchlauf() throws Exception {
	is.initializeShop(driver, baseUrl, "Amstetten");  
	login.login(driver,"annastoermer@gmx.de", "!bekannt23");
  }

  @After
  public void tearDown() throws Exception {
    driver.quit();
    String verificationErrorString = verificationErrors.toString();
    if (!"".equals(verificationErrorString)) {
      fail(verificationErrorString);
    }
  }

  private boolean isElementPresent(By by) {
    try {
      driver.findElement(by);
      return true;
    } catch (NoSuchElementException e) {
      return false;
    }
  }

  private boolean isAlertPresent() {
    try {
      driver.switchTo().alert();
      return true;
    } catch (NoAlertPresentException e) {
      return false;
    }
  }

  private String closeAlertAndGetItsText() {
    try {
      Alert alert = driver.switchTo().alert();
      String alertText = alert.getText();
      if (acceptNextAlert) {
        alert.accept();
      } else {
        alert.dismiss();
      }
      return alertText;
    } finally {
      acceptNextAlert = true;
    }
  }
}

