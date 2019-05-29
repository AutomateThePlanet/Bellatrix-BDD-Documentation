---
layout: default
title:  "Navigate to Pages"
excerpt: "Learn how to navigate to web pages with BELLATRIX web module."
date:   2018-06-22 06:50:17 +0200
parent: web-automation
permalink: /web-automation/navigate-to-pages/
anchors:
  example: Example
  explanations: Explanations
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
When I navigate to URL http://demos.bellatrix.solutions/product/falcon-9/
```
A predefined step to navigate to specific URL.
```
When I wait for partial URL falcon-9
```
Sometimes before proceeding with searching and making actions on the next page, we need to wait for something.
It is useful in some cases to wait for a partial URL instead hard-coding the whole URL since it can change depending on the environment. Keep in mind that usually this is not necessary since BELLATRIX has a complex built-in mechanism for handling element waits.
```csharp
When I navigate to local page testPage.html
```
Sometimes you may need to navigate to a local HTML file. We make it easier for you since it is complicated depending on the different browsers. Make sure to copy the file to the folder with your tests files. To do it, include it in the project and mark it as Copy Always.