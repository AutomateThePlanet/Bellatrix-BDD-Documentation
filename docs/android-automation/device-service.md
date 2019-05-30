---
layout: default
title:  "DeviceService"
excerpt: "Learn how to use BELLATRIX Android DeviceService."
date:   2019-05-30 06:50:17 +0200
parent: android-automation
permalink: /android-automation/device-service/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```
Feature: Navigate to BELLATRIX Online Rocket Shop
	To purchase a new rocket
	As a Nuclear Engineer 
	I want to be able to buy a new rocket.

Background:
Given I use app with path AssemblyFolder\Demos\ApiDemos.apk
And I restart the app on test fail
And I use device with name android25-test
And I use Android version 7.1
And I use app package com.example.android.apis
And I use app activity .view.Controls1
And I open app

Scenario: Successfully Transfer Item
	When I open notifications
    And I turn on the location service
    And I lock the device
    And I rotate the android device portrait
```

Explanations
------------
BELLATRIX gives you predefined steps for most common operations for controlling the device through the DeviceService class.
```
I rotate the android device landscape
```
Rotates the device horizontally.
```
I rotate the android device portrait
```
Rotates the device portrait.
```
I change the android device orientation to landscape
```
Changes the orientation to landscape.
```
I change the android device orientation to portrait
```
Changes the orientation to portrait.
```
I unlock the device
```
Unlocks the device.
```
I lock the device
```
Locks the device.
```
I change the connection type to airplane mode
```
Changes the connection to Airplane mode.
```
I change the connection type to all network on
```
Changes the connection to all network on.
```
I change the connection type to data only
```
Changes the connection to all data only.
```
I change the connection type to none
```
Changes the connection to all none.
```
I change the connection type to wifi only
```
Changes the connection to wifi only.
```
I turn on the location service
```
Turns on the location service.
```
I open notifications
```
Opens notifications.