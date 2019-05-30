---
layout: default
title:  "KeyboardService"
excerpt: "Learn how to use BELLATRIX Android KeyboardService."
date:   2019-05-30 06:50:17 +0200
parent: android-automation
permalink: /android-automation/keyboard-service/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
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
	When I long press key A with meta key Shift
	And I hide the android app keyboard
```

Explanations
------------
BELLATRIX gives you predefined steps for easier work with device's keyboard through KeyboardService class.
```csharp
I hide the android app keyboard
```
Hides the keyboard.
```csharp
I press key Space with meta key Shift
```
Presses Space key simulating that the Shift key is ON.
```
I long press key Space with meta key Shift
```
Long presses Space key simulating that the Shift key is ON.