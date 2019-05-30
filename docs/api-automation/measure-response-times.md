---
layout: default
title:  "Measure Response Times"
excerpt: "Learn how to measure response times using BELLATRIX API library."
date:   2019-05-30 06:50:17 +0200
parent: api-automation
permalink: /api-automation/measure-response-times/
anchors:
  example: Example
  explanations: Explanations
---
Example
--------
```
Feature: Make requests to Music Shop
	To get music information
	As a Music Developer 
	I want to be able to get information about the music pieces

Background:
Given I use JSON web token authentication with access token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJiZWxsYXRyaXhVc2VyIiwianRpIjoiNjEyYjIzOTktNDUzMS00NmU0LTg5NjYtN2UxYmRhY2VmZTFlIiwibmJmIjoxNTE4NTI0NDg0LCJleHAiOjE1MjM3MDg0ODQsImlzcyI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSIsImF1ZCI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSJ9.Nq6OXqrK82KSmWNrpcokRIWYrXHanpinrqwbUlKT_cs
And I set max retry attempts to 3
And I pause between failures 2 seconds

@executiontimeunder-6-seconds
Scenario: Successfully Get Album By ID
	When I get album by ID = 10
	Then I assert album ID = 10
```

Explanations
------------
```csharp
@executiontimeunder-6-seconds
```
Sometimes it is useful to use your functional tests to measure performance. Or to just make sure that your app is not slow. To do that BELLATRIX libraries offer the **@executiontimeunder** attribute. You specify a timeout and if the test is executed over it the test will fail.