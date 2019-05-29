---
layout: default
title:  "Troubleshooting- Video Recording"
excerpt: "Learn how to use BELLATRIX cross-platform video recording."
date:   2018-06-22 06:50:17 +0200
parent: web-automation
permalink: /web-automation/troubleshooting-video-recording/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
Feature: CommonServices
	In order to use the browser
	As a automation engineer
	I want BELLATRIX to provide me handy method to do my job

Background: 
Given I use Firefox browser on Windows
And I reuse the browser if started
And I record a video for failed tests
And I open browser

@executiontimeunder-6-seconds
Scenario: Browser Service Common Steps
	When I navigate to URL http://demos.bellatrix.solutions/product/falcon-9/
	And I refresh the browser
	When I wait until the browser is ready
	And I wait for all AJAX requests to finish
	And I maximize the browser
	And I navigate to URL http://demos.bellatrix.solutions/
	And I click browser's back button
	And I click browser's forward button
    And I click browser's back button
	And I wait for partial URL falcon-9
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