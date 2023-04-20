# Lab-8_202001170

<h4>Name:KEVIN RAVAL</h4>
<h4>ID: 202001170</h4>
<h4>Unit Testing with JUnit</h4>
<hr>
<h3>Creating Java Package and Boa Class</h3>
<p> i created a new eclipse project with name Lab8_202001170 and then create package,create class for Boa, the code is as follow</p>

```java
package tests;

public class Boa {
	private String name; 
	private int length; // the length of the boa, in feet 
	private String favoriteFood; 
	public Boa (String name, int length, String favoriteFood){
		this.name = name; 
		this.length = length; 
		this.favoriteFood = favoriteFood; 
	} 
	 // returns true if this boa constrictor is healthy 
	public boolean isHealthy(){ 
		return this.favoriteFood.equals("granola bars");
	} 
	// returns true if the length of this boa constrictor is 
	// less than the given cage length 
	public boolean fitsInCage(int cageLength){
		return this.length < cageLength; 
	}
}
```
<hr>
<h3>Creating a JUnit Test Class in Eclipse</h3>

i created testcase file tests.java for Boa.java

After configuring the test case file, i define the _setUp()_ function as follows

```java
package tests;
import org.junit.Before;
import org.junit.Test;
public class tests {
	Boa jen,ken;
	
	@Before
	public void setUp() throws Exception { 
		jen = new Boa("Jennifer", 2, "grapes");
		ken = new Boa ("Kenneth", 3, "granola bars");
	} 
}
```
## Testing _Boa_ class methods

### _isHealthy()_ method

It is important to note that the _isHealthy()_ function does not take any parameters. Due to this, the only test cases possible are to call the method on _Boa_ objects _"jen"_ and _"ken"_.  
Thus, the test cases defined in the _testIsHealthy()_ test function is as follows:

```java
  @Test
  public void testIsHealthy() {
      assertEquals("Error in isHealthy()",false, jen.isHealthy());
      assertEquals("Error in isHealthy()",true, ken.isHealthy());
  }
```
### _FitsInCage()_ method

The _FitsInCage()_ function takes an integer parameter as input and hence can have a range of test-cases possible.  
Although _jen_ and _ken_ both will be executing the same function definition for _FitsInCage(<cage_length>)_ function call, it is better to call methods from both the instances to ensure independency of the function definition from the instance.

The test-cases defined can thus go as follows:

```java
@Test
public void testFitsInCage() {
    assertEquals("Error in fitsInCage()",true,jen.fitsInCage(5));  // For length of cage greater than jen's boa
    assertEquals("Error in fitsInCage()",false,jen.fitsInCage(2)); // For length of cage equal to jen's boa
    assertEquals("Error in fitsInCage()",false,jen.fitsInCage(1)); // For length of cage less than jen's boa
    assertEquals("Error in fitsInCage()",false,ken.fitsInCage(2)); // For length of cage less than ken's boa
    assertEquals("Error in fitsInCage()",false,ken.fitsInCage(3)); // For length of cage equal to ken's boa
    assertEquals("Error in fitsInCage()",true,ken.fitsInCage(5));  // For length of cage greater than ken's boa
}
```
## Running the Test Cases



To run the test cases, i simply right-click on the file(_BoaTest.java_ here), click on _Coverage As_, and then _1 JUnit Test_.

on the first run 2 out of 2 test cases are passed

<img width="849" alt="image" src="https://user-images.githubusercontent.com/90209818/233391635-c7c02d32-71cb-4633-ab26-df2036c86c0e.png">

## Adding new Method

i add a new method _lengthInches()_ to return the length of the Boa in inches.

```java
// produces the length of the Boa in inches 
public int lengthInInches(){ 
    return this.length*12;
}
```

The new test cases defined for the same are as follows:

```java
@Test
public void testlengthInInches() {
    assertEquals("Error in fitsInCage()",24,jen.lengthInInches());
    assertEquals("Error in fitsInCage()",36,ken.lengthInInches());
}
```
The test case pass successfully as shown below

![WhatsApp Image 2023-04-20 at 15 26 19](https://user-images.githubusercontent.com/90209818/233388246-494ca457-a32b-4e7c-b66d-68cfb2398ea3.jpg)
