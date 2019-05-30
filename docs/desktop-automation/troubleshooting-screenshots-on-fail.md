---
layout: default
title:  "Troubleshooting- Screenshots on Fail"
excerpt: "Learn how to generate screenshots on test's fail."
date:   2018-05-30 06:50:17 +0200
parent: desktop-automation
permalink: /desktop-automation/troubleshooting-screenshots-on-fail/
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
Given I use app with path AssemblyFolder\Demos\Wpf\WPFSampleApp.exe
And I restart the app on test fail
And I take a screenshot for failed tests
And I open app

Scenario: Successfully Transfer Item
	When I transfer item FalconRocket user name bellatrix password secret
	Then I assert that keep me logged is checked
    And I assert that permanent trasnfer is checked
    And I assert that Item2 right item is selected
    And I assert that bellatrix user name is set
```

Explanations
------------
```
Given I take a screenshot for failed tests
```
This is a predefined BELLATRIX step for automatic generation of screen screenshots. The engine checks after each test, its result, if failed, makes the screenshots.

Configuration
-------------
If you open the **testFrameworkSettings.json** file, you find the **screenshotsSettings** section that controls this behaviour.
```json
"screenshotsSettings": {
    "isEnabled": "true",
    "filePath": "C:\\Troubleshooting\\Screenshots"
}
```
You can turn off the making of screenshots for all tests and specify where the screenshots to be saved. In the extensibility chapters read more about how you can create different screenshots engine or change the saving strategy.