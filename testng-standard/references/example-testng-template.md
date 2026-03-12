# Example: TestNG test template (secw_base)

## Full template (with DataProvider)

```java
// Test Template (TestNG data-driven) – secw_base
// Package: sec.test  |  Class naming: <ClassUnderTest>Test

package sec.test;

import org.testng.Assert;
import org.testng.annotations.AfterMethod;
import org.testng.annotations.BeforeMethod;
import org.testng.annotations.DataProvider;
import org.testng.annotations.Test;
import sec.obj.SECO00160;  // replace with class under test

public class SECO00160Test {  // replace with YourObjTest

  private SECO00160 target;  // replace with class under test

  @BeforeMethod
  public void setUp() {
    target = new SECO00160();
  }

  @AfterMethod
  public void tearDown() {
    // TODO: cleanup if needed
  }

  @DataProvider(name = "functionName_cases")
  public Object[][] provideFunctionNameCases() {
    return new Object[][] {
      { "happyPath", "validInput", true },
      { "edgeCase_empty", "", false },
      { "error_invalid", "invalid", false },
    };
  }

  @Test(description = "functionName - data-driven")
  public void testFunctionName_DataDriven(String testCaseId, String input, boolean expected) {
    // Arrange
    // Act
    // boolean result = target.functionName(input);
    // Assert
    // Assert.assertEquals(result, expected, "Case: " + testCaseId);
    Assert.assertNotNull(target);  // placeholder
  }

  @Test(description = "getter/setter round-trip")
  public void testTrxChlRoundTrip() {
    target.setTrxChl("WEB");
    Assert.assertEquals(target.getTrxChl(), "WEB");
  }
}
```

## Checklist for new tests

1. Create class in package `sec.test` with name `<ClassUnderTest>Test`.
2. Add `<class name="sec.test.YourObjTest"/>` to `WEB-INF/test-classes/testng.xml`.
3. Use `@BeforeMethod` for per-test setup; keep tests independent.
4. Use AAA (Arrange–Act–Assert) and `@Test(description = "...")`.
5. Use a DataProvider for multiple inputs; include a test case id for reporting.
6. Mock external dependencies (DB, HTTP, MQ); do not use real services in unit tests.
