---
layout: default
title:  "Execute Tests in Selenium Grid"
excerpt: "Learn to use BELLATRIX to execute tests in Selenium Grid."
date:   2019-05-30 06:50:17 +0200
parent: web-automation
permalink: /web-automation/execute-tests-selenium-grid/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
Feature: Selenium Grid Integration
	In order to use the browser in a Selenium Grid
	As a automation engineer
	I want BELLATRIX to provide me handy method to do my job

Background: 
Given I open Chrome browser 68 in Grid
And I want to run the browser on Windows platform in Gird
And I restart the browser on test fail
And I resize the browser 1200 px x 800 px
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
Given I open Chrome browser 68 in Grid
And I want to run the browser on Windows platform in Gird
And I restart the browser on test fail
And I resize the browser 1200 px x 800 px
And I open browser
```
To use BELLATRIX with Selenium Grid, you should use the Grid predefined steps. You have ones for specifying- browser version and platform type.

Configuration
-------------
```json
"remote": {
     "pageLoadTimeout": "30",
     "scriptTimeout": "1",
     "artificialDelayBeforeAction": "0",
     "gridUri":  "http://127.0.0.1:4444/wd/hub"
}
```
You can find a dedicated section about Selenium grid in **testFrameworkSettings.json** file under the **webSettings** section. There you can set the grid URL and set some additional timeouts.