---
layout: default
title:  "Behaviour Driven Development BDD Logging"
excerpt: "Learn the BELLATRIX Behaviour Driven Development BDD Logging works and how to use it."
date:   2018-06-2s 06:50:17 +0200
parent: web-automation
permalink: /web-automation/bdd-logging/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
Feature: Navigate to BELLATRIX Online Rocket Shop
	To purchase a new rocket
	As a Nuclear Engineer 
	I want to be able to buy a new rocket.

Background: 
Given Add Custom Driver Capabilities
And I use Chrome browser on Windows
And I restart the browser every time
And I open browser

@loadTest
Scenario: Successfully By Product 28 with Coupon
	
	When I navigate to home page
	And I filter products by popularity
	And I add product by ID = 28
	And I click view cart button
	And I apply coupon happybirthday
	And I update product 1 quantity to 2
	Then I assert total price is equal to 114.00
    When I click proceed to checkout button
    And I set first name = In
    And I set last name = Deepthought
    And I set company = Automate The Planet Ltd.
    And I set country = Bulgaria
    And I set address 1 = bul. Yerusalim 5
    And I set address 2 = bul. Yerusalim 6
    And I set city = Sofia
    And I set state = Sofia-Grad
    And I set zip = 1000
    And I set phone = +00359894646464
    And I set email = info@bellatrix.solutions
    And I add  order comments = cool product
    And I check payments button

```

Explanations
------------
There are cases when you need to show your colleagues or managers what tests do you have. Sometimes you may have manual test cases, but their maintenance and up-to-date state are questionable. Also, many times you need additional work to associate the tests with the test cases. Some frameworks give you a way to write human readable tests through the Gherkin language. The main idea is non-technical people to write these tests. However, we believe this approach is doomed. Or it is doable only for simple tests. This is why in BELLATRIX we built a feature that generates the test cases after the tests execution. After each action or assertion, a new entry is logged.

After the test is executed the following log is created:

```
>Start Chrome on PORT = 34079
Start Test
Class = BDDLoggingTests Name = PurchaseRocketWithLogs
Select 'Sort by price: low to high' from control (Name ending with orderby)
Hover control (InnerText containing Read more)
Focus control (data-product_id = 28)
Click control (data-product_id = 28)
Click control (Class = added_to_cart wc-forward)
Type 'happybirthday' into control (ID = coupon_code)
Click control (Value containing Apply coupon)
Ensure control (Class = woocommerce-message) inner text is 'Coupon code applied successfully.'
Set '0' into control (Class = input-text qty text)
Set '2' into control (Class = input-text qty text)
Click control (Value containing Update cart)
Ensure control (XPath = //*[@class='order-total']//span) inner text is '95.00€'
Click control (Class = checkout-button button alt wc-forward)
Ensure control (InnerText containing Click here) href is 'http://demos.bellatrix.solutions/checkout/#'
Ensure control (InnerText containing Click here) CSS class is 'showlogin'
Scroll to visible control (ID = order_comments)
Type 'Please send the rocket to my door step!' into control (ID = order_comments)
Type 'In' into control (ID = billing_first_name)
Type 'Deepthought' into control (ID = billing_last_name)
Type 'Automate The Planet Ltd.' into control (ID = billing_company)
Select 'Bulgaria' from control (ID = billing_country)
Ensure control (ID = billing_address_1) placeholder is 'House number and street name'
Type 'bul. Yerusalim 5' into control (ID = billing_address_1)
Type 'bul. Yerusalim 6' into control (ID = billing_address_2)
Type 'Sofia' into control (ID = billing_city)
Select 'Sofia-Grad' from control (ID = billing_state)
Type '1000' into control (ID = billing_postcode)
Type '+00359894646464' into control (ID = billing_phone)
Type 'info@bellatrix.solutions' into control (ID = billing_email)
Check control (ID = createaccount)
Click control (for = payment_method_cheque)
```

You can notice that since we use Ensure assertions not the regular one they also present in the log: *Ensure control (XPath = //*[@class='order-total']//span) inner text is '95.00€'*

There are two specifics about the generation of the logs. If page objects are used, which are discussed in next chapters. Two things change.
1. Instead of locators, the exact names of the element properties are printed.
2. Instead of page URL, the name of the page is displayed.

Configuration
-------------
```json
"logging": {
       "isEnabled": "true",
       "isConsoleLoggingEnabled": "true",
       "isDebugLoggingEnabled": "true",
       "isEventLoggingEnabled": "false",
       "isFileLoggingEnabled": "true",
       "outputTemplate":  "{Message:lj}{NewLine}",
       "addUrlToBddLogging": "false"
   }
```
In the **testFrameworkSettings.json** file find a section called logging, responsible for controlling the BDD logs generation. You can disable the logs entirely. There are different places where the logs are populated. By default, you can see the logs in the output window of each test. Also, a file called logs.txt is generated in the folder with the DLLs of your tests. If you execute your tests in CI with some CLI test runner the logs are printed there as well. **outputTemplate** - controls how the message is formatted. You can add additional info such as timestamp and much more.
For more info visit- [https://github.com/serilog/serilog/wiki/Formatting-Output](https://github.com/serilog/serilog/wiki/Formatting-Output)
If **addUrlToBddLogging** is true, after each action the current page's URL will be added.****