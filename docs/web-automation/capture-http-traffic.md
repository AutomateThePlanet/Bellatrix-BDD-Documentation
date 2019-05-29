---
layout: default
title:  "Capture HTTP Traffic"
excerpt: "Learn to capture HTTP traffic and make assertions using BELLATRIX."
date:   2018-06-23 06:50:17 +0200
parent: web-automation
permalink: /web-automation/capture-http-traffic/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
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
Capture HTTP traffic is one of the most requested features for WebDriver. However by design WebDriver does not include such feature. Happily, for you, we added it to BELLATRIX.
```
Given  I capture HTTP traffic
```
By default, the proxy is not used in your tests even if it is enabled. You need to call the predefined SpecFlow step to turn it on. After that, each request and response made by the browser is captured, and you have the option to modify it or make assertions against it. Later in your custom steps you can call the bellow methods to access and assert the recorded requests.
```csharp
App.ProxyService.AssertNoErrorCodes();
```
You can access the proxy through the BELLATRIX **App** service. The proxy service includes several useful assert methods. The first one asserts that no error codes are present in the requests. This way we can catch problems with not loaded images or CSS files.
```csharp
App.ProxyService.AssertNoLargeImagesRequested();
```
Make sure that our images size is optimised.
```csharp
App.ProxyService.AssertRequestMade("http://demos.bellatrix.solutions/favicon.ico");
```
Check if some specific request is made.
```csharp
App.ProxyService.SetUrlToBeRedirectedTo(
		"http://demos.bellatrix.solutions/favicon.ico", 
		"https://www.automatetheplanet.com/wp-content/uploads/2016/12/logo.svg");
```
You can set various URLs to be redirected. This is useful if you do not have access to production code and want to use a mock service instead.
```csharp
App.ProxyService.SetUrlToBeBlocked("http://demos.bellatrix.solutions/favicon.ico");
```
To make web pages load faster, you can block some not required services- for example analytics scripts, you do not need them in test environments.
```csharp
App.ProxyService.AssertRequestNotMade("http://demos.bellatrix.solutions/welcome");
```
Check that no request is made to specific URL.

Configuration
-------------
```json
"webProxySettings": {
     "isEnabled": "true"
}
```
To turn it on you need to **testFrameworkSettings.json** file and set the isEnabled to true.