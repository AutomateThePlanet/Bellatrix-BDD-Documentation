---
layout: default
title:  "Templates"
excerpt: "Learn how to use pre-built BELLATRIX templates."
date:   2019-05-30 06:50:17 +0200
parent: api-automation
permalink: /api-automation/templates/
anchors:
  create-projects-from-visual-studio: Create Projects from Visual Studio
  create-projects-from-cli: Create Projects from CLI
---
Create Projects from Visual Studio
----------------------------------
You can use built-in Visual Studio templates to create BELLATRIX test projects.
From **File -> New -> Project** you can find all BELLATRIX projects too

![Create New Project Visual Studio](images/create-new-project-visual-studio.png)

![Create Getting Started Visual Studio](images/create-getting-started-solution-visual-studio.png)

Create Projects from CLI
------------------------
You can create an empty tests project with all required files through dotnet CLI
1. Open CMD
2. Using the command "dotnet new -l" you can see all available templates 

Before you can create a new project, you need to install the BELLATRIX template first.

**All available templates:**

- Bellatrix.SpecFlow.Desktop.MSTest.Tests
- Bellatrix.SpecFlow.Web.MSTest.Tests
- Bellatrix.SpecFlow.Android.MSTest.Tests
- Bellatrix.SpecFlow.IOS.MSTest.Tests
- Bellatrix.SpecFlow.API.MSTest.Tests

**Install Template**

```
dotnet new -i Bellatrix.SpecFlow.API.MSTest.Tests
```

**Create Project from Template**
1. Open the folder where you want the files to be placed
2. Open CMD
3. Type the bellow command for the desired template

```
dotnet new Bellatrix.SpecFlow.API.MSTest.Tests
```

![Create Getting Started CLI](images/create-getting-started-console.png)