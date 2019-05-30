---
layout: default
title:  "Control App"
excerpt: "Learn how to control Android applications with BELLATRIX Android module."
date:   2019-05-30 06:50:17 +0200
parent: android-automation
permalink: /android-automation/control-app/
anchors:
  overview: Overview
  explanations: Explanations
---
Overview
--------

This is how one BELLATRIX test class looks like.
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
	When I navigate to main page
	And I transfer item Jupiter user name antares password secret
	Then I assert that keep me logged is checked
    And I assert that permanent trasnfer is checked
    And I assert that Jupiter right item is selected
    And I assert that antares user name is set
```

Explanations
------------
```
Background:
```
This marks the beginning of a special SpecFlow section which will be executed before each scenario.
```csharp
Given I use app with path AssemblyFolder\Demos\ApiDemos.apk
And I restart the app on test fail
And I use device with name android25-test
And I use Android version 7.1
And I use app package com.example.android.apis
And I use app activity .view.Controls1
And I open app
```
These are predefined SpecFlow steps for automatic start/control of Appium and the app by BELLATRIX. If you have to do it manually properly, you will need thousands of lines of code.
Though the second step you can control the app behavior whether it is reused or restarted. This can drastically increase or decrease the tests execution time, depending on your needs. However you need to be careful because in case of tests failures the app may need to be restarted.
Available options:
```
Given I restart the app every time
```
For each scenario a separate WebDriver instance is created and the previous browser is closed. The new browser comes with new cookies and cache.
```
I restart the app on test fail
```
The browser is only restarted if the previous scenario failed. Alternatively, if the previous test's browser was different.
```
I reuse the app if started
```
The app is only restarted if the previous scenario's app was different. In all other cases, the app is reused if possible.

**Note**: *However, use this option with caution since in some rare cases if you have not properly setup your tests you may need to restart the app if the test fails otherwise all other tests may fail too.*
```csharp
[Binding]
public class PageObjectsSteps : AndroidSteps
{
    private MainAndroidPage _mainPage;

    [When(@"I navigate to main page")]
    public void WhenINavigateMainPage()
    {
        _mainPage = App.Create<MainAndroidPage>();
        _mainPage.GoTo();
    }

    [When(@"I transfer item (.*) user name (.*) password (.*)")]
    public void WhenITrasnferItem(string itemName, string userName, string password)
    {
        _mainPage.TransferItem(itemName, userName, password);
    }

    [Then(@"I assert that keep me logged is checked")]
    public void AssertKeepMeLoggedChecked()
    {
        _mainPage.AssertKeepMeLoggedChecked();
    }

    [Then(@"I assert that (.*) user name is set")]
    public void AssertRightUserNameSet(string userName)
    {
        _mainPage.AssertRightUserNameSet(userName);
    }
}
```
To define your SpecFlow steps, create a new class file. It needs to inherit **AndroidSteps** which gives you access to all BELLATRIX services.