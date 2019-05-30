---
layout: default
title:  "Behaviour Driven Development BDD Logging"
excerpt: "Learn the BELLATRIX Behaviour Driven Development BDD Logging works and how to use it."
date:   2018-05-30 06:50:17 +0200
parent: api-automation
permalink: /api-automation/bdd-logging/
anchors:
  example: Example
  explanations: Explanations
  configuration: Configuration
---
Example
-------
```
Feature: Make requests to Music Shop
	To get music information
	As a Music Developer 
	I want to be able to get information about the music pieces

Background:
Given I use JSON web token authentication with access token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJiZWxsYXRyaXhVc2VyIiwianRpIjoiNjEyYjIzOTktNDUzMS00NmU0LTg5NjYtN2UxYmRhY2VmZTFlIiwibmJmIjoxNTE4NTI0NDg0LCJleHAiOjE1MjM3MDg0ODQsImlzcyI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSIsImF1ZCI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSJ9.Nq6OXqrK82KSmWNrpcokRIWYrXHanpinrqwbUlKT_cs
And I set max retry attempts to 3
And I pause between failures 2 seconds

Scenario: Successfully Get Album By ID
	When I get album by ID = 10
	Then I assert album ID = 10
```

Explanations
------------
There cases when you need to show your colleagues or managers what tests do you have. Sometimes you may have manual test cases, but their maintenance and up-to-date state are questionable. Also, many times you need additional work to associate the tests with the test cases. Some frameworks give you a way to write human readable tests through the Gherkin language. The main idea is non-technical people to write these tests. However, we believe this approach is doomed. Or it is doable only for simple tests. This is why in BELLATRIX we built a feature that generates the test cases after the tests execution. After each action or assertion, a new entry is logged.

After the tests are executed the following log is created:

```
>Start Test
Class = BDDLoggingTests Name = ContentPopulated_When_GetAlbums
Making GET request against resource api/Albums
Response of request GET against resource api/Albums - Completed
Start Test
Class = BDDLoggingTests Name = ContentPopulated_When_NewAlbumInsertedViaPost
Making GET request against resource api/Genres
Response of request GET against resource api/Genres - Completed
Making POST request against resource api/Genres with parameters application/json={"GenreId":74,"Name":"b6f831d3-42c7-462c-9c8b-4bc0aeb870dc","Tracks":[]}
Response of request POST against resource api/Genres - Completed
```

Configuration
-------------
```json
"logging": {
    "isEnabled": "true",
    "isConsoleLoggingEnabled": "true",
    "isDebugLoggingEnabled": "true",
    "isEventLoggingEnabled": "false",
    "isFileLoggingEnabled": "true",
    "outputTemplate":  "{Message:lj}{NewLine}",
    "addUrlToBddLogging": "false"
}
```
In the **testFrameworkSettings.json** file find a section called logging, responsible for controlling the BDD logs generation. You can disable the logs entirely. There are different places where the logs are populated. By default, you can see the logs in the output window of each test. Also, a file called logs.txt is generated in the folder with the DLLs of your tests. If you execute your tests in CI with some CLI test runner the logs are printed there as well. **outputTemplate** - controls how the message is formatted. You can add additional info such as timestamp and much more.
For more info visit- [https://github.com/serilog/serilog/wiki/Formatting-Output](https://github.com/serilog/serilog/wiki/Formatting-Output)