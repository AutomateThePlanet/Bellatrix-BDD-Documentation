---
layout: default
title:  "Add Custom WebDriver Capabilities"
excerpt: "Learn how to add custom WebDriver capabilities."
date:   2019-05-30 06:50:17 +0200
parent: desktop-automation
permalink: /desktop-automation/add-custom-webdriver-capabilities/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
[Binding]
public class CustomWebSteps : DesktopSteps
{
    [Given(@"Add Custom Driver Capabilities")]
    public void AddCustomWebDriverCapabilities()
    {
        App.AddWebDriverCapability("appArguments", @"MyTestFile.txt");
        App.AddWebDriverCapability("appWorkingDir", @"C:\MyTestFolder\");
    }
}
```

Explanations
------------
```csharp
App.AddWebDriverCapability("appArguments", @"MyTestFile.txt");
App.AddWebDriverCapability("appWorkingDir", @"C:\MyTestFolder\");
```
BELLATRIX hides the complexity of initialisation of WebDriver and all related services. In some cases, you need to customise the set up of a app with using WebDriver options or adding driver capabilities. Using the **App** service methods you can add all of these with ease. Make sure to call them in a step definition method. Later you can call this step in your feature files. These options are used only for the tests in this particular class.