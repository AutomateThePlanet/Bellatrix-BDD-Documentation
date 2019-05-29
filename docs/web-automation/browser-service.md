---
layout: default
title:  "BrowserService"
excerpt: "Learn how to use BELLATRIX BrowserService."
date:   2018-06-22 06:50:17 +0200
parent: web-automation
permalink: /web-automation/browser-service/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
Feature: BrowserServices
	In order to use the browser
	As a automation engineer
	I want BELLATRIX to provide me handy method to do my job

Background: 
Given I use Firefox browser on Windows
And I reuse the browser if started
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
BELLATRIX gives you predefined SpecFlow steps for most common operations for controlling the started browser.
```
When I wait until the browser is ready
And I wait for all AJAX requests to finish
```
Sometimes, some AJAX async calls are not caught natively by WebDriver. So you can use the BELLATRIX browser service's step. It waits for these calls automatically to finish. Keep in mind that usually this is not necessary since BELLATRIX has a complex built-in mechanism for handling element waits.
```
When I maximize the browser
```
Maximizes the browser.
```
When I click browser's back button
```
Simulates clicking the browser's Back button.
```
When I click browser's forward button
```
Simulates clicking the browser's Forward button.
```
When I refresh the browser
```
Simulates clicking the browser's Refresh button.