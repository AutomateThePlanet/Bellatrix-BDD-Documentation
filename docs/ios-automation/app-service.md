---
layout: default
title:  "AppService"
excerpt: "Learn how to use BELLATRIX IOS AppService."
date:   2019-05-30 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/app-service/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```
Feature: Navigate to BELLATRIX Online Calculator
	To purchase a new rocket
	As a Nuclear Engineer 
	I want to be able to buy a new rocket.

Background:
Given I use app with path AssemblyFolder/Demos/TestApp.app.zip
And I restart the app on test fail
And I use device with name iPhone 6
And I use iOS version 11.3
And I open app

Scenario: Successfully Sum 5 And 6
	When I sum 5 and 6
	And I background the android app for 2 seconds
    And I reset the iOS app
    And I remove iOS app with appId com.apple.mobilecal
	Then I assert answer is 11
```

Explanations
------------
BELLATRIX gives you predefined steps for most common operations for controlling the iOS app through the AppService class.class.
```
When I background the iOS app for 2 seconds
```
Backgrounds the app for the specified number of seconds.
```
When I reset the iOS app
```
Resets the app.
```
When I launch the iOS app
```
Launches the app.
```
When I close the iOS app
```
Closes the app.
```
When I install android app with path AssemblyFolder/Demos/TestApp.app.zip
```
Installs the app file on the device.
```csharp
When I remove iOS app with appId com.apple.mobilecal
```
Uninstalls the app with the specified app id. You can get your app's bundleId from XCode.