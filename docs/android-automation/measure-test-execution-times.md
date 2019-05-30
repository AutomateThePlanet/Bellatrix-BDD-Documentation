---
layout: default
title:  "Measure Response Times"
excerpt: "Learn how to measure text execution times using BELLATRIX Android module."
date:   2019-05-30 06:50:17 +0200
parent: android-automation
permalink: /android-automation/measure-test-execution-times/
anchors:
  example: Example
  explanations: Explanations
---
Example
--------
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

@executiontimeunder-6-seconds
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
```csharp
@executiontimeunder-6-seconds
```
Sometimes it is useful to use your functional tests to measure performance. Or to just make sure that your app is not slow. To do that BELLATRIX libraries offer the **@executiontimeunder** attribute. You specify a timeout and if the test is executed over it the test will fail.