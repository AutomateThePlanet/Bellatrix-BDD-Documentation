---
layout: default
title:  "Measure Response Times"
excerpt: "Learn how to measure text execution times using BELLATRIX iOS module."
date:   2019-05-31 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/measure-test-execution-times/
anchors:
  example: Example
  explanations: Explanations
---
Example
--------
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

@executiontimeunder-6-seconds
Scenario: Successfully Sum 5 And 6
	When I sum 5 and 6
	Then I assert answer is 11
```

Explanations
------------
```csharp
@executiontimeunder-6-seconds
```
Sometimes it is useful to use your functional tests to measure performance. Or to just make sure that your app is not slow. To do that BELLATRIX libraries offer the **@executiontimeunder** attribute. You specify a timeout and if the test is executed over it the test will fail.