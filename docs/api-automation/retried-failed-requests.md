---
layout: default
title:  "Retry Failed Requests"
excerpt: "Learn how to retry failed requests with BELLATRIX API attributes."
date:   2019-05-30 06:50:17 +0200
parent: api-automation
permalink: /api-automation/retry-failed-requests/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
Feature: Make requests to Music Shop
	To get music information
	As a Music Developer 
	I want to be able to get information about the music pieces

Background:
Given I set max retry attempts to 3
And I pause between failures 2 seconds

Scenario: Successfully Get Album By ID
	When I get album by ID = 10
	Then I assert album ID = 10
```

Explanations
------------
```csharp
Given I set max retry attempts to 3
```
Instructs BELLATRIX to retry all failed requests 3 times until they succeed.