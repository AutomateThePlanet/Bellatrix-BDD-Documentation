---
layout: default
title:  "Authentication"
excerpt: "Learn how to authenticate your requests using BELLATRIX API library."
date:   2019-05-30 06:50:17 +0200
parent: api-automation
permalink: /api-automation/authentication/
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
Given I use JSON web token authentication with access token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJiZWxsYXRyaXhVc2VyIiwianRpIjoiNjEyYjIzOTktNDUzMS00NmU0LTg5NjYtN2UxYmRhY2VmZTFlIiwibmJmIjoxNTE4NTI0NDg0LCJleHAiOjE1MjM3MDg0ODQsImlzcyI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSIsImF1ZCI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSJ9.Nq6OXqrK82KSmWNrpcokRIWYrXHanpinrqwbUlKT_cs
And I set max retry attempts to 3
And I pause between failures 2 seconds

Scenario: Successfully Get Album By ID
	When I get album by ID = 10
	Then I assert album ID = 10
```

Explanations
------------
BELLATRIX provides an easy way to authenticate through the usage of few predefined SpecFlow steps.
```csharp
Given I use JSON web token authentication with access token eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJiZWxsYXRyaXhVc2VyIiwianRpIjoiNjEyYjIzOTktNDUzMS00NmU0LTg5NjYtN2UxYmRhY2VmZTFlIiwibmJmIjoxNTE4NTI0NDg0LCJleHAiOjE1MjM3MDg0ODQsImlzcyI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSIsImF1ZCI6ImF1dG9tYXRldGhlcGxhbmV0LmNvbSJ9.Nq6OXqrK82KSmWNrpcokRIWYrXHanpinrqwbUlKT_cs
```
We use [JwtToken authentication]( https://tools.ietf.org/html/draft-ietf-oauth-json-web-token). The attribute accepts your text tocken.
Other authentication strategy attributes:

```csharp
Given I use basic authentication username myUserName password myPass
```
Authenticate through user name and password.
```csharp
Given I use NTLM authentication
```
Authenticate with the credentials of the currently logged in user, or impersonate a user.
```csharp
Given I use OAuth 2 access token yourToken
```
The OAuth 2 authenticator using the authorization request header field.
```csharp
Given I use simple authentication username key (.*) username (.*) password key (.*) password (.*)
```
userKey, user, passwordKey, password.
```csharp
I use OAuth 2 URI access token yourToken
```
The OAuth 2 authenticator using URI query parameter.