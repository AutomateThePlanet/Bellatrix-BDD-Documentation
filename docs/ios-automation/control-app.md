---
layout: default
title:  "Control App"
excerpt: "Learn how to control iOS applications with BELLATRIX iOS module."
date:   2019-05-31 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/control-app/
anchors:
  overview: Overview
  explanations: Explanations
---
Overview
--------

This is how one BELLATRIX feature file looks like.
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
	Then I assert answer is 11
```

Explanations
------------
```
Background:
```
This marks the beginning of a special SpecFlow section which will be executed before each scenario.
```
Background:
Given I use app with path AssemblyFolder/Demos/TestApp.app.zip
And I restart the app on test fail
And I use device with name iPhone 6
And I use iOS version 11.3
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

```
[Binding]
public class PageObjectsSteps : AndroidSteps
{
    private CalculatorPage _calculatorPage;

    [When(@"I sum (.*) and (.*)")]
    public void WhenSumNumbers(int firstNumber, int secondNumber)
    {
        _calculatorPage = App.Create<CalculatorPage>();
        _calculatorPage.Sum(firstNumber, secondNumber);
    }

    [Then(@"I assert answer is (.*)")]
    public void AssertAnswer(int answer)
    {
        _calculatorPage.AssertAnswer(answer);
    }
}
```
To define your SpecFlow steps, create a new class file. It needs to inherit **IOSSteps** which gives you access to all BELLATRIX services.
