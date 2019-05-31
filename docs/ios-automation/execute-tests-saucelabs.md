---
layout: default
title:  "Execute Tests in SauceLabs"
excerpt: "Learn to use BELLATRIX to execute iOS tests in SauceLabs."
date:   2019-05-31 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/execute-tests-saucelabs/
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
Given I open iOS app with path AssemblyFolder/Demos/TestApp.app.zip in SauceLabs
And I restart the app on test fail
And I use device with name iPhone 6
And I use iOS version 11.3
And I want to record a video of the execution
And I want to user screen resolution 1200 px x 800 px
And I want to record screenshots of the execution
And I open app

Scenario: Successfully Sum 5 And 6
	When I sum 5 and 6
	Then I assert answer is 11
```
Explanations
------------
```
Given I open iOS app with path AssemblyFolder/Demos/TestApp.app.zip in SauceLabs
And I restart the app on test fail
And I use device with name iPhone 6
And I use iOS version 11.3
And I want to record a video of the execution
And I want to user screen resolution 1200 px x 800 px
And I want to record screenshots of the execution
And I open app
```
To execute BELLATRIX tests in SauceLabs cloud, you could use the SauceLabs predefined steps. SauceLabs integration provides additional steps for capturing video and capturing screenshots. The last are optional and have default values.

Configuration
-------------
```json
"sauceLabs": {
         "gridUri":  "http://ondemand.saucelabs.com:80/wd/hub",
         "user": "aangelov",
         "key":  "mySecretKey"
     }
```
You can find a dedicated section about SauceLabs in **testFrameworkSettings.json** file under the **mobileSettings** section. There you can set the grid URL and credentials.