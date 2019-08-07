---
title: Te.exe Command Options
description: Te.exe Command Options
ms.assetid: E9A9292D-FA30-410d-9322-BD0F321314F9
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# <a name="teexe-command-options"></a><span data-ttu-id="4b6d3-103">Te.exe Command Options</span><span class="sxs-lookup"><span data-stu-id="4b6d3-103">Te.exe Command Options</span></span>

## <a name="usage"></a><span data-ttu-id="4b6d3-104">Usage</span><span class="sxs-lookup"><span data-stu-id="4b6d3-104">Usage</span></span>

<span data-ttu-id="4b6d3-105">**te.exe** \<[test\_binaries](#test_binaries)> \[[/appendWttLogging](#appendwttlogging)\] \[[/breakOnCreate](#breakoncreate)\] \[[/breakOnError](#breakonerror)\] \[[/breakOnInvoke](#breakoninvoke)\] \[[/coloredConsoleOutput](#coloredconsoleoutputtruefalse)\] \[ [/console:flushWrites](#consoleflushwrites)\] \[[/console:position=\[x,y | current\]](#consolepositionxy--current-) \[[/console:size=&lt;x,y&gt;\]](#consolesize-xy--current-) \[ [/console:topmost \]](#consoletopmost) [\[/defaultAppDomain\]](#defaultappdomain) \[[/disableConsoleLogging](#disableconsolelogging)\] \[[/disableTimeouts](#disabletimeouts)\] \[[/dpiaware](#dpiaware) \] \[[/enableWttLogging](#enablewttlogging)\] \[[/inproc](#inproc)\] \[[/isolationLevel](#isolationlevellevel)\] \[[/labMode](#labmode)\] \[[/list](#list)\] \[[/listProperties](#listproperties)\] \[[/logFile:&lt;name&gt;](#logfilename)\] \[[/logOutput:&lt;mode&gt;](#logoutputmode)\] \[[/miniDumpOnCrash](#minidumponcrash)\] \[[/miniDumpOnError](#minidumponerror)\] \[[/name:&lt;testname&gt;](#nametestname)\] \[[/outputFolder:&lt;folderName&gt;](#outputfolderfoldername)\] \[[/p:&lt;ParamName&gt;=&lt;ParamValue&gt;](#pparamnameparamvalue)\] \[[/parallel](#parallel)\] \[[/persistPictResults](#persistpictresults)\] \[[/pict:&lt;OptionName&gt;=&lt;OptionValue&gt;](#pictoptionnameoptionvalue)\] [\[/rebootStateFile\]](#rebootstatefile) \[[/reportLoadingIssue](#reportloadingissue)\] \[[/runas:&lt;RunAsType&gt;](#runasrunastype)\] \[[/runIgnoredTests](#runignoredtests)\] \[[/runon:&lt;MachineName&gt;](#runonmachinename)\] \[[/screenCaptureOnError](#screencaptureonerror)\] \[[/select:&lt;query&gt;](#selectquery)\] \[[/sessionTimeout:&lt;value&gt;](#sessiontimeoutvalue)\] \[[/stackFrameCount:&lt;value&gt;](#stackframecountvalue)\] \[[/stackTraceOnError](#stacktraceonerror)\] \[[/terminateOnFirstFailure](#terminateonfirstfailure)\] \[[/testDependencies:&lt;files&gt;](#testdependenciesfiles)\] \[[/testmode:Loop](#testmodeloop)\] \[[/testmode:Stress](#testmodestress)\] \[[/testTimeout:&lt;value&gt;](#testtimeoutvalue)\] \[[/unicodeOutput:&lt;true/false&gt;](#unicodeoutputtruefalse)\] [\[/version\]](#version) \[[/wttDeviceString:&lt;value&gt;](#wttdevicestringvalue)\] \[[/wttDeviceStringSuffix:&lt;value&gt;](#wttdevicestringsuffixvalue)\]</span><span class="sxs-lookup"><span data-stu-id="4b6d3-105">**te.exe** \<[test\_binaries](#test_binaries)> \[[/appendWttLogging](#appendwttlogging)\] \[[/breakOnCreate](#breakoncreate)\] \[[/breakOnError](#breakonerror)\] \[[/breakOnInvoke](#breakoninvoke)\] \[[/coloredConsoleOutput](#coloredconsoleoutputtruefalse)\] \[ [/console:flushWrites](#consoleflushwrites)\] \[[/console:position=\[x,y | current\]](#consolepositionxy--current-) \[[/console:size=&lt;x,y&gt;\]](#consolesize-xy--current-) \[ [/console:topmost \]](#consoletopmost) [\[/defaultAppDomain\]](#defaultappdomain) \[[/disableConsoleLogging](#disableconsolelogging)\] \[[/disableTimeouts](#disabletimeouts)\] \[[/dpiaware](#dpiaware) \] \[[/enableWttLogging](#enablewttlogging)\] \[[/inproc](#inproc)\] \[[/isolationLevel](#isolationlevellevel)\] \[[/labMode](#labmode)\] \[[/list](#list)\] \[[/listProperties](#listproperties)\] \[[/logFile:&lt;name&gt;](#logfilename)\] \[[/logOutput:&lt;mode&gt;](#logoutputmode)\] \[[/miniDumpOnCrash](#minidumponcrash)\] \[[/miniDumpOnError](#minidumponerror)\] \[[/name:&lt;testname&gt;](#nametestname)\] \[[/outputFolder:&lt;folderName&gt;](#outputfolderfoldername)\] \[[/p:&lt;ParamName&gt;=&lt;ParamValue&gt;](#pparamnameparamvalue)\] \[[/parallel](#parallel)\] \[[/persistPictResults](#persistpictresults)\] \[[/pict:&lt;OptionName&gt;=&lt;OptionValue&gt;](#pictoptionnameoptionvalue)\] [\[/rebootStateFile\]](#rebootstatefile) \[[/reportLoadingIssue](#reportloadingissue)\] \[[/runas:&lt;RunAsType&gt;](#runasrunastype)\] \[[/runIgnoredTests](#runignoredtests)\] \[[/runon:&lt;MachineName&gt;](#runonmachinename)\] \[[/screenCaptureOnError](#screencaptureonerror)\] \[[/select:&lt;query&gt;](#selectquery)\] \[[/sessionTimeout:&lt;value&gt;](#sessiontimeoutvalue)\] \[[/stackFrameCount:&lt;value&gt;](#stackframecountvalue)\] \[[/stackTraceOnError](#stacktraceonerror)\] \[[/terminateOnFirstFailure](#terminateonfirstfailure)\] \[[/testDependencies:&lt;files&gt;](#testdependenciesfiles)\] \[[/testmode:Loop](#testmodeloop)\] \[[/testmode:Stress](#testmodestress)\] \[[/testTimeout:&lt;value&gt;](#testtimeoutvalue)\] \[[/unicodeOutput:&lt;true/false&gt;](#unicodeoutputtruefalse)\] [\[/version\]](#version) \[[/wttDeviceString:&lt;value&gt;](#wttdevicestringvalue)\] \[[/wttDeviceStringSuffix:&lt;value&gt;](#wttdevicestringsuffixvalue)\]</span></span>

## <a name="selectionexecution-commands"></a><span data-ttu-id="4b6d3-106">Selection/Execution Commands</span><span class="sxs-lookup"><span data-stu-id="4b6d3-106">Selection/Execution Commands</span></span>

### <a name="test_binaries"></a><span data-ttu-id="4b6d3-107">test_binaries</span><span class="sxs-lookup"><span data-stu-id="4b6d3-107">test_binaries</span></span>

<span data-ttu-id="4b6d3-108">Specify one or more test files to execute (separated by spaces).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-108">Specify one or more test files to execute (separated by spaces).</span></span> <span data-ttu-id="4b6d3-109">Wildcard characters are supported.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-109">Wildcard characters are supported.</span></span>

#### <a name="teexe-test1dll"></a><span data-ttu-id="4b6d3-110">te.exe test1.dll</span><span class="sxs-lookup"><span data-stu-id="4b6d3-110">te.exe test1.dll</span></span>

<span data-ttu-id="4b6d3-111">**Interpretation:** Run all tests in test1.dll.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-111">**Interpretation:** Run all tests in test1.dll.</span></span>

#### <a name="teexe-test1dll-test2dll-test3dll"></a><span data-ttu-id="4b6d3-112">te.exe test1.dll test2.dll test3.dll</span><span class="sxs-lookup"><span data-stu-id="4b6d3-112">te.exe test1.dll test2.dll test3.dll</span></span>

<span data-ttu-id="4b6d3-113">**Interpretation:** Run all tests in test1.dll, test2.dll and test3.dll.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-113">**Interpretation:** Run all tests in test1.dll, test2.dll and test3.dll.</span></span>

#### <a name="teexe-dll"></a><span data-ttu-id="4b6d3-114">te.exe \*.dll</span><span class="sxs-lookup"><span data-stu-id="4b6d3-114">te.exe \*.dll</span></span>

<span data-ttu-id="4b6d3-115">**Interpretation:** Run all tests in all dlls in the current directory.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-115">**Interpretation:** Run all tests in all dlls in the current directory.</span></span>

### <a name="coloredconsoleoutputtruefalse"></a><span data-ttu-id="4b6d3-116">/coloredConsoleOutput:\<true/false></span><span class="sxs-lookup"><span data-stu-id="4b6d3-116">/coloredConsoleOutput:\<true/false></span></span>

<span data-ttu-id="4b6d3-117">Specifies whether or not TAEF should output colored console text.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-117">Specifies whether or not TAEF should output colored console text.</span></span> <span data-ttu-id="4b6d3-118">The default is true.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-118">The default is true.</span></span> <span data-ttu-id="4b6d3-119">If set to false, TAEF will output all text with the default console color.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-119">If set to false, TAEF will output all text with the default console color.</span></span>

`te.exe test1.dll /coloredConsoleOutput:false`

### <a name="consoleoptionnamevalue"></a><span data-ttu-id="4b6d3-120">/console:\<optionName>=\<value></span><span class="sxs-lookup"><span data-stu-id="4b6d3-120">/console:\<optionName>=\<value></span></span>

<span data-ttu-id="4b6d3-121">Provides options for configuring TE's use of the console.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-121">Provides options for configuring TE's use of the console.</span></span> <span data-ttu-id="4b6d3-122">The following options are available:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-122">The following options are available:</span></span>

#### <a name="consoleflushwrites"></a><span data-ttu-id="4b6d3-123">/console:flushWrites</span><span class="sxs-lookup"><span data-stu-id="4b6d3-123">/console:flushWrites</span></span>

<span data-ttu-id="4b6d3-124">Causes console output to be flushed after every line is written - useful when TE.exe's output has been redirected.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-124">Causes console output to be flushed after every line is written - useful when TE.exe's output has been redirected.</span></span>

#### <a name="consolepositionxy--current-"></a><span data-ttu-id="4b6d3-125">/console:position=\[x,y | current \]</span><span class="sxs-lookup"><span data-stu-id="4b6d3-125">/console:position=\[x,y | current \]</span></span>

<span data-ttu-id="4b6d3-126">Sets the position (in pixels) of the console window relative to the corner of the primary monitor.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-126">Sets the position (in pixels) of the console window relative to the corner of the primary monitor.</span></span> <span data-ttu-id="4b6d3-127">Use a value of **current** to specify that the current console position should be stored and used when resuming from reboot.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-127">Use a value of **current** to specify that the current console position should be stored and used when resuming from reboot.</span></span>

#### <a name="consolesize-ltxygt--current-"></a><span data-ttu-id="4b6d3-128">/console:size=\[ &lt;x,y&gt; | current \]</span><span class="sxs-lookup"><span data-stu-id="4b6d3-128">/console:size=\[ &lt;x,y&gt; | current \]</span></span>

<span data-ttu-id="4b6d3-129">Sets the size of the console window (in character dimensions).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-129">Sets the size of the console window (in character dimensions).</span></span> <span data-ttu-id="4b6d3-130">The screen buffer size will be increased to match the size of the window if necessary.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-130">The screen buffer size will be increased to match the size of the window if necessary.</span></span> <span data-ttu-id="4b6d3-131">Use a value of **current** to specify that the current console size should be stored and used when resuming from reboot.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-131">Use a value of **current** to specify that the current console size should be stored and used when resuming from reboot.</span></span>

#### <a name="consoletopmost"></a><span data-ttu-id="4b6d3-132">/console:topmost</span><span class="sxs-lookup"><span data-stu-id="4b6d3-132">/console:topmost</span></span>

<span data-ttu-id="4b6d3-133">Keeps the console running te.exe 'topmost' in the desktop z-order for the duration of execution.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-133">Keeps the console running te.exe 'topmost' in the desktop z-order for the duration of execution.</span></span>

### <a name="dpiaware"></a><span data-ttu-id="4b6d3-134">/dpiaware</span><span class="sxs-lookup"><span data-stu-id="4b6d3-134">/dpiaware</span></span>

<span data-ttu-id="4b6d3-135">Executes tests in a process marked as DPI-aware, see [High DPI](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-135">Executes tests in a process marked as DPI-aware, see [High DPI](https://docs.microsoft.com/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span> <span data-ttu-id="4b6d3-136">This can also be set via metadata ("DpiAware").</span><span class="sxs-lookup"><span data-stu-id="4b6d3-136">This can also be set via metadata ("DpiAware").</span></span>

### <a name="inproc"></a><span data-ttu-id="4b6d3-137">/inproc</span><span class="sxs-lookup"><span data-stu-id="4b6d3-137">/inproc</span></span>

<span data-ttu-id="4b6d3-138">Execute all tests within the TE.exe process itself rather than within TE.ProcessHost.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-138">Execute all tests within the TE.exe process itself rather than within TE.ProcessHost.exe.</span></span>

<span data-ttu-id="4b6d3-139">te.exe test1.dll /inproc</span><span class="sxs-lookup"><span data-stu-id="4b6d3-139">te.exe test1.dll /inproc</span></span>

> [!NOTE]
> <span data-ttu-id="4b6d3-140">TE only supports executing one test dll at a time when using the */inproc* setting.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-140">TE only supports executing one test dll at a time when using the */inproc* setting.</span></span>

### <a name="isolationlevellevel"></a><span data-ttu-id="4b6d3-141">/isolationLevel:\<Level></span><span class="sxs-lookup"><span data-stu-id="4b6d3-141">/isolationLevel:\<Level></span></span>

<span data-ttu-id="4b6d3-142">Specifies the minimum level of isolation to be used when executing TAEF tests.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-142">Specifies the minimum level of isolation to be used when executing TAEF tests.</span></span> <span data-ttu-id="4b6d3-143">If this value conflicts with the IsolationLevel specified as metadata, the value becomes the isolation level with the tightest scope.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-143">If this value conflicts with the IsolationLevel specified as metadata, the value becomes the isolation level with the tightest scope.</span></span> <span data-ttu-id="4b6d3-144">See [Test Isolation](test-isolation.md) for more details.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-144">See [Test Isolation](test-isolation.md) for more details.</span></span>

`te.exe test1.dll /isolationLevel:Class`

### <a name="labmode"></a><span data-ttu-id="4b6d3-145">/labMode</span><span class="sxs-lookup"><span data-stu-id="4b6d3-145">/labMode</span></span>

<span data-ttu-id="4b6d3-146">Executes tests and removes potential blocking UI (for example, Windows Error Reporting dialogs on crashing tests).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-146">Executes tests and removes potential blocking UI (for example, Windows Error Reporting dialogs on crashing tests).</span></span>

### <a name="list"></a><span data-ttu-id="4b6d3-147">/list</span><span class="sxs-lookup"><span data-stu-id="4b6d3-147">/list</span></span>

<span data-ttu-id="4b6d3-148">Lists the names of all the [test\_binaries](#test_binaries) and the classes and methods within them.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-148">Lists the names of all the [test\_binaries](#test_binaries) and the classes and methods within them.</span></span> <span data-ttu-id="4b6d3-149">If selection criteria is specified, lists only the names of those which meet the criteria.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-149">If selection criteria is specified, lists only the names of those which meet the criteria.</span></span>

```cpp
 te.exe test1.dll test2.dll /list

 WEX::UnitTests::Test1
  WEX::UnitTests::Test1::Example1
  WEX::UnitTests::Test1::Example2
  WEX::UnitTests::Test1::Example3

 WEX::UnitTests::Test2
  WEX::UnitTests::Test2::Example1
  WEX::UnitTests::Test2::Example2
  WEX::UnitTests::Test2::Example3
```

```cpp
 te.exe test1.dll test2.dll /select:@name='*Example2*' /list

 WEX::UnitTests::Test1
  WEX::UnitTests::Test1::Example2

 WEX: :UnitTests::Test2
  WEX::UnitTests::Test2::Example2
```

### <a name="listproperties"></a><span data-ttu-id="4b6d3-150">/listProperties</span><span class="sxs-lookup"><span data-stu-id="4b6d3-150">/listProperties</span></span>

<span data-ttu-id="4b6d3-151">Lists the names and properties of all the test\_binaries and the classes and methods in them along with Setup and Teardown function names, if available.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-151">Lists the names and properties of all the test\_binaries and the classes and methods in them along with Setup and Teardown function names, if available.</span></span> <span data-ttu-id="4b6d3-152">If selection criteria is specified, lists only the names of those which meet the criteria.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-152">If selection criteria is specified, lists only the names of those which meet the criteria.</span></span>

```cpp
 te.exe test1.dll test2.dll /listProperties

 WEX::UnitTests::Test1
  WEX::UnitTests::Test1::Example1
   Setup: Test1Setup
   Teardown: Test1Teardown
   Property[ThreadingModel] = MTA
  WEX::UnitTests::Test1::Example2
   Setup: Test1Setup
   Teardown: Test1Teardown
   Property[ThreadingModel] = STA
  WEX::UnitTests::Test1::Example3
   Setup: Test1Setup
   Teardown: Test1Teardown
   Property[ThreadingModel] = STA

 WEX::UnitTests::Test2
  WEX::UnitTests::Test2::Example1
   Property[ThreadingModel] = MTA
  WEX::UnitTests::Test2::Example2
   Property[ThreadingModel] = STA
  WEX::UnitTests::Test2::Example3
   Property[ThreadingModel] = MTA
```

```cpp
 te.exe test1.dll test2.dll /select:@name='*Example2*' /listProperties

 WEX::UnitTests::Test1
  WEX::UnitTests::Test1::Example2
   Setup: Test1Setup
   Teardown: Test1Teardown
   Property[ThreadingModel] = STA

 WEX::UnitTests::Test2
  WEX::UnitTests::Test2::Example2
   Property[ThreadingModel] = STA
```

### <a name="nametestname"></a><span data-ttu-id="4b6d3-153">/name:\<testname></span><span class="sxs-lookup"><span data-stu-id="4b6d3-153">/name:\<testname></span></span>

<span data-ttu-id="4b6d3-154">Test name based selection is an easy alternative to "/select:@Name='&lt;testname&gt;'".</span><span class="sxs-lookup"><span data-stu-id="4b6d3-154">Test name based selection is an easy alternative to "/select:@Name='&lt;testname&gt;'".</span></span> <span data-ttu-id="4b6d3-155">The &lt;testname&gt; can still contain wildcard characters ("\*" and "?"), but should not be contained within single quotes.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-155">The &lt;testname&gt; can still contain wildcard characters ("\*" and "?"), but should not be contained within single quotes.</span></span> <span data-ttu-id="4b6d3-156">If /select and /name both are specified at the command prompt, then /select query takes precedence and /name is ignored.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-156">If /select and /name both are specified at the command prompt, then /select query takes precedence and /name is ignored.</span></span>

<span data-ttu-id="4b6d3-157">te.exe test1.dll /name:\*TestToLower</span><span class="sxs-lookup"><span data-stu-id="4b6d3-157">te.exe test1.dll /name:\*TestToLower</span></span>  

<span data-ttu-id="4b6d3-158">**Interpretation:** Run all tests in test1.dll where method names end with 'TestToLower'.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-158">**Interpretation:** Run all tests in test1.dll where method names end with 'TestToLower'.</span></span> <span data-ttu-id="4b6d3-159">The same can be represented using selection criteria as /select:@Name='\*TestToLower'.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-159">The same can be represented using selection criteria as /select:@Name='\*TestToLower'.</span></span>

<span data-ttu-id="4b6d3-160">te.exe test1.dll /name:\*StringTest\*</span><span class="sxs-lookup"><span data-stu-id="4b6d3-160">te.exe test1.dll /name:\*StringTest\*</span></span>  

<span data-ttu-id="4b6d3-161">**Interpretation:** Run all tests in test1.dll which contain the phrase 'StringTest' in their namespace, class or method name.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-161">**Interpretation:** Run all tests in test1.dll which contain the phrase 'StringTest' in their namespace, class or method name.</span></span>

### <a name="outputfolderfoldername"></a><span data-ttu-id="4b6d3-162">/outputFolder:\<folderName></span><span class="sxs-lookup"><span data-stu-id="4b6d3-162">/outputFolder:\<folderName></span></span>

<span data-ttu-id="4b6d3-163">Specifies a folder to place all generated files.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-163">Specifies a folder to place all generated files.</span></span> <span data-ttu-id="4b6d3-164">The default is the current directory.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-164">The default is the current directory.</span></span> <span data-ttu-id="4b6d3-165">You can use environment variables, for example:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-165">You can use environment variables, for example:</span></span>

`te.exe test1.dll /outputFolder:%TEMP%\\MyOutput`

### <a name="pparamnameparamvalue"></a><span data-ttu-id="4b6d3-166">/p:\<ParamName>=\<ParamValue></span><span class="sxs-lookup"><span data-stu-id="4b6d3-166">/p:\<ParamName>=\<ParamValue></span></span>

<span data-ttu-id="4b6d3-167">Defines a runtime parameter with parameter name=ParamName and parameter value=ParamValue.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-167">Defines a runtime parameter with parameter name=ParamName and parameter value=ParamValue.</span></span> <span data-ttu-id="4b6d3-168">These parameters are accessible from a test method or setup/cleanup methods.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-168">These parameters are accessible from a test method or setup/cleanup methods.</span></span>

`te.exe test1.dll /p:x=5 /p:myParm=cool`

<span data-ttu-id="4b6d3-169">You can grab x as one of several supported types in your test code.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-169">You can grab x as one of several supported types in your test code.</span></span> <span data-ttu-id="4b6d3-170">For example, here you can see us retrieving it as both an int and a WEX::Common::String:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-170">For example, here you can see us retrieving it as both an int and a WEX::Common::String:</span></span>

```cpp
                int x = 0;
                String xString;
                RuntimeParameters::TryGetValue(L"x", x);
                RuntimeParameters::TryGetValue(L"x", xString);
```

<span data-ttu-id="4b6d3-171">For more information, please visit the [TAEF.Runtime Parameters](runtime-parameters.md) help page.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-171">For more information, please visit the [TAEF.Runtime Parameters](runtime-parameters.md) help page.</span></span>

### <a name="parallel"></a><span data-ttu-id="4b6d3-172">/parallel</span><span class="sxs-lookup"><span data-stu-id="4b6d3-172">/parallel</span></span>

<span data-ttu-id="4b6d3-173">Executes tests in parallel across multiple processors.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-173">Executes tests in parallel across multiple processors.</span></span> <span data-ttu-id="4b6d3-174">Tests must opt-in to parallel execution by being marked with the 'Parallel' metadata.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-174">Tests must opt-in to parallel execution by being marked with the 'Parallel' metadata.</span></span>

`te.exe test1.dll /parallel`

<span data-ttu-id="4b6d3-175">For more information, please visit the [Parallel](parallel.md) help page.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-175">For more information, please visit the [Parallel](parallel.md) help page.</span></span>

### <a name="persistpictresults"></a><span data-ttu-id="4b6d3-176">/persistPictResults</span><span class="sxs-lookup"><span data-stu-id="4b6d3-176">/persistPictResults</span></span>

<span data-ttu-id="4b6d3-177">Caches results generated by PICT.exe for tests using [PICT DataSource](pict-data-source.md) in the current execution.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-177">Caches results generated by PICT.exe for tests using [PICT DataSource](pict-data-source.md) in the current execution.</span></span> <span data-ttu-id="4b6d3-178">The subsequent test execution will try to utilize the cached results as against running PICT.exe against the same model and seed files.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-178">The subsequent test execution will try to utilize the cached results as against running PICT.exe against the same model and seed files.</span></span>

### <a name="pictoptionnameoptionvalue"></a><span data-ttu-id="4b6d3-179">/pict:\<OptionName>=\<OptionValue></span><span class="sxs-lookup"><span data-stu-id="4b6d3-179">/pict:\<OptionName>=\<OptionValue></span></span>

<span data-ttu-id="4b6d3-180">Provides options for controlling PICT.exe when it is called for tests using a [PICT DataSource](pict-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-180">Provides options for controlling PICT.exe when it is called for tests using a [PICT DataSource](pict-data-source.md).</span></span> <span data-ttu-id="4b6d3-181">Setting one of these options currently overrides all associated metadata in the code.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-181">Setting one of these options currently overrides all associated metadata in the code.</span></span> <span data-ttu-id="4b6d3-182">The following options are available:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-182">The following options are available:</span></span>

<span data-ttu-id="4b6d3-183">/Pict:Order=3</span><span class="sxs-lookup"><span data-stu-id="4b6d3-183">/Pict:Order=3</span></span>  
<span data-ttu-id="4b6d3-184">Sets the order of combinations by passing the value via the /o command option for PICT.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-184">Sets the order of combinations by passing the value via the /o command option for PICT.exe.</span></span>

<span data-ttu-id="4b6d3-185">/Pict:ValueSeparator=;</span><span class="sxs-lookup"><span data-stu-id="4b6d3-185">/Pict:ValueSeparator=;</span></span>  
<span data-ttu-id="4b6d3-186">Sets the value separator by passing the value via the /d command option for PICT.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-186">Sets the value separator by passing the value via the /d command option for PICT.exe.</span></span>

<span data-ttu-id="4b6d3-187">/Pict:AliasSeparator=+</span><span class="sxs-lookup"><span data-stu-id="4b6d3-187">/Pict:AliasSeparator=+</span></span>  
<span data-ttu-id="4b6d3-188">Sets the alias separator by passing the value via the /a command option for PICT.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-188">Sets the alias separator by passing the value via the /a command option for PICT.exe.</span></span>

<span data-ttu-id="4b6d3-189">Pict:NegativeValuePrefix=!</span><span class="sxs-lookup"><span data-stu-id="4b6d3-189">Pict:NegativeValuePrefix=!</span></span>  
<span data-ttu-id="4b6d3-190">Sets the negative value prefix by passing the value via the /n command option for PICT.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-190">Sets the negative value prefix by passing the value via the /n command option for PICT.exe.</span></span>

<span data-ttu-id="4b6d3-191">/Pict:SeedingFile=test.seed</span><span class="sxs-lookup"><span data-stu-id="4b6d3-191">/Pict:SeedingFile=test.seed</span></span>  
<span data-ttu-id="4b6d3-192">Sets the path to the seeding file by passing the value via the /e command option for PICT.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-192">Sets the path to the seeding file by passing the value via the /e command option for PICT.exe.</span></span>

<span data-ttu-id="4b6d3-193">/Pict:Random=true</span><span class="sxs-lookup"><span data-stu-id="4b6d3-193">/Pict:Random=true</span></span>  
<span data-ttu-id="4b6d3-194">Turns on or off randomness in the PICT results and makes the PICT data source log the random seed that was used.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-194">Turns on or off randomness in the PICT results and makes the PICT data source log the random seed that was used.</span></span>

<span data-ttu-id="4b6d3-195">/Pict:RandomSeed=33</span><span class="sxs-lookup"><span data-stu-id="4b6d3-195">/Pict:RandomSeed=33</span></span>  
<span data-ttu-id="4b6d3-196">Sets the random seed by passing the value via the /r command option for PICT.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-196">Sets the random seed by passing the value via the /r command option for PICT.exe.</span></span> <span data-ttu-id="4b6d3-197">Setting this will turn on Pict:Random unless Pict:Random is explicitly set to false.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-197">Setting this will turn on Pict:Random unless Pict:Random is explicitly set to false.</span></span>

<span data-ttu-id="4b6d3-198">/Pict:CaseSensitive=true</span><span class="sxs-lookup"><span data-stu-id="4b6d3-198">/Pict:CaseSensitive=true</span></span>  
<span data-ttu-id="4b6d3-199">When set to true, turns on case sensitivity by passing the /c command option to PICT.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-199">When set to true, turns on case sensitivity by passing the /c command option to PICT.exe.</span></span>

<span data-ttu-id="4b6d3-200">/Pict:Timeout=00:01:30</span><span class="sxs-lookup"><span data-stu-id="4b6d3-200">/Pict:Timeout=00:01:30</span></span>  
<span data-ttu-id="4b6d3-201">Sets the time to wait for PICT.exe to finish before killing its process.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-201">Sets the time to wait for PICT.exe to finish before killing its process.</span></span> <span data-ttu-id="4b6d3-202">The value is in the format \[Day.\]Hour\[:Minute\[:Second\[.FractionalSeconds\]\]\].</span><span class="sxs-lookup"><span data-stu-id="4b6d3-202">The value is in the format \[Day.\]Hour\[:Minute\[:Second\[.FractionalSeconds\]\]\].</span></span>

### <a name="runasrunastype"></a><span data-ttu-id="4b6d3-203">/runas:\<RunAsType></span><span class="sxs-lookup"><span data-stu-id="4b6d3-203">/runas:\<RunAsType></span></span>

<span data-ttu-id="4b6d3-204">Executes tests in specified environment.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-204">Executes tests in specified environment.</span></span> <span data-ttu-id="4b6d3-205">Please refer to the [RunAs](runas.md) documentation for detailed usage information.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-205">Please refer to the [RunAs](runas.md) documentation for detailed usage information.</span></span>

<span data-ttu-id="4b6d3-206">te.exe \*.dll /runas:System</span><span class="sxs-lookup"><span data-stu-id="4b6d3-206">te.exe \*.dll /runas:System</span></span>  

<span data-ttu-id="4b6d3-207">**Interpretation:** Run all tests as System.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-207">**Interpretation:** Run all tests as System.</span></span>

<span data-ttu-id="4b6d3-208">te.exe \*.dll /runas:Elevated</span><span class="sxs-lookup"><span data-stu-id="4b6d3-208">te.exe \*.dll /runas:Elevated</span></span>  

<span data-ttu-id="4b6d3-209">**Interpretation:** Run all tests as an elevated user.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-209">**Interpretation:** Run all tests as an elevated user.</span></span>

<span data-ttu-id="4b6d3-210">te.exe \*.dll /runas:Restricted</span><span class="sxs-lookup"><span data-stu-id="4b6d3-210">te.exe \*.dll /runas:Restricted</span></span>  

<span data-ttu-id="4b6d3-211">**Interpretation:** Run all tests as a non-elevated user.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-211">**Interpretation:** Run all tests as a non-elevated user.</span></span>

<span data-ttu-id="4b6d3-212">te.exe \*.dll /runas:LowIL</span><span class="sxs-lookup"><span data-stu-id="4b6d3-212">te.exe \*.dll /runas:LowIL</span></span>  

<span data-ttu-id="4b6d3-213">**Interpretation:** Run all tests in a Low Integrity process.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-213">**Interpretation:** Run all tests in a Low Integrity process.</span></span>

### <a name="runignoredtests"></a><span data-ttu-id="4b6d3-214">/runIgnoredTests</span><span class="sxs-lookup"><span data-stu-id="4b6d3-214">/runIgnoredTests</span></span>

<span data-ttu-id="4b6d3-215">Executes or lists (if in conjunction with [/list](#list) or [/listProperties](#listproperties)) all tests, including test classes and test methods with "Ignore" metadata set to "true".</span><span class="sxs-lookup"><span data-stu-id="4b6d3-215">Executes or lists (if in conjunction with [/list](#list) or [/listProperties](#listproperties)) all tests, including test classes and test methods with "Ignore" metadata set to "true".</span></span> <span data-ttu-id="4b6d3-216">By default test classes and test methods with "Ignore" metadata set to "true" are skipped during execution and while listing.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-216">By default test classes and test methods with "Ignore" metadata set to "true" are skipped during execution and while listing.</span></span>

### <a name="runonmachinename"></a><span data-ttu-id="4b6d3-217">/runon:\<MachineName></span><span class="sxs-lookup"><span data-stu-id="4b6d3-217">/runon:\<MachineName></span></span>

<span data-ttu-id="4b6d3-218">Executes tests remotely, on the specified machine.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-218">Executes tests remotely, on the specified machine.</span></span> <span data-ttu-id="4b6d3-219">TAEF authenticates, authorizes and deploys the necessary binaries to execute the tests, and logs all information back to the originating console.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-219">TAEF authenticates, authorizes and deploys the necessary binaries to execute the tests, and logs all information back to the originating console.</span></span> <span data-ttu-id="4b6d3-220">Please refer to the [Cross Machine Test Execution](cross-machine-execution.md) documentation for detailed usage information.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-220">Please refer to the [Cross Machine Test Execution](cross-machine-execution.md) documentation for detailed usage information.</span></span>

<span data-ttu-id="4b6d3-221">te.exe \*.dll /runon:TestMachine1</span><span class="sxs-lookup"><span data-stu-id="4b6d3-221">te.exe \*.dll /runon:TestMachine1</span></span>

<span data-ttu-id="4b6d3-222">**Interpretation:** Run all tests remotely on "TestMachine1".</span><span class="sxs-lookup"><span data-stu-id="4b6d3-222">**Interpretation:** Run all tests remotely on "TestMachine1".</span></span>

### <a name="selectquery"></a><span data-ttu-id="4b6d3-223">/select:\<query></span><span class="sxs-lookup"><span data-stu-id="4b6d3-223">/select:\<query></span></span>

<span data-ttu-id="4b6d3-224">The selection criteria to be used when selecting tests from each test binary.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-224">The selection criteria to be used when selecting tests from each test binary.</span></span> <span data-ttu-id="4b6d3-225">Selection criteria is composed of one or more of the following:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-225">Selection criteria is composed of one or more of the following:</span></span>

<span data-ttu-id="4b6d3-226">@\[property name\] = \[value as string\]
@\[property name\] &gt;= \[value as float or integer\]
@\[property name\] &gt; \[value as float or integer\]
@\[property name\] &lt;= \[value as float or integer\]
@\[property name\] &lt; \[value as float or integer\]</span><span class="sxs-lookup"><span data-stu-id="4b6d3-226">@\[property name\] = \[value as string\]
@\[property name\] &gt;= \[value as float or integer\]
@\[property name\] &gt; \[value as float or integer\]
@\[property name\] &lt;= \[value as float or integer\]
@\[property name\] &lt; \[value as float or integer\]</span></span>

* <span data-ttu-id="4b6d3-227">*Property values as strings must be within single quotes.*</span><span class="sxs-lookup"><span data-stu-id="4b6d3-227">*Property values as strings must be within single quotes.*</span></span>
* <span data-ttu-id="4b6d3-228">*You can specify a composite selection criteria using "and", "or" and "not" (case insensitive).*</span><span class="sxs-lookup"><span data-stu-id="4b6d3-228">*You can specify a composite selection criteria using "and", "or" and "not" (case insensitive).*</span></span>
* <span data-ttu-id="4b6d3-229">*Property string values support wildcard characters via "\*" and "?" characters.*</span><span class="sxs-lookup"><span data-stu-id="4b6d3-229">*Property string values support wildcard characters via "\*" and "?" characters.*</span></span>
* <span data-ttu-id="4b6d3-230">*For float and integer values, the "\*" character may also be used as 'exists', but may not be used for partial matching.*</span><span class="sxs-lookup"><span data-stu-id="4b6d3-230">*For float and integer values, the "\*" character may also be used as 'exists', but may not be used for partial matching.*</span></span> <span data-ttu-id="4b6d3-231">For example: **/select:"@Priority=\*"** is valid, but **/select:"@Priority=4\*"** is not.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-231">For example: **/select:"@Priority=\*"** is valid, but **/select:"@Priority=4\*"** is not.</span></span>

<span data-ttu-id="4b6d3-232">te.exe test1.dll /select:"(@Name='\*TestToLower' or @Owner='C2') and not(@Priority &lt; 3)"</span><span class="sxs-lookup"><span data-stu-id="4b6d3-232">te.exe test1.dll /select:"(@Name='\*TestToLower' or @Owner='C2') and not(@Priority &lt; 3)"</span></span>

<span data-ttu-id="4b6d3-233">**Interpretation:** Run all tests in test1.dll where method names end with 'TestToLower' or where owner is 'C2'; and where Priority is not less than 3.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-233">**Interpretation:** Run all tests in test1.dll where method names end with 'TestToLower' or where owner is 'C2'; and where Priority is not less than 3.</span></span>

<span data-ttu-id="4b6d3-234">te.exe test1.dll test2.dll /select:@Priority=\*</span><span class="sxs-lookup"><span data-stu-id="4b6d3-234">te.exe test1.dll test2.dll /select:@Priority=\*</span></span>

<span data-ttu-id="4b6d3-235">**Interpretation:** Run all tests in test1.dll and test2.dll where the Priority has been specified in their test metadata.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-235">**Interpretation:** Run all tests in test1.dll and test2.dll where the Priority has been specified in their test metadata.</span></span>

<span data-ttu-id="4b6d3-236">te.exe test1.dll /select:@Name='\*StringTest\*'</span><span class="sxs-lookup"><span data-stu-id="4b6d3-236">te.exe test1.dll /select:@Name='\*StringTest\*'</span></span>  

<span data-ttu-id="4b6d3-237">**Interpretation:** Run all tests in test1.dll which contain the phrase 'StringTest' in their namespace, class or method name.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-237">**Interpretation:** Run all tests in test1.dll which contain the phrase 'StringTest' in their namespace, class or method name.</span></span>

### <a name="sessiontimeoutvalue"></a><span data-ttu-id="4b6d3-238">/sessionTimeout:\<value></span><span class="sxs-lookup"><span data-stu-id="4b6d3-238">/sessionTimeout:\<value></span></span>

<span data-ttu-id="4b6d3-239">Sets a session time-out for the entire execution of Te.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-239">Sets a session time-out for the entire execution of Te.exe.</span></span> <span data-ttu-id="4b6d3-240">If the time-out expires, the test session will be gracefully aborted, and the process exit code will signify that a time-out occurred.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-240">If the time-out expires, the test session will be gracefully aborted, and the process exit code will signify that a time-out occurred.</span></span>

> [!NOTE]
> <span data-ttu-id="4b6d3-241">The time-out value must be specified in the following format:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-241">The time-out value must be specified in the following format:</span></span>

```cpp
[Day.]Hour[:Minute[:Second[.FractionalSeconds]]]
```

> [!NOTE]
> <span data-ttu-id="4b6d3-242">If running under WTT, this value can be used to ensure that the Wtt log file remains intact even if the TAEF session times out.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-242">If running under WTT, this value can be used to ensure that the Wtt log file remains intact even if the TAEF session times out.</span></span>

<span data-ttu-id="4b6d3-243">te.exe test1.dll /sessionTimeout:0:0:0.5</span><span class="sxs-lookup"><span data-stu-id="4b6d3-243">te.exe test1.dll /sessionTimeout:0:0:0.5</span></span>  

<span data-ttu-id="4b6d3-244">The entire test session will time out after .5 seconds.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-244">The entire test session will time out after .5 seconds.</span></span>

<span data-ttu-id="4b6d3-245">te.exe test1.dll /sessionTimeout:0:0:45</span><span class="sxs-lookup"><span data-stu-id="4b6d3-245">te.exe test1.dll /sessionTimeout:0:0:45</span></span>  

<span data-ttu-id="4b6d3-246">The entire test session will time out after 45 seconds.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-246">The entire test session will time out after 45 seconds.</span></span>

<span data-ttu-id="4b6d3-247">te.exe test1.dll /sessionTimeout:0:20</span><span class="sxs-lookup"><span data-stu-id="4b6d3-247">te.exe test1.dll /sessionTimeout:0:20</span></span>  

<span data-ttu-id="4b6d3-248">The entire test session will time out after 20 minutes.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-248">The entire test session will time out after 20 minutes.</span></span>

<span data-ttu-id="4b6d3-249">te.exe test1.dll /sessionTimeout:5</span><span class="sxs-lookup"><span data-stu-id="4b6d3-249">te.exe test1.dll /sessionTimeout:5</span></span>  

<span data-ttu-id="4b6d3-250">The entire test session will time out after 5 hours.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-250">The entire test session will time out after 5 hours.</span></span>

<span data-ttu-id="4b6d3-251">te.exe test1.dll /sessionTimeout:1.2</span><span class="sxs-lookup"><span data-stu-id="4b6d3-251">te.exe test1.dll /sessionTimeout:1.2</span></span>  

<span data-ttu-id="4b6d3-252">The entire test session will time out after 1 day and 2 hours.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-252">The entire test session will time out after 1 day and 2 hours.</span></span>

### <a name="terminateonfirstfailure"></a><span data-ttu-id="4b6d3-253">/terminateOnFirstFailure</span><span class="sxs-lookup"><span data-stu-id="4b6d3-253">/terminateOnFirstFailure</span></span>

<span data-ttu-id="4b6d3-254">Terminates the test run the first time a test failure is encountered.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-254">Terminates the test run the first time a test failure is encountered.</span></span> <span data-ttu-id="4b6d3-255">All teardown operations for that test are invoked, but all subsequent tests are marked as ignored.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-255">All teardown operations for that test are invoked, but all subsequent tests are marked as ignored.</span></span> <span data-ttu-id="4b6d3-256">Due to a known issue, tests might continue to run when using a test mode.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-256">Due to a known issue, tests might continue to run when using a test mode.</span></span>

`te.exe test1.dll /terminateOnFirstFailure`

### <a name="testdependenciesfiles"></a><span data-ttu-id="4b6d3-257">/testDependencies:\<files></span><span class="sxs-lookup"><span data-stu-id="4b6d3-257">/testDependencies:\<files></span></span>

<span data-ttu-id="4b6d3-258">Specifies additional test dependencies to deploy when using [cross machine test execution](cross-machine-execution.md).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-258">Specifies additional test dependencies to deploy when using [cross machine test execution](cross-machine-execution.md).</span></span> <span data-ttu-id="4b6d3-259">Unless a full path is provided, TAEF will search relative to the current directory, not the test directory.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-259">Unless a full path is provided, TAEF will search relative to the current directory, not the test directory.</span></span>

<span data-ttu-id="4b6d3-260">te.exe \*.dll /runon:TestMachine1 /TestDependencies:test\*.jpg;file1.doc</span><span class="sxs-lookup"><span data-stu-id="4b6d3-260">te.exe \*.dll /runon:TestMachine1 /TestDependencies:test\*.jpg;file1.doc</span></span>  

<span data-ttu-id="4b6d3-261">**Interpretation:** Run all tests remotely on "TestMachine1", and copy 'test\*.jpg' and 'file1.doc' over to the remote machine before executing any tests.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-261">**Interpretation:** Run all tests remotely on "TestMachine1", and copy 'test\*.jpg' and 'file1.doc' over to the remote machine before executing any tests.</span></span> <span data-ttu-id="4b6d3-262">Each file specification can contain wildcard characters (test.txt; test\*.dll; etc.) to match one or more files.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-262">Each file specification can contain wildcard characters (test.txt; test\*.dll; etc.) to match one or more files.</span></span>

### <a name="testtimeoutvalue"></a><span data-ttu-id="4b6d3-263">/testTimeout:\<value></span><span class="sxs-lookup"><span data-stu-id="4b6d3-263">/testTimeout:\<value></span></span>

<span data-ttu-id="4b6d3-264">Sets a global test time-out for the entire execution of Te.exe.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-264">Sets a global test time-out for the entire execution of Te.exe.</span></span> <span data-ttu-id="4b6d3-265">This value overrides any [test time-out](standard-test-metadata.md) metadata that may have been set for a given test being executed.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-265">This value overrides any [test time-out](standard-test-metadata.md) metadata that may have been set for a given test being executed.</span></span>

> [!NOTE]
> <span data-ttu-id="4b6d3-266">The time-out value must be specified in the following format:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-266">The time-out value must be specified in the following format:</span></span>

```cpp
[Day.]Hour[:Minute[:Second[.FractionalSeconds]]]
```

> [!NOTE]
> <span data-ttu-id="4b6d3-267">Will be ignored when used in conjunction with [/inproc](#inproc).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-267">Will be ignored when used in conjunction with [/inproc](#inproc).</span></span>

<span data-ttu-id="4b6d3-268">te.exe test1.dll /testTimeout:0:0:0.5</span><span class="sxs-lookup"><span data-stu-id="4b6d3-268">te.exe test1.dll /testTimeout:0:0:0.5</span></span>  

<span data-ttu-id="4b6d3-269">Every test and setup/cleanup method will time out after .5 seconds.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-269">Every test and setup/cleanup method will time out after .5 seconds.</span></span>

<span data-ttu-id="4b6d3-270">te.exe test1.dll /testTimeout:0:0:45</span><span class="sxs-lookup"><span data-stu-id="4b6d3-270">te.exe test1.dll /testTimeout:0:0:45</span></span>  

<span data-ttu-id="4b6d3-271">Every test and setup/cleanup method will time out after 45 seconds.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-271">Every test and setup/cleanup method will time out after 45 seconds.</span></span>

<span data-ttu-id="4b6d3-272">te.exe test1.dll /testTimeout:0:20</span><span class="sxs-lookup"><span data-stu-id="4b6d3-272">te.exe test1.dll /testTimeout:0:20</span></span>  

<span data-ttu-id="4b6d3-273">Every test and setup/cleanup method will time out after 20 minutes.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-273">Every test and setup/cleanup method will time out after 20 minutes.</span></span>

<span data-ttu-id="4b6d3-274">te.exe test1.dll /testTimeout:5</span><span class="sxs-lookup"><span data-stu-id="4b6d3-274">te.exe test1.dll /testTimeout:5</span></span>  

<span data-ttu-id="4b6d3-275">Every test and setup/cleanup method will time out after 5 hours.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-275">Every test and setup/cleanup method will time out after 5 hours.</span></span>

<span data-ttu-id="4b6d3-276">te.exe test1.dll /testTimeout:1.2</span><span class="sxs-lookup"><span data-stu-id="4b6d3-276">te.exe test1.dll /testTimeout:1.2</span></span>  

<span data-ttu-id="4b6d3-277">Every test and setup/cleanup method will time out after 1 day and 2 hours.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-277">Every test and setup/cleanup method will time out after 1 day and 2 hours.</span></span>

### <a name="unicodeoutputtruefalse"></a><span data-ttu-id="4b6d3-278">/unicodeOutput:\<true/false></span><span class="sxs-lookup"><span data-stu-id="4b6d3-278">/unicodeOutput:\<true/false></span></span>

<span data-ttu-id="4b6d3-279">When TE is piped to a text file, it outputs unicode by default.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-279">When TE is piped to a text file, it outputs unicode by default.</span></span> <span data-ttu-id="4b6d3-280">The one exception to this is if you have requested to append to an existing ANSII file (via '&gt;&gt;').</span><span class="sxs-lookup"><span data-stu-id="4b6d3-280">The one exception to this is if you have requested to append to an existing ANSII file (via '&gt;&gt;').</span></span>

<span data-ttu-id="4b6d3-281">In order to override this behavior, you may specify /unicodeOutput:false.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-281">In order to override this behavior, you may specify /unicodeOutput:false.</span></span> <span data-ttu-id="4b6d3-282">This will force TE to always output ANSII to the file.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-282">This will force TE to always output ANSII to the file.</span></span>

`te.exe test1.dll /unicodeOutput:false > output.txt`

## <a name="logger-settings"></a><span data-ttu-id="4b6d3-283">Logger Settings</span><span class="sxs-lookup"><span data-stu-id="4b6d3-283">Logger Settings</span></span>

### <a name="appendwttlogging"></a><span data-ttu-id="4b6d3-284">/appendWttLogging</span><span class="sxs-lookup"><span data-stu-id="4b6d3-284">/appendWttLogging</span></span>

<span data-ttu-id="4b6d3-285">When WTT logging is enabled, appends to the log file rather than overwriting it.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-285">When WTT logging is enabled, appends to the log file rather than overwriting it.</span></span> <span data-ttu-id="4b6d3-286">Must be used in conjunction with [/enableWttLogging](#enablewttlogging).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-286">Must be used in conjunction with [/enableWttLogging](#enablewttlogging).</span></span>

<span data-ttu-id="4b6d3-287">te.exe test1.dll /enableWttLogging /appendWttLogging</span><span class="sxs-lookup"><span data-stu-id="4b6d3-287">te.exe test1.dll /enableWttLogging /appendWttLogging</span></span>  

<span data-ttu-id="4b6d3-288">Will create, or append to a log file called *TE.wtl* upon test execution completion.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-288">Will create, or append to a log file called *TE.wtl* upon test execution completion.</span></span>

### <a name="enablewttlogging"></a><span data-ttu-id="4b6d3-289">/enableWttLogging</span><span class="sxs-lookup"><span data-stu-id="4b6d3-289">/enableWttLogging</span></span>

<span data-ttu-id="4b6d3-290">Enables WTT logging; Wttlog.dll must be available in your path.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-290">Enables WTT logging; Wttlog.dll must be available in your path.</span></span>

<span data-ttu-id="4b6d3-291">te.exe test1.dll /enableWttLogging</span><span class="sxs-lookup"><span data-stu-id="4b6d3-291">te.exe test1.dll /enableWttLogging</span></span>

<span data-ttu-id="4b6d3-292">Will produce a log file called *TE.wtl* upon test execution completion.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-292">Will produce a log file called *TE.wtl* upon test execution completion.</span></span>

### <a name="defaultappdomain"></a><span data-ttu-id="4b6d3-293">/defaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="4b6d3-293">/defaultAppDomain</span></span>

<span data-ttu-id="4b6d3-294">Executes managed tests in the default application domain.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-294">Executes managed tests in the default application domain.</span></span>

<span data-ttu-id="4b6d3-295">te.exe managed.test1.dll /defaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="4b6d3-295">te.exe managed.test1.dll /defaultAppDomain</span></span>  

### <a name="disableconsolelogging"></a><span data-ttu-id="4b6d3-296">/disableConsoleLogging</span><span class="sxs-lookup"><span data-stu-id="4b6d3-296">/disableConsoleLogging</span></span>

<span data-ttu-id="4b6d3-297">Disables console log output; must be used in conjunction with [/enableWttLogging](#enablewttlogging).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-297">Disables console log output; must be used in conjunction with [/enableWttLogging](#enablewttlogging).</span></span>

`te.exe test1.dll /disableConsoleLogging /enableWttLogging`

### <a name="logfilename"></a><span data-ttu-id="4b6d3-298">/logFile:\<name></span><span class="sxs-lookup"><span data-stu-id="4b6d3-298">/logFile:\<name></span></span>

<span data-ttu-id="4b6d3-299">Specify a name to use as the wtt log file; must be used in conjunction with [/enableWttLogging](#enablewttlogging).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-299">Specify a name to use as the wtt log file; must be used in conjunction with [/enableWttLogging](#enablewttlogging).</span></span>

<span data-ttu-id="4b6d3-300">te.exe test1.dll /logFile:myCustomLogFile.xml /enableWttLogging</span><span class="sxs-lookup"><span data-stu-id="4b6d3-300">te.exe test1.dll /logFile:myCustomLogFile.xml /enableWttLogging</span></span>  

<span data-ttu-id="4b6d3-301">Will produce a log file called *myCustomeLogFile.xml* upon test execution completion.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-301">Will produce a log file called *myCustomeLogFile.xml* upon test execution completion.</span></span>

### <a name="logoutputmode"></a><span data-ttu-id="4b6d3-302">/logOutput:\<mode></span><span class="sxs-lookup"><span data-stu-id="4b6d3-302">/logOutput:\<mode></span></span>

<span data-ttu-id="4b6d3-303">Sets the output level of the logger.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-303">Sets the output level of the logger.</span></span> <span data-ttu-id="4b6d3-304">Valid values are:</span><span class="sxs-lookup"><span data-stu-id="4b6d3-304">Valid values are:</span></span>

* <span data-ttu-id="4b6d3-305">*High*: Enables some additional console output such as printing a time stamp next to every trace.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-305">*High*: Enables some additional console output such as printing a time stamp next to every trace.</span></span>
* <span data-ttu-id="4b6d3-306">*Low*: Emits only core events (start, end group, etc) and errors.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-306">*Low*: Emits only core events (start, end group, etc) and errors.</span></span> <span data-ttu-id="4b6d3-307">The log file includes lower priority details preceeding any errors to provide context for failures.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-307">The log file includes lower priority details preceeding any errors to provide context for failures.</span></span>
* <span data-ttu-id="4b6d3-308">*LowWithConsoleBuffering*: Same as *Low*, but includes the context of failures in both the log file and console output.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-308">*LowWithConsoleBuffering*: Same as *Low*, but includes the context of failures in both the log file and console output.</span></span>
* <span data-ttu-id="4b6d3-309">*Lowest*: Same as *Low*, but console output includes only errors, test failures, and the summary of execution.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-309">*Lowest*: Same as *Low*, but console output includes only errors, test failures, and the summary of execution.</span></span>

### <a name="version"></a><span data-ttu-id="4b6d3-310">/version</span><span class="sxs-lookup"><span data-stu-id="4b6d3-310">/version</span></span>

<span data-ttu-id="4b6d3-311">Outputs detailed version information.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-311">Outputs detailed version information.</span></span>

### <a name="wttdevicestringvalue"></a><span data-ttu-id="4b6d3-312">/wttDeviceString:\<value></span><span class="sxs-lookup"><span data-stu-id="4b6d3-312">/wttDeviceString:\<value></span></span>

<span data-ttu-id="4b6d3-313">Completely overrides the WttDeviceString used by WexLogger when it initializes WttLogger.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-313">Completely overrides the WttDeviceString used by WexLogger when it initializes WttLogger.</span></span>

`te.exe test1.dll /wttDeviceString:$Console`

### <a name="wttdevicestringsuffixvalue"></a><span data-ttu-id="4b6d3-314">/wttDeviceStringSuffix:\<value></span><span class="sxs-lookup"><span data-stu-id="4b6d3-314">/wttDeviceStringSuffix:\<value></span></span>

<span data-ttu-id="4b6d3-315">Appends the specified value to the default WttDeviceString used by WexLogger when it initializes WttLogger.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-315">Appends the specified value to the default WttDeviceString used by WexLogger when it initializes WttLogger.</span></span> <span data-ttu-id="4b6d3-316">Ignored if [wttDeviceString](#wttdevicestringvalue) is also specified.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-316">Ignored if [wttDeviceString](#wttdevicestringvalue) is also specified.</span></span>

`te.exe test1.dll /wttDeviceStringSuffix:$Console`

## <a name="debug-settings"></a><span data-ttu-id="4b6d3-317">Debug Settings</span><span class="sxs-lookup"><span data-stu-id="4b6d3-317">Debug Settings</span></span>

### <a name="breakoncreate"></a><span data-ttu-id="4b6d3-318">/breakOnCreate</span><span class="sxs-lookup"><span data-stu-id="4b6d3-318">/breakOnCreate</span></span>

<span data-ttu-id="4b6d3-319">Breaks into the debugger prior to instantiating each test class.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-319">Breaks into the debugger prior to instantiating each test class.</span></span>

`te.exe test1.dll /breakOnCreate`

### <a name="breakonerror"></a><span data-ttu-id="4b6d3-320">/breakOnError</span><span class="sxs-lookup"><span data-stu-id="4b6d3-320">/breakOnError</span></span>

<span data-ttu-id="4b6d3-321">Breaks into the debugger if an error or test failure is logged.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-321">Breaks into the debugger if an error or test failure is logged.</span></span>

`te.exe test1.dll /breakOnError`

### <a name="breakoninvoke"></a><span data-ttu-id="4b6d3-322">/breakOnInvoke</span><span class="sxs-lookup"><span data-stu-id="4b6d3-322">/breakOnInvoke</span></span>

<span data-ttu-id="4b6d3-323">Breaks into the debugger prior to invoking each test method.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-323">Breaks into the debugger prior to invoking each test method.</span></span>

`te.exe test1.dll /breakOnInvoke`

### <a name="disabletimeouts"></a><span data-ttu-id="4b6d3-324">/disableTimeouts</span><span class="sxs-lookup"><span data-stu-id="4b6d3-324">/disableTimeouts</span></span>

<span data-ttu-id="4b6d3-325">Disables all time-outs during execution.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-325">Disables all time-outs during execution.</span></span> <span data-ttu-id="4b6d3-326">This can be useful while debugging to prevent a timeout when TAEF is waiting on the part of the program that is being debugged.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-326">This can be useful while debugging to prevent a timeout when TAEF is waiting on the part of the program that is being debugged.</span></span>

`te.exe test1.dll /disableTimeouts`

### <a name="minidumponerror"></a><span data-ttu-id="4b6d3-327">/miniDumpOnError</span><span class="sxs-lookup"><span data-stu-id="4b6d3-327">/miniDumpOnError</span></span>

<span data-ttu-id="4b6d3-328">Takes and logs a mini dump if a test error or failure occurs.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-328">Takes and logs a mini dump if a test error or failure occurs.</span></span>

`te.exe test1.dll /miniDumpOnError`

### <a name="minidumponcrash"></a><span data-ttu-id="4b6d3-329">/miniDumpOnCrash</span><span class="sxs-lookup"><span data-stu-id="4b6d3-329">/miniDumpOnCrash</span></span>

<span data-ttu-id="4b6d3-330">Takes and logs a mini dump if a test crash occurs.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-330">Takes and logs a mini dump if a test crash occurs.</span></span>

`te.exe test1.dll /miniDumpOnCrash`

### <a name="rebootstatefile"></a><span data-ttu-id="4b6d3-331">/rebootStateFile</span><span class="sxs-lookup"><span data-stu-id="4b6d3-331">/rebootStateFile</span></span>

<span data-ttu-id="4b6d3-332">Explicitly enables execution of [Reboot](reboot.md) tests.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-332">Explicitly enables execution of [Reboot](reboot.md) tests.</span></span>

`te.exe test1.dll /rebootStateFile:myFile.xml`

### <a name="reportloadingissue"></a><span data-ttu-id="4b6d3-333">/reportLoadingIssue</span><span class="sxs-lookup"><span data-stu-id="4b6d3-333">/reportLoadingIssue</span></span>

<span data-ttu-id="4b6d3-334">Displays an error description dialog when TAEF fails to load a test dll.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-334">Displays an error description dialog when TAEF fails to load a test dll.</span></span> <span data-ttu-id="4b6d3-335">Must only be used for investigation of native test dll loading issues.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-335">Must only be used for investigation of native test dll loading issues.</span></span>

`te.exe test1.dll /reportLoadingIssue`

### <a name="screencaptureonerror"></a><span data-ttu-id="4b6d3-336">/screenCaptureOnError</span><span class="sxs-lookup"><span data-stu-id="4b6d3-336">/screenCaptureOnError</span></span>

<span data-ttu-id="4b6d3-337">Takes and logs a screen capture if a test error or failure occurs.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-337">Takes and logs a screen capture if a test error or failure occurs.</span></span>

`te.exe test1.dll /screenCaptureOnError`

### <a name="stackframecountvalue"></a><span data-ttu-id="4b6d3-338">/stackFrameCount:\<value></span><span class="sxs-lookup"><span data-stu-id="4b6d3-338">/stackFrameCount:\<value></span></span>

<span data-ttu-id="4b6d3-339">Specifies the number of stack frames to display when getting call stacks.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-339">Specifies the number of stack frames to display when getting call stacks.</span></span> <span data-ttu-id="4b6d3-340">The default value is 50.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-340">The default value is 50.</span></span>

`te.exe test1.dll /stackFrameCount:100`

### <a name="stacktraceonerror"></a><span data-ttu-id="4b6d3-341">/stackTraceOnError</span><span class="sxs-lookup"><span data-stu-id="4b6d3-341">/stackTraceOnError</span></span>

<span data-ttu-id="4b6d3-342">Takes and logs a stack trace if a test error or failure occurs.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-342">Takes and logs a stack trace if a test error or failure occurs.</span></span>

`te.exe test1.dll /stackTraceOnError`

## <a name="test-modes"></a><span data-ttu-id="4b6d3-343">Test Modes</span><span class="sxs-lookup"><span data-stu-id="4b6d3-343">Test Modes</span></span>

### <a name="testmodeloop"></a><span data-ttu-id="4b6d3-344">/testmode:Loop</span><span class="sxs-lookup"><span data-stu-id="4b6d3-344">/testmode:Loop</span></span>

<span data-ttu-id="4b6d3-345">Allows controlling the execution using two variables *Loop* and *LoopTest*.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-345">Allows controlling the execution using two variables *Loop* and *LoopTest*.</span></span>

* <span data-ttu-id="4b6d3-346">*Loop*: Controls how many times the whole run is executed.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-346">*Loop*: Controls how many times the whole run is executed.</span></span> <span data-ttu-id="4b6d3-347">Default 1.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-347">Default 1.</span></span>
* <span data-ttu-id="4b6d3-348">*LoopTest*: Controls how many times an individual test is executed.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-348">*LoopTest*: Controls how many times an individual test is executed.</span></span> <span data-ttu-id="4b6d3-349">Default 10.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-349">Default 10.</span></span>

<span data-ttu-id="4b6d3-350">te.exe test1.dll /testmode:Loop</span><span class="sxs-lookup"><span data-stu-id="4b6d3-350">te.exe test1.dll /testmode:Loop</span></span>  

<span data-ttu-id="4b6d3-351">**Interpretation:** Run every test in test1.dll 10 times (default value for *LoopTest*).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-351">**Interpretation:** Run every test in test1.dll 10 times (default value for *LoopTest*).</span></span> <span data-ttu-id="4b6d3-352">The whole execution is run once (default value for *Loop*).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-352">The whole execution is run once (default value for *Loop*).</span></span>

<span data-ttu-id="4b6d3-353">te.exe test1.dll test2.dll /testmode:Loop /Loop:3 /LoopTest:1</span><span class="sxs-lookup"><span data-stu-id="4b6d3-353">te.exe test1.dll test2.dll /testmode:Loop /Loop:3 /LoopTest:1</span></span>  

<span data-ttu-id="4b6d3-354">**Interpretation:** Run every test in test1.dll and test2.dll once (determined by *LoopTest*).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-354">**Interpretation:** Run every test in test1.dll and test2.dll once (determined by *LoopTest*).</span></span> <span data-ttu-id="4b6d3-355">The whole execution (all combined tests in test1.dll and test2.dll) is run 3 times - as determined by *Loop*.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-355">The whole execution (all combined tests in test1.dll and test2.dll) is run 3 times - as determined by *Loop*.</span></span>

### <a name="testmodestress"></a><span data-ttu-id="4b6d3-356">/testmode:Stress</span><span class="sxs-lookup"><span data-stu-id="4b6d3-356">/testmode:Stress</span></span>

<span data-ttu-id="4b6d3-357">In 'stress' test mode, TAEF will run tests indefinitely, until Ctrl+C is entered or until a WM\_CLOSE message is sent to TAEF's hidden window.</span><span class="sxs-lookup"><span data-stu-id="4b6d3-357">In 'stress' test mode, TAEF will run tests indefinitely, until Ctrl+C is entered or until a WM\_CLOSE message is sent to TAEF's hidden window.</span></span> <span data-ttu-id="4b6d3-358">/testmode:stress must be run in conjunction with [/inproc](#inproc).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-358">/testmode:stress must be run in conjunction with [/inproc](#inproc).</span></span>

`te.exe test1.dll /testmode:Stress /inproc`

<span data-ttu-id="4b6d3-359">For detailed information and other parameters supported in this mode, see [Test Modes](test-modes.md).</span><span class="sxs-lookup"><span data-stu-id="4b6d3-359">For detailed information and other parameters supported in this mode, see [Test Modes](test-modes.md).</span></span>