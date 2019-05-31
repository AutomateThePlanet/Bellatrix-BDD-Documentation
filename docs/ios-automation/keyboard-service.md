---
layout: default
title:  "KeyboardService"
excerpt: "Learn how to use BELLATRIX iOS KeyboardService."
date:   2019-05-31 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/keyboard-service/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
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
	And I hide the iOS app keyboard
	Then I assert answer is 11
```

Explanations
------------
BELLATRIX gives you predefined steps for easier work with device's keyboard through **KeyboardService** class.
```
I hide the iOS app keyboard
```
Hides the keyboard.