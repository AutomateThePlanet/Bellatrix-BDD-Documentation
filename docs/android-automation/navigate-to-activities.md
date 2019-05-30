---
layout: default
title:  "Navigate to Activities"
excerpt: "Learn how to navigate to Android activities with BELLATRIX mobile module."
date:   2019-05-30 06:50:17 +0200
parent: android-automation
permalink: /android-automation/navigate-to-activities/
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
Given I use app with path AssemblyFolder\Demos\ApiDemos.apk
And I restart the app on test fail
And I use device with name android25-test
And I use Android version 7.1
And I use app package com.example.android.apis
And I use app activity .view.Controls1
And I open app
```
Depending on the types of tests you want to write there are a couple of ways to navigate to specific activity.
If you use the predefined steps the first time the app is started it navigates to the specified activity.
```csharp
I start activity .view.Controls1 from package com.example.android.apis
```
You can always navigate in each separate scenario, but if all of them open the same activity, you can use the above techniques for code reuse.