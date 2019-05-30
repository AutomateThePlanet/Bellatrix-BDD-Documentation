---
layout: default
title:  "AppService"
excerpt: "Learn how to use BELLATRIX Android AppService."
date:   2019-05-30 06:50:17 +0200
parent: android-automation
permalink: /android-automation/app-service/
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
	When I reset the android app
	And I reset the android app
    And I start activity .view.Controls1 from package com.example.android.apis
```

Explanations
------------
BELLATRIX gives you predefined steps for most common operations for controlling the Android app through the AppService class.
```
I close the android app
```
Closes the app.
```
I launch the android app
```
Launches the app.
```
I background the android app for 2 seconds
```
Backgrounds the app for the specified number of seconds.
```
I reset the android app
```
Resets the app.
```
I start activity .view.Controls1 from package com.example.android.apis
```
Starts activity from the specified package.
```
I install android app with path AssemblyFolder\Demos\ApiDemos.apk
```
Installs the APK file on the device.
```
I remove android app with package io.appium.android.apis
```
Uninstalls the app with the specified app package.