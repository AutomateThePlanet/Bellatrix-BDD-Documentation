---
layout: default
title:  "Control Browser"
excerpt: "Learn how to control browsers with BELLATRIX web module."
date:   2018-06-22 06:50:17 +0200
parent: web-automation
permalink: /web-automation/control-browser/
anchors:
  overview: Overview
  explanations: Explanations
---
Overview
--------

This is how one BELLATRIX feature file looks.
```csharp
Feature: CommonServices
	In order to use the browser
	As a automation engineer
	I want BELLATRIX to provide me handy method to do my job

Background: 
Given I use Firefox browser on Windows
And I reuse the browser if started
And I capture HTTP traffic
And I take a screenshot for failed tests
And I record a video for failed tests
And I open browser

Scenario: Browser Service Common Steps
	When I navigate to URL http://demos.bellatrix.solutions/product/falcon-9/
	And I refresh the browser
	When I wait until the browser is ready
	And I wait for all AJAX requests to finish
	And I maximize the browser
	And I navigate to URL http://demos.bellatrix.solutions/
	And I click browser's back button
	And I click browser's forward button
    And I click browser's back button
	And I wait for partial URL falcon-9
```

Explanations
------------
```
Background:
```
This marks the beginning of a special SpecFlow section which will be executed before each scenario.
```
Given I use Firefox browser on Windows
And I reuse the browser if started
```
These are predefined SpecFlow steps for automatic start/control of WebDriver browsers by BELLATRIX. If you have to do it manually properly, you will need thousands of lines of code.
Available options are:
- Chrome
- ChromeHeadless
- Firefox
- FirefoxHeadless
- InternetExplorer
- Edge
- Opera
- Safari

Available OS options are:
- Windows
- OSX

**Note**: *Headless mode = executed in the browser but the browser's UI is not rendered, in theory, should be faster. In practice the time gain is little.*

Though the second step you can control the browser behavior whether it is reused or restarted. This can drastically increase or decrease the tests execution time, depending on your needs. However you need to be careful because in case of tests failures the browser may need to be restarted.
Available options:
```
Given I restart the browser every time
```
For each scenario a separate WebDriver instance is created and the previous browser is closed. The new browser comes with new cookies and cache.
```
I restart the browser on test fail
```
The browser is only restarted if the previous scenario failed. Alternatively, if the previous test's browser was different.
```
I reuse the browser if started
```
The browser is only restarted if the previous scenario's browser was different. In all other cases, the browser is reused if possible.

**Note**: *However, use this option with caution since in some rare cases if you have not properly setup your tests you may need to restart the browser if the test fails otherwise all other tests may fail too.*

```
I resize the browser 600 px x 1200 px
```
Resizes the browser.

```csharp
[Binding]
public class CustomWebSteps : WebSteps
{
    private HomePage _homePage;
    private CartPage _cartPage;
    private CheckoutPage _checkoutPage;

    public PageObjectsSteps()
    {
    }

    [When(@"I navigate to home page")]
    public void WhenINavigateHomePage()
    {
        _homePage = App.GoTo<HomePage>();
    }

    [When(@"I filter products by popularity")]
    public void WhenIFilterProductsByPopularity()
    {
        _homePage.FilterProducts(ProductFilter.Popularity);
    }
}
```
To define your SpecFlow steps, create a new class file. It needs to inherit **WebSteps** which gives you access to all BELLATRIX services.