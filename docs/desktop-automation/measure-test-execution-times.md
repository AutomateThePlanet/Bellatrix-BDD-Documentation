---
layout: default
title:  "Measure Response Times"
excerpt: "Learn how to measure text execution times using BELLATRIX desktop module."
date:   2019-05-30 06:50:17 +0200
parent: desktop-automation
permalink: /desktop-automation/measure-test-execution-times/
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
Given I use app with path AssemblyFolder\Demos\Wpf\WPFSampleApp.exe
And I restart the app on test fail
And I take a screenshot for failed tests
And I record a video for failed tests
And I open app

@executiontimeunder-6-seconds
Scenario: Successfully Transfer Item
	When I transfer item FalconRocket user name bellatrix password secret
	Then I assert that keep me logged is checked
    And I assert that permanent trasnfer is checked
    And I assert that Item2 right item is selected
    And I assert that bellatrix user name is set
```

Explanations
------------
```csharp
@executiontimeunder-6-seconds
```
Sometimes it is useful to use your functional tests to measure performance. Or to just make sure that your app is not slow. To do that BELLATRIX libraries offer the **@executiontimeunder** attribute. You specify a timeout and if the test is executed over it the test will fail.