---
layout: default
title:  "Execute Tests in SauceLabs"
excerpt: "Learn to use BELLATRIX to execute Android tests in SauceLabs."
date:   2019-05-30 06:50:17 +0200
parent: android-automation
permalink: /android-automation/execute-tests-saucelabs/
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
Given I open Android app with path AssemblyFolder\Demos\ApiDemos.apk in SauceLabs
And I restart the app on test fail
And I use device with name android25-test
And I use Android version 7.1
And I use app package com.example.android.apis
And I use app activity .view.Controls1
And I want to record a video of the execution
And I want to user screen resolution 1200 px x 800 px
And I want to record screenshots of the execution
And I open app

Scenario: Successfully Transfer Item
	When I navigate to main page
	And I transfer item Jupiter user name antares password secret
	Then I assert that keep me logged is checked
    And I assert that permanent trasnfer is checked
    And I assert that Jupiter right item is selected
    And I assert that antares user name is set
```

Explanations
------------
```
Given I open Android app with path AssemblyFolder\Demos\ApiDemos.apk in SauceLabs
And I restart the app on test fail
And I use device with name android25-test
And I use Android version 7.1
And I use app package com.example.android.apis
And I use app activity .view.Controls1
And I want to record a video of the execution
And I want to user screen resolution 1200 px x 800 px
And I want to record screenshots of the execution
And I open app
```
To execute BELLATRIX tests in SauceLabs cloud, you could use the BrowserStack predefined steps. SauceLabs integreation provides additional steps for capturing video and capturing screenshots. The last are optional and have default values.

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