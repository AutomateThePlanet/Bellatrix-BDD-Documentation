---
layout: default
title:  "DeviceService"
excerpt: "Learn how to use BELLATRIX iOS DeviceService."
date:   2019-05-31 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/device-service/
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
	When I shake the iOS device
	And I change the iOS device orientation to landscape
```

Explanations
------------
BELLATRIX gives you predefined steps for most common operations for controlling the device through the **DeviceService** class.
```
I rotate the iOS device landscape
```
Rotates the device horizontally.
```
I rotate the iOS device portrait
```
Rotates the device vertically.
```
I change the iOS device orientation to landscape
```
Changes the orientation to landscape.
```
I change the iOS device orientation to portrait
```
Changes the orientation to portrait.
```
I lock the iOS device for 3 seconds
```
Locks the device for 3 seconds.
```
I shake the iOS device
```
Shakes the device.