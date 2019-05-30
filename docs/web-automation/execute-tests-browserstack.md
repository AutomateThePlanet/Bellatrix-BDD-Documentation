---
layout: default
title:  "Execute Tests in BrowserStack"
excerpt: "Learn to use BELLATRIX to execute web tests in BrowserStack."
date:   2018-06-23 06:50:17 +0200
parent: web-automation
permalink: /web-automation/execute-tests-browserstack/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
Feature: BrowserStack Integration
	In order to use the browser in the BrowserStack Cloud
	As a automation engineer
	I want BELLATRIX to provide me handy method to do my job

Background: 
Given I open Chrome browser 68 in BrowserStack
And I want to run the browser on Windows platform
And I want to run the browser on 10 OS version
And I want to use console log type Warnings
And I want to record a video of the execution
And I want to capture a network logs of the execution
And I want to capture a network logs of the execution
And I want to set build = OrionBeta
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
Given I open Chrome browser 68 in BrowserStack
And I want to run the browser on Windows platform
And I want to run the browser on 10 OS version
And I want to use console log type Warnings
And I want to record a video of the execution
And I want to capture a network logs of the execution
And I want to capture a network logs of the execution
And I want to set build = OrionBeta
And I resize the browser 1200 px x 800 px
And I open browser
```
To execute BELLATRIX tests in BrowserStack cloud, you should use the BrowserStack predefined steps. You have ones for specifying the browser version, platform type, platform version, captureNetworkLogs, consoleLogType, build and debug. The last five are optional and have default values.

Configuration
-------------
```json
"browserStack": {
   "pageLoadTimeout": "30",
   "scriptTimeout": "1",
   "artificialDelayBeforeAction": "0",
   "gridUri":  "http://hub-cloud.browserstack.com/wd/hub/",
   "user": "soioa1",
   "key":  "pnFG3Ky2yLZ5muB1p46P"
}
```
You can find a dedicated section about SauceLabs in **testFrameworkSettings.json** file under the **webSettings** section. There you can set the grid URL, credentials and set some additional timeouts.