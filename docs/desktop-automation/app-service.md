---
layout: default
title:  "AppService"
excerpt: "Learn how to use BELLATRIX AppService."
date:   2018-05-30 06:50:17 +0200
parent: desktop-automation
permalink: /desktop-automation/app-service/
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
Given I use app with path AssemblyFolder\Demos\Wpf\WPFSampleApp.exe
And I restart the app on test fail
And I take a screenshot for failed tests
And I record a video for failed tests
And I open app

Scenario: Successfully Transfer Item
	When I click app's back button
	And I click app's forward button
    And I maximize the app
    Then I assert that Item2 right item is selected
```

Explanations
------------
With the BELLATRIX desktop library, you can test various Windows applications written in different technologies such as- WPF, WinForms or UWP (Universal Windows Platform).
```
Given I use app with path AssemblyFolder\Demos\WPFSampleApp.exe
And I open app
```
For the first two, you need to pass the path to your application's executable.
```
Given I use app with path AssemblyFolder\Demos\WindowsFormsSampleApp.exe
And I open app
```
Starts WinForms app.
```
Given I use app with path 369ede42-bebe-41ea-a02a-0da04991478e_q6s448gyj2xsw!App
And I open app
```
For Universal applications you need to set the application's installation GUID.
```
When I click app's back button
And I click app's forward button
And I maximize the app
Then I assert that Item2 right item is selected
```
Through predefined steps you can control the certain aspects of your application such as maximise it or going backwards or forward.