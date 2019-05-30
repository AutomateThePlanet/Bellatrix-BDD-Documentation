---
layout: default
title:  "Troubleshooting- Video Recording"
excerpt: "Learn how to use BELLATRIX cross-platform video recording."
date:   2018-05-30 06:50:17 +0200
parent: desktop-automation
permalink: /desktop-automation/troubleshooting-video-recording/
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
And I record a video for failed tests
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
Given I record a video for failed tests
```
This is a predefined BELLATRIX SpecFlow step for cross-platform video recording. The engine checks after each test, its result, depending on the specified video saves the video.
All video recording modes:

```
Given I record a video for all tests
```
Records and save video for all tests.
```
Given I record a video for passed tests
```
Saves the videos only for pass tests.
```
Given I record a video for failed tests
```
Saves the videos only for failed tests.
```
Given I record a video for failed tests
```

Configuration
-------------
If you open the **testFrameworkSettings.json** file, you find the **videoRecordingSettings** section that controls this behaviour.
```json
"videoRecordingSettings": {
       "isEnabled": "true",
        "waitAfterFinishRecordingMilliseconds": "500",
        "filePath": "C:\\Troubleshooting\\Videos"
}
```
You can turn off the making of videos for all tests and specify where the videos to be saved. **waitAfterFinishRecordingMilliseconds** adds some time to the end of the test, making the video not going black immediately. In the extensibility chapters read more about how you can create custom video recorder or change the saving strategy.