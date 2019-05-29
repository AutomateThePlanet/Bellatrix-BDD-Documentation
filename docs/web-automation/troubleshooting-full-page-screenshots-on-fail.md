---
layout: default
title:  "Troubleshooting- Full Page Screenshots on Fail"
excerpt: "Learn how to generate full page screenshots on test's fail."
date:   2018-06-22 06:50:17 +0200
parent: web-automation
permalink: /web-automation/troubleshooting-full-page-screenshots-on-fail/
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
And I take a screenshot for failed tests
And I open browser

@executiontimeunder-6-seconds
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
Given I take a screenshot for failed tests
```
This is a predefined BELLATRIX step for automatic generation of full-page screenshots. The engine checks after each test, its result, if failed, makes the screenshots. We have a unique engine for the screenshots. We do not use vanilla WebDriver. If you use the WebDriver method, it makes a screenshot only of the visible part of the page. If you have to do it manually precisely, you need thousands of lines of code.

Configuration
-------------
If you open the **testFrameworkSettings.json** file, you find the **screenshotsSettings** section that controls this behaviour.
```json
"screenshotsSettings": {
    "isEnabled": "true",
    "filePath": "C:\\Troubleshooting\\Screenshots"
}
```
You can turn off the making of screenshots for all tests and specify where the screenshots to be saved. In the extensibility chapters read more about how you can create different screenshots engine or change the saving strategy.