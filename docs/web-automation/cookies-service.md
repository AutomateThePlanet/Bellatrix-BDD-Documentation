---
layout: default
title:  "CookiesService"
excerpt: "Learn how to use BELLATRIX CookiesService."
date:   2018-06-22 06:50:17 +0200
parent: web-automation
permalink: /web-automation/cookies-service/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
Feature: CommonServices
	In order to use the browser
	As a automation engineer
	I want BELLATRIX to provide me handy method to do my job

Background: 
Given I use Firefox browser on Windows
And I reuse the browser if started
And I open browser

Scenario: Cookies Service Common Steps
	When I navigate to URL http://demos.bellatrix.solutions/product/falcon-9/
	And I add cookie name = testCookie value = 99
    And I delete cookie testCookie
    And I add cookie name = testCookie1 value = 100
    And I delete all cookies
```

Explanations
------------
BELLATRIX gives you predefined steps for easier work with cookies. You need to make sure that you have navigated to the desired web page.
```
When I delete cookie testCookie
```
Deletes a specific cookie by name.
```
When I delete all cookies
```
Delete all cookies.
```
When I add cookie name = testCookie1 value = 100
```
Add a new cookie.