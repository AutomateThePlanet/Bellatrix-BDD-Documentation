---
layout: default
title:  "Add Custom Appium Options"
excerpt: "Learn how to add custom Appium options."
date:   2019-05-30 06:50:17 +0200
parent: ios-automation
permalink: /ios-automation/add-custom-appium-options/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
[Binding]
public class CustomAndroidSteps : IOSSteps
{
    [Given(@"Add Custom Appium Options")]
    public void AddCustomAppiumOptions()
    {
		App.AddAppiumOptions("locale", "fr_CA");
		App.AddAppiumOptions("language", "fr");
		App.AddAppiumOptions("autoWebview", "true");
		App.AddAppiumOptions("noReset", "false");
    }
}
```

Explanations
------------
```csharp
App.AddAppiumCapability("locale", "fr_CA");
App.AddAppiumCapability("language", "fr");
App.AddAppiumCapability("autoWebview", "true");
App.AddAppiumCapability("noReset", "false");
```
BELLATRIX hides the complexity of initialisation of WebDriver/Appium and all related services. In some cases, you need to customise the set up of a Appium with using custom Appium options. Using the **App** service methods you can add all of these with ease.