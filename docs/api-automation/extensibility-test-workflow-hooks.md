---
layout: default
title:  "Extensibility- Test Workflow Hooks"
excerpt: "Learn how to extend the BELLATRIX test workflow using hooks."
date:   2019-05-30 06:50:17 +0200
parent: api-automation
permalink: /api-automation/extensibility-test-workflow-hooks/
anchors:
  example: Example
  explanations: Explanations
---
Example
-------
```csharp
[Binding]
[TestClass]
public class TestsInitialize : APIHooks
{
    private static Process _testApiProcess;

    [BeforeTestRun(Order = 1)]
    public static void PreBeforeTestRun()
    {
        App.UseUnityContainer();
        App.UseMsTestSettings();
        App.UseLogger();
        App.UseExecutionTimeUnderExtensions();
        App.UseApiExtensionsBddLogging();
        App.UseAssertExtensionsBddLogging();
        App.UseLogExecution();
        App.UseRetryFailedRequests();
        App.AssemblyInitialize();
        string workingDir = Path.Combine(ProcessProvider.GetEntryProcessApplicationPath(), "Demos", "TestAPI");
        _testApiProcess = ProcessProvider.StartProcess("dotnet", workingDir, " run", true);
        ProcessProvider.WaitPortToGetBusy(55215);

        InitializeAssemblyTestExecutionBehaviorObservers(TestExecutionProvider);
        InitializeTestExecutionBehaviorObservers(TestExecutionProvider);
        TestExecutionProvider.PreAssemblyInitialize();
    }

    [BeforeTestRun(Order = 100)]
    public static void PostBeforeTestRun()
    {
        TestExecutionProvider.PostAssemblyInitialize();
    }

    [AfterTestRun(Order = 1)]
    public static void PreAfterTestRun()
    {
        ProcessProvider.CloseProcess(_testApiProcess);
    }

    [AfterTestRun(Order = 100)]
    public static void PostAfterTestRun()
    {
        TestExecutionProvider.PreAssemblyCleanup();
    }

    [BeforeFeature(Order = 1)]
    public static void PreBeforeFeatureArrange(FeatureContext featureContext)
    {
        try
        {
            TestExecutionProvider.PreBeforeFeatureArrange(featureContext.FeatureInfo.Title, featureContext.FeatureInfo.Tags.ToList());
        }
        catch (Exception ex)
        {
            TestExecutionProvider.BeforeFeatureFailed(ex);
            throw;
        }
    }

    [BeforeFeature(Order = 100)]
    public static void PostBeforeFeatureArrange(FeatureContext featureContext)
    {
        try
        {
            TestExecutionProvider.PostBeforeFeatureArrange(featureContext.FeatureInfo.Title, featureContext.FeatureInfo.Tags.ToList());
        }
        catch (Exception ex)
        {
            TestExecutionProvider.BeforeFeatureFailed(ex);
            throw;
        }
    }

    [BeforeFeature(Order = 101)]
    public static void PreBeforeFeatureAct(FeatureContext featureContext)
    {
        try
        {
            TestExecutionProvider.PreBeforeFeatureAct(featureContext.FeatureInfo.Title, featureContext.FeatureInfo.Tags.ToList());
        }
        catch (Exception ex)
        {
            TestExecutionProvider.BeforeFeatureFailed(ex);
            throw;
        }
    }

    [BeforeFeature(Order = 200)]
    public static void PostBeforeFeatureAct(FeatureContext featureContext)
    {
        try
        {
            TestExecutionProvider.PostBeforeFeatureAct(featureContext.FeatureInfo.Title, featureContext.FeatureInfo.Tags.ToList());
        }
        catch (Exception ex)
        {
            TestExecutionProvider.BeforeFeatureFailed(ex);
            throw;
        }
    }
}
```

Explanations
------------
One of the greatest features of BELLATRIX is test workflow hooks. It gives you the possibility to execute your logic in every part of the test workflow. Also, as you can read in the next chapter write plug-ins that execute code in different places of the workflow every time. This is happening no matter what test framework you use- MSTest or NUnit. As you know, MSTest is not extension friendly.

BELLATRIX Default Test Workflow.

The following methods are called once for test class:

1. All plug-ins **PreBeforeTestRun** logic executes (PreAssemblyInitialize)
2. Current Project **BeforeTestRun** executes (Order > 1 and < 100)
3. All plug-ins **PostBeforeTestRun** logic executes (PostAssemblyInitialize)
4. All plug-ins **PreBeforeFeatureArrange** logic executes.
5. Current Project **BeforeFeatureArrange** method executes. (Order > 1 and < 100)
6. All plug-ins **PostBeforeFeatureArrange** logic executes.
7. All plug-ins **PreBeforeFeatureAct** logic executes.
8. Current class **BeforeFeatureAct** method executes. (Order > 101 and < 200)
9. All plug-ins **PostBeforeFeatureAct** logic executes.
10. 10.1. In case there is an exception thrown in the BeforeFeature phase **BeforeFeatureFailed** logic of all plug-ins is run.

The following methods are called once for each scenario in the feature file:

11. All plug-ins **PreBeforeScenario** logic executes.
12. Current class **BeforeScenario** method executes. By default it is empty, but you can override it in each class and execute your logic. You can add some logic that is executed for each test instead of copy pasting it for each test. For example- navigating to a specific Android activity.
13. All plug-ins **PostBeforeScenario** logic executes.
14. All plug-ins **PreAfterScenario** logic executes.
15. Current class **AfterScenario** method executes. By default it is empty, but you can override it in each class and execute your logic.
You can add some logic that is executed after each test instead of copy pasting it. For example- deleting some entity from DB.

16. All plug-ins **PreAfterTestRun** logic executes. (PreAssemblyCleanup)
17. Current Project **AfterTestRun** executes (Order > 1 and < 100)
18. All plug-ins **PostAfterTestRun** logic executes (PostAssemblyCleanup)

```csharp
[AfterTestRun(Order = 20)]
public static void AfterTestRun()
{
    // call custom logic
}
```
This is how you can add your own after test run logic. It is important to use the **Order** property.