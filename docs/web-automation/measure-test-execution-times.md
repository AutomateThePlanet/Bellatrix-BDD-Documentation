---
layout: default
title:  "Measure Response Times"
excerpt: "Learn how to measure text execution times using BELLATRIX web module."
date:   2018-10-20 06:50:17 +0200
parent: web-automation
permalink: /web-automation/measure-test-execution-times/
anchors:
  example: Example
  explanations: Explanations
---
Example
--------
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
```csharp
@executiontimeunder-6-seconds
```
Sometimes it is useful to use your functional tests to measure performance. Or to just make sure that your app is not slow. To do that BELLATRIX libraries offer the **@executiontimeunder** attribute. You specify a timeout and if the test is executed over it the test will fail.