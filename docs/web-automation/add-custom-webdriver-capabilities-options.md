---
layout: default
title:  "Add Custom WebDriver Capabilities and Options"
excerpt: "Learn how to add custom WebDriver capabilities and/or options."
date:   2018-02-20 06:50:17 +0200
parent: web-automation
permalink: /web-automation/add-custom-webdriver-capabilities-options/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
[Binding]
public class CustomWebSteps : WebSteps
{
    [Given(@"Add Custom Driver Capabilities")]
    public void AddCustomWebDriverCapabilities()
    {
        var firefoxOptions = new FirefoxOptions
        {
            AcceptInsecureCertificates = true,
            UnhandledPromptBehavior = UnhandledPromptBehavior.Accept,
            PageLoadStrategy = PageLoadStrategy.Eager,
        };

        App.AddWebDriverOptions(firefoxOptions);

        App.AddAdditionalCapability("disable-popup-blocking", true);

        var profileManager = new FirefoxProfileManager();
        FirefoxProfile profile = profileManager.GetProfile("BELLATRIX");

        App.AddWebDriverBrowserProfile(profile);
    }
}
```

Explanations
------------
```csharp
[Binding]
public class CustomWebSteps : WebSteps
{
    [Given(@"Add Custom Driver Capabilities")]
    public void AddCustomWebDriverCapabilities()
    {
        var firefoxOptions = new FirefoxOptions
        {
            AcceptInsecureCertificates = true,
            UnhandledPromptBehavior = UnhandledPromptBehavior.Accept,
            PageLoadStrategy = PageLoadStrategy.Eager,
        };

        App.AddWebDriverOptions(firefoxOptions);

        App.AddWebDriverOptions("disable-popup-blocking", true);

        var profileManager = new FirefoxProfileManager();
        FirefoxProfile profile = profileManager.GetProfile("BELLATRIX");

        App.AddWebDriverBrowserProfile(profile);
    }
}
```
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

Scenario: Successfully By Product 28 with Coupon
	
	When I navigate to home page
```
Explanations
------------
```csharp
var firefoxOptions = new FirefoxOptions
{
    AcceptInsecureCertificates = true,
    UnhandledPromptBehavior = UnhandledPromptBehavior.Accept,
    PageLoadStrategy = PageLoadStrategy.Eager,
};

App.AddWebDriverOptions(firefoxOptions);
```
BELLATRIX hides the complexity of initialisation of WebDriver and all related services. In some cases, you need to customise the set up of a browser with using WebDriver options, adding driver capabilities or using browser profile. Using the **App** service methods you can add all of these with ease. Make sure to call them in a step definition method. Later you can call this step in your feature files. These options are used only for the tests in this particular class.

**Note**: *You can use all of these methods no matter which run option you use- Browser, Remote, SauceLabs, BrowserStack or CrossBrowserTesting.*
```csharp
App.AddWebDriverOptions("disable-popup-blocking", true);
```
Add custom WebDriver capability.
```csharp
var profileManager = new FirefoxProfileManager();
FirefoxProfile profile = profileManager.GetProfile("BELLATRIX");

App.AddWebDriverBrowserProfile(profile);
```
Add an existing Firefox profile. You may want to test your application in together with some specific browser extension.