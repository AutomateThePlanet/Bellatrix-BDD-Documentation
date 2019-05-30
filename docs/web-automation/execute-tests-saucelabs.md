---
layout: default
title:  "Execute Tests in SauceLabs"
excerpt: "Learn to use BELLATRIX to execute web tests in SauceLabs."
date:   2019-05-30 06:50:17 +0200
parent: web-automation
permalink: /web-automation/execute-tests-saucelabs/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
Feature: SauceLabs Integration
	In order to use the browser in the SauceLabs Cloud
	As a automation engineer
	I want BELLATRIX to provide me handy method to do my job

Background: 
Given I open Chrome browser 68 in SauceLabs
And I want to run the browser on Windows platform
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
}
```

Explanations
------------
```
Background: 
Given I open Chrome browser 68 in SauceLabs
And I want to run the browser on Windows platform
And I want to record a video of the execution
And I want to capture a network logs of the execution
And I want to capture a network logs of the execution
And I want to set build = OrionBeta
And I resize the browser 1200 px x 800 px
And I open browser
```
To execute BELLATRIX tests in SauceLabs cloud you should use the SauceLabs predefined steps. You have ones for specifying- browser version, platform type, recordVideo and recordScreenshots. 

Configuration
-------------
```json
"sauceLabs": {
    "pageLoadTimeout": "30",
    "scriptTimeout": "1",
    "artificialDelayBeforeAction": "0",
    "gridUri":  "http://ondemand.saucelabs.com:80/wd/hub",
    "user": "aangelov",
    "key":  "mySecretKey"
}
```
You can find a dedicated section about SauceLabs in **testFrameworkSettings.json** file under the **webSettings** section. There you can set the grid URL, credentials and set some additional timeouts.