---
layout: default
title:  "Execute Tests in CrossBrowserTesting"
excerpt: "Learn to use BELLATRIX to execute iOS tests in CrossBrowserTesting."
date:   2019-05-31 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/execute-tests-crossbrowsertesting/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
Feature: Navigate to BELLATRIX Online Rocket Shop
	To purchase a new rocket
	As a Nuclear Engineer 
	I want to be able to buy a new rocket.

Background:
Given I open iOS app with path AssemblyFolder/Demos/TestApp.app.zip in CrossBrowserTesting
And I use device with name iPhone 6
And I use iOS version 11.3
And I want to record a video of the execution
And I want to user screen resolution 1200 px x 800 px
And I want to capture a network logs of the execution
And I want to set build = myCustomName
And I open app

Scenario: Successfully Sum 5 And 6
	When I sum 5 and 6
	Then I assert answer is 11
```
Explanations
------------
```
Given I open iOS app with path AssemblyFolder/Demos/TestApp.app.zip in CrossBrowserTesting
And I use device with name iPhone 6
And I use iOS version 11.3
And I want to record a video of the execution
And I want to user screen resolution 1200 px x 800 px
And I want to capture a network logs of the execution
And I want to set build = myCustomName
And I open app
```
To execute BELLATRIX tests in CrossBrowserTesting cloud, you could use the BrowserStack predefined steps. CrossBrowserTesting integration provides additional steps for capturing video, capturing network logs, build and debug. The last four are optional and have default values.

Configuration
-------------
```json
"browserStack": {
	"gridUri":  "http://hub-cloud.browserstack.com/wd/hub/",
	"user": "soioa1",
	"key":  "pnFG3Ky2yLZ5muB1p46P"
}
```
You can find a dedicated section about SauceLabs in **testFrameworkSettings.json** file under the **mobileSettings** section. There you can set the grid URL and credentials.