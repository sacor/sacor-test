---
title: Xamarin.iOS 錯誤
description: 本文件說明各種 mtouch，用來連結相同的 Xamarin.iOS 應用程式的工具所產生的錯誤。 錯誤的程式碼列出並提供完整的說明。
ms.topic: troubleshooting
ms.prod: xamarin
ms.assetid: 9F76162B-D622-45DA-996B-2FBF8017E208
ms.technology: xamarin-ios
author: lobrien
ms.author: laobri
ms.date: 03/06/2018
ms.openlocfilehash: e6e3a989db922dc2941cca4c888c862ffe159241
ms.sourcegitcommit: 4b402d1c508fa84e4fc3171a6e43b811323948fc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61422048"
---
# <a name="xamarinios-errors"></a><span data-ttu-id="c22ab-104">Xamarin.iOS 錯誤</span><span class="sxs-lookup"><span data-stu-id="c22ab-104">Xamarin.iOS errors</span></span>

## <a name="mt0xxx-mtouch-error-messages"></a><span data-ttu-id="c22ab-105">MT0xxx: mtouch 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-105">MT0xxx: mtouch error messages</span></span>

<span data-ttu-id="c22ab-106">例如，</span><span class="sxs-lookup"><span data-stu-id="c22ab-106">E.g.</span></span> <span data-ttu-id="c22ab-107">參數、 遺漏工具的環境。</span><span class="sxs-lookup"><span data-stu-id="c22ab-107">parameters, environment, missing tools.</span></span>

<!--
 MT0xxx mtouch itself, e.g. parameters, environment (e.g. missing tools)
 https://github.com/xamarin/xamarin-macios/blob/master/tools/mtouch/error.cs
    -->

<a name="MT0000" />

### <a name="mt0000-unexpected-error---please-fill-a-bug-report-at-httpsgithubcomxamarinxamarin-maciosissuesnew"></a><span data-ttu-id="c22ab-108">MT0000:未預期的錯誤-請填寫在錯誤報告 https://github.com/xamarin/xamarin-macios/issues/new</span><span class="sxs-lookup"><span data-stu-id="c22ab-108">MT0000: Unexpected error - Please fill a bug report at https://github.com/xamarin/xamarin-macios/issues/new</span></span>

<span data-ttu-id="c22ab-109">發生未預期的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="c22ab-109">An unexpected error condition occurred.</span></span> <span data-ttu-id="c22ab-110">請[提出 bug 報告](https://github.com/xamarin/xamarin-macios/issues/new)盡可能最多資訊，包括：</span><span class="sxs-lookup"><span data-stu-id="c22ab-110">Please [file a bug report](https://github.com/xamarin/xamarin-macios/issues/new) with as much information as possible, including:</span></span>

* <span data-ttu-id="c22ab-111">完整建置記錄檔，並以最詳細 (例如`-v -v -v -v`中**其他 mtouch 引數**);</span><span class="sxs-lookup"><span data-stu-id="c22ab-111">Full build logs, with maximum verbosity (e.g. `-v -v -v -v` in the **Additional mtouch arguments**);</span></span>
* <span data-ttu-id="c22ab-112">最少重現錯誤，測試案例和</span><span class="sxs-lookup"><span data-stu-id="c22ab-112">A minimal test case that reproduce the error; and</span></span>
* <span data-ttu-id="c22ab-113">所有的版本資訊</span><span class="sxs-lookup"><span data-stu-id="c22ab-113">All version informations</span></span>

<span data-ttu-id="c22ab-114">若要取得正確的版本資訊最簡單的方式是使用**Visual Studio for Mac**  功能表**關於 Visual Studio for Mac**項目，**顯示詳細資料**按鈕和複製/貼上版本資訊 (您可以使用**複製資訊**按鈕)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-114">The easiest way to get exact version information is to use the **Visual Studio for Mac** menu, **About Visual Studio for Mac** item, **Show Details** button and copy/paste the version informations (you can use the **Copy Information** button).</span></span>

<a name="MT0001" />

### <a name="mt0001--devname-was-provided-without-any-device-specific-action"></a><span data-ttu-id="c22ab-115">MT0001: '-devname' 並無任何裝置特定動作所提供</span><span class="sxs-lookup"><span data-stu-id="c22ab-115">MT0001: '-devname' was provided without any device-specific action</span></span>

<span data-ttu-id="c22ab-116">這是如果-devname 傳遞給 mtouch 任何裝置特定動作時，就會發出警告 (層 logdev /-installdev /-killdev /-launchdev /-listapps) 要求。</span><span class="sxs-lookup"><span data-stu-id="c22ab-116">This is a warning that is emitted if -devname is passed to mtouch when no device-specific action (-logdev/-installdev/-killdev/-launchdev/-listapps) was requested.</span></span>

<a name="MT0002" />

### <a name="mt0002-could-not-parse-the-environment-variable-"></a><span data-ttu-id="c22ab-117">MT0002:無法剖析環境變數 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-117">MT0002: Could not parse the environment variable \*.</span></span>

<span data-ttu-id="c22ab-118">如果您嘗試設定無效的環境索引鍵，就會發生此錯誤 = 值組的變數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-118">This error happens if you try to set an invalid environment key=value variable pair.</span></span> <span data-ttu-id="c22ab-119">正確的格式為： `mtouch --setenv=VARIABLE=VALUE`</span><span class="sxs-lookup"><span data-stu-id="c22ab-119">The correct format is: `mtouch --setenv=VARIABLE=VALUE`</span></span>

<a name="MT0003" />

### <a name="mt0003-application-name-exe-conflicts-with-an-sdk-or-product-assembly-dll-name"></a><span data-ttu-id="c22ab-120">MT0003:應用程式名稱 '\*.exe' je v konfliktu SDK 或產品組件 (.dll) 名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-120">MT0003: Application name '\*.exe' conflicts with an SDK or product assembly (.dll) name.</span></span>

<span data-ttu-id="c22ab-121">可執行組件的名稱和應用程式的名稱不符合應用程式中的任何 dll 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-121">The executable assembly's name and the application's name can't match the name of any dll in the app.</span></span> <span data-ttu-id="c22ab-122">請修改可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-122">Please modify the name of your executable.</span></span>

<a name="MT0004" />

### <a name="mt0004-new-refcounting-logic-requires-sgen-to-be-enabled-too"></a><span data-ttu-id="c22ab-123">MT0004:新的 refcounting 邏輯需要太啟用 SGen。</span><span class="sxs-lookup"><span data-stu-id="c22ab-123">MT0004: New refcounting logic requires SGen to be enabled too.</span></span>

<span data-ttu-id="c22ab-124">如果您啟用 refcounting 擴充功能，您也必須啟用 SGen 記憶體回收行程，在專案的 iOS 組建 選項 （進階索引標籤）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-124">If you enable the refcounting extension you must also enable the SGen garbage collector in the project's iOS Build options (Advanced tab).</span></span>

<span data-ttu-id="c22ab-125">開始使用 Xamarin.iOS 7.2.1 此需求已提高，可以啟用新的 refcounting 邏輯 Boehm 和 SGen 記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="c22ab-125">Starting with Xamarin.iOS 7.2.1 this requirement has been lifted, the new refcounting logic can be enabled with both Boehm and SGen Garbage Collectors.</span></span>

<a name="MT0005" />

### <a name="mt0005-the-output-directory--does-not-exist"></a><span data-ttu-id="c22ab-126">MT0005:輸出目錄 \* 不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-126">MT0005: The output directory \* does not exist.</span></span>

<span data-ttu-id="c22ab-127">請建立目錄。</span><span class="sxs-lookup"><span data-stu-id="c22ab-127">Please create the directory.</span></span>

<span data-ttu-id="c22ab-128">不會再產生這個錯誤，mtouch 會自動建立目錄，如果不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-128">This error is not generated anymore, mtouch will automatically create the directory if it doesn't exist.</span></span>

<a name="MT0006" />

### <a name="mt0006-there-is-no-devel-platform-at--use---platformplat-to-specify-the-sdk"></a><span data-ttu-id="c22ab-129">MT0006:沒有任何提供平台 \*，使用-平台 = 指定 SDK 的平台。</span><span class="sxs-lookup"><span data-stu-id="c22ab-129">MT0006: There is no devel platform at \*, use --platform=PLAT to specify the SDK.</span></span>

<span data-ttu-id="c22ab-130">Xamarin.iOS 找不到 SDK 目錄中的錯誤訊息中所述的位置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-130">Xamarin.iOS cannot find the SDK directory at the location mentioned in the error message.</span></span> <span data-ttu-id="c22ab-131">請確認路徑正確。</span><span class="sxs-lookup"><span data-stu-id="c22ab-131">Please verify that the path is correct.</span></span>

<a name="MT0007" />

### <a name="mt0007-the-root-assembly--does-not-exist"></a><span data-ttu-id="c22ab-132">MT0007:根組件 \* 不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-132">MT0007: The root assembly \* does not exist.</span></span>

<span data-ttu-id="c22ab-133">Xamarin.iOS 找不到錯誤訊息中所述的位置中的組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-133">Xamarin.iOS cannot find the assembly at the location mentioned in the error message.</span></span> <span data-ttu-id="c22ab-134">請確認路徑正確。</span><span class="sxs-lookup"><span data-stu-id="c22ab-134">Please verify that the path is correct.</span></span>

<a name="MT0008" />

### <a name="mt0008-you-should-provide-one-root-assembly-only-found--assemblies-"></a><span data-ttu-id="c22ab-135">MT0008:您應提供根組件，找到 # 組件: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-135">MT0008: You should provide one root assembly only, found # assemblies: \*.</span></span>

<span data-ttu-id="c22ab-136">一個以上的根組件傳遞給 mtouch，雖然可能只能有一個根組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-136">More than one root assembly was passed to mtouch, while there can be only one root assembly.</span></span>

<a name="MT0009" />

### <a name="mt0009-error-while-loading-assemblies-"></a><span data-ttu-id="c22ab-137">MT0009:載入組件時發生錯誤: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-137">MT0009: Error while loading assemblies: \*.</span></span>

<span data-ttu-id="c22ab-138">載入組件的根組件參考時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-138">An error occurred while loading the assemblies the root assembly references.</span></span> <span data-ttu-id="c22ab-139">建置輸出中，可能會提供詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c22ab-139">More information may be provided in the build output.</span></span>

<a name="MT0010" />

### <a name="mt0010-could-not-parse-the-command-line-arguments-"></a><span data-ttu-id="c22ab-140">MT0010:無法剖析命令列引數: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-140">MT0010: Could not parse the command line arguments: \*.</span></span>

<span data-ttu-id="c22ab-141">剖析命令列引數時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-141">An error occurred while parsing the command line arguments.</span></span> <span data-ttu-id="c22ab-142">請確認它們都正確。</span><span class="sxs-lookup"><span data-stu-id="c22ab-142">Please verify that they are all correct.</span></span>

<a name="MT0011" />

### <a name="mt0011--was-built-against-a-more-recent-runtime--than-monotouch-supports"></a><span data-ttu-id="c22ab-143">MT0011: \* 高於 MonoTouch 支援較新的執行階段 （\*） 建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-143">MT0011: \* was built against a more recent runtime (\*) than MonoTouch supports.</span></span>

<span data-ttu-id="c22ab-144">因為專案不是使用 Xamarin.iOS BCL 類別程式庫的參考，通常會報告這個警告。</span><span class="sxs-lookup"><span data-stu-id="c22ab-144">This warning is typically reported because the project has a reference to a class library that was not built using the Xamarin.iOS BCL.</span></span>

<span data-ttu-id="c22ab-145">使用.NET 4.0 SDK 的應用程式可能無法只支援.NET 2.0 中，在系統的相同方式建置使用.NET 4.0 的程式庫，可能無法在 Xamarin.iOS 上運作，它可能會使用 API 不會出現在 Xamarin.iOS 上。</span><span class="sxs-lookup"><span data-stu-id="c22ab-145">The same way an app using the .NET 4.0 SDK may not work on a system only supporting .NET 2.0, a library built using .NET 4.0 may not work on Xamarin.iOS, it may use API not present on Xamarin.iOS.</span></span>

<span data-ttu-id="c22ab-146">一般的解決方法是建置為 Xamarin.iOS 類別庫的程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-146">The general solution is to build the library as a Xamarin.iOS Class Library.</span></span> <span data-ttu-id="c22ab-147">這可藉由建立新的 Xamarin.iOS 類別庫專案，並將它的所有原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-147">This can be accomplished by creating a new Xamarin.iOS Class Library project and add all the source files to it.</span></span> <span data-ttu-id="c22ab-148">如果您沒有程式庫的原始程式碼，您應該連絡廠商，並要求他們提供其程式庫的 Xamarin.iOS 相容版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-148">If you do not have the source code for the library, you should contact the vendor and request that they provide a Xamarin.iOS-compatible version of their library.</span></span>

<a name="MT0012" />

### <a name="mt0012-incomplete-data-is-provided-to-complete-"></a><span data-ttu-id="c22ab-149">MT0012:若要完成不完整的資料提供 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-149">MT0012: Incomplete data is provided to complete \*.</span></span>

<span data-ttu-id="c22ab-150">此錯誤不會再報告在目前版本中的 Xamarin.iOS。</span><span class="sxs-lookup"><span data-stu-id="c22ab-150">This error is not reported anymore in the current version of Xamarin.iOS.</span></span>

<a name="MT0013" />

### <a name="mt0013-profiling-support-requires-sgen-to-be-enabled-too"></a><span data-ttu-id="c22ab-151">MT0013:程式碼剖析支援需要太啟用 sgen。</span><span class="sxs-lookup"><span data-stu-id="c22ab-151">MT0013: Profiling support requires sgen to be enabled too.</span></span>

<span data-ttu-id="c22ab-152">SGen (-sgen)，程式碼剖析，則必須啟用 (-程式碼剖析) 已啟用。</span><span class="sxs-lookup"><span data-stu-id="c22ab-152">SGen (--sgen) must be enabled if profiling (--profiling) is enabled.</span></span>

<a name="MT0014" />

### <a name="mt0014-the-ios--sdk-does-not-support-building-applications-targeting-"></a><span data-ttu-id="c22ab-153">MT0014:IOS \* SDK 不支援建置應用程式目標設為 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-153">MT0014: The iOS \* SDK does not support building applications targeting \*.</span></span>

<span data-ttu-id="c22ab-154">這會發生在下列情況：</span><span class="sxs-lookup"><span data-stu-id="c22ab-154">This can happen in the following circumstances:</span></span>

*  <span data-ttu-id="c22ab-155">ARMv6 已啟用，並已安裝 Xcode 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-155">ARMv6 is enabled and Xcode 4.5 or later is installed.</span></span>
*  <span data-ttu-id="c22ab-156">ARMv7s 已啟用，並已安裝 Xcode 4.4 或更早版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-156">ARMv7s is enabled and Xcode 4.4 or earlier is installed.</span></span>

<span data-ttu-id="c22ab-157">請確認已安裝的 Xcode 版本支援選取的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-157">Please verify that the installed version of Xcode supports the selected architectures.</span></span>

<a name="MT0015" />

### <a name="mt0015-invalid-abi--supported-abis-are-i386-x8664--armv7-armv7llvm-armv7llvmthumb2-armv7s-armv7sllvm-armv7sllvmthumb2-arm64-and-arm64llvm"></a><span data-ttu-id="c22ab-158">MT0015:無效的 ABI: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-158">MT0015: Invalid ABI: \*.</span></span> <span data-ttu-id="c22ab-159">支援的 Abi 會： i386，x86_64，armv7，armv7 + llvm、 armv7 + llvm + thumb2、 armv7s、 armv7s + llvm、 armv7s + llvm + thumb2、 arm64 和 arm64 + llvm。</span><span class="sxs-lookup"><span data-stu-id="c22ab-159">Supported ABIs are: i386, x86_64,  armv7, armv7+llvm, armv7+llvm+thumb2, armv7s, armv7s+llvm, armv7s+llvm+thumb2, arm64 and arm64+llvm.</span></span>

<span data-ttu-id="c22ab-160">無效的 ABI 傳遞給 mtouch。</span><span class="sxs-lookup"><span data-stu-id="c22ab-160">An invalid ABI was passed to mtouch.</span></span> <span data-ttu-id="c22ab-161">請指定有效的 ABI。</span><span class="sxs-lookup"><span data-stu-id="c22ab-161">Please specify a valid ABI.</span></span>

<a name="MT0016" />

### <a name="mt0016-the-option--has-been-deprecated"></a><span data-ttu-id="c22ab-162">MT0016:此選項 \* 已被取代。</span><span class="sxs-lookup"><span data-stu-id="c22ab-162">MT0016: The option \* has been deprecated.</span></span>

<span data-ttu-id="c22ab-163">提及的 mtouch 選項已被取代，且會被忽略。</span><span class="sxs-lookup"><span data-stu-id="c22ab-163">The mentioned mtouch option has been deprecated and will be ignored.</span></span>

<a name="MT0017" />

### <a name="mt0017-you-should-provide-a-root-assembly"></a><span data-ttu-id="c22ab-164">MT0017:您應提供根組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-164">MT0017: You should provide a root assembly.</span></span>

<span data-ttu-id="c22ab-165">需要指定根組件 （通常是主要可執行檔） 建置應用程式時。</span><span class="sxs-lookup"><span data-stu-id="c22ab-165">It is required to specify a root assembly (typically the main executable) when building an app.</span></span>

<a name="MT0018" />

### <a name="mt0018-unknown-command-line-argument-"></a><span data-ttu-id="c22ab-166">MT0018:未知的命令列引數: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-166">MT0018: Unknown command line argument: \*.</span></span>

<span data-ttu-id="c22ab-167">Mtouch 無法辨識的錯誤訊息中所述的命令列引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-167">Mtouch does not recognize the command line argument mentioned in the error message.</span></span>

<a name="MT0019" />

### <a name="mt0019-only-one---loginstallkilllaunchdev-or---launchdebugsim-option-can-be-used"></a><span data-ttu-id="c22ab-168">MT0019:只有一個-[記錄檔 | 安裝 | 刪除 | 啟動] 開發或--[啟動 | 偵錯] sim 選項可用。</span><span class="sxs-lookup"><span data-stu-id="c22ab-168">MT0019: Only one --[log|install|kill|launch]dev or --[launch|debug]sim option can be used.</span></span>

<span data-ttu-id="c22ab-169">有幾個選項不能同時使用的 mtouch:</span><span class="sxs-lookup"><span data-stu-id="c22ab-169">There are several options for mtouch that can't be used simultaneously:</span></span>

-  <span data-ttu-id="c22ab-170">--logdev</span><span class="sxs-lookup"><span data-stu-id="c22ab-170">--logdev</span></span>
-  <span data-ttu-id="c22ab-171">--installdev</span><span class="sxs-lookup"><span data-stu-id="c22ab-171">--installdev</span></span>
-  <span data-ttu-id="c22ab-172">--killdev</span><span class="sxs-lookup"><span data-stu-id="c22ab-172">--killdev</span></span>
-  <span data-ttu-id="c22ab-173">--launchdev</span><span class="sxs-lookup"><span data-stu-id="c22ab-173">--launchdev</span></span>
-  <span data-ttu-id="c22ab-174">--launchdebug</span><span class="sxs-lookup"><span data-stu-id="c22ab-174">--launchdebug</span></span>
-  <span data-ttu-id="c22ab-175">--launchsim</span><span class="sxs-lookup"><span data-stu-id="c22ab-175">--launchsim</span></span>

<a name="MT0020" />

### <a name="mt0020-the-valid-options-for--are-"></a><span data-ttu-id="c22ab-176">MT0020:有效的選項為 '\*'是'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-176">MT0020: The valid options for '\*' are '\*'.</span></span>

<a name="MT0021" />

### <a name="mt0021-cannot-compile-using-gccg---use-gcc-when-using-the-static-registrar-this-is-the-default-when-compiling-for-device-either-remove-the---use-gcc-flag-or-use-the-dynamic-registrar---registrardynamic"></a><span data-ttu-id="c22ab-177">MT0021:無法編譯使用 gcc / g + + (-使用 gcc) 時使用靜態的註冊機構 （裝置進行編譯時，這是預設值）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-177">MT0021: Cannot compile using gcc/g++ (--use-gcc) when using the static registrar (this is the default when compiling for device).</span></span> <span data-ttu-id="c22ab-178">請移除--使用 gcc 旗標，或使用動態的註冊機構 (-註冊機構： 動態)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-178">Either remove the --use-gcc flag or use the dynamic registrar (--registrar:dynamic).</span></span>

<a name="MT0022" />

### <a name="mt0022-the-options---unsupported--enable-generics-in-registrar-and---registrar-are-not-compatible"></a><span data-ttu-id="c22ab-179">MT0022:選項 '-不支援-啟用-泛型-中-登錄器' 和 '-登錄器 ' 不相容。</span><span class="sxs-lookup"><span data-stu-id="c22ab-179">MT0022: The options '--unsupported--enable-generics-in-registrar' and '--registrar' are not compatible.</span></span>

<span data-ttu-id="c22ab-180">移除兩個選項`--unsupported--enable-generics-in-registrar`和`--registrar`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-180">Remove both the options `--unsupported--enable-generics-in-registrar` and `--registrar`.</span></span> <span data-ttu-id="c22ab-181">從 Xamarin.iOS 7.2.1 預設註冊機構支援泛型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-181">Starting with Xamarin.iOS 7.2.1 the default registrar supports generics.</span></span>

<span data-ttu-id="c22ab-182">不會再看到這個錯誤 (命令列引數`--unsupported--enable-generics-in-registrar`已經移除了 mtouch)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-182">This error is no longer shown (the command-line argument `--unsupported--enable-generics-in-registrar` has been removed from mtouch).</span></span>

<a name="MT0023" />

### <a name="mt0023-application-name-exe-conflicts-with-another-user-assembly"></a><span data-ttu-id="c22ab-183">MT0023:應用程式名稱 '\*.exe' 與另一個使用者組件衝突。</span><span class="sxs-lookup"><span data-stu-id="c22ab-183">MT0023: Application name '\*.exe' conflicts with another user assembly.</span></span>

<span data-ttu-id="c22ab-184">可執行組件的名稱和應用程式的名稱不符合應用程式中的任何 dll 的名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-184">The executable assembly's name and the application's name can't match the name of any dll in the app.</span></span> <span data-ttu-id="c22ab-185">請修改可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-185">Please modify the name of your executable.</span></span>

<a name="MT0024" />

### <a name="mt0024-could-not-find-required-file-"></a><span data-ttu-id="c22ab-186">MT0024:找不到必要的檔案 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-186">MT0024: Could not find required file '\*'.</span></span>

<a name="MT0025" />

### <a name="mt0025-no-sdk-version-was-provided-please-add---sdkxy-to-specify-which-ios-sdk-should-be-used-to-build-your-application"></a><span data-ttu-id="c22ab-187">MT0025:未不提供任何 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-187">MT0025: No SDK version was provided.</span></span> <span data-ttu-id="c22ab-188">請新增`--sdk=X.Y`來指定哪些 iOS SDK 應該用來建置您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-188">Please add `--sdk=X.Y` to specify which iOS SDK should be used to build your application.</span></span>

<a name="MT0026" />

### <a name="mt0026-could-not-parse-the-command-line-argument--"></a><span data-ttu-id="c22ab-189">MT0026:無法剖析命令列引數 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-189">MT0026: Could not parse the command line argument '\*': \*</span></span>

<a name="MT0027" />

### <a name="mt0027-the-options--and--are-not-compatible"></a><span data-ttu-id="c22ab-190">MT0027:選項\*'和'\*' 不相容。</span><span class="sxs-lookup"><span data-stu-id="c22ab-190">MT0027: The options '\*' and '\*' are not compatible.</span></span>

<a name="MT0028" />

### <a name="mt0028-cannot-enable-pie--pie-when-targeting-ios-41-or-earlier-please-disable-pie--piefalse-or-set-the-deployment-target-to-at-least-ios-42"></a><span data-ttu-id="c22ab-191">MT0028:無法啟用圓形圖 (-圓形圖) 為目標 iOS 4.1 或更早版本時。</span><span class="sxs-lookup"><span data-stu-id="c22ab-191">MT0028: Cannot enable PIE (-pie) when targeting iOS 4.1 or earlier.</span></span> <span data-ttu-id="c22ab-192">請停用圓形圖 (-圓形圖： false) 或至少將部署目標設定為 iOS 4.2</span><span class="sxs-lookup"><span data-stu-id="c22ab-192">Please disable PIE (-pie:false) or set the deployment target to at least iOS 4.2</span></span>

<a name="MT0029" />

### <a name="mt0029-repl---enable-repl-is-only-supported-in-the-simulator---sim"></a><span data-ttu-id="c22ab-193">MT0029:REPL (-啟用 repl) 才支援在模擬器中 (-sim)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-193">MT0029: REPL (--enable-repl) is only supported in the simulator (--sim).</span></span>

<span data-ttu-id="c22ab-194">如果您正在建置模擬器僅支援複寫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-194">REPL is only supported if you're building for the simulator.</span></span> <span data-ttu-id="c22ab-195">這表示，如果您傳遞`--enable-repl`mtouch，您必須也傳遞`--sim`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-195">This means that if you pass `--enable-repl` to mtouch, you must also pass `--sim`.</span></span>

<a name="MT0030" />

### <a name="mt0030-the-executable-name--and-the-app-name--are-different-this-may-prevent-crash-logs-from-getting-symbolicated-properly"></a><span data-ttu-id="c22ab-196">MT0030:可執行檔的名稱 (\*) 和應用程式名稱 (\*) 不同，這可能會導致當機記錄檔無法取得符號式正確。</span><span class="sxs-lookup"><span data-stu-id="c22ab-196">MT0030: The executable name (\*) and the app name (\*) are different, this may prevent crash logs from getting symbolicated properly.</span></span>

<span data-ttu-id="c22ab-197">當 Xcode symbolicates （轉換函式名稱和檔案/行數字的記憶體位址） 如果可執行檔和應用程式有不同的名稱 （不含副檔名），此程序可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="c22ab-197">When Xcode symbolicates (translates memory addresses to function names and file/line numbers) the process may fail if the executable and app have different names (without the extension).</span></span>

<span data-ttu-id="c22ab-198">若要修正這個變更 '應用程式名稱' 在專案的建置/iOS 應用程式選項或在專案的建置/輸出選項 中的變更 ' Assembly Name'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-198">To fix this either change 'Application Name' in the project's Build/iOS Application options, or change 'Assembly Name' in the project's Build/Output options.</span></span>

<a name="MT0031" />

### <a name="mt0031-the-command-line-arguments---enable-background-fetch-and---launch-for-background-fetch-require---launchsim-too"></a><span data-ttu-id="c22ab-199">MT0031:命令列引數 '-啟用背景擷取 '和 '-啟動的背景擷取' 需要 '-launchsim' 太。</span><span class="sxs-lookup"><span data-stu-id="c22ab-199">MT0031: The command line arguments '--enable-background-fetch' and '--launch-for-background-fetch' require '--launchsim' too.</span></span>

<a name="MT0032" />

### <a name="mt0032-the-option---debugtrack-is-ignored-unless---debug-is-also-specified"></a><span data-ttu-id="c22ab-200">MT0032:選項 '-debugtrack' 會被忽略，除非 '-偵錯 ' 同時指定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-200">MT0032: The option '--debugtrack' is ignored unless '--debug' is also specified.</span></span>

<a name="MT0033" />

### <a name="mt0033-a-xamarinios-project-must-reference-either-monotouchdll-or-xamariniosdll"></a><span data-ttu-id="c22ab-201">MT0033:在 Xamarin.iOS 專案必須參考 monotouch.dll 或 Xamarin.iOS.dll</span><span class="sxs-lookup"><span data-stu-id="c22ab-201">MT0033: A Xamarin.iOS project must reference either monotouch.dll or Xamarin.iOS.dll</span></span>

<a name="MT0034" />

### <a name="mt0034-cannot-include-both-monotouchdll-and-xamariniosdll-in-the-same-xamarinios-project----is-referenced-explicitly-while--is-referenced-by-"></a><span data-ttu-id="c22ab-202">MT0034:不能包含 'monotouch.dll' 和 'Xamarin.iOS.dll' 在相同的 Xamarin.iOS 專案中為 '\*' 是明確參考，而 '\*' 參考的 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-202">MT0034: Cannot include both 'monotouch.dll' and 'Xamarin.iOS.dll' in the same Xamarin.iOS project - '\*' is referenced explicitly, while '\*' is referenced by '\*'.</span></span>

<!-- MT0035 unused -->

<a name="MT0036" />

### <a name="mt0036-cannot-launch-a--simulator-for-a--app-please-enable-the-correct-architectures-in-your-projects-ios-build-options-advanced-page"></a><span data-ttu-id="c22ab-203">MT0036:無法啟動 \* 模擬器 \* 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-203">MT0036: Cannot launch a \* simulator for a \* app.</span></span> <span data-ttu-id="c22ab-204">請啟用正確的 architecture(s) 中專案的 iOS 組建 選項 （進階頁面）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-204">Please enable the correct architecture(s) in your project's iOS Build options (Advanced page).</span></span>

<a name="MT0037" />

### <a name="mt0037-monotouchdll-is-not-64-bit-compatible-either-reference-xamariniosdll-or-do-not-build-for-a-64-bit-architecture-arm64-andor-x8664"></a><span data-ttu-id="c22ab-205">MT0037: monotouch.dll 與 64 位元不相容。</span><span class="sxs-lookup"><span data-stu-id="c22ab-205">MT0037: monotouch.dll is not 64-bit compatible.</span></span> <span data-ttu-id="c22ab-206">請參考 Xamarin.iOS.dll，或針對 64 位元的架構 （ARM64 和/或 x86_64） 不會建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-206">Either reference Xamarin.iOS.dll, or do not build for a 64-bit architecture (ARM64 and/or x86_64).</span></span>

<a name="MT0038" />

### <a name="mt0038-the-old-registrars---registraroldstaticolddynamic-are-not-supported-when-referencing-xamariniosdll"></a><span data-ttu-id="c22ab-207">MT0038:舊的註冊機構 (-註冊機構： oldstatic | olddynamic) 不支援參考 Xamarin.iOS.dll 時。</span><span class="sxs-lookup"><span data-stu-id="c22ab-207">MT0038: The old registrars (--registrar:oldstatic|olddynamic) are not supported when referencing Xamarin.iOS.dll.</span></span>

<a name="MT0039" />

### <a name="mt0039-applications-targeting-armv6-cannot-reference-xamariniosdll"></a><span data-ttu-id="c22ab-208">MT0039:目標 ARMv6 的應用程式無法參考 Xamarin.iOS.dll。</span><span class="sxs-lookup"><span data-stu-id="c22ab-208">MT0039: Applications targeting ARMv6 cannot reference Xamarin.iOS.dll.</span></span>

<a name="MT0040" />

### <a name="mt0040-could-not-find-the-assembly--referenced-by-"></a><span data-ttu-id="c22ab-209">MT0040:找不到組件 '\*'，參考的'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-209">MT0040: Could not find the assembly '\*', referenced by '\*'.</span></span>

<a name="MT0041" />

### <a name="mt0041-cannot-reference-both-monotouchdll-and-xamariniosdll"></a><span data-ttu-id="c22ab-210">MT0041:無法參考 'monotouch.dll' 和 'Xamarin.iOS.dll'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-210">MT0041: Cannot reference both 'monotouch.dll' and 'Xamarin.iOS.dll'.</span></span>

<a name="MT0042" />

### <a name="mt0042-no-reference-to-either-monotouchdll-or-xamariniosdll-was-found-a-reference-to-monotouchdll-will-be-added"></a><span data-ttu-id="c22ab-211">MT0042:找不到 monotouch.dll 或 Xamarin.iOS.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-211">MT0042: No reference to either monotouch.dll or Xamarin.iOS.dll was found.</span></span> <span data-ttu-id="c22ab-212">將加入 monotouch.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-212">A reference to monotouch.dll will be added.</span></span>

<a name="MT0043" />

### <a name="mt0043-the-boehm-garbage-collector-is-currently-not-supported-when-referencing-xamariniosdll-the-sgen-garbage-collector-has-been-selected-instead"></a><span data-ttu-id="c22ab-213">MT0043:Boehm 記憶體回收行程目前不支援參考 'Xamarin.iOS.dll' 時。</span><span class="sxs-lookup"><span data-stu-id="c22ab-213">MT0043: The Boehm garbage collector is currently not supported when referencing 'Xamarin.iOS.dll'.</span></span> <span data-ttu-id="c22ab-214">SGen 記憶體回收行程已改為選取。</span><span class="sxs-lookup"><span data-stu-id="c22ab-214">The SGen garbage collector has been selected instead.</span></span>

<span data-ttu-id="c22ab-215">整合專案支援只 SGen 記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="c22ab-215">Only the SGen garbage collector is supported with Unified projects.</span></span> <span data-ttu-id="c22ab-216">請確定有指定 Boehm 記憶體回收行程為任何其他 mtouch 旗標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-216">Ensure there are no additional mtouch flags specifying Boehm as the garbage collector.</span></span>

<a name="MT0044" />

### <a name="mt0044---listsim-is-only-supported-with-xcode-60-or-later"></a><span data-ttu-id="c22ab-217">MT0044:-listsim 僅適用於 Xcode 6.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-217">MT0044: --listsim is only supported with Xcode 6.0 or later.</span></span>

<span data-ttu-id="c22ab-218">安裝較新的 Xcode 版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-218">Install a newer Xcode version.</span></span>

<a name="MT0045" />

### <a name="mt0045---extension-is-only-supported-when-using-the-ios-80-or-later-sdk"></a><span data-ttu-id="c22ab-219">MT0045:-擴充功能僅適用於當使用 iOS 8.0 （含） 以後的 SDK。</span><span class="sxs-lookup"><span data-stu-id="c22ab-219">MT0045: --extension is only supported when using the iOS 8.0 (or later) SDK.</span></span>

<!-- MT0046 is not reported anymore -->

<a name="MT0047" />

### <a name="mt0047-the-minimum-deployment-target-for-unified-applications-is-511-the-current-deployment-target-is--please-select-a-newer-deployment-target-in-your-projects-ios-application-options"></a><span data-ttu-id="c22ab-220">MT0047:整合應用程式的最小的部署目標為 5.1.1，目前的部署目標為 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-220">MT0047: The minimum deployment target for Unified applications is 5.1.1, the current deployment target is '\*'.</span></span> <span data-ttu-id="c22ab-221">請在您專案的 iOS 應用程式的選項，選取較新的部署目標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-221">Please select a newer deployment target in your project's iOS Application options.</span></span>

<!-- MT0048 is not reported anymore -->

<a name="MT0049" />

### <a name="mt0049-framework-is-supported-only-if-deployment-target-is-80-or-later--features-might-not-work-correctly"></a><span data-ttu-id="c22ab-222">MT0049: \*.framework 才支援部署目標是 8.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-222">MT0049: \*.framework is supported only if deployment target is 8.0 or later.</span></span> <span data-ttu-id="c22ab-223">\* 功能可能無法正確運作。</span><span class="sxs-lookup"><span data-stu-id="c22ab-223">\* features might not work correctly.</span></span>

<span data-ttu-id="c22ab-224">在部署目標是指的 iOS 版本不支援指定的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-224">The specified framework is not supported in the iOS version the deployment target refers to.</span></span> <span data-ttu-id="c22ab-225">更新部署目標為較新的 iOS 版本，或是從應用程式中移除指定之 framework 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-225">Either update the deployment target to a newer iOS version, or remove usage of the specified framework from the app.</span></span>

<!-- MT0050 is not reported anymore -->

<a name="MT0051" />

### <a name="mt0051-xamarinios--requires-xcode-50-or-later-the-current-xcode-version-found-in--is-"></a><span data-ttu-id="c22ab-226">MT0051:Xamarin.iOS \* 需要 Xcode 5.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-226">MT0051: Xamarin.iOS \* requires Xcode 5.0 or later.</span></span> <span data-ttu-id="c22ab-227">目前的 Xcode 版本 (位於 \*) 是 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-227">The current Xcode version (found in \*) is \*.</span></span>

<span data-ttu-id="c22ab-228">安裝較新的 Xcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-228">Install a newer Xcode.</span></span>

<a name="MT0052" />

### <a name="mt0052-no-command-specified"></a><span data-ttu-id="c22ab-229">MT0052:指定任何命令。</span><span class="sxs-lookup"><span data-stu-id="c22ab-229">MT0052: No command specified.</span></span>

<span data-ttu-id="c22ab-230">對 mtouch 不指定任何動作。</span><span class="sxs-lookup"><span data-stu-id="c22ab-230">No action was specified for mtouch.</span></span>

<!-- 0053 is used by mmp -->

<a name="MT0054" />

### <a name="mt0054-unable-to-canonicalize-the-path--"></a><span data-ttu-id="c22ab-231">MT0054:無法規範化路徑 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-231">MT0054: Unable to canonicalize the path '\*': \*</span></span>

<span data-ttu-id="c22ab-232">這是內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-232">This is an internal error.</span></span> <span data-ttu-id="c22ab-233">如果您看到此錯誤，請將 bug 歸檔[http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-233">If you see this error, please file a bug [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT0055" />

### <a name="mt0055-the-xcode-path--does-not-exist"></a><span data-ttu-id="c22ab-234">MT0055:Xcode 路徑 ' \*' 不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-234">MT0055: The Xcode path '\*' does not exist.</span></span>

<span data-ttu-id="c22ab-235">使用 Xcode 路徑傳遞`--sdkroot`不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-235">The Xcode path passed using `--sdkroot` does not exist.</span></span> <span data-ttu-id="c22ab-236">請指定有效的路徑。</span><span class="sxs-lookup"><span data-stu-id="c22ab-236">Please specify a valid path.</span></span>

<a name="MT0056" />

### <a name="mt0056-cannot-find-xcode-in-the-default-location-applicationsxcodeapp-please-install-xcode-or-pass-a-custom-path-using---sdkroot-path"></a><span data-ttu-id="c22ab-237">MT0056:在預設位置找不到 Xcode (/ /applications/xcode.app)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-237">MT0056: Cannot find Xcode in the default location (/Applications/Xcode.app).</span></span> <span data-ttu-id="c22ab-238">請安裝 Xcode，或傳遞自訂路徑使用--sdkroot <path>。</span><span class="sxs-lookup"><span data-stu-id="c22ab-238">Please install Xcode, or pass a custom path using --sdkroot <path>.</span></span>

<a name="MT0057" />

### <a name="mt0057-cannot-determine-the-path-to-xcodeapp-from-the-sdk-root--please-specify-the-full-path-to-the-xcodeapp-bundle"></a><span data-ttu-id="c22ab-239">MT0057:無法判定要 Xcode.app 的路徑從 sdk 根目錄 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-239">MT0057: Cannot determine the path to Xcode.app from the sdk root '\*'.</span></span> <span data-ttu-id="c22ab-240">請指定 Xcode.app 套件組合的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c22ab-240">Please specify the full path to the Xcode.app bundle.</span></span>

<span data-ttu-id="c22ab-241">路徑可讓您傳遞使用`--sdkroot`未指定有效的 Xcode 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-241">The path passed using `--sdkroot` does not specify a valid Xcode app.</span></span> <span data-ttu-id="c22ab-242">請指定要將 Xcode 應用程式的路徑。</span><span class="sxs-lookup"><span data-stu-id="c22ab-242">Please specify a path to an Xcode app.</span></span>

<a name="MT0058" />

### <a name="mt0058-the-xcodeapp--is-invalid-the-file--does-not-exist"></a><span data-ttu-id="c22ab-243">MT0058:Xcode.app '\*' 無效 (檔案 '\*' 不存在)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-243">MT0058: The Xcode.app '\*' is invalid (the file '\*' does not exist).</span></span>

<span data-ttu-id="c22ab-244">路徑可讓您傳遞使用`--sdkroot`未指定有效的 Xcode 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-244">The path passed using `--sdkroot` does not specify a valid Xcode app.</span></span> <span data-ttu-id="c22ab-245">請指定要將 Xcode 應用程式的路徑。</span><span class="sxs-lookup"><span data-stu-id="c22ab-245">Please specify a path to an Xcode app.</span></span>

<a name="MT0059" />

### <a name="mt0059-could-not-find-the-currently-selected-xcode-on-the-system-"></a><span data-ttu-id="c22ab-246">MT0059:在系統上找不到目前選取的 Xcode: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-246">MT0059: Could not find the currently selected Xcode on the system: \*</span></span>

<a name="MT0060" />

### <a name="mt0060-could-not-find-the-currently-selected-xcode-on-the-system-xcode-select---print-path-returned--but-that-directory-does-not-exist"></a><span data-ttu-id="c22ab-247">MT0060:在系統上找不到目前選取的 Xcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-247">MT0060: Could not find the currently selected Xcode on the system.</span></span> <span data-ttu-id="c22ab-248">'xcode-select--列印路徑' 傳回 ' \*'，但該目錄不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-248">'xcode-select --print-path' returned '\*', but that directory does not exist.</span></span>

<a name="MT0061" />

### <a name="mt0061-no-xcodeapp-specified-using---sdkroot-using-the-system-xcode-as-reported-by-xcode-select---print-path-"></a><span data-ttu-id="c22ab-249">MT0061:沒有 Xcode.app specified （使用--sdkroot），使用系統 Xcode 所報告 ' xcode-select--列印路徑 ': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-249">MT0061: No Xcode.app specified (using --sdkroot), using the system Xcode as reported by 'xcode-select --print-path': \*</span></span>

<span data-ttu-id="c22ab-250">此為參考用的警告，說明 Xcode 會使用，因為未指定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-250">This is a informational warning, explaining which Xcode will be used, since none was specified.</span></span>

<a name="MT0062" />

### <a name="mt0062-no-xcodeapp-specified-using---sdkroot-or-xcode-select---print-path-using-the-default-xcode-instead-"></a><span data-ttu-id="c22ab-251">MT0062:沒有 Xcode.app specified （使用--sdkroot 或 ' xcode-select--列印路徑 '），改為使用預設 Xcode: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-251">MT0062: No Xcode.app specified (using --sdkroot or 'xcode-select --print-path'), using the default Xcode instead: \*</span></span>

<span data-ttu-id="c22ab-252">此為參考用的警告，說明 Xcode 會使用，因為未指定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-252">This is a informational warning, explaining which Xcode will be used, since none was specified.</span></span>

<a name="MT0063" />

### <a name="mt0063-cannot-find-the-executable-in-the-extension--no-cfbundleexecutable-entry-in-its-infoplist"></a><span data-ttu-id="c22ab-253">MT0063:找不到延伸模組中可執行檔 \* （在其 Info.plist 中的沒有 CFBundleExecutable 項目）</span><span class="sxs-lookup"><span data-stu-id="c22ab-253">MT0063: Cannot find the executable in the extension \* (no CFBundleExecutable entry in its Info.plist)</span></span>

<span data-ttu-id="c22ab-254">每個 Info.plist 必須有可執行檔 （使用 CFBundleExecutable 項目），不過應該會自動產生的項目，在建置期間。</span><span class="sxs-lookup"><span data-stu-id="c22ab-254">Every Info.plist must have an executable (using the CFBundleExecutable entry), however an entry should be generated automatically during the build.</span></span>

<span data-ttu-id="c22ab-255">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-255">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0064" />

### <a name="mt0064-xamarinios-only-supports-embedded-frameworks-with-unified-projects"></a><span data-ttu-id="c22ab-256">MT0064:Xamarin.iOS 只支援內嵌的架構，與整合專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-256">MT0064: Xamarin.iOS only supports embedded frameworks with Unified projects.</span></span>

<span data-ttu-id="c22ab-257">Xamarin.iOS 時，才支援內嵌的架構使用統一的 API;請更新您的專案使用統一的 API。</span><span class="sxs-lookup"><span data-stu-id="c22ab-257">Xamarin.iOS only supports embedded frameworks when using the Unified API; please update your project to use the Unified API.</span></span>

<a name="MT0065" />

### <a name="mt0065-xamarinios-only-supports-embedded-frameworks-when-deployment-target-is-at-least-80-current-deployment-target--embedded-frameworks-"></a><span data-ttu-id="c22ab-258">MT0065:Xamarin.iOS 時，才支援內嵌的架構部署目標是至少 8.0 (目前的部署目標: \* 內嵌架構: \*)</span><span class="sxs-lookup"><span data-stu-id="c22ab-258">MT0065: Xamarin.iOS only supports embedded frameworks when deployment target is at least 8.0 (current deployment target: \* embedded frameworks: \*)</span></span>

<span data-ttu-id="c22ab-259">Xamarin.iOS 會在部署目標是至少 8.0 （因為舊版 iOS 不支援內嵌的架構） 時，才支援內嵌的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-259">Xamarin.iOS only supports embedded frameworks when the deployment target is at least 8.0 (because earlier versions of iOS does not support embedded frameworks).</span></span>

<span data-ttu-id="c22ab-260">請更新至 8.0 或更新版本的專案的 Info.plist 中的部署目標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-260">Please update the deployment target in the project's Info.plist to 8.0 or higher.</span></span>

<a name="MT0066" />

### <a name="mt0066-invalid-build-registrar-assembly-"></a><span data-ttu-id="c22ab-261">MT0066:無效的組建註冊機構的組件: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-261">MT0066: Invalid build registrar assembly: \*</span></span>

<span data-ttu-id="c22ab-262">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-262">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0067" />

### <a name="mt0067-invalid-registrar-"></a><span data-ttu-id="c22ab-263">MT0067:無效的註冊機構: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-263">MT0067: Invalid registrar: \*</span></span>

<span data-ttu-id="c22ab-264">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-264">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0068" />

### <a name="mt0068-invalid-value-for-target-framework-"></a><span data-ttu-id="c22ab-265">MT0068:目標 framework 的值無效: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-265">MT0068: Invalid value for target framework: \*.</span></span>

<span data-ttu-id="c22ab-266">使用已傳遞無效的目標 framework-目標 framework 引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-266">An invalid target framework was passed using the --target-framework argument.</span></span> <span data-ttu-id="c22ab-267">請指定有效的目標 framework。</span><span class="sxs-lookup"><span data-stu-id="c22ab-267">Please specify a valid target framework.</span></span>

<a name="MT0069" />

<!--### MT0069: currently unused -->

<a name="MT0070" />

### <a name="mt0070-invalid-target-framework--valid-target-frameworks-are-"></a><span data-ttu-id="c22ab-268">MT0070:無效的目標 framework: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-268">MT0070: Invalid target framework: \*.</span></span> <span data-ttu-id="c22ab-269">有效的目標架構: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-269">Valid target frameworks are: \*.</span></span>

<span data-ttu-id="c22ab-270">使用已傳遞無效的目標 framework-目標 framework 引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-270">An invalid target framework was passed using the --target-framework argument.</span></span> <span data-ttu-id="c22ab-271">請指定有效的目標 framework。</span><span class="sxs-lookup"><span data-stu-id="c22ab-271">Please specify a valid target framework.</span></span>

<a name="MT0071" />

### <a name="mt0071-unknown-platform--this-usually-indicates-a-bug-in-xamarinios-please-file-a-bug-report-at-httpbugzillaxamarincom-with-a-test-case"></a><span data-ttu-id="c22ab-272">MT0071:未知的平台: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-272">MT0071: Unknown platform: \*.</span></span> <span data-ttu-id="c22ab-273">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 http://bugzilla.xamarin.com 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-273">This usually indicates a bug in Xamarin.iOS; please file a bug report at http://bugzilla.xamarin.com with a test case.</span></span>

<span data-ttu-id="c22ab-274">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-274">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0072" />

### <a name="mt0072-extensions-are-not-supported-for-the-platform-"></a><span data-ttu-id="c22ab-275">MT0072:平台不支援的副檔名 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-275">MT0072: Extensions are not supported for the platform '\*'.</span></span>

<span data-ttu-id="c22ab-276">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-276">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0073" />

### <a name="mt0073-xamarinios--does-not-support-a-deployment-target-of--the-minimum-is--please-select-a-newer-deployment-target-in-your-projects-infoplist"></a><span data-ttu-id="c22ab-277">MT0073:Xamarin.iOS \* 不支援的部署目標 \* (最小值是 \*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-277">MT0073: Xamarin.iOS \* does not support a deployment target of \* (the minimum is \*).</span></span> <span data-ttu-id="c22ab-278">請在您專案的 Info.plist 中，選取較新的部署目標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-278">Please select a newer deployment target in your project's Info.plist.</span></span>

<span data-ttu-id="c22ab-279">最小的部署目標是所指定的錯誤訊息;請選取專案的 Info.plist 中的較新的部署目標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-279">The minimum deployment target is the one specified in the error message; please select a newer deployment target in the project's Info.plist.</span></span>

<span data-ttu-id="c22ab-280">如果更新部署的目標不可行，請使用較舊版本的 Xamarin.iOS。</span><span class="sxs-lookup"><span data-stu-id="c22ab-280">If updating the deployment target is not possible, then please use an older version of Xamarin.iOS.</span></span>

<a name="MT0074" />

### <a name="mt0074-xamarinios--does-not-support-a-minimum-deployment-target-of--the-maximum-is--please-select-an-older-deployment-target-in-your-projects-infoplist-or-upgrade-to-a-newer-version-of-xamarinios"></a><span data-ttu-id="c22ab-281">MT0074:Xamarin.iOS \* 不支援的最小的部署目標 \* (最大值是 \*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-281">MT0074: Xamarin.iOS \* does not support a minimum deployment target of \* (the maximum is \*).</span></span> <span data-ttu-id="c22ab-282">請選取您專案的 Info.plist 中的較舊的部署目標，或升級至較新的 Xamarin.iOS 版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-282">Please select an older deployment target in your project's Info.plist or upgrade to a newer version of Xamarin.iOS.</span></span>

<span data-ttu-id="c22ab-283">Xamarin.iOS 不支援將最小的部署目標設定為版本高於此特定版本的 Xamarin.iOS 建置的版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-283">Xamarin.iOS does not support setting the minimum deployment target to a higher version than the version this particular version of Xamarin.iOS was built for.</span></span>

<span data-ttu-id="c22ab-284">請在專案的 Info.plist 中，選取舊的最低部署目標或升級至較新的 Xamarin.iOS 版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-284">Please select an older minimum deployment target in the project's Info.plist, or upgrade to a newer version of Xamarin.iOS.</span></span>

<a name="MT0075" />

### <a name="mt0075-invalid-architecture--for--projects-valid-architectures-are-"></a><span data-ttu-id="c22ab-285">MT0075:無效的架構 ' \*' 的 \* 專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-285">MT0075: Invalid architecture '\*' for \* projects.</span></span> <span data-ttu-id="c22ab-286">有效的架構: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-286">Valid architectures are: \*</span></span>

<span data-ttu-id="c22ab-287">指定無效的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-287">An invalid architecture was specified.</span></span> <span data-ttu-id="c22ab-288">請確認該架構有效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-288">Please verify that architecture is valid.</span></span>

<a name="MT0076" />

### <a name="mt0075-no-architecture-specified-using-the---abi-argument-an-architecture-is-required-for--projects"></a><span data-ttu-id="c22ab-289">MT0075:（使用-abi 引數） 指定任何架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-289">MT0075: No architecture specified (using the --abi argument).</span></span> <span data-ttu-id="c22ab-290">架構是為了 \* 專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-290">An architecture is required for \* projects.</span></span>

<span data-ttu-id="c22ab-291">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-291">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0077" />

### <a name="mt0076-watchos-projects-must-be-extensions"></a><span data-ttu-id="c22ab-292">MT0076:WatchOS 專案必須是延伸模組。</span><span class="sxs-lookup"><span data-stu-id="c22ab-292">MT0076: WatchOS projects must be extensions.</span></span>

<span data-ttu-id="c22ab-293">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-293">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0078" />

### <a name="mt0077-incremental-builds-are-enabled-with-a-deployment-target--80-currently--this-is-not-supported-the-resulting-application-will-not-launch-on-ios-9-so-the-deployment-target-will-be-set-to-80"></a><span data-ttu-id="c22ab-294">MT0077:啟用累加建置與部署目標 < 8.0 (目前 \*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-294">MT0077: Incremental builds are enabled with a deployment target < 8.0 (currently \*).</span></span> <span data-ttu-id="c22ab-295">這不支援 （產生的應用程式將不會啟動在 iOS 9），因此部署目標將設為 8.0。</span><span class="sxs-lookup"><span data-stu-id="c22ab-295">This is not supported (the resulting application will not launch on iOS 9), so the deployment target will be set to 8.0.</span></span>

<span data-ttu-id="c22ab-296">這是警告，通知，部署目標已設定為此組建的 8.0，累加建置才能工作正確。</span><span class="sxs-lookup"><span data-stu-id="c22ab-296">This is a warning informing that the deployment target has been set to 8.0 for this build so that incremental builds work properly.</span></span>

<span data-ttu-id="c22ab-297">當部署目標是至少 8.0 （因為產生的應用程式將不會啟動在 iOS 9 否則） 時，才支援累加建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-297">Incremental builds are only supported when the deployment target is at least 8.0 (because the resulting application will not launch on iOS 9 otherwise).</span></span>

<a name="MT0079" />

### <a name="mt0078-the-recommended-xcode-version-for-xamarinios--is-xcode--or-later-the-current-xcode-version-found-in--is-"></a><span data-ttu-id="c22ab-298">MT0078:建議的 Xcode 版本，適用於 Xamarin.iOS \* 是 Xcode \* 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-298">MT0078: The recommended Xcode version for Xamarin.iOS \* is Xcode \* or later.</span></span> <span data-ttu-id="c22ab-299">目前的 Xcode 版本 (位於 \*) 是 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-299">The current Xcode version (found in \*) is \*.</span></span>

<span data-ttu-id="c22ab-300">這是警告，通知目前的 Xcode 版本不此版本的 Xamarin.iOS 的建議的版本的 Xcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-300">This is a warning informing that the current version of Xcode is not the recommended version of Xcode for this version of Xamarin.iOS.</span></span>

<span data-ttu-id="c22ab-301">請先升級 Xcode，以確保最佳的行為。</span><span class="sxs-lookup"><span data-stu-id="c22ab-301">Please upgrade Xcode to ensure optimal behavior.</span></span>

<a name="MT0080" />

### <a name="mt0080-disabling-newrefcount---new-refcountfalse-is-deprecated"></a><span data-ttu-id="c22ab-302">MT0080:停用 NewRefCount、--新增-refcount:false，已被取代。</span><span class="sxs-lookup"><span data-stu-id="c22ab-302">MT0080: Disabling NewRefCount, --new-refcount:false, is deprecated.</span></span>

<span data-ttu-id="c22ab-303">這是警告，通知，若要停用新要求 refcount (-新增-refcount:false) 已被忽略。</span><span class="sxs-lookup"><span data-stu-id="c22ab-303">This is a warning informing that the request to disable the new refcount (--new-refcount:false) has been ignored.</span></span>

<span data-ttu-id="c22ab-304">新的 refcount 功能現在是必要的所有專案，而且不因此可以再停用。</span><span class="sxs-lookup"><span data-stu-id="c22ab-304">The new refcount feature is now mandatory for all projects, and it's thus not possible to disable anymore.</span></span>

<a name="MT0081" />

### <a name="mt0081-the-command-line-argument---download-crash-report-also-requires---download-crash-report-to"></a><span data-ttu-id="c22ab-305">MT0081:命令列引數--下載損毀報表也需要-下載-損毀-報表。</span><span class="sxs-lookup"><span data-stu-id="c22ab-305">MT0081: The command line argument --download-crash-report also requires --download-crash-report-to.</span></span>

<a name="MT0082" />

### <a name="mt0082-repl---enable-repl-is-only-supported-when-linking-is-not-used---nolink"></a><span data-ttu-id="c22ab-306">MT0082:REPL (-啟用 repl) 不使用連結時，才支援 (-nolink)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-306">MT0082: REPL (--enable-repl) is only supported when linking is not used (--nolink).</span></span>

<a name="MT0083" />

### <a name="mt0083-asm-only-bitcode-is-not-supported-on-watchos-use-either---bitcodemarker-or---bitcodefull"></a><span data-ttu-id="c22ab-307">MT0083:WatchOS 不支援僅限 Asm 的 bitcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-307">MT0083: Asm-only bitcode is not supported on watchOS.</span></span> <span data-ttu-id="c22ab-308">使用任一-bitcode： 標記或-bitcode： 完整。</span><span class="sxs-lookup"><span data-stu-id="c22ab-308">Use either --bitcode:marker or --bitcode:full.</span></span>

<a name="MT0084" />

### <a name="mt0084-bitcode-is-not-supported-in-the-simulator-do-not-pass---bitcode-when-building-for-the-simulator"></a><span data-ttu-id="c22ab-309">MT0084:在模擬器中不支援 Bitcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-309">MT0084: Bitcode is not supported in the simulator.</span></span> <span data-ttu-id="c22ab-310">當模擬器的建置，請不要傳遞-bitcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-310">Do not pass --bitcode when building for the simulator.</span></span>

<a name="MT0085" />

### <a name="mt0085-no-reference-to--was-found-it-will-be-added-automatically"></a><span data-ttu-id="c22ab-311">MT0085:不到參考 ' \*' 找不到。</span><span class="sxs-lookup"><span data-stu-id="c22ab-311">MT0085: No reference to '\*' was found.</span></span> <span data-ttu-id="c22ab-312">它會自動加入。</span><span class="sxs-lookup"><span data-stu-id="c22ab-312">It will be added automatically.</span></span>

<a name="MT0086" />

### <a name="mt0086-a-target-framework---target-framework-must-be-specified-when-building-for-tvos-or-watchos"></a><span data-ttu-id="c22ab-313">MT0086:目標 framework (-目標架構) 建置 TVOS 或 WatchOS 時必須指定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-313">MT0086: A target framework (--target-framework) must be specified when building for TVOS or WatchOS.</span></span>

<span data-ttu-id="c22ab-314">這通常表示 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-314">This usually indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0087" />

### <a name="mt0087-incremental-builds---fastdev-is-not-supported-with-the-boehm-gc-incremental-builds-will-be-disabled"></a><span data-ttu-id="c22ab-315">MT0087:累加建置 (-fastdev) 不支援 Boehm GC。</span><span class="sxs-lookup"><span data-stu-id="c22ab-315">MT0087: Incremental builds (--fastdev) is not supported with the Boehm GC.</span></span> <span data-ttu-id="c22ab-316">將停用累加建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-316">Incremental builds will be disabled.</span></span>

<a name="MT0088" />

### <a name="mt0088-the-gc-must-be-in-cooperative-mode-for-watchos-apps-please-remove-the---coopfalse-argument-to-mtouch"></a><span data-ttu-id="c22ab-317">MT0088:GC 必須是合作式 watchOS 應用程式的模式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-317">MT0088: The GC must be in cooperative mode for watchOS apps.</span></span> <span data-ttu-id="c22ab-318">請移除 mtouch--coop: false 引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-318">Please remove the --coop:false argument to mtouch.</span></span>

<a name="MT0089" />

### <a name="mt0089-the-option--cannot-take-the-value--when-cooperative-mode-is-enabled-for-the-gc"></a><span data-ttu-id="c22ab-319">MT0089:選項 '\*'無法接受的值'\*' GC 啟用合作式的模式時。</span><span class="sxs-lookup"><span data-stu-id="c22ab-319">MT0089: The option '\*' cannot take the value '\*' when cooperative mode is enabled for the GC.</span></span>

<a name="MT0091" />

### <a name="mt0091-this-version-of-xamarinios-requires-the--sdk-shipped-with-xcode--either-upgrade-xcode-to-get-the-required-header-files-or-set-the-managed-linker-behaviour-to-link-framework-sdks-only-to-try-to-avoid-the-new-apis"></a><span data-ttu-id="c22ab-320">MT0091:此版本的 Xamarin.iOS 需要 \* SDK (隨附於 Xcode \*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-320">MT0091: This version of Xamarin.iOS requires the \* SDK (shipped with Xcode \*).</span></span> <span data-ttu-id="c22ab-321">請升級以取得必要的標頭檔，或設為 僅連結 Framework Sdk （若要盡量避免新的 Api） 的受管理的連結器行為的 Xcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-321">Either upgrade Xcode to get the required header files or set the managed linker behaviour to Link Framework SDKs Only (to try to avoid the new APIs).</span></span>

<span data-ttu-id="c22ab-322">Xamarin.iOS 需要的標頭檔，從指定的錯誤訊息，來建置您的應用程式中的 SDK 版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-322">Xamarin.iOS requires the header files, from the SDK version specified in the error message, to build your application.</span></span> <span data-ttu-id="c22ab-323">若要修正此錯誤的建議的方式是升級 Xcode 來取得必要的 SDK，這將包含所有必要的標頭檔案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-323">The recommended way to fix this error is to upgrade Xcode to get the required SDK, this will include all the required header files.</span></span> <span data-ttu-id="c22ab-324">如果您有多個版本的 Xcode 安裝，或想要使用 Xcode，在非預設位置，請確定您的 IDE 喜好設定中設定正確的 Xcode 位置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-324">If you have multiple versions of Xcode installed, or want to use an Xcode in a non-default location, make sure to set the correct Xcode location in your IDE's preferences.</span></span>

<span data-ttu-id="c22ab-325">潛在的優點，替代方案是讓受管理的連結器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-325">A potential, alternative solution is to enable the managed linker.</span></span> <span data-ttu-id="c22ab-326">這會移除未使用的 API 包括在大部分情況下，新的 API，其中的標頭檔案已遺失 （或不完整）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-326">This will remove unused API including, in most cases, the new API where the header files are missing (or incomplete).</span></span> <span data-ttu-id="c22ab-327">不過如果您的專案使用較新的 SDK 與您的 Xcode 中所導入的 API，將不會運作這所提供。</span><span class="sxs-lookup"><span data-stu-id="c22ab-327">However this will not work if your project uses API that was introduced in a newer SDK than the one your Xcode provides.</span></span>

<span data-ttu-id="c22ab-328">最後一個 straw 解決方案是使用較舊版本的 Xamarin.iOS，支援您的專案的 SDK 需要。</span><span class="sxs-lookup"><span data-stu-id="c22ab-328">A last-straw solution would be to use an older version of Xamarin.iOS, one that supports the SDK your project requires.</span></span>

<!-- MT0092 used by mlaunch -->

<a name="MT0093" />

### <a name="mt0093-could-not-find-mlaunch"></a><span data-ttu-id="c22ab-329">MT0093:找不到 'mlaunch'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-329">MT0093: Could not find 'mlaunch'.</span></span>

<!-- MT0094 is not reported anymore -->

<a name="MT0095" />

### <a name="mt0095-aot-files-could-not-be-copied-to-the-destination-directory-dest-error"></a><span data-ttu-id="c22ab-330">MT0095:Aot 檔案無法複製的目的地目錄 {dest}: {error}</span><span class="sxs-lookup"><span data-stu-id="c22ab-330">MT0095: Aot files could not be copied to the destination directory {dest}: {error}</span></span>

<a name="MT0096" />

### <a name="mt0096-no-reference-to-xamariniosdll-was-found"></a><span data-ttu-id="c22ab-331">MT0096:找不到 Xamarin.iOS.dll 的參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-331">MT0096: No reference to Xamarin.iOS.dll was found.</span></span>

<!-- MT0097: used by mmp -->
<!-- MT0098: used by mmp -->

<a name="MT0099" />

### <a name="mt0099-internal-error--please-file-a-bug-report-with-a-test-case-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-332">MT0099:內部錯誤 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-332">MT0099: Internal error \*.</span></span> <span data-ttu-id="c22ab-333">請提出問題報告與測試案例 ( http://bugzilla.xamarin.com) 。</span><span class="sxs-lookup"><span data-stu-id="c22ab-333">Please file a bug report with a test case (http://bugzilla.xamarin.com).</span></span>

<span data-ttu-id="c22ab-334">在 Xamarin.iOS 中的內部一致性檢查失敗時，會報告此錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c22ab-334">This error message is reported when an internal consistency check in Xamarin.iOS fails.</span></span>

<span data-ttu-id="c22ab-335">這表示在 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-335">This indicates a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0100" />

### <a name="mt0100-invalid-assembly-build-target--please-file-a-bug-report-with-a-test-case-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-336">MT0100:無效的組件建置目標: ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-336">MT0100: Invalid assembly build target: '\*'.</span></span> <span data-ttu-id="c22ab-337">請提出問題報告與測試案例 ( http://bugzilla.xamarin.com) 。</span><span class="sxs-lookup"><span data-stu-id="c22ab-337">Please file a bug report with a test case (http://bugzilla.xamarin.com).</span></span>

<span data-ttu-id="c22ab-338">在 Xamarin.iOS 中的內部一致性檢查失敗時，會報告此錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c22ab-338">This error message is reported when an internal consistency check in Xamarin.iOS fails.</span></span>

<span data-ttu-id="c22ab-339">這一律是 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-339">This is always a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test case.</span></span>

<a name="MT0101" />

### <a name="mt0101-the-assembly--is-specified-multiple-times-in---assembly-build-target-arguments"></a><span data-ttu-id="c22ab-340">MT0101:組件 ' \*'-組件建置目標引數中指定多次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-340">MT0101: The assembly '\*' is specified multiple times in --assembly-build-target arguments.</span></span>

<span data-ttu-id="c22ab-341">錯誤訊息中所述的組件指定了多次-組件建置目標引數中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-341">The assembly mentioned in the error message is specified multiple times in --assembly-build-target arguments.</span></span> <span data-ttu-id="c22ab-342">請確定每個組件只提及一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-342">Please make sure each assembly is only mentioned once.</span></span>

<a name="MT0102" />

### <a name="mt0102-the-assemblies--and--have-the-same-target-name--but-different-targets--and-"></a><span data-ttu-id="c22ab-343">MT0102:組件\*'和'\*'具有相同的目標名稱 ('\*')，但不同的目標 ('\*' 和 ' \*')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-343">MT0102: The assemblies '\*' and '\*' have the same target name ('\*'), but different targets ('\*' and '\*').</span></span>

<span data-ttu-id="c22ab-344">錯誤訊息中所述的組件具有衝突的建置目標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-344">The assemblies mentioned in the error message have conflicting build targets.</span></span>

<span data-ttu-id="c22ab-345">例如：</span><span class="sxs-lookup"><span data-stu-id="c22ab-345">For example:</span></span>

    --assembly-build-target:Assembly1.dll=framework=MyBinary --assembly-build-target:Assembly2.dll=dynamiclibrary=MyBinary

<span data-ttu-id="c22ab-346">此範例中嘗試使用相同的廠牌建立動態程式庫和架構 (`MyBinary`)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-346">This example is trying to create both a dynamic library and a framework with the same make (`MyBinary`).</span></span>

<a name="MT0103" />

### <a name="mt0103-the-static-object--contains-more-than-one-assembly--but-each-static-object-must-correspond-with-exactly-one-assembly"></a><span data-ttu-id="c22ab-347">MT0103:靜態物件 '\*' 包含多個組件 ('\*')，但每個靜態物件必須對應至一個組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-347">MT0103: The static object '\*' contains more than one assembly ('\*'), but each static object must correspond with exactly one assembly.</span></span>

<span data-ttu-id="c22ab-348">錯誤訊息中所述的組件全部會編譯成單一的靜態物件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-348">The assemblies mentioned in the error message are all compiled to a single static object.</span></span> <span data-ttu-id="c22ab-349">這不允許，每個組件必須先編譯成不同的靜態物件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-349">This is not allowed, every assembly must be compiled to a different static object.</span></span>

<span data-ttu-id="c22ab-350">例如: </span><span class="sxs-lookup"><span data-stu-id="c22ab-350">For example:</span></span>

    --assembly-build-target:Assembly1.dll=staticobject=MyBinary --assembly-build-target:Assembly2.dll=staticobject=MyBinary

<span data-ttu-id="c22ab-351">此範例會嘗試建立靜態物件 (`MyBinary`) 包含兩個組件 (`Assembly1.dll`和`Assembly2.dll`)，這不允許。</span><span class="sxs-lookup"><span data-stu-id="c22ab-351">This example tries to build a static object (`MyBinary`) comprised of two assemblies (`Assembly1.dll` and `Assembly2.dll`), which is not allowed.</span></span>

<a name="MT0105" />

### <a name="mt0105-no-assembly-build-target-was-specified-for-"></a><span data-ttu-id="c22ab-352">MT0105:沒有組件建置目標已指定 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-352">MT0105: No assembly build target was specified for '\*'.</span></span>

<span data-ttu-id="c22ab-353">指定的組件時建置目標使用`--assembly-build-target`，應用程式中的每個組件必須具有指派的建置目標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-353">When specifying the assembly build target using `--assembly-build-target`, every assembly in the app must have a build target assigned.</span></span>

<span data-ttu-id="c22ab-354">錯誤訊息中所述的組件沒有建立指派的目標組件時，會報告此錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-354">This error is reported when the assembly mentioned in the error message does not have an assembly build target assigned.</span></span>

<span data-ttu-id="c22ab-355">請參閱的文件`--assembly-build-target`如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c22ab-355">See the documentation about `--assembly-build-target` for further information.</span></span>

<a name="MT0106" />

### <a name="mt0106-the-assembly-build-target-name--is-invalid-the-character--is-not-allowed"></a><span data-ttu-id="c22ab-356">MT0106:組件建置目標名稱 '\*' 無效： 字元 '\*' 不允許。</span><span class="sxs-lookup"><span data-stu-id="c22ab-356">MT0106: The assembly build target name '\*' is invalid: the character '\*' is not allowed.</span></span>

<span data-ttu-id="c22ab-357">組件的 build 目標名稱必須是有效的檔名。</span><span class="sxs-lookup"><span data-stu-id="c22ab-357">The assembly build target name must be a valid filename.</span></span>

<span data-ttu-id="c22ab-358">比方說這些值將會觸發此錯誤：</span><span class="sxs-lookup"><span data-stu-id="c22ab-358">For example these values will trigger this error:</span></span>

    --assembly-build-target:Assembly1.dll=staticobject=my/path.o

<span data-ttu-id="c22ab-359">因為`my/path.o`不是有效的檔名，因為目錄分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="c22ab-359">because `my/path.o` is not a valid filename due to the directory separator character.</span></span>

<a name="MT0107" />

### <a name="mt0107-the-assemblies--have-different-custom-llvm-optimizations--which-is-not-allowed-when-they-are-all-compiled-to-a-single-binary"></a><span data-ttu-id="c22ab-360">MT0107:組件\*' 有不同的自訂 LLVM 最佳化 (\*)，這不允許在所有編譯時與單一的二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-360">MT0107: The assemblies '\*' have different custom LLVM optimizations (\*), which is not allowed when they are all compiled to a single binary.</span></span>

<a name="MT0108" />

### <a name="mt0108-the-assembly-build-target--did-not-match-any-assemblies"></a><span data-ttu-id="c22ab-361">MT0108:組件建置目標 ' \*' 不符合任何組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-361">MT0108: The assembly build target '\*' did not match any assemblies.</span></span>

<a name="MT0109" />

### <a name="mt0109-the-assembly-0-was-loaded-from-a-different-path-than-the-provided-path-provided-path-1-actual-path-2"></a><span data-ttu-id="c22ab-362">MT0109:組件 '{0}' 已從提供的路徑不同的路徑載入 (提供路徑： {1}，實際路徑： {2})。</span><span class="sxs-lookup"><span data-stu-id="c22ab-362">MT0109: The assembly '{0}' was loaded from a different path than the provided path (provided path: {1}, actual path: {2}).</span></span>

<span data-ttu-id="c22ab-363">這是一個警告，指出應用程式所參考的組件已載入不同的位置從比要求。</span><span class="sxs-lookup"><span data-stu-id="c22ab-363">This is a warning indicating that an assembly referenced by the application was loaded from a different location than requested.</span></span>

<span data-ttu-id="c22ab-364">這可能表示應用程式會參考多個組件名稱相同，但從不同的位置，可能會導致非預期的結果 （將使用第一個組件）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-364">This might mean that the app is referencing multiple assemblies with the same name, but from different locations, which might lead to unexpected results (only the first assembly will be used).</span></span>

<a name="MT0110" />

### <a name="mt0110-incremental-builds-have-been-disabled-because-this-version-of-xamarinios-does-not-support-incremental-builds-in-projects-that-include-third-party-binding-libraries-and-that-compiles-to-bitcode"></a><span data-ttu-id="c22ab-365">MT0110:因為此版本的 Xamarin.iOS 不支援累加建置專案，包含第三方繫結程式庫，且會編譯成 bitcode 中已停用累加建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-365">MT0110: Incremental builds have been disabled because this version of Xamarin.iOS does not support incremental builds in projects that include third-party binding libraries and that compiles to bitcode.</span></span>

<span data-ttu-id="c22ab-366">因為此版本的 Xamarin.iOS 不支援累加建置專案，包含第三方繫結程式庫，且會編譯成 bitcode （tvOS 和 watchOS 專案） 中已停用累加建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-366">Incremental builds have been disabled because this version of Xamarin.iOS does not support incremental builds in projects that include third-party binding libraries and that compiles to bitcode (tvOS and watchOS projects).</span></span>

<span data-ttu-id="c22ab-367">您需要採取任何動作，此訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-367">No action is required on your part, this message is purely informational.</span></span>

<span data-ttu-id="c22ab-368">如需進一步資訊 bug #[51710](https://bugzilla.xamarin.com/show_bug.cgi?id=51710)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-368">For further information see bug #[51710](https://bugzilla.xamarin.com/show_bug.cgi?id=51710).</span></span>

<span data-ttu-id="c22ab-369">不會再報告這個警告。</span><span class="sxs-lookup"><span data-stu-id="c22ab-369">This warning is not reported anymore.</span></span>

<a name="MT0111" />

### <a name="mt0111-bitcode-has-been-enabled-because-this-version-of-xamarinios-does-not-support-building-watchos-projects-using-llvm-without-enabling-bitcode"></a><span data-ttu-id="c22ab-370">MT0111:Bitcode 尚未啟用，因為此版本的 Xamarin.iOS 不支援建置 watchOS 專案而不啟用 bitcode 使用 LLVM。</span><span class="sxs-lookup"><span data-stu-id="c22ab-370">MT0111: Bitcode has been enabled because this version of Xamarin.iOS does not support building watchOS projects using LLVM without enabling bitcode.</span></span>

<span data-ttu-id="c22ab-371">Bitcode 已啟用自動因為此版本的 Xamarin.iOS 不支援建置 watchOS 專案而不啟用 bitcode 使用 LLVM。</span><span class="sxs-lookup"><span data-stu-id="c22ab-371">Bitcode has been enabled automatically because this version of Xamarin.iOS does not support building watchOS projects using LLVM without enabling bitcode.</span></span>

<span data-ttu-id="c22ab-372">您需要採取任何動作，此訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-372">No action is required on your part, this message is purely informational.</span></span>

<span data-ttu-id="c22ab-373">如需進一步資訊 bug #[51634](https://bugzilla.xamarin.com/show_bug.cgi?id=51634)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-373">For further information see bug #[51634](https://bugzilla.xamarin.com/show_bug.cgi?id=51634).</span></span>

<a name="MT0112" />

### <a name="mt0112-native-code-sharing-has-been-disabled-because-"></a><span data-ttu-id="c22ab-374">MT0112:原生程式碼共用已停用，因為 \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-374">MT0112: Native code sharing has been disabled because \*</span></span>

<span data-ttu-id="c22ab-375">有多個原因，可以停用共用程式碼：</span><span class="sxs-lookup"><span data-stu-id="c22ab-375">There are multiple reasons code sharing can be disabled:</span></span>

* <span data-ttu-id="c22ab-376">因為容器應用程式的部署目標是早於 iOS 8.0 以上版本 (它有 \*))。</span><span class="sxs-lookup"><span data-stu-id="c22ab-376">because the container app's deployment target is earlier than iOS 8.0 (it's \*)).</span></span>

<span data-ttu-id="c22ab-377">與 iOS 8.0 以上版本導入在因為共用原生程式碼使用使用者架構實作，原生程式碼共用需要 iOS 8.0 以上版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-377">Native code sharing requires iOS 8.0 because native code sharing is implemented using user frameworks, which was introduced with iOS 8.0.</span></span>

* <span data-ttu-id="c22ab-378">因為容器應用程式包含 I18N 組件 （\*）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-378">because the container app includes I18N assemblies (\*).</span></span>

<span data-ttu-id="c22ab-379">目前不支援原生程式碼共用，如果容器應用程式包含 I18N 組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-379">Native code sharing is currently not supported if the container app includes I18N assemblies.</span></span>

* <span data-ttu-id="c22ab-380">因為容器應用程式有自訂的 xml 定義的受管理的連結器 （\*）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-380">because the container app has custom xml definitions for the managed linker (\*).</span></span>

<span data-ttu-id="c22ab-381">原生程式碼共用需要不支援受管理的連結器使用自訂的 xml 定義的專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-381">Native code sharing requires is not supported for projects that use custom xml definitions for the managed linker.</span></span>

<a name="MT0113" />

### <a name="mt0113-native-code-sharing-has-been-disabled-for-the-extension--because-"></a><span data-ttu-id="c22ab-382">MT0113:原生程式碼共用已停用擴充功能 ' \*' 因為 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-382">MT0113: Native code sharing has been disabled for the extension '\*' because \*.</span></span>

* <span data-ttu-id="c22ab-383">因為容器應用程式之間的差異的 bitcode 選項 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-383">because the bitcode options differ between the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-384">原生程式碼共用需要的 bitcode 選項符合之間共用程式碼的專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-384">Native code sharing requires that the bitcode options match between the projects that share code.</span></span>

* <span data-ttu-id="c22ab-385">因為--組件建置目標有不同的容器應用程式之間的選項 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-385">because the --assembly-build-target options are different between the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-386">原生程式碼共用需要--組件建置目標的選項都是一樣的共用程式碼的專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-386">Native code sharing requires that the --assembly-build-target options are identical between the projects that share code.</span></span>

  <span data-ttu-id="c22ab-387">為不啟用或停用所有專案中，如果累加建置會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="c22ab-387">This condition can occur if incremental builds are not either enabled or disabled in all the projects.</span></span>

* <span data-ttu-id="c22ab-388">因為 I18N 組件是不同的容器應用程式 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-388">because the I18N assemblies are different between the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-389">原生程式碼共用目前不支援包含 I18N 組件的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="c22ab-389">Native code sharing is currently not supported for extensions that include I18N assemblies.</span></span>

* <span data-ttu-id="c22ab-390">由於 AOT 編譯器的引數是不同的容器應用程式 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-390">because the arguments to the AOT compiler are different between the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-391">原生程式碼共用需要 AOT 編譯器的引數亦共用程式碼的專案之間無差異。</span><span class="sxs-lookup"><span data-stu-id="c22ab-391">Native code sharing requires that the arguments to the AOT compiler do not differ between projects that share code.</span></span>

* <span data-ttu-id="c22ab-392">由於 AOT 編譯器的其他引數是不同的容器應用程式 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-392">because the other arguments to the AOT compiler are different between the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-393">原生程式碼共用需要 AOT 編譯器的引數亦共用程式碼的專案之間無差異。</span><span class="sxs-lookup"><span data-stu-id="c22ab-393">Native code sharing requires that the arguments to the AOT compiler do not differ between projects that share code.</span></span>

  <span data-ttu-id="c22ab-394">如果 '執行所有 32 位元浮點作業與 64 位元浮點數' 不同的專案，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="c22ab-394">This condition occurs if the 'Perform all 32-bit float operations as 64-bit float' differs between projects.</span></span>

* <span data-ttu-id="c22ab-395">因為 LLVM 未啟用或停用這兩個容器應用程式中 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-395">because LLVM is not enabled or disabled in both the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-396">原生程式碼共用需要 LLVM 會是啟用或停用所有共用程式碼的專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-396">Native code sharing requires that LLVM is either enabled or disabled for all projects that share code.</span></span>

* <span data-ttu-id="c22ab-397">因為受管理的連結器設定不同的容器應用程式之間 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-397">because the managed linker settings are different between the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-398">原生程式碼共用需要受管理的連結器設定完全相同的共用程式碼的所有專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-398">Native code sharing requires that the managed linker settings are identical for all projects that share code.</span></span>

* <span data-ttu-id="c22ab-399">因為受管理的連結器略過的組件是不同的容器應用程式 (\*) 和延伸模組 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-399">because the skipped assemblies for the managed linker are different between the container app (\*) and the extension (\*).</span></span>

  <span data-ttu-id="c22ab-400">原生程式碼共用需要受管理的連結器設定完全相同的共用程式碼的所有專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-400">Native code sharing requires that the managed linker settings are identical for all projects that share code.</span></span>

* <span data-ttu-id="c22ab-401">因為擴充功能有自訂的 xml 定義的受管理的連結器 （\*）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-401">because the extension has custom xml definitions for the managed linker (\*).</span></span>

  <span data-ttu-id="c22ab-402">原生程式碼共用需要不支援受管理的連結器使用自訂的 xml 定義的專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-402">Native code sharing requires is not supported for projects that use custom xml definitions for the managed linker.</span></span>

* <span data-ttu-id="c22ab-403">因為容器應用程式不會建置 abi \* （雖然此 ABI 會建置擴充功能）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-403">because the container app does not build for the ABI \* (while the extension is building for this ABI).</span></span>

  <span data-ttu-id="c22ab-404">原生程式碼共用需要容器應用程式建置適用於任何應用程式擴充功能會針對建立的所有架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-404">Native code sharing requires that the container app builds for all the architectures any app extension builds for.</span></span>

  <span data-ttu-id="c22ab-405">例如： ARM64 + ARMv7，建置延伸模組，但只建置適用於 ARM64 的容器應用程式時，會發生此狀況。</span><span class="sxs-lookup"><span data-stu-id="c22ab-405">For instance: this condition occurs when an extension builds for ARM64+ARMv7, but the container app only builds for ARM64.</span></span>

* <span data-ttu-id="c22ab-406">因為容器應用程式專為 ABI \*，這不是與擴充功能的 ABI 相容 (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-406">because the container app is building for the ABI \*, which is not compatible with the extension's ABI (\*).</span></span>

  <span data-ttu-id="c22ab-407">原生程式碼共用需要的所有專案，都建置完全相同的 API。</span><span class="sxs-lookup"><span data-stu-id="c22ab-407">Native code sharing requires that all the projects build for the exact same API.</span></span>

  <span data-ttu-id="c22ab-408">例如： 為 ARMv7 + llvm thumb2，建置延伸模組，但為 ARMv7 + llvm 只建置容器應用程式時，會發生此狀況。</span><span class="sxs-lookup"><span data-stu-id="c22ab-408">For instance: this condition occurs when an extension builds for ARMv7+llvm+thumb2, but the container app only builds for ARMv7+llvm.</span></span>

* <span data-ttu-id="c22ab-409">因為容器應用程式所參考的組件 '\*'from'\*'，而延伸模組參考中的不同版本' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-409">because the container app is referencing the assembly '\*' from '\*', while the extension references a different version from '\*'.</span></span>

  <span data-ttu-id="c22ab-410">原生程式碼共用需要共用程式碼的所有專案，都使用的所有組件的版本相同。</span><span class="sxs-lookup"><span data-stu-id="c22ab-410">Native code sharing requires that all the projects that share code use the same versions for all assemblies.</span></span>

<!-- MT0114: used by mmp -->

<a name="MT0115" />

### <a name="mt0115-it-is-recommended-to-reference-dynamic-symbols-using-code---dynamic-symbol-modecode-when-bitcode-is-enabled"></a><span data-ttu-id="c22ab-411">MT0115:建議您參考動態使用程式碼的符號 (-動態符號模式 = 程式碼) 啟用 bitcode 時。</span><span class="sxs-lookup"><span data-stu-id="c22ab-411">MT0115: It is recommended to reference dynamic symbols using code (--dynamic-symbol-mode=code) when bitcode is enabled.</span></span>

<span data-ttu-id="c22ab-412">Xamarin.iOS 專案會經常參考原生的符號，以動態方式表示原生連結器可能會移除這類原生的符號，在原生的連結過程中，因為原生連結器不會看到，會使用這些符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-412">Xamarin.iOS projects will often reference native symbols dynamically, which means that the native linker might remove such native symbols during the native linking process, because the native linker does not see that these symbols are used.</span></span>

<span data-ttu-id="c22ab-413">通常是 Xamarin.iOS 的原生連結器来保留這類符號會被要求 (使用`-u symbol`連結器旗標)，但是當編譯 bitcode 原生連結器不接受`-u`旗標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-413">Usually Xamarin.iOS will ask the native linker to keep such symbols (using the `-u symbol` linker flag), but when compiling for bitcode the native linker does not accept the `-u` flag.</span></span>

<span data-ttu-id="c22ab-414">Xamarin.iOS 已實作替代方案： 我們會產生額外的原生程式碼會參考這些符號，並因此原生連結器將會看到，會使用這些符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-414">Xamarin.iOS has implemented an alternative solution: we generate extra native code which references these symbols, and thus the native linker will see that these symbols are used.</span></span> <span data-ttu-id="c22ab-415">這會自動完成編譯為 bitcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-415">This is automatically done when compiling to bitcode.</span></span>

<span data-ttu-id="c22ab-416">如果`--dynamic-symbol-mode=linker`傳遞給 mtouch，此替代方案將會停用，和 Xamarin.iOS 會嘗試將傳遞`-u`原生連結器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-416">If `--dynamic-symbol-mode=linker` is passed to mtouch, this alternative solution will be disabled, and Xamarin.iOS will try to pass `-u` to the native linker.</span></span> <span data-ttu-id="c22ab-417">這很可能會導致原生連結器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-417">This will most likely result in native linker errors.</span></span>

<span data-ttu-id="c22ab-418">解決方法是移除`--dynamic-symbol-mode=linker`從專案的組建選項中的其他 mtouch 引數的引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-418">The solution is to remove the `--dynamic-symbol-mode=linker` argument from the additional mtouch arguments in the project's Build options.</span></span>

<!-- 0116 - 0124: free to use -->

<a name="MT0116" />

### <a name="mt0116-invalid-architecture-arch-32-bit-architectures-are-not-supported-when-deployment-target-is-11-or-later-make-sure-the-project-does-not-build-for-a-32-bit-architecture"></a><span data-ttu-id="c22ab-419">MT0116:無效的架構: {arch}。</span><span class="sxs-lookup"><span data-stu-id="c22ab-419">MT0116: Invalid architecture: {arch}.</span></span> <span data-ttu-id="c22ab-420">部署目標為 11 或更新版本時，不支援 32 位元架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-420">32-bit architectures are not supported when deployment target is 11 or later.</span></span> <span data-ttu-id="c22ab-421">請確定不會建置專案，這是適用於 32 位元架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-421">Make sure the project does not build for a 32-bit architecture.</span></span>

<span data-ttu-id="c22ab-422">iOS 11 不包含 32 位元應用程式，支援，因此它不支援建置 32 位元應用程式的部署目標是 iOS 11 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-422">iOS 11 does not contain support for 32-bit applications, so it's not supported to build for a 32-bit application when the deployment target is iOS 11 or later.</span></span>

<span data-ttu-id="c22ab-423">Arm64，變更專案的 iOS 組建選項中的目標架構，或變更部署目標專案的 Info.plist 中的較舊 iOS 版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-423">Either change the target architecture in the project's iOS build options to arm64, or change the deployment target in the project's Info.plist to an earlier iOS version.</span></span>

<a name="MT0117" />

### <a name="mt0117-cant-launch-a-32-bit-app-on-a-simulator-that-only-supports-64-bit"></a><span data-ttu-id="c22ab-424">MT0117:無法啟動模擬器僅支援 64 位元上的 32 位元應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-424">MT0117: Can't launch a 32-bit app on a simulator that only supports 64-bit.</span></span>

<a name="MT0118" />

### <a name="mt0118-aot-files-could-not-be-found-at-the-expected-directory-msymdir"></a><span data-ttu-id="c22ab-425">MT0118:在預期的目錄 '{msymdir}' 中找不到 Aot 檔案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-425">MT0118: Aot files could not be found at the expected directory '{msymdir}'.</span></span>

<!-- 0119 - 0123: free to use -->

<a name="MT0123" />

### <a name="mt0123-the-executable-assembly--does-not-reference-"></a><span data-ttu-id="c22ab-426">MT0123:可執行組件 \* 未參考 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-426">MT0123: The executable assembly \* does not reference \*.</span></span>

<span data-ttu-id="c22ab-427">平台組件找不到任何參考 (Xamarin.iOS.dll / Xamarin.TVOS.dll / Xamarin.WatchOS.dll) 可執行檔的組件中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-427">No reference could be found to the platform assembly (Xamarin.iOS.dll / Xamarin.TVOS.dll / Xamarin.WatchOS.dll) in the executable assembly.</span></span>

<span data-ttu-id="c22ab-428">這通常發生在使用任何平台組件中，從可執行檔專案中沒有任何程式碼執行個體的空白的 Main 方法 （和任何其他程式碼） 會顯示此錯誤︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-428">This typically happens where there is no code in the executable project that uses anything from the platform assembly; for instance an empty Main method (and no other code) would show this error:</span></span>

```csharp
class Program {
    void Main (string[] args)
    {
    }
}
```

<span data-ttu-id="c22ab-429">使用平台組件的 API，將會解決錯誤：</span><span class="sxs-lookup"><span data-stu-id="c22ab-429">Using an API from the platform assembly will solve the error:</span></span>

```csharp
class Program {
    void Main (string[] args)
    {
        System.Console.WriteLine (typeof (UIKit.UIWindow));
    }
}
```

<a name="MT0124" />

### <a name="mt0124-could-not-set-the-current-language-to-lang-according-to-langlang-exception"></a><span data-ttu-id="c22ab-430">MT0124:無法設定目前的語言為 '{lang}' （根據 l a n G = {LANG}）: {exception}</span><span class="sxs-lookup"><span data-stu-id="c22ab-430">MT0124: Could not set the current language to '{lang}' (according to LANG={LANG}): {exception}</span></span>

<span data-ttu-id="c22ab-431">這是警告，指出目前的語言，無法設定為錯誤訊息中的語言。</span><span class="sxs-lookup"><span data-stu-id="c22ab-431">This is a warning, indicating that the current language couldn't be set to the language in the error message.</span></span>

<span data-ttu-id="c22ab-432">目前的語言會預設為系統語言。</span><span class="sxs-lookup"><span data-stu-id="c22ab-432">The current language will default to the system language.</span></span>

<a name="MT0125" />

### <a name="mt0125-the---assembly-build-target-command-line-argument-is-ignored-in-the-simulator"></a><span data-ttu-id="c22ab-433">MT0125:--組件建置目標命令列引數會忽略在模擬器中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-433">MT0125: The --assembly-build-target command-line argument is ignored in the simulator.</span></span>

<span data-ttu-id="c22ab-434">不不需要任何動作，此訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-434">No action is required, this message is purely informational.</span></span>

<a name="MT0126" />

### <a name="mt0126-incremental-builds-have-been-disabled-because-incremental-builds-are-not-supported-in-the-simulator"></a><span data-ttu-id="c22ab-435">MT0126:累加建置已停用，因為在模擬器中不支援累加建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-435">MT0126: Incremental builds have been disabled because incremental builds are not supported in the simulator.</span></span>

<span data-ttu-id="c22ab-436">不不需要任何動作，此訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-436">No action is required, this message is purely informational.</span></span>

<a name="MT0127" />

### <a name="mt0127-incremental-builds-have-been-disabled-because-this-version-of-xamarinios-does-not-support-incremental-builds-in-projects-that-include-more-than-one-third-party-binding-libraries"></a><span data-ttu-id="c22ab-437">MT0127:因為此版本的 Xamarin.iOS 不支援累加建置包含多個協力廠商的繫結程式庫的專案中已停用累加建置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-437">MT0127: Incremental builds have been disabled because this version of Xamarin.iOS does not support incremental builds in projects that include more than one third-party binding libraries.</span></span>

<span data-ttu-id="c22ab-438">自動擁有停用累加建置，因為此版本的 Xamarin.iOS 不會永遠建置具有多個第三方繫結程式庫專案正確。</span><span class="sxs-lookup"><span data-stu-id="c22ab-438">Incremental builds have been disabled automatically because this version of Xamarin.iOS does not always build projects with multiple third-party binding libraries correctly.</span></span>

<span data-ttu-id="c22ab-439">不不需要任何動作，此訊息僅供參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-439">No action is required, this message is purely informational.</span></span>

<span data-ttu-id="c22ab-440">如需進一步資訊 bug #[52727](https://bugzilla.xamarin.com/show_bug.cgi?id=52727)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-440">For further information see bug #[52727](https://bugzilla.xamarin.com/show_bug.cgi?id=52727).</span></span>

<a name="MT0128" />

### <a name="mt0128-could-not-touch-the-file--"></a><span data-ttu-id="c22ab-441">MT0128:可能不碰觸到檔案 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-441">MT0128: Could not touch the file '\*': \*</span></span>

<span data-ttu-id="c22ab-442">碰觸的檔案 （這為了要確保正確地完成部分組建） 時，就會發生失敗。</span><span class="sxs-lookup"><span data-stu-id="c22ab-442">A failure occurred when touching a file (which is done to ensure partial builds are done correctly).</span></span>

<span data-ttu-id="c22ab-443">最有可能可以忽略這個警告;發生任何問題時提報 bug (https://bugzilla.xamarin.com] (https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)) ，將會加以調查。</span><span class="sxs-lookup"><span data-stu-id="c22ab-443">This warning can most likely be ignored; in case of any problems file a bug (https://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)) and it will be investigated.</span></span>

## <a name="mt1xxx-project-related-error-messages"></a><span data-ttu-id="c22ab-444">MT1xxx:專案相關的錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-444">MT1xxx: Project related error messages</span></span>

### <a name="mt10xx-installer--mtouch"></a><span data-ttu-id="c22ab-445">MT10xx:安裝程式 / mtouch</span><span class="sxs-lookup"><span data-stu-id="c22ab-445">MT10xx: Installer / mtouch</span></span>

<!--
 MT1xxx file copy / symlinks (project related)
  MT10xx installer.cs / mtouch.cs
  -->

<a name="MT1001" />

### <a name="mt1001-could-not-find-an-application-at-the-specified-directory"></a><span data-ttu-id="c22ab-446">MT1001:找不到指定目錄的應用程式</span><span class="sxs-lookup"><span data-stu-id="c22ab-446">MT1001: Could not find an application at the specified directory</span></span>

<a name="MT1002" />

### <a name="mt1002-could-not-create-symlinks-files-were-copied"></a><span data-ttu-id="c22ab-447">MT1002:無法建立符號連結、 已複製檔案</span><span class="sxs-lookup"><span data-stu-id="c22ab-447">MT1002: Could not create symlinks, files were copied</span></span>

<a name="MT1003" />

### <a name="mt1003-could-not-kill-the-application--you-may-have-to-kill-the-application-manually"></a><span data-ttu-id="c22ab-448">MT1003:無法終止應用程式 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-448">MT1003: Could not kill the application '\*'.</span></span> <span data-ttu-id="c22ab-449">您可能必須手動終止的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-449">You may have to kill the application manually.</span></span>

<a name="MT1004" />

### <a name="mt1004-could-not-get-the-list-of-installed-applications"></a><span data-ttu-id="c22ab-450">MT1004:無法取得已安裝的應用程式清單。</span><span class="sxs-lookup"><span data-stu-id="c22ab-450">MT1004: Could not get the list of installed applications.</span></span>

<a name="MT1005" />

### <a name="mt1005-could-not-kill-the-application--on-the-device----you-may-have-to-kill-the-application-manually"></a><span data-ttu-id="c22ab-451">MT1005:無法終止應用程式 '\*'上的裝置\*': \*-您可能必須手動終止的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-451">MT1005: Could not kill the application '\*' on the device '\*': \*- You may have to kill the application manually.</span></span>

<a name="MT1006" />

### <a name="mt1006-could-not-install-the-application--on-the-device--"></a><span data-ttu-id="c22ab-452">MT1006:無法安裝應用程式 '\*'上的裝置\*': \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-452">MT1006: Could not install the application '\*' on the device '\*': \*.</span></span>

<a name="MT1007" />

### <a name="mt1007-failed-to-launch-the-application--on-the-device---you-can-still-launch-the-application-manually-by-tapping-on-it"></a><span data-ttu-id="c22ab-453">MT1007:無法啟動應用程式 '\*'上的裝置\*': \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-453">MT1007: Failed to launch the application '\*' on the device '\*': \*.</span></span> <span data-ttu-id="c22ab-454">您仍然可以在其上的點選以手動方式啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-454">You can still launch the application manually by tapping on it.</span></span>

<a name="MT1008" />

### <a name="mt1008-failed-to-launch-the-simulator"></a><span data-ttu-id="c22ab-455">MT1008:無法啟動模擬器</span><span class="sxs-lookup"><span data-stu-id="c22ab-455">MT1008: Failed to launch the simulator</span></span>

<span data-ttu-id="c22ab-456">如果 mtouch 無法啟動模擬器時，會報告此錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-456">This error is reported if mtouch failed to launch the simulator.</span></span>   <span data-ttu-id="c22ab-457">這種情形有時因為已執行的過時和無效的模擬器處理序。</span><span class="sxs-lookup"><span data-stu-id="c22ab-457">This can happen sometimes because there is already a stale or dead simulator process running.</span></span>

<span data-ttu-id="c22ab-458">在 Unix 命令列上發出下列命令可用來刪除停滯的模擬器處理序：</span><span class="sxs-lookup"><span data-stu-id="c22ab-458">The following command issued on the Unix command line can be used to kill stuck simulator processes:</span></span>

```bash
$ launchctl list|grep UIKitApplication|awk '{print $3}'|xargs launchctl remove
```

<a name="MT1009" />

### <a name="mt1009-could-not-copy-the-assembly--to--"></a><span data-ttu-id="c22ab-459">MT1009:無法複製組件 '\*'到'\*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-459">MT1009: Could not copy the assembly '\*' to '\*': \*</span></span>

<span data-ttu-id="c22ab-460">這是特定版本的 Xamarin.iOS 中已知的問題。</span><span class="sxs-lookup"><span data-stu-id="c22ab-460">This is a known issue in certain versions of Xamarin.iOS.</span></span>

<span data-ttu-id="c22ab-461">如果您發生此問題，請嘗試下列因應措施：</span><span class="sxs-lookup"><span data-stu-id="c22ab-461">If this occurs to you, try the following workaround:</span></span>

```bash
sudo chmod 0644 /Library/Frameworks/Xamarin.iOS.framework/Versions/Current/lib/mono/*/*.mdb
```

<span data-ttu-id="c22ab-462">不過，因為在最新的 Xamarin.iOS 版本中已解決此問題，請將新 bug 歸檔在[http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)完整版本資訊與組建記錄檔輸出。</span><span class="sxs-lookup"><span data-stu-id="c22ab-462">However, since this issue has been resolved in the latest version of Xamarin.iOS, please file a new bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with your full version information and build log output.</span></span>

<a name="MT1010" />

### <a name="mt1010-could-not-load-the-assembly--"></a><span data-ttu-id="c22ab-463">MT1010:無法載入組件 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-463">MT1010: Could not load the assembly '\*': \*</span></span>

<a name="MT1011" />

### <a name="mt1011-could-not-add-missing-resource-file-"></a><span data-ttu-id="c22ab-464">MT1011:無法加入遺漏的資源檔: ' \*'</span><span class="sxs-lookup"><span data-stu-id="c22ab-464">MT1011: Could not add missing resource file: '\*'</span></span>

<a name="MT1012" />

### <a name="mt1012-failed-to-list-the-apps-on-the-device--"></a><span data-ttu-id="c22ab-465">MT1012:無法列出在裝置上的應用程式 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-465">MT1012: Failed to list the apps on the device '\*': \*</span></span>

<a name="MT1013" />

### <a name="mt1013-dependency-tracking-error-no-files-to-compare-please-file-a-bug-report-at-httpbugzillaxamarincom-with-a-test-case"></a><span data-ttu-id="c22ab-466">MT1013:相依性追蹤錯誤： 沒有要比較的檔案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-466">MT1013: Dependency tracking error: no files to compare.</span></span> <span data-ttu-id="c22ab-467">請提出錯誤報告在 http://bugzilla.xamarin.com 與測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-467">Please file a bug report at http://bugzilla.xamarin.com with a test case.</span></span>

<span data-ttu-id="c22ab-468">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-468">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-469">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)與測試 caes。</span><span class="sxs-lookup"><span data-stu-id="c22ab-469">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a test caes.</span></span>

<a name="MT1014" />

### <a name="mt1014-failed-to-re-use-cached-version-of--"></a><span data-ttu-id="c22ab-470">MT1014:無法重新使用的快取的版本 ' \*': \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-470">MT1014: Failed to re-use cached version of '\*': \*.</span></span>

<a name="MT1015" />

### <a name="mt1015-failed-to-create-the-executable--"></a><span data-ttu-id="c22ab-471">MT1015:無法建立可執行檔 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-471">MT1015: Failed to create the executable '\*': \*</span></span>

<a name="MT1015" />

### <a name="mt1015-failed-to-create-the-executable--"></a><span data-ttu-id="c22ab-472">MT1015:無法建立可執行檔 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-472">MT1015: Failed to create the executable '\*': \*</span></span>

<a name="MT1016" />

### <a name="mt1016-failed-to-create-the-notice-file-because-a-directory-already-exists-with-the-same-name"></a><span data-ttu-id="c22ab-473">MT1016:無法建立通知檔案，因為目錄已存在具有相同名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-473">MT1016: Failed to create the NOTICE file because a directory already exists with the same name.</span></span>

<span data-ttu-id="c22ab-474">移除目錄`NOTICE`從專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-474">Remove the directory `NOTICE` from the project.</span></span>

<a name="MT1017" />

### <a name="mt1017-failed-to-create-the-notice-file-"></a><span data-ttu-id="c22ab-475">MT1017:無法建立通知檔案: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-475">MT1017: Failed to create the NOTICE file: \*.</span></span>

<a name="MT1018" />

### <a name="mt1018-your-application-failed-code-signing-checks-and-could-not-be-installed-on-the-device--check-your-certificates-provisioning-profiles-and-bundle-ids-probably-your-device-is-not-part-of-the-selected-provisioning-profile-error-0xe8008015"></a><span data-ttu-id="c22ab-476">MT1018:您的應用程式程式碼簽章檢查失敗，並無法安裝在裝置上 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-476">MT1018: Your application failed code-signing checks and could not be installed on the device '\*'.</span></span> <span data-ttu-id="c22ab-477">請檢查您的憑證，佈建設定檔，以及套件組合識別碼。</span><span class="sxs-lookup"><span data-stu-id="c22ab-477">Check your certificates, provisioning profiles, and bundle ids.</span></span> <span data-ttu-id="c22ab-478">可能您的裝置不是所選的佈建設定檔的一部分 (錯誤：0xe8008015)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-478">Probably your device is not part of the selected provisioning profile (error: 0xe8008015).</span></span>

<a name="MT1019" />

### <a name="mt1019-your-application-has-entitlements-not-supported-by-your-current-provisioning-profile-and-could-not-be-installed-on-the-device--please-check-the-ios-device-log-for-more-detailed-information-error-0xe8008016"></a><span data-ttu-id="c22ab-479">MT1019:您的應用程式具有不支援您目前的佈建設定檔的權利和無法安裝在裝置上 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-479">MT1019: Your application has entitlements not supported by your current provisioning profile and could not be installed on the device '\*'.</span></span> <span data-ttu-id="c22ab-480">如需詳細資訊，請參閱 iOS 裝置記錄檔 (錯誤：0xe8008016)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-480">Please check the iOS Device Log for more detailed information (error: 0xe8008016).</span></span>

<span data-ttu-id="c22ab-481">如果此情形：</span><span class="sxs-lookup"><span data-stu-id="c22ab-481">This can happen if:</span></span>

* <span data-ttu-id="c22ab-482">您的應用程式有目前的佈建設定檔不支援的權利。</span><span class="sxs-lookup"><span data-stu-id="c22ab-482">Your application has entitlements that the current provisioning profile does not support.</span></span>
  <span data-ttu-id="c22ab-483">可能的解決方案：</span><span class="sxs-lookup"><span data-stu-id="c22ab-483">Possible solutions:</span></span>
  - <span data-ttu-id="c22ab-484">指定不同的佈建設定檔支援的權利，您的應用程式的需求。</span><span class="sxs-lookup"><span data-stu-id="c22ab-484">Specify a different provisioning profile that supports the entitlements your application needs.</span></span>
  - <span data-ttu-id="c22ab-485">移除目前的佈建設定檔中不支援的權利。</span><span class="sxs-lookup"><span data-stu-id="c22ab-485">Remove the entitlements not supported in current provisioning profile.</span></span>
* <span data-ttu-id="c22ab-486">您嘗試部署至不包含在您使用的佈建設定檔裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-486">The device you're trying to deploy to is not included in the provisioning profile you're using.</span></span>
  <span data-ttu-id="c22ab-487">可能的解決方案：</span><span class="sxs-lookup"><span data-stu-id="c22ab-487">Possible solutions:</span></span>
  - <span data-ttu-id="c22ab-488">從範本，以在 Xcode 中建立新的應用程式，選取相同的佈建設定檔，並部署至相同裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-488">Create a new app from a template in Xcode, select the same provisioning profile, and deploy to same device.</span></span> <span data-ttu-id="c22ab-489">有時候 Xcode 重新整理佈建設定檔與新的裝置 （Xcode 會詢問您要執行的其他情況下）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-489">Sometimes Xcode can automatically refresh provisioning profiles with new devices (in other cases Xcode will ask you what to do).</span></span>
  <span data-ttu-id="c22ab-490">-移至 iOS 開發人員中心並更新佈建設定檔與新的裝置，然後下載到您電腦的更新佈建設定檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-490">-Go to the iOS Dev Center and update the provisioning profile with the new device, then download the updated provisioning profile to your machine.</span></span>

<span data-ttu-id="c22ab-491">在 iOS 裝置記錄檔將會顯示有關失敗的詳細資訊的大部分情況下，這可以幫助診斷問題。</span><span class="sxs-lookup"><span data-stu-id="c22ab-491">In most cases more information about the failure will be printed to the iOS Device Log, which can help diagnosing the issue.</span></span>

<a name="MT1020" />

### <a name="mt1020-failed-to-launch-the-application--on-the-device--"></a><span data-ttu-id="c22ab-492">MT1020:無法啟動應用程式 '\*'上的裝置\*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-492">MT1020: Failed to launch the application '\*' on the device '\*': \*</span></span>

<a name="MT1021" />

### <a name="mt1021-could-not-copy-the-file--to--2"></a><span data-ttu-id="c22ab-493">MT1021:無法複製檔案 '\*'到'\*': {2}</span><span class="sxs-lookup"><span data-stu-id="c22ab-493">MT1021: Could not copy the file '\*' to '\*': {2}</span></span>

<span data-ttu-id="c22ab-494">無法複製檔案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-494">A file could not be copied.</span></span> <span data-ttu-id="c22ab-495">複製作業的錯誤訊息有錯誤的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c22ab-495">The error message from the copy operation has more information about the error.</span></span>

<a name="MT1022" />

### <a name="mt1022-could-not-copy-the-directory--to--2"></a><span data-ttu-id="c22ab-496">MT1022:無法複製目錄 '\*'到'\*': {2}</span><span class="sxs-lookup"><span data-stu-id="c22ab-496">MT1022: Could not copy the directory '\*' to '\*': {2}</span></span>

<span data-ttu-id="c22ab-497">無法複製目錄。</span><span class="sxs-lookup"><span data-stu-id="c22ab-497">A directory could not be copied.</span></span> <span data-ttu-id="c22ab-498">複製作業的錯誤訊息有錯誤的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c22ab-498">The error message from the copy operation has more information about the error.</span></span>

<a name="MT1023" />

### <a name="mt1023-could-not-communicate-with-the-device-to-find-the-application---"></a><span data-ttu-id="c22ab-499">MT1023:無法與裝置，以尋找應用程式通訊以 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-499">MT1023: Could not communicate with the device to find the application '\*' : \*</span></span>

<span data-ttu-id="c22ab-500">嘗試將查閱裝置上的應用程式時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-500">An error occurred when trying to lookup an application on device.</span></span>

<span data-ttu-id="c22ab-501">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-501">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-502">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-502">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-503">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-503">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-504">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-504">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-505">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-505">Reboot the Mac.</span></span>

<a name="MT1024" />

### <a name="mt1024-the-application-signature-could-not-be-verified-on-device--please-make-sure-that-the-provisioning-profile-is-installed-and-not-expired-error-0xe8008017"></a><span data-ttu-id="c22ab-506">MT1024:無法在裝置上驗證應用程式簽章 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-506">MT1024: The application signature could not be verified on device '\*'.</span></span> <span data-ttu-id="c22ab-507">請確定佈建設定檔已安裝且過期 (錯誤：0xe8008017)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-507">Please make sure that the provisioning profile is installed and not expired (error: 0xe8008017).</span></span>

<span data-ttu-id="c22ab-508">裝置會拒絕應用程式進行安裝，因為無法驗證簽章。</span><span class="sxs-lookup"><span data-stu-id="c22ab-508">The device rejected the application install because the signature could not be verified.</span></span>

<span data-ttu-id="c22ab-509">請確定已安裝佈建設定檔，並不過期。</span><span class="sxs-lookup"><span data-stu-id="c22ab-509">Please make sure that the provisioning profile is installed and not expired.</span></span>

<a name="MT1025" />

### <a name="mt1025-could-not-list-the-crash-reports-on-the-device-"></a><span data-ttu-id="c22ab-510">MT1025:無法列出在裝置上的損毀報表 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-510">MT1025: Could not list the crash reports on the device \*.</span></span>

<span data-ttu-id="c22ab-511">嘗試將列出在裝置上的損毀報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-511">An error occurred when trying to list the crash reports on the device.</span></span>

<span data-ttu-id="c22ab-512">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-512">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-513">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-513">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-514">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-514">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-515">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-515">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-516">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-516">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-517">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-517">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1026" />

### <a name="mt1026-could-not-download-the-crash-report--from-the-device-"></a><span data-ttu-id="c22ab-518">MT1026:無法下載的當機報告 \* 從裝置 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-518">MT1026: Could not download the crash report \* from the device \*.</span></span>

<span data-ttu-id="c22ab-519">嘗試從裝置下載損毀報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-519">An error occurred when trying to download the crash reports from the device.</span></span>

<span data-ttu-id="c22ab-520">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-520">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-521">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-521">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-522">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-522">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-523">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-523">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-524">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-524">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-525">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-525">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1027" />

### <a name="mt1027-cant-use-xcode-7-to-launch-applications-on-devices-with-ios--xcode-7-only-supports-ios-6"></a><span data-ttu-id="c22ab-526">MT1027:無法啟動 iOS 裝置上的應用程式使用 Xcode 7 + \* （Xcode 7 只支援 iOS 6 +）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-526">MT1027: Can't use Xcode 7+ to launch applications on devices with iOS \* (Xcode 7 only supports iOS 6+).</span></span>

<span data-ttu-id="c22ab-527">您不可以使用 Xcode 7 + 啟動 iOS 版本，低於 6.0 裝置上的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-527">It is not possible to use Xcode 7+ to launch applications on devices with iOS version below 6.0.</span></span>

<span data-ttu-id="c22ab-528">請使用較舊版本的 Xcode，或點選應用程式以手動方式啟動它。</span><span class="sxs-lookup"><span data-stu-id="c22ab-528">Please use an older version of Xcode, or tap on the app manually to launch it.</span></span>

<a name="MT1028" />

### <a name="mt1028-invalid-device-specification--expected-ios-watchos-or-all"></a><span data-ttu-id="c22ab-529">MT1028:不正確的裝置規格: ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-529">MT1028: Invalid device specification: '\*'.</span></span> <span data-ttu-id="c22ab-530">必須是 'ios'、 'watchos' 或者 'all'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-530">Expected 'ios', 'watchos' or 'all'.</span></span>

<span data-ttu-id="c22ab-531">裝置規格可讓您傳遞使用--裝置無效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-531">The device specification passed using --device is invalid.</span></span> <span data-ttu-id="c22ab-532">有效值為: 'ios'、 'watchos' 或 'all'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-532">Valid values are: 'ios', 'watchos' or 'all'.</span></span>

<a name="MT1029" />

### <a name="mt1029-could-not-find-an-application-at-the-specified-directory-"></a><span data-ttu-id="c22ab-533">MT1029:找不到指定目錄的應用程式: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-533">MT1029: Could not find an application at the specified directory: \*</span></span>

<span data-ttu-id="c22ab-534">傳遞給-launchdev 的應用程式路徑不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-534">The application path passed to --launchdev does not exist.</span></span> <span data-ttu-id="c22ab-535">請指定有效的應用程式套件組合。</span><span class="sxs-lookup"><span data-stu-id="c22ab-535">Please specify a valid app bundle.</span></span>

<a name="MT1030" />

### <a name="mt1030-launching-applications-on-device-using-a-bundle-identifier-is-deprecated-please-pass-the-full-path-to-the-bundle-to-launch"></a><span data-ttu-id="c22ab-536">MT1030:啟動應用程式在裝置上使用套件組合識別碼已被取代。</span><span class="sxs-lookup"><span data-stu-id="c22ab-536">MT1030: Launching applications on device using a bundle identifier is deprecated.</span></span> <span data-ttu-id="c22ab-537">請將完整路徑傳遞至要啟動的組合中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-537">Please pass the full path to the bundle to launch.</span></span>

<span data-ttu-id="c22ab-538">建議將路徑傳遞至應用程式，而非只是套件組合識別碼的裝置上啟動。</span><span class="sxs-lookup"><span data-stu-id="c22ab-538">It's recommended to pass the path to the app to launch on device instead of just the bundle id.</span></span>

<a name="MT1031" />

### <a name="mt1031-could-not-launch-the-app--on-the-device--because-the-device-is-locked-please-unlock-the-device-and-try-again"></a><span data-ttu-id="c22ab-539">MT1031:無法啟動應用程式 '\*'上的裝置\*' 因為裝置已被鎖定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-539">MT1031: Could not launch the app '\*' on the device '\*' because the device is locked.</span></span> <span data-ttu-id="c22ab-540">請將裝置解除鎖定，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-540">Please unlock the device and try again.</span></span>

<span data-ttu-id="c22ab-541">請將裝置解除鎖定，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-541">Please unlock the device and try again.</span></span>

<a name="MT1032" />

### <a name="mt1032-this-application-executable-might-be-too-large--mb-to-execute-on-device-if-bitcode-was-enabled-you-might-want-to-disable-it-for-development-it-is-only-required-to-submit-applications-to-apple"></a><span data-ttu-id="c22ab-542">MT1032:此應用程式可執行檔可能會太大 (\* MB) 裝置上執行。</span><span class="sxs-lookup"><span data-stu-id="c22ab-542">MT1032: This application executable might be too large (\* MB) to execute on device.</span></span> <span data-ttu-id="c22ab-543">如果已啟用 bitcode 要停用它進行開發，只需要提交給 Apple 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-543">If bitcode was enabled you might want to disable it for development, it is only required to submit applications to Apple.</span></span>

<a name="MT1033" />

### <a name="mt1033-could-not-uninstall-the-application--from-the-device--"></a><span data-ttu-id="c22ab-544">MT1033:無法解除安裝應用程式 '\*「 from 裝置'\*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-544">MT1033: Could not uninstall the application '\*' from the device '\*': \*</span></span>

<!-- 1034 used by mmp -->

<a name="MT1035" />

### <a name="mt1035-cannot-include-different-versions-of-the-framework-name"></a><span data-ttu-id="c22ab-545">MT1035:不能包含不同的 framework 版本為 '{name}'</span><span class="sxs-lookup"><span data-stu-id="c22ab-545">MT1035: Cannot include different versions of the framework '{name}'</span></span>

<span data-ttu-id="c22ab-546">您不可能時要連結的不同版本的相同的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-546">It is not possible to link with different versions of the same framework.</span></span>

<span data-ttu-id="c22ab-547">此外，這通常會發生於延伸模組參考不同版本的架構比容器應用程式 （可能是透過第三方繫結組件）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-547">This typically happens when an extension references a different version of a framework than the container app (possibly through a third-party binding assembly).</span></span>

<span data-ttu-id="c22ab-548">遵循此錯誤會有多個[MT1036](#MT1036)列出之路徑的每個不同的架構的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-548">Following this error there will be multiple [MT1036](#MT1036) errors listing the paths for each different framework.</span></span>

<a name="MT1036" />

### <a name="mt1036-framework-name-included-from-path-related-to-previous-error"></a><span data-ttu-id="c22ab-549">MT1036:來自所包含的 framework '{name}': {path} （與之前錯誤相關）</span><span class="sxs-lookup"><span data-stu-id="c22ab-549">MT1036: Framework '{name}' included from: {path} (Related to previous error)</span></span>

<span data-ttu-id="c22ab-550">會報告此錯誤只搭配[MT1036](#MT1036)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-550">This error is reported only together with [MT1036](#MT1036).</span></span> <span data-ttu-id="c22ab-551">請參閱[MT1036](#MT1036)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c22ab-551">Please see [MT1036](#MT1036) for more information.</span></span>

### <a name="mt11xx-debug-service"></a><span data-ttu-id="c22ab-552">MT11xx:偵錯服務</span><span class="sxs-lookup"><span data-stu-id="c22ab-552">MT11xx: Debug Service</span></span>

<!--
  MT11xx DebugService.cs
  -->

<a name="MT1101" />

### <a name="mt1101-could-not-start-app"></a><span data-ttu-id="c22ab-553">MT1101:無法啟動應用程式</span><span class="sxs-lookup"><span data-stu-id="c22ab-553">MT1101: Could not start app</span></span>

<a name="MT1102" />

### <a name="mt1102-could-not-attach-to-the-app-to-kill-it-"></a><span data-ttu-id="c22ab-554">MT1102:無法附加至應用程式 （以終止為止）: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-554">MT1102: Could not attach to the app (to kill it): \*</span></span>

<a name="MT1103" />

### <a name="mt1103-could-not-detach"></a><span data-ttu-id="c22ab-555">MT1103:無法中斷連結</span><span class="sxs-lookup"><span data-stu-id="c22ab-555">MT1103: Could not detach</span></span>

<a name="MT1104" />

### <a name="mt1104-failed-to-send-packet-"></a><span data-ttu-id="c22ab-556">MT1104:無法傳送封包: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-556">MT1104: Failed to send packet: \*</span></span>

<a name="MT1105" />

### <a name="mt1105-unexpected-response-type"></a><span data-ttu-id="c22ab-557">MT1105:未預期的回應類型</span><span class="sxs-lookup"><span data-stu-id="c22ab-557">MT1105: Unexpected response type</span></span>

<a name="MT1106" />

### <a name="mt1106-could-not-get-list-of-applications-on-the-device-request-timed-out"></a><span data-ttu-id="c22ab-558">MT1106:無法在裝置上取得應用程式的清單：要求已逾時。</span><span class="sxs-lookup"><span data-stu-id="c22ab-558">MT1106: Could not get list of applications on the device: Request timed out.</span></span>

<a name="MT1107" />

### <a name="mt1107-application-failed-to-launch-"></a><span data-ttu-id="c22ab-559">MT1107:應用程式無法啟動: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-559">MT1107: Application failed to launch: \*</span></span>

<span data-ttu-id="c22ab-560">請檢查您的裝置是否鎖定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-560">Please check if your device is locked.</span></span>

<span data-ttu-id="c22ab-561">如果您要部署企業應用程式，或使用免費的佈建設定檔，您可能需要信任的開發人員 (這會說明<a href="https://stackoverflow.com/a/30726375/183422">此處</a>)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-561">If you're deploying an enterprise app or using a free provisioning profile, you might have trust the developer (this is explained <a href="https://stackoverflow.com/a/30726375/183422">here</a>).</span></span>

<a name="MT1108" />

### <a name="mt1108-could-not-find-developer-tools-for-this-xx-yy-device"></a><span data-ttu-id="c22ab-562">MT1108:找不到此的 XX (YY) 裝置的開發人員工具。</span><span class="sxs-lookup"><span data-stu-id="c22ab-562">MT1108: Could not find developer tools for this XX (YY) device.</span></span>

<span data-ttu-id="c22ab-563">從 mtouch 的幾個作業都需要<tt>DeveloperDiskImage.dmg</tt>檔案會出現。</span><span class="sxs-lookup"><span data-stu-id="c22ab-563">A few operations from mtouch require the <tt>DeveloperDiskImage.dmg</tt> file to be present.</span></span>   <span data-ttu-id="c22ab-564">此檔案屬於 Xcode 的而且通常位於相對於您用來在建置，SDK <tt>Xcode.app/Contents/Developer/iPhoneOS.platform/DeviceSupport/VERSION/DeveloperDiskImage.dmg</tt>。</span><span class="sxs-lookup"><span data-stu-id="c22ab-564">This file is part of Xcode and is usually located relative to the SDK that you are using to build against, in the <tt>Xcode.app/Contents/Developer/iPhoneOS.platform/DeviceSupport/VERSION/DeveloperDiskImage.dmg</tt>.</span></span>

<span data-ttu-id="c22ab-565">這就會發生錯誤是因為您不需要符合您已連接之裝置 DeveloperDiskImage.dmg。</span><span class="sxs-lookup"><span data-stu-id="c22ab-565">This error can happen either because you do not have a DeveloperDiskImage.dmg that matches the device that you have connected.</span></span>

<a name="MT1109" />

### <a name="mt1109-application-failed-to-launch-because-the-device-is-locked-please-unlock-the-device-and-try-again"></a><span data-ttu-id="c22ab-566">MT1109:應用程式無法啟動，因為在裝置鎖定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-566">MT1109: Application failed to launch because the device is locked.</span></span> <span data-ttu-id="c22ab-567">請將裝置解除鎖定，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-567">Please unlock the device and try again.</span></span>

<span data-ttu-id="c22ab-568">請檢查您的裝置是否鎖定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-568">Please check if your device is locked.</span></span>

<a name="MT1110" />

### <a name="mt1110-application-failed-to-launch-because-of-ios-security-restrictions-please-ensure-the-developer-is-trusted"></a><span data-ttu-id="c22ab-569">MT1110:應用程式無法啟動，因為 iOS 安全性限制。</span><span class="sxs-lookup"><span data-stu-id="c22ab-569">MT1110: Application failed to launch because of iOS security restrictions.</span></span> <span data-ttu-id="c22ab-570">請確定開發人員的受信任。</span><span class="sxs-lookup"><span data-stu-id="c22ab-570">Please ensure the developer is trusted.</span></span>

<span data-ttu-id="c22ab-571">如果您要部署企業應用程式，或使用免費的佈建設定檔，您可能需要信任的開發人員 (這會說明<a href="https://stackoverflow.com/a/30726375/183422">此處</a>)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-571">If you're deploying an enterprise app or using a free provisioning profile, you might have trust the developer (this is explained <a href="https://stackoverflow.com/a/30726375/183422">here</a>).</span></span>

<a name="MT1111" />

### <a name="mt1111-application-launched-successfully-but-its-not-possible-to-wait-for-the-app-to-exit-as-requested-because-its-not-possible-to-detect-app-termination-when-launching-using-gdbserver"></a><span data-ttu-id="c22ab-572">MT1111:應用程式啟動成功，但它的不可以等候結束要求，因為它不能啟動使用 gdbserver 偵測應用程式終止的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-572">MT1111: Application launched successfully, but it's not possible to wait for the app to exit as requested because it's not possible to detect app termination when launching using gdbserver.</span></span>

### <a name="mt12xx-simulator"></a><span data-ttu-id="c22ab-573">MT12xx:模擬器</span><span class="sxs-lookup"><span data-stu-id="c22ab-573">MT12xx: Simulator</span></span>

<!--
  MT12xx simcontroller.cs
  -->

<a name="MT1201" />

### <a name="mt1201-could-not-load-the-simulator-"></a><span data-ttu-id="c22ab-574">MT1201:無法載入模擬器: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-574">MT1201: Could not load the simulator: \*</span></span>

<a name="MT1202" />

### <a name="mt1202-invalid-simulator-configuration-"></a><span data-ttu-id="c22ab-575">MT1202:無效的模擬器組態: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-575">MT1202: Invalid simulator configuration: \*</span></span>

<a name="MT1203" />

### <a name="mt1203-invalid-simulator-specification-"></a><span data-ttu-id="c22ab-576">MT1203:無效的模擬器規格: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-576">MT1203: Invalid simulator specification: \*</span></span>

<a name="MT1204" />

### <a name="mt1204-invalid-simulator-specification--runtime-not-specified"></a><span data-ttu-id="c22ab-577">MT1204:無效的模擬器規格 ' \*': 未指定的執行階段。</span><span class="sxs-lookup"><span data-stu-id="c22ab-577">MT1204: Invalid simulator specification '\*': runtime not specified.</span></span>

<a name="MT1205" />

### <a name="mt1205-invalid-simulator-specification--device-type-not-specified"></a><span data-ttu-id="c22ab-578">MT1205:無效的模擬器規格 ' \*': 未指定的裝置類型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-578">MT1205: Invalid simulator specification '\*': device type not specified.</span></span>

<a name="MT1206" />

### <a name="mt1206-could-not-find-the-simulator-runtime-"></a><span data-ttu-id="c22ab-579">MT1206:找不到模擬器執行階段 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-579">MT1206: Could not find the simulator runtime '\*'.</span></span>

<a name="MT1207" />

### <a name="mt1207-could-not-find-the-simulator-device-type-"></a><span data-ttu-id="c22ab-580">MT1207:找不到模擬器裝置類型 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-580">MT1207: Could not find the simulator device type '\*'.</span></span>

<a name="MT1208" />

### <a name="mt1208-could-not-find-the-simulator-runtime-"></a><span data-ttu-id="c22ab-581">MT1208:找不到模擬器執行階段 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-581">MT1208: Could not find the simulator runtime '\*'.</span></span>

<a name="MT1209" />

### <a name="mt1209-could-not-find-the-simulator-device-type-"></a><span data-ttu-id="c22ab-582">MT1209:找不到模擬器裝置類型 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-582">MT1209: Could not find the simulator device type '\*'.</span></span>

<a name="MT1210" />

### <a name="mt1210-invalid-simulator-specification--unknown-key-"></a><span data-ttu-id="c22ab-583">MT1210:無效的模擬器規格： \*，未知的索引鍵 '\*'</span><span class="sxs-lookup"><span data-stu-id="c22ab-583">MT1210: Invalid simulator specification: \*, unknown key '\*'</span></span>

<a name="MT1211" />

### <a name="mt1211-the-simulator-version--does-not-support-the-simulator-type-"></a><span data-ttu-id="c22ab-584">MT1211:模擬器版本 '\*'不支援模擬器類型'\*'</span><span class="sxs-lookup"><span data-stu-id="c22ab-584">MT1211: The simulator version '\*' does not support the simulator type '\*'</span></span>

<a name="MT1212" />

### <a name="mt1212-failed-to-create-a-simulator-version-where-type---and-runtime--"></a><span data-ttu-id="c22ab-585">MT1212:無法建立模擬器版本，類型 = \* 和執行階段 = \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-585">MT1212: Failed to create a simulator version where type = \* and runtime = \*.</span></span>

<a name="MT1213" />

### <a name="mt1213-invalid-simulator-specification-for-xcode-4-"></a><span data-ttu-id="c22ab-586">MT1213:無效的模擬器規格 Xcode 4: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-586">MT1213: Invalid simulator specification for Xcode 4: \*</span></span>

<a name="MT1214" />

### <a name="mt1214-invalid-simulator-specification-for-xcode-5-"></a><span data-ttu-id="c22ab-587">MT1214:無效的模擬器規格 Xcode 5: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-587">MT1214: Invalid simulator specification for Xcode 5: \*</span></span>

<a name="MT1215" />

### <a name="mt1215-invalid-sdk-specified-"></a><span data-ttu-id="c22ab-588">MT1215:指定了無效的 SDK: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-588">MT1215: Invalid SDK specified: \*</span></span>

<a name="MT1216" />

### <a name="mt1216-could-not-find-the-simulator-udid-"></a><span data-ttu-id="c22ab-589">MT1216:找不到模擬器 UDID ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-589">MT1216: Could not find the simulator UDID '\*'.</span></span>

<a name="MT1217" />

### <a name="mt1217-could-not-load-the-app-bundle-at-"></a><span data-ttu-id="c22ab-590">MT1217:無法載入應用程式套件組合，在 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-590">MT1217: Could not load the app bundle at '\*'.</span></span>

<a name="MT1218" />

### <a name="mt1218-no-bundle-identifier-found-in-the-app-at-"></a><span data-ttu-id="c22ab-591">MT1218:在應用程式中找到的任何套件組合識別碼 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-591">MT1218: No bundle identifier found in the app at '\*'.</span></span>

<a name="MT1219" />

### <a name="mt1219-could-not-find-the-simulator-for-"></a><span data-ttu-id="c22ab-592">MT1219:找不到適用的模擬器 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-592">MT1219: Could not find the simulator for '\*'.</span></span>

<a name="MT1220" />

### <a name="mt1220-could-not-find-the-latest-simulator-runtime-for-device-"></a><span data-ttu-id="c22ab-593">MT1220:找不到裝置的最新的模擬器執行階段 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-593">MT1220: Could not find the latest simulator runtime for device '\*'.</span></span>

<span data-ttu-id="c22ab-594">這通常表示 Xcode 的問題。</span><span class="sxs-lookup"><span data-stu-id="c22ab-594">This usually indicates a problem with Xcode.</span></span>

<span data-ttu-id="c22ab-595">若要嘗試修正此問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-595">Things to try to fix this:</span></span>

* <span data-ttu-id="c22ab-596">在 Xcode 中，一次使用模擬器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-596">Use the simulator once in Xcode.</span></span>
* <span data-ttu-id="c22ab-597">傳遞明確的 SDK 版本，使用-sdk <version>。</span><span class="sxs-lookup"><span data-stu-id="c22ab-597">Pass an explicit SDK version using --sdk <version>.</span></span>
* <span data-ttu-id="c22ab-598">重新安裝 Xcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-598">Reinstall Xcode.</span></span>

<a name="MT1221" />

### <a name="mt1221-could-not-find-the-paired-iphone-simulator-for-the-watchos-simulator-"></a><span data-ttu-id="c22ab-599">MT1221:找不到 WatchOS 模擬器配對的 iPhone 模擬器 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-599">MT1221: Could not find the paired iPhone simulator for the WatchOS simulator '\*'.</span></span>

<span data-ttu-id="c22ab-600">當啟動 WatchOS 應用程式在 WatchOS 模擬器中的，必須是配對的 iOS 模擬器以及。</span><span class="sxs-lookup"><span data-stu-id="c22ab-600">When launching a WatchOS app in a WatchOS simulator, there must be a paired iOS Simulator as well.</span></span>

<span data-ttu-id="c22ab-601">觀看模擬器可搭配 iOS 模擬器使用 Xcode 的裝置 UI (視窗 功能表-> 裝置)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-601">Watch simulators can be paired with iOS Simulators using Xcode's Devices UI (menu Window -> Devices).</span></span>

### <a name="mt13xx-linkwith"></a><span data-ttu-id="c22ab-602">MT13xx: [LinkWith]</span><span class="sxs-lookup"><span data-stu-id="c22ab-602">MT13xx: [LinkWith]</span></span>

<!--
  MT13xx [LinkWith]
  -->

<a name="MT1301" />

### <a name="mt1301-native-library---was-ignored-since-it-does-not-match-the-current-build-architectures-"></a><span data-ttu-id="c22ab-603">MT1301:原生程式庫`*`(\*) 已被忽略，因為它不符合目前的組建 architecture(s) (\*)</span><span class="sxs-lookup"><span data-stu-id="c22ab-603">MT1301: Native library `*` (\*) was ignored since it does not match the current build architecture(s) (\*)</span></span>

<a name="MT1302" />

### <a name="mt1302-could-not-extract-the-native-library--from--please-ensure-the-native-library-was-properly-embedded-in-the-managed-assembly-if-the-assembly-was-built-using-a-binding-project-the-native-library-must-be-included-in-the-project-and-its-build-action-must-be-objcbindingnativelibrary"></a><span data-ttu-id="c22ab-604">MT1302:無法擷取原生程式庫 ' \*' 從 '+'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-604">MT1302: Could not extract the native library '\*' from '+'.</span></span> <span data-ttu-id="c22ab-605">請確定原生程式庫已正確內嵌的 managed 組件中 （如果使用繫結專案建置的組件時，原生程式庫必須包含在專案中，且其 建置動作必須是 'ObjcBindingNativeLibrary'）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-605">Please ensure the native library was properly embedded in the managed assembly (if the assembly was built using a binding project, the native library must be included in the project, and its Build Action must be 'ObjcBindingNativeLibrary').</span></span>

<a name="MT1303" />

### <a name="mt1303-could-not-decompress-the-native-framework--from--please-review-the-build-log-for-more-information-from-the-native-zip-command"></a><span data-ttu-id="c22ab-606">MT1303:無法解壓縮原生架構 '\*'from'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-606">MT1303: Could not decompress the native framework '\*' from '\*'.</span></span> <span data-ttu-id="c22ab-607">請檢閱建置記錄檔，如需詳細資訊，請從原生 'zip' 命令。</span><span class="sxs-lookup"><span data-stu-id="c22ab-607">Please review the build log for more information from the native 'zip' command.</span></span>

<span data-ttu-id="c22ab-608">無法解壓縮從繫結程式庫指定的原生架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-608">Could not decompress the specified native framework from the binding library.</span></span>

<span data-ttu-id="c22ab-609">請檢閱 bulid 記錄檔，如需有關此原生 'zip' 命令失敗。</span><span class="sxs-lookup"><span data-stu-id="c22ab-609">Please review the bulid log for more information about this failure from the native 'zip' command.</span></span>

<a name="MT1304" />

### <a name="mt1304-the-embedded-framework--in--is-invalid-it-does-not-contain-an-infoplist"></a><span data-ttu-id="c22ab-610">MT1304:內嵌的 framework ' \*' 在 \* 無效： 它不包含 Info.plist。</span><span class="sxs-lookup"><span data-stu-id="c22ab-610">MT1304: The embedded framework '\*' in \* is invalid: it does not contain an Info.plist.</span></span>

<span data-ttu-id="c22ab-611">指定內嵌的架構不包含 Info.plist 中，並因此不是有效的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-611">The specified embedded framework does not contain an Info.plist, and is therefore not a valid framework.</span></span>

<span data-ttu-id="c22ab-612">請確定 「 架構 」 是有效的。</span><span class="sxs-lookup"><span data-stu-id="c22ab-612">Please make sure the framework is valid.</span></span>

<a name="MT1305" />

### <a name="mt1305-the-binding-library--contains-a-user-framework--but-embedded-user-frameworks-require-ios-80-the-current-deployment-target-is--please-set-the-deployment-target-in-the-infoplist-file-to-at-least-80"></a><span data-ttu-id="c22ab-613">MT1305:繫結程式庫 '\*' 包含的使用者架構 (\*)，但內嵌的使用者架構需要 iOS 8.0 以上版本 (目前的部署目標是 \*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-613">MT1305: The binding library '\*' contains a user framework (\*), but embedded user frameworks require iOS 8.0 (the current deployment target is \*).</span></span> <span data-ttu-id="c22ab-614">請至少 8.0 Info.plist 檔案中將部署目標。</span><span class="sxs-lookup"><span data-stu-id="c22ab-614">Please set the deployment target in the Info.plist file to at least 8.0.</span></span>

<span data-ttu-id="c22ab-615">指定的繫結程式庫包含內嵌的架構，但 Xamarin.iOS ios 8.0 或更新版本只支援內嵌的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-615">The specified binding library contains an embedded framework, but Xamarin.iOS only supports embedded frameworks on iOS 8.0 or later.</span></span>

<span data-ttu-id="c22ab-616">請至少可解決此錯誤的 8.0 Info.plist 檔案中將部署目標 （或不使用內嵌的架構）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-616">Please set the deployment target in the Info.plist file to at least 8.0 to solve this error (or don't use embedded frameworks).</span></span>

### <a name="mt14xx-crash-reports"></a><span data-ttu-id="c22ab-617">MT14xx:當機報告</span><span class="sxs-lookup"><span data-stu-id="c22ab-617">MT14xx: Crash Reports</span></span>

<!--
  MT14xx    CrashReports.cs
  -->

<a name="MT1400" />

### <a name="mt1400-could-not-open-crash-report-service-afcconnectionopen-returned-"></a><span data-ttu-id="c22ab-618">MT1400:無法開啟損毀報表服務：AFCConnectionOpen 傳回 \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-618">MT1400: Could not open crash report service: AFCConnectionOpen returned \*</span></span>

<span data-ttu-id="c22ab-619">嘗試從裝置存取的當機報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-619">An error occurred when trying to access crash reports from the device.</span></span>

<span data-ttu-id="c22ab-620">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-620">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-621">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-621">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-622">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-622">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-623">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-623">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-624">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-624">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-625">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-625">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1401" />

### <a name="mt1401-could-not-close-crash-report-service-afcconnectionclose-returned-"></a><span data-ttu-id="c22ab-626">MT1401:無法關閉損毀報表服務：AFCConnectionClose 傳回 \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-626">MT1401: Could not close crash report service: AFCConnectionClose returned \*</span></span>

<span data-ttu-id="c22ab-627">嘗試從裝置存取的當機報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-627">An error occurred when trying to access crash reports from the device.</span></span>

<span data-ttu-id="c22ab-628">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-628">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-629">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-629">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-630">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-630">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-631">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-631">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-632">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-632">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-633">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-633">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1402" />

### <a name="mt1402-could-not-read-file-info-for--afcfileinfoopen-returned-"></a><span data-ttu-id="c22ab-634">MT1402:無法讀取的檔案資訊 \*:AFCFileInfoOpen 傳回 \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-634">MT1402: Could not read file info for \*: AFCFileInfoOpen returned \*</span></span>

<span data-ttu-id="c22ab-635">嘗試從裝置存取的當機報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-635">An error occurred when trying to access crash reports from the device.</span></span>

<span data-ttu-id="c22ab-636">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-636">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-637">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-637">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-638">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-638">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-639">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-639">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-640">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-640">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-641">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-641">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1403" />

### <a name="mt1403-could-not-read-crash-report-afcdirectoryopen--returned-"></a><span data-ttu-id="c22ab-642">MT1403:無法讀取的當機報告：AFCDirectoryOpen （\*） 傳回: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-642">MT1403: Could not read crash report: AFCDirectoryOpen (\*) returned: \*</span></span>

<span data-ttu-id="c22ab-643">嘗試從裝置存取的當機報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-643">An error occurred when trying to access crash reports from the device.</span></span>

<span data-ttu-id="c22ab-644">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-644">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-645">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-645">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-646">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-646">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-647">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-647">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-648">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-648">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-649">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-649">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1404" />

### <a name="mt1404-could-not-read-crash-report-afcfilerefopen--returned-"></a><span data-ttu-id="c22ab-650">MT1404:無法讀取的當機報告：AFCFileRefOpen （\*） 傳回: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-650">MT1404: Could not read crash report: AFCFileRefOpen (\*) returned: \*</span></span>

<span data-ttu-id="c22ab-651">嘗試從裝置存取的當機報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-651">An error occurred when trying to access crash reports from the device.</span></span>

<span data-ttu-id="c22ab-652">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-652">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-653">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-653">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-654">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-654">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-655">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-655">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-656">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-656">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-657">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-657">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1405" />

### <a name="mt1405-could-not-read-crash-report-afcfilerefread--returned-"></a><span data-ttu-id="c22ab-658">MT1405:無法讀取的當機報告：AFCFileRefRead （\*） 傳回: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-658">MT1405: Could not read crash report: AFCFileRefRead (\*) returned: \*</span></span>

<span data-ttu-id="c22ab-659">嘗試從裝置存取的當機報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-659">An error occurred when trying to access crash reports from the device.</span></span>

<span data-ttu-id="c22ab-660">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-660">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-661">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-661">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-662">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-662">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-663">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-663">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-664">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-664">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-665">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-665">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<a name="MT1406" />

### <a name="mt1406-could-not-list-crash-reports-afcdirectoryopen--returned-"></a><span data-ttu-id="c22ab-666">MT1406:無法列出當機報告：AFCDirectoryOpen （\*） 傳回: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-666">MT1406: Could not list crash reports: AFCDirectoryOpen (\*) returned: \*</span></span>

<span data-ttu-id="c22ab-667">嘗試從裝置存取的當機報告時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-667">An error occurred when trying to access crash reports from the device.</span></span>

<span data-ttu-id="c22ab-668">若要嘗試解決這個問題的重要事項︰</span><span class="sxs-lookup"><span data-stu-id="c22ab-668">Things to try to solve this:</span></span>

* <span data-ttu-id="c22ab-669">從裝置刪除應用程式，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-669">Delete the application from the device and try again.</span></span>
* <span data-ttu-id="c22ab-670">中斷連接裝置並重新建立。</span><span class="sxs-lookup"><span data-stu-id="c22ab-670">Disconnect the device and reconnect it.</span></span>
* <span data-ttu-id="c22ab-671">重新啟動裝置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-671">Reboot the device.</span></span>
* <span data-ttu-id="c22ab-672">重新啟動 mac。</span><span class="sxs-lookup"><span data-stu-id="c22ab-672">Reboot the Mac.</span></span>
* <span data-ttu-id="c22ab-673">同步處理裝置與 iTunes （這會從裝置移除任何損毀報告）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-673">Synchronize the device with iTunes (this will remove any crash reports from the device).</span></span>

<!--- 1407 used by mmp -->

### <a name="mt16xx-macho"></a><span data-ttu-id="c22ab-674">MT16xx:MachO</span><span class="sxs-lookup"><span data-stu-id="c22ab-674">MT16xx: MachO</span></span>

<!--
  MT16xx    MachO.cs
  -->

<a name="MT1600" />

### <a name="mt1600-not-a-mach-o-dynamic-library-unknown-header-0x-"></a><span data-ttu-id="c22ab-675">MT1600:不是 MACH-O 動態程式庫 （未知標頭 ' 0 x \*'）: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-675">MT1600: Not a Mach-O dynamic library (unknown header '0x\*'): \*.</span></span>

<span data-ttu-id="c22ab-676">處理的動態程式庫時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-676">An error occurred while processing the dynamic library in question.</span></span>

<span data-ttu-id="c22ab-677">請確定動態程式庫是有效的 MACH-O 動態程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-677">Please make sure the dynamic library is a valid Mach-O dynamic library.</span></span>

<span data-ttu-id="c22ab-678">可以使用驗證程式庫格式`file`從終端機命令：</span><span class="sxs-lookup"><span data-stu-id="c22ab-678">The format of a library can be verified using the `file` command from a terminal:</span></span>

    file -arch all -l /path/to/library.dylib

<a name="MT1601" />

### <a name="mt1601-not-a-static-library-unknown-header--"></a><span data-ttu-id="c22ab-679">MT1601:不是靜態程式庫 (未知標頭 ' \*'): \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-679">MT1601: Not a static library (unknown header '\*'): \*.</span></span>

<span data-ttu-id="c22ab-680">處理的靜態程式庫時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-680">An error occurred while processing the static library in question.</span></span>

<span data-ttu-id="c22ab-681">請確定靜態程式庫是有效的 MACH-O 靜態程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-681">Please make sure the static library is a valid Mach-O static library.</span></span>

<span data-ttu-id="c22ab-682">可以使用驗證程式庫格式`file`從終端機命令：</span><span class="sxs-lookup"><span data-stu-id="c22ab-682">The format of a library can be verified using the `file` command from a terminal:</span></span>

    file -arch all -l /path/to/library.a

<a name="MT1602" />

### <a name="mt1602-not-a-mach-o-dynamic-library-unknown-header-0x-"></a><span data-ttu-id="c22ab-683">MT1602:不是 MACH-O 動態程式庫 （未知標頭 ' 0 x \*'）: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-683">MT1602: Not a Mach-O dynamic library (unknown header '0x\*'): \*.</span></span>

<span data-ttu-id="c22ab-684">處理的動態程式庫時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-684">An error occurred while processing the dynamic library in question.</span></span>

<span data-ttu-id="c22ab-685">請確定動態程式庫是有效的 MACH-O 動態程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-685">Please make sure the dynamic library is a valid Mach-O dynamic library.</span></span>

<span data-ttu-id="c22ab-686">可以使用驗證程式庫格式`file`從終端機命令：</span><span class="sxs-lookup"><span data-stu-id="c22ab-686">The format of a library can be verified using the `file` command from a terminal:</span></span>

    file -arch all -l /path/to/library.dylib

<a name="MT1603" />

### <a name="mt1603-unknown-format-for-fat-entry-at-position--in-"></a><span data-ttu-id="c22ab-687">MT1603:未知的格式，fat 項目的位置 \* 的 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-687">MT1603: Unknown format for fat entry at position \* in \*.</span></span>

<span data-ttu-id="c22ab-688">處理有問題的 fat 封存時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-688">An error occurred while processing the fat archive in question.</span></span>

<span data-ttu-id="c22ab-689">請確定 fat 封存有效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-689">Please make sure the fat archive is valid.</span></span>

<span data-ttu-id="c22ab-690">可以使用驗證的 fat 封存格式`file`從終端機命令：</span><span class="sxs-lookup"><span data-stu-id="c22ab-690">The format of a fat archive can be verified using the `file` command from a terminal:</span></span>

    file -arch all -l /path/to/file

<a name="MT1604" />

### <a name="mt1604-file-of-type--is-not-a-macho-file-"></a><span data-ttu-id="c22ab-691">MT1604:類型的檔案 \* 不是 MachO 檔案 （\*）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-691">MT1604: File of type \* is not a MachO file (\*).</span></span>

<span data-ttu-id="c22ab-692">處理 MachO 檔案有問題時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-692">An error occurred while processing the MachO file in question.</span></span>

<span data-ttu-id="c22ab-693">請確定檔案是有效的 MACH-O 動態程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-693">Please make sure the file is a valid Mach-O dynamic library.</span></span>

<span data-ttu-id="c22ab-694">可以使用驗證檔案的格式`file`從終端機命令：</span><span class="sxs-lookup"><span data-stu-id="c22ab-694">The format of a file can be verified using the `file` command from a terminal:</span></span>

    file -arch all -l /path/to/file

## <a name="mt2xxx-linker-error-messages"></a><span data-ttu-id="c22ab-695">MT2xxx:連結器錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-695">MT2xxx: Linker error messages</span></span>

<!--
 MT2xxx Linker
  MT20xx Linker (general) errors
  -->

<a name="MT2001" />

### <a name="mt2001-could-not-link-assemblies"></a><span data-ttu-id="c22ab-696">MT2001:無法將組件的連結</span><span class="sxs-lookup"><span data-stu-id="c22ab-696">MT2001: Could not link assemblies</span></span>

<span data-ttu-id="c22ab-697">此錯誤表示受管理的連結器遇到意外的錯誤，例如例外狀況，並無法完成或儲存處理組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-697">This error means that the managed linker encountered an unexpected error, e.g. an exception, and could not complete or save the assembly being processed.</span></span> <span data-ttu-id="c22ab-698">確切的錯誤的詳細資訊會屬於組建記錄檔例如</span><span class="sxs-lookup"><span data-stu-id="c22ab-698">More information about the exact error will be part of the build log, e.g.</span></span>

```
error MT2001: Could not link assemblies.
    Method: `System.Void Todo.TodoListPageCS/<<-ctor>b__1_0>d::SetStateMachine(System.Runtime.CompilerServices.IAsyncStateMachine)`
    Assembly: `QuickTodo, Version=1.0.6297.28241, Culture=neutral, PublicKeyToken=null`
Reason: Value cannot be null.
Parameter name: instruction
```

<span data-ttu-id="c22ab-699">請務必提出這類問題的 bug 報告。</span><span class="sxs-lookup"><span data-stu-id="c22ab-699">It is important to file a bug report for such issues.</span></span> <span data-ttu-id="c22ab-700">在大部分情況下發行適當的修正程式之前可以提供因應措施。</span><span class="sxs-lookup"><span data-stu-id="c22ab-700">In most case a workaround can be provided until a proper fix is published.</span></span> <span data-ttu-id="c22ab-701">若要解決此問題，上述資訊是關鍵 （以及測試案例和/或組件 binairy）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-701">The above information is critical (along with a test case and/or the assembly binairy) to resolve the issue.</span></span>

<a name="MT2002" />

### <a name="mt2002-can-not-resolve-reference-"></a><span data-ttu-id="c22ab-702">MT2002:無法解析參考: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-702">MT2002: Can not resolve reference: \*</span></span>

<a name="MT2003" />

### <a name="mt2003-option--will-be-ignored-since-linking-is-disabled"></a><span data-ttu-id="c22ab-703">MT2003:選項 ' \*' 將被忽略，因為連結已停用</span><span class="sxs-lookup"><span data-stu-id="c22ab-703">MT2003: Option '\*' will be ignored since linking is disabled</span></span>

<a name="MT2004" />

### <a name="mt2004-extra-linker-definitions-file--could-not-be-located"></a><span data-ttu-id="c22ab-704">MT2004:額外的連結器定義檔 ' \*' 找不到。</span><span class="sxs-lookup"><span data-stu-id="c22ab-704">MT2004: Extra linker definitions file '\*' could not be located.</span></span>

<a name="MT2005" />

### <a name="mt2005-definitions-from--could-not-be-parsed"></a><span data-ttu-id="c22ab-705">MT2005:定義從 ' \*' 無法剖析。</span><span class="sxs-lookup"><span data-stu-id="c22ab-705">MT2005: Definitions from '\*' could not be parsed.</span></span>

<a name="MT2006" />

### <a name="mt2006-can-not-load-mscorlibdll-from--please-reinstall-xamarinios"></a><span data-ttu-id="c22ab-706">MT2006:無法載入 mscorlib.dll 與: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-706">MT2006: Can not load mscorlib.dll from: \*.</span></span> <span data-ttu-id="c22ab-707">請重新安裝 Xamarin.iOS。</span><span class="sxs-lookup"><span data-stu-id="c22ab-707">Please reinstall Xamarin.iOS.</span></span>

<span data-ttu-id="c22ab-708">這通常表示會有與您的 Xamarin.iOS 安裝問題。</span><span class="sxs-lookup"><span data-stu-id="c22ab-708">This generally indicates that there is a problem with your Xamarin.iOS installation.</span></span> <span data-ttu-id="c22ab-709">請嘗試重新安裝 Xamarin.iOS。</span><span class="sxs-lookup"><span data-stu-id="c22ab-709">Please try reinstalling Xamarin.iOS.</span></span>

<!--- 2007 used by mmp -->
<!--- 2009 used by mmp -->

<a name="MT2010" />

### <a name="mt2010-unknown-httpmessagehandler--valid-values-are-httpclienthandler-default-cfnetworkhandler-or-nsurlsessionhandler"></a><span data-ttu-id="c22ab-710">MT2010:未知的 HttpMessageHandler `*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-710">MT2010: Unknown HttpMessageHandler `*`.</span></span> <span data-ttu-id="c22ab-711">有效值為 HttpClientHandler （預設值）、 CFNetworkHandler 或 NSUrlSessionHandler</span><span class="sxs-lookup"><span data-stu-id="c22ab-711">Valid values are HttpClientHandler (default), CFNetworkHandler or NSUrlSessionHandler</span></span>

<a name="MT2011" />

### <a name="mt2011-unknown-tlsprovider---valid-values-are-default-or-appletls"></a><span data-ttu-id="c22ab-712">MT2011:未知的 TlsProvider `*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-712">MT2011: Unknown TlsProvider `*`.</span></span>  <span data-ttu-id="c22ab-713">有效值為 default 或 appletls。</span><span class="sxs-lookup"><span data-stu-id="c22ab-713">Valid values are default or appletls.</span></span>

<span data-ttu-id="c22ab-714">若要指定的值`tls-provider=`不是有效的 TLS （傳輸層安全性） 提供者。</span><span class="sxs-lookup"><span data-stu-id="c22ab-714">The value given to `tls-provider=` is not a valid TLS (Transport Layer Security) provider.</span></span>

<span data-ttu-id="c22ab-715">`default`和`appletls`是唯一有效的值，同時兩者皆表示相同的選項，也就是提供 SSL/TLS 支援使用原生 Apple TLS API。</span><span class="sxs-lookup"><span data-stu-id="c22ab-715">The `default` and `appletls` are the only valid values and both represent the same option, which is to provide the SSL/TLS support using the native Apple TLS API.</span></span>

<!--- 2012 used by mmp -->
<!--- 2013 used by mmp -->
<!--- 2014 used by mmp -->

<a name="MT2015" />

### <a name="mt2015-invalid-httpmessagehandler--for-watchos-the-only-valid-value-is-nsurlsessionhandler"></a><span data-ttu-id="c22ab-716">MT2015:無效的 HttpMessageHandler`*`進行 watchOS。</span><span class="sxs-lookup"><span data-stu-id="c22ab-716">MT2015: Invalid HttpMessageHandler `*` for watchOS.</span></span> <span data-ttu-id="c22ab-717">唯一有效的值是 NSUrlSessionHandler。</span><span class="sxs-lookup"><span data-stu-id="c22ab-717">The only valid value is NSUrlSessionHandler.</span></span>

<span data-ttu-id="c22ab-718">這是因為專案檔指定了無效的 HttpMessageHandler，就會發生警告。</span><span class="sxs-lookup"><span data-stu-id="c22ab-718">This is a warning that occurs because the project file specifies an invalid HttpMessageHandler.</span></span>

<span data-ttu-id="c22ab-719">產生預設情況下我們的預覽工具的舊版專案檔中無效的值。</span><span class="sxs-lookup"><span data-stu-id="c22ab-719">Earlier versions of our preview tools generated by default an invalid value in the project file.</span></span>

<span data-ttu-id="c22ab-720">若要修正這個警告，在文字編輯器中，開啟專案檔案，並從 XML 移除所有的 HttpMessageHandler 節點。</span><span class="sxs-lookup"><span data-stu-id="c22ab-720">To fix this warning, open the project file in a text editor, and remove all HttpMessageHandler nodes from the XML.</span></span>

<a name="MT2016" />

### <a name="mt2016-invalid-tlsprovider-legacy-option-the-only-valid-value-appletls-will-be-used"></a><span data-ttu-id="c22ab-721">MT2016:無效的 TlsProvider`legacy`選項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-721">MT2016: Invalid TlsProvider `legacy` option.</span></span> <span data-ttu-id="c22ab-722">唯一有效的值`appletls`將使用。</span><span class="sxs-lookup"><span data-stu-id="c22ab-722">The only valid value `appletls` will be used.</span></span>

<span data-ttu-id="c22ab-723">`legacy`提供者，也就是完全受控的 SSLv3 / TLSv1 唯一的提供者，再也不會隨附 Xamarin.iOS。</span><span class="sxs-lookup"><span data-stu-id="c22ab-723">The `legacy` provider, which was a fully managed SSLv3 / TLSv1 only provider, is not shipped with Xamarin.iOS anymore.</span></span> <span data-ttu-id="c22ab-724">使用這個舊的提供者，現在使用較新建置的專案`appletls`其中一個。</span><span class="sxs-lookup"><span data-stu-id="c22ab-724">Projects that were using this old provider and now build with the newer `appletls` one.</span></span>

<span data-ttu-id="c22ab-725">若要修正這個警告，請在文字編輯器中，開啟專案檔案，並移除所有 'MtouchTlsProvider' 的 xml 節點。</span><span class="sxs-lookup"><span data-stu-id="c22ab-725">To fix this warning, open the project file in a text editor, and remove all \`MtouchTlsProvider\`\` nodes from the XML.</span></span>

<a name="MT2017" />

### <a name="mt2017-could-not-process-xml-description"></a><span data-ttu-id="c22ab-726">MT2017:無法處理 XML 描述。</span><span class="sxs-lookup"><span data-stu-id="c22ab-726">MT2017: Could not process XML description.</span></span>

<span data-ttu-id="c22ab-727">這表示在沒有錯誤[自訂 XML 連結器組態檔](https://developer.xamarin.com/guides/cross-platform/advanced/custom_linking/)提供時，請檢閱您的檔案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-727">This means there is an error on the [custom XML linker configuration file](https://developer.xamarin.com/guides/cross-platform/advanced/custom_linking/) you provided, please review your file.</span></span>

<a name="MT2018" />

### <a name="mt2018-the-assembly--is-referenced-from-two-different-locations--and-"></a><span data-ttu-id="c22ab-728">MT2018:組件 '\*' 所參考的兩個不同位置: '\*' 和 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-728">MT2018: The assembly '\*' is referenced from two different locations: '\*' and '\*'.</span></span>

<span data-ttu-id="c22ab-729">從多個位置中的錯誤訊息提到組件會載入的。</span><span class="sxs-lookup"><span data-stu-id="c22ab-729">The assembly mentioned in the error message is loaded from multiple locations.</span></span> <span data-ttu-id="c22ab-730">請務必一律使用相同版本的組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-730">Make sure to always use the same version of an assembly.</span></span>

<a name="MT2019" />

### <a name="mt2019-can-not-load-the-root-assembly-"></a><span data-ttu-id="c22ab-731">MT2019:無法載入根組件 ' \*'</span><span class="sxs-lookup"><span data-stu-id="c22ab-731">MT2019: Can not load the root assembly '\*'</span></span>

<span data-ttu-id="c22ab-732">無法載入根組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-732">The root assembly could not be loaded.</span></span> <span data-ttu-id="c22ab-733">請確認該路徑中的錯誤訊息參考到現有的檔案，而且它是有效的.NET 組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-733">Please verify that the path in the error message refers to an existing file, and that it's a valid .NET assembly.</span></span>

<a name="MT202x" />

### <a name="mt202x-binding-optimizer-failed-processing-"></a><span data-ttu-id="c22ab-734">MT202x:繫結最佳化工具無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-734">MT202x: Binding Optimizer failed processing `...`.</span></span>

<span data-ttu-id="c22ab-735">發生未預期發生時嘗試最佳化產生的繫結程式碼。</span><span class="sxs-lookup"><span data-stu-id="c22ab-735">Something unexpected occured when trying to optimize generated binding code.</span></span> <span data-ttu-id="c22ab-736">造成這個問題的項目出現在錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c22ab-736">The element causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-737">若要修正此問題，名為組件 （或包含的型別或方法） 需要提供[bug 報表](http://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`在**其他 mtouch引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-737">To fix this issue the assembly named (or containing the type or method named) will need to be provided in a [bug report](http://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<span data-ttu-id="c22ab-738">最後一位數`x`會：</span><span class="sxs-lookup"><span data-stu-id="c22ab-738">The last digit `x` will be:</span></span>
* <span data-ttu-id="c22ab-739">`0` 組件名稱;</span><span class="sxs-lookup"><span data-stu-id="c22ab-739">`0` for an assembly name;</span></span>
* <span data-ttu-id="c22ab-740">`1` 型別名稱;</span><span class="sxs-lookup"><span data-stu-id="c22ab-740">`1` for a type name;</span></span>
* <span data-ttu-id="c22ab-741">`3` 方法名稱;</span><span class="sxs-lookup"><span data-stu-id="c22ab-741">`3` for a method name;</span></span>

<a name="MT2030" />

### <a name="mt2030-remove-user-resources-failed-processing-"></a><span data-ttu-id="c22ab-742">MT2030:移除使用者的資源無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-742">MT2030: Remove User Resources failed processing `...`.</span></span>

<span data-ttu-id="c22ab-743">發生未預期發生時嘗試移除使用者的資源。</span><span class="sxs-lookup"><span data-stu-id="c22ab-743">Something unexpected occured when trying to remove user resources.</span></span> <span data-ttu-id="c22ab-744">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-744">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-745">若要修正此問題的組件必須在中提供[bug 報表](http://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-745">To fix this issue the assembly will need to be provided in a [bug report](http://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<span data-ttu-id="c22ab-746">使用者資源是 （如資源） 必須解壓縮，在建置時，若要建立應用程式套件組合的組件內所包含的檔案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-746">User resources are files included inside assemblies (as resources) that needs to be extracted, at build time, to create the application bundle.</span></span> <span data-ttu-id="c22ab-747">包括：</span><span class="sxs-lookup"><span data-stu-id="c22ab-747">This includes:</span></span>

* <span data-ttu-id="c22ab-748">`__monotouch_content_*` 和`__monotouch_pages_*`資源; 以及</span><span class="sxs-lookup"><span data-stu-id="c22ab-748">`__monotouch_content_*` and `__monotouch_pages_*` resources; and</span></span>
* <span data-ttu-id="c22ab-749">原生程式庫內嵌在繫結的組件;</span><span class="sxs-lookup"><span data-stu-id="c22ab-749">Native libraries embedded inside a binding assembly;</span></span>

<a name="MT2040" />

### <a name="mt2040-default-httpmessagehandler-setter-failed-processing-"></a><span data-ttu-id="c22ab-750">MT2040:預設 HttpMessageHandler setter 無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-750">MT2040: Default HttpMessageHandler setter failed processing `...`.</span></span>

<span data-ttu-id="c22ab-751">嘗試將設為預設值時，發生未預期發生`HttpMessageHandler`應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-751">Something unexpected occured when trying to set the default `HttpMessageHandler` for the application.</span></span> <span data-ttu-id="c22ab-752">請提出[bug 報表](http://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-752">Please file a [bug report](http://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2050" />

### <a name="mt2050-code-remover-failed-processing-"></a><span data-ttu-id="c22ab-753">MT2050:程式碼 Remover 無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-753">MT2050: Code Remover failed processing `...`.</span></span>

<span data-ttu-id="c22ab-754">發生未預期發生時嘗試移除與應用程式傳送的 BCL 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c22ab-754">Something unexpected occured when trying to remove code from BCL shipping with the application.</span></span> <span data-ttu-id="c22ab-755">請提出[bug 報表](http://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-755">Please file a [bug report](http://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2060" />

### <a name="mt2060-sealer-failed-processing-"></a><span data-ttu-id="c22ab-756">MT2060:密封程式無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-756">MT2060: Sealer failed processing `...`.</span></span>

<span data-ttu-id="c22ab-757">發生未預期發生或 devirtualizing 某些方法時嘗試密封類型或方法 （最後一個）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-757">Something unexpected occured when trying to seal types or methods (final) or when devirtualizing some methods.</span></span> <span data-ttu-id="c22ab-758">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-758">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-759">若要修正此問題的組件必須在中提供[bug 報表](http://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-759">To fix this issue the assembly will need to be provided in a [bug report](http://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2070" />

### <a name="mt2070-metadata-reducer-failed-processing-"></a><span data-ttu-id="c22ab-760">MT2070:中繼資料的歸納器無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-760">MT2070: Metadata Reducer failed processing `...`.</span></span>

<span data-ttu-id="c22ab-761">發生未預期發生時嘗試減少從應用程式的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c22ab-761">Something unexpected occured when trying to reduce the metadata from the application.</span></span> <span data-ttu-id="c22ab-762">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-762">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-763">若要修正此問題的組件必須在中提供[bug 報表](http://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-763">To fix this issue the assembly will need to be provided in a [bug report](http://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2080" />

### <a name="mt2080-marknsobjects-failed-processing-"></a><span data-ttu-id="c22ab-764">MT2080:處理失敗 MarkNSObjects `...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-764">MT2080: MarkNSObjects failed processing `...`.</span></span>

<span data-ttu-id="c22ab-765">嘗試將標記時，發生未預期發生`NSObject`從應用程式的子類別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-765">Something unexpected occured when trying to mark `NSObject` subclasses from the application.</span></span> <span data-ttu-id="c22ab-766">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-766">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-767">若要修正此問題的組件必須在中提供[bug 報表](http://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-767">To fix this issue the assembly will need to be provided in a [bug report](http://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2090" />

### <a name="mt2090-inliner-failed-processing-"></a><span data-ttu-id="c22ab-768">MT2090:內嵌者無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-768">MT2090: Inliner failed processing `...`.</span></span>

<span data-ttu-id="c22ab-769">發生未預期發生時嘗試從應用程式的內嵌程式碼。</span><span class="sxs-lookup"><span data-stu-id="c22ab-769">Something unexpected occured when trying to inline code from the application.</span></span> <span data-ttu-id="c22ab-770">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-770">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-771">若要修正此問題的組件必須在中提供[bug 報表](https://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-771">In order to fix this issue the assembly will need to be provided in a [bug report](https://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<!-- MT21xx: more linker errors -->

<!--- 2100 used by mmp -->

<a name="MT2100" />

### <a name="mt2100-smart-enum-conversion-preserver-failed-processing-"></a><span data-ttu-id="c22ab-772">MT2100:智慧型列舉轉換守護者無法處理`...`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-772">MT2100: Smart Enum Conversion Preserver failed processing `...`.</span></span>

<span data-ttu-id="c22ab-773">發生未預期發生時嘗試轉換方法，從應用程式的智慧列舉標記。</span><span class="sxs-lookup"><span data-stu-id="c22ab-773">Something unexpected occured when trying to mark the conversion methods for smart enums from the application.</span></span> <span data-ttu-id="c22ab-774">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-774">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-775">若要修正此問題的組件必須在中提供[bug 報表](https://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-775">In order to fix this issue the assembly will need to be provided in a [bug report](https://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2101" />

### <a name="mt2101-cant-resolve-the-reference--referenced-from-the-method--in-"></a><span data-ttu-id="c22ab-776">MT2101:無法解析參考 '\*'，參考從方法'\*' 中 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-776">MT2101: Can't resolve the reference '\*', referenced from the method '\*' in '\*'.</span></span>

<span data-ttu-id="c22ab-777">處理錯誤訊息中所述的方法時遇到無效的組件參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-777">An invalid assembly reference was encountered when processing the method mentioned in the error message.</span></span>

<span data-ttu-id="c22ab-778">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-778">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-779">若要修正此問題的組件必須在中提供[bug 報表](https://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-779">To fix this issue the assembly will need to be provided in a [bug report](https://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2102" />

### <a name="mt2102-error-processing-the-method--in-the-assembly--"></a><span data-ttu-id="c22ab-780">MT2102:錯誤處理方法 '\*'中的組件'\*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-780">MT2102: Error processing the method '\*' in the assembly '\*': \*</span></span>

<span data-ttu-id="c22ab-781">發生未預期發生時，嘗試將錯誤訊息中所述的方法。</span><span class="sxs-lookup"><span data-stu-id="c22ab-781">Something unexpected occured when trying to mark the method mentioned in the error message.</span></span>

<span data-ttu-id="c22ab-782">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-782">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-783">若要修正此問題的組件必須在中提供[bug 報表](https://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-783">To fix this issue the assembly will need to be provided in a [bug report](https://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2103" />

### <a name="mt2103-error-processing-assembly--"></a><span data-ttu-id="c22ab-784">MT2103:處理組件時發生錯誤 '\*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-784">MT2103: Error processing assembly '\*': \*</span></span>

<span data-ttu-id="c22ab-785">處理組件時，就會發生意外的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-785">An unexpected error occured when processing an assembly.</span></span>

<span data-ttu-id="c22ab-786">造成這個問題的組件是名為錯誤訊息中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-786">The assembly causing the issue is named in the error message.</span></span> <span data-ttu-id="c22ab-787">若要修正此問題的組件必須在中提供[bug 報表](https://bugzilla.xamarin.com)以及完成的組建記錄檔與啟用的詳細資訊 (亦即`-v -v -v -v`中**其他 mtouch 引數**)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-787">In order to fix this issue the assembly will need to be provided in a [bug report](https://bugzilla.xamarin.com) along with a complete build log with verbosity enabled (i.e. `-v -v -v -v` in the **Additional mtouch arguments**).</span></span>

<a name="MT2104" />

### <a name="mm2104-unable-to-link-assembly-0-as-it-is-mixed-mode"></a><span data-ttu-id="c22ab-788">MM2104:無法將連結的組件 '{0}' 因為它是混合模式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-788">MM2104: Unable to link assembly '{0}' as it is mixed-mode.</span></span>

<span data-ttu-id="c22ab-789">連結器可以處理混合模式組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-789">Mixed-mode assemblies can not be processed by the linker.</span></span>

<span data-ttu-id="c22ab-790">請參閱 https://msdn.microsoft.com/library/x0w2664k.aspx 如需有關混合模式組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-790">See https://msdn.microsoft.com/library/x0w2664k.aspx for more information on mixed-mode assemblies.</span></span>

## <a name="mt3xxx-aot-error-messages"></a><span data-ttu-id="c22ab-791">MT3xxx:AOT 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-791">MT3xxx: AOT error messages</span></span>

<!--
 MT3xxx AOT
  MT30xx AOT (general) errors
  -->

<a name="MT3001" />

### <a name="mt3001-could-not-aot-the-assembly-"></a><span data-ttu-id="c22ab-792">MT3001:無法 AOT 的組件 ' \*'</span><span class="sxs-lookup"><span data-stu-id="c22ab-792">MT3001: Could not AOT the assembly '\*'</span></span>

<span data-ttu-id="c22ab-793">這通常表示 AOT 編譯器中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-793">This generally indicates a bug in the AOT compiler.</span></span> <span data-ttu-id="c22ab-794">請將 bug 歸檔[ http://bugzilla.xamarin.com ](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)可以用來重現錯誤的專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-794">Please file a bug [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS) with a project that can be used to reproduce the error.</span></span>

<span data-ttu-id="c22ab-795">有時候很可能可解決此停用累加建置專案的 iOS 組建選項中 (但它仍是一個 bug，因此請回報還是)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-795">Sometimes it's possible to work around this by disabling incremental builds in the project's iOS Build option (but it's still a bug, so please report it anyways).</span></span>

<a name="MT3002" />

### <a name="mt3002-aot-restriction-method--must-be-static-since-it-is-decorated-with-monopinvokecallback-see-httpsdeveloperxamarincomguidesiosadvancedtopicslimitationsreversecallbackshttpsdeveloperxamarincomguidesiosadvancedtopicslimitationsreversecallbacks"></a><span data-ttu-id="c22ab-796">MT3002:AOT 限制：方法 ' \*' 必須是靜態，因為它附有 [MonoPInvokeCallback]。</span><span class="sxs-lookup"><span data-stu-id="c22ab-796">MT3002: AOT restriction: Method '\*' must be static since it is decorated with [MonoPInvokeCallback].</span></span> <span data-ttu-id="c22ab-797">請參閱 [https://developer.xamarin.com/guides/ios/advanced_topics/limitations/#Reverse_Callbacks](https://developer.xamarin.com/guides/ios/advanced_topics/limitations/#Reverse_Callbacks)</span><span class="sxs-lookup"><span data-stu-id="c22ab-797">See [https://developer.xamarin.com/guides/ios/advanced_topics/limitations/#Reverse_Callbacks](https://developer.xamarin.com/guides/ios/advanced_topics/limitations/#Reverse_Callbacks)</span></span>

<span data-ttu-id="c22ab-798">此錯誤訊息是來自 AOT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-798">This error message comes from the AOT compiler.</span></span>

<a name="MT3003" />

### <a name="mt3003-conflicting---debug-and---llvm-options-soft-debugging-is-disabled"></a><span data-ttu-id="c22ab-799">MT3003:衝突-偵錯和-llvm 選項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-799">MT3003: Conflicting --debug and --llvm options.</span></span> <span data-ttu-id="c22ab-800">軟偵錯已停用。</span><span class="sxs-lookup"><span data-stu-id="c22ab-800">Soft-debugging is disabled.</span></span>

<span data-ttu-id="c22ab-801">偵錯時，不支援在啟用 LLVM。</span><span class="sxs-lookup"><span data-stu-id="c22ab-801">Debugging is not supported when LLVM is enabled.</span></span> <span data-ttu-id="c22ab-802">如果您需要偵錯應用程式，請先停用 LLVM。</span><span class="sxs-lookup"><span data-stu-id="c22ab-802">If you need to debug the app, disable LLVM first.</span></span>

<a name="MT3004" />

### <a name="mt3004-could-not-aot-the-assembly--because-it-doesnt-exist"></a><span data-ttu-id="c22ab-803">MT3004:無法 AOT 的組件 ' \*' 因為不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-803">MT3004: Could not AOT the assembly '\*' because it doesn't exist.</span></span>

<a name="MT3005" />

### <a name="mt3005-the-dependency--of-the-assembly--was-not-found-please-review-the-projects-references"></a><span data-ttu-id="c22ab-804">MT3005:相依性 '\*'的組件'\*' 找不到。</span><span class="sxs-lookup"><span data-stu-id="c22ab-804">MT3005: The dependency '\*' of the assembly '\*' was not found.</span></span> <span data-ttu-id="c22ab-805">請檢閱專案的參考。</span><span class="sxs-lookup"><span data-stu-id="c22ab-805">Please review the project's references.</span></span>

<span data-ttu-id="c22ab-806">此外，這通常會發生時的組件參考另一個版本的平台組件 （通常是.NET 4 版本的 mscorlib.dll）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-806">This typically occurs when an assembly references another version of a platform assembly (usually the .NET 4 version of mscorlib.dll).</span></span>

<span data-ttu-id="c22ab-807">這不支援，可能無法建置，或要正確執行 （組件可能會使用 API，從.NET 4 版本的 Xamarin.iOS 版本沒有的 mscorlib.dll）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-807">This is not supported, and may not build or execute properly (the assembly may use API from the .NET 4 version of mscorlib.dll that the Xamarin.iOS version does not have).</span></span>

<a name="MT3006" />

### <a name="mt3006-could-not-compute-a-complete-dependency-map-for-the-project-this-will-result-in-slower-build-times-because-xamarinios-cant-properly-detect-what-needs-to-be-rebuilt-and-what-does-not-need-to-be-rebuilt-please-review-previous-warnings-for-more-details"></a><span data-ttu-id="c22ab-808">MT3006:無法計算專案的完整相依性對應。</span><span class="sxs-lookup"><span data-stu-id="c22ab-808">MT3006: Could not compute a complete dependency map for the project.</span></span> <span data-ttu-id="c22ab-809">這將會導致較慢的建置時間，因為 Xamarin.iOS 無法正確偵測到什麼需要重建 （和什麼不需要重建）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-809">This will result in slower build times because Xamarin.iOS can't properly detect what needs to be rebuilt (and what does not need to be rebuilt).</span></span> <span data-ttu-id="c22ab-810">請之前的警告，如需詳細資訊，檢閱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-810">Please review previous warnings for more details.</span></span>

 <span data-ttu-id="c22ab-811">建置或正確執行 （組件可能會使用 API，從.NET 4 版本的 Xamarin.iOS 版本沒有的 mscorlib.dll）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-811">build or execute properly (the assembly may use API from the .NET 4 version of mscorlib.dll that the Xamarin.iOS version does not have).</span></span>

<a name="MT3007" />

### <a name="mt3007-debug-info-files-mdb-will-not-be-loaded-when-llvm-is-enabled"></a><span data-ttu-id="c22ab-812">MT3007:啟用 llvm 時，將不會載入偵錯資訊檔案 (\*.mdb)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-812">MT3007: Debug info files (\*.mdb) will not be loaded when llvm is enabled.</span></span>

<a name="MT3008" />

### <a name="mt3008-bitcode-support-requires-the-use-of-the-llvm-aot-backend---llvm"></a><span data-ttu-id="c22ab-813">MT3008:Bitcode 支援需要使用 LLVM AOT 後端 (-llvm)</span><span class="sxs-lookup"><span data-stu-id="c22ab-813">MT3008: Bitcode support requires the use of the LLVM AOT backend (--llvm)</span></span>

<span data-ttu-id="c22ab-814">Bitcode 支援需要使用 LLVM AOT 後端 (-llvm)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-814">Bitcode support requires the use of the LLVM AOT backend (--llvm).</span></span>

<span data-ttu-id="c22ab-815">停用 Bitcode 支援或啟用 LLVM。</span><span class="sxs-lookup"><span data-stu-id="c22ab-815">Either disable Bitcode support or enable LLVM.</span></span>

<!--- 3009 used by mmp -->
<!--- 3010 used by mmp -->

## <a name="mt4xxx-code-generation-error-messages"></a><span data-ttu-id="c22ab-816">MT4xxx:程式碼產生錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-816">MT4xxx: Code generation error messages</span></span>

### <a name="mt40xx-main"></a><span data-ttu-id="c22ab-817">MT40xx:主要</span><span class="sxs-lookup"><span data-stu-id="c22ab-817">MT40xx: Main</span></span>

<!--
 MT4xxx code generation
  MT40xx main.m
  -->

<a name="MT4001" />

### <a name="mt4001-the-main-template-could-not-be-expanded-to-"></a><span data-ttu-id="c22ab-818">MT4001:主要的範本無法展開至`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-818">MT4001: The main template could not be expanded to `*`.</span></span>

<span data-ttu-id="c22ab-819">產生 main.m 時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-819">An error occurred when generating main.m.</span></span> <span data-ttu-id="c22ab-820">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-820">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4002" />

### <a name="mt4002-failed-to-compile-the-generated-code-for-pinvoke-methods-please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-821">MT4002:無法編譯產生的程式碼，P/Invoke 方法。</span><span class="sxs-lookup"><span data-stu-id="c22ab-821">MT4002: Failed to compile the generated code for P/Invoke methods.</span></span> <span data-ttu-id="c22ab-822">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-822">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<span data-ttu-id="c22ab-823">無法編譯產生的程式碼，P/Invoke 方法。</span><span class="sxs-lookup"><span data-stu-id="c22ab-823">Failed to compile the generated code for P/Invoke methods.</span></span> <span data-ttu-id="c22ab-824">請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-824">Please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

### <a name="mt41xx-registrar"></a><span data-ttu-id="c22ab-825">MT41xx:登錄器</span><span class="sxs-lookup"><span data-stu-id="c22ab-825">MT41xx: Registrar</span></span>

<!--
  MT41xx registrar.m
  -->

<a name="MT4101" />

### <a name="mt4101-the-registrar-cannot-build-a-signature-for-type-"></a><span data-ttu-id="c22ab-826">MT4101:在註冊機構的版本無法建立類型的簽章`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-826">MT4101: The registrar cannot build a signature for type `*`.</span></span>

<span data-ttu-id="c22ab-827">在執行階段不知道如何封送處理從 OBJECTIVE-C 的匯出 API 中找不到型別</span><span class="sxs-lookup"><span data-stu-id="c22ab-827">A type was found in exported API that the runtime doesn't know how to marshal to/from Objective-C.</span></span>

<span data-ttu-id="c22ab-828">如果您認為 Xamarin.iOS 應該支援的類型有問題，請提出的增強功能要求[ http://bugzilla.xamarin.com ](http://bugzilla.xamarin.com)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-828">If you believe Xamarin.iOS should support the type in question, please file an enhancement request at [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com).</span></span>

<a name="MT4102" />

### <a name="mt4102-the-registrar-found-an-invalid-type--in-signature-for-method--use--instead"></a><span data-ttu-id="c22ab-829">MT4102:在註冊機構找到無效的型別`*`方法的簽章中`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-829">MT4102: The registrar found an invalid type `*` in signature for method `*`.</span></span> <span data-ttu-id="c22ab-830">請改用 `*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-830">Use `*` instead.</span></span>

<span data-ttu-id="c22ab-831">這目前僅發生一種類型：System.DateTime。</span><span class="sxs-lookup"><span data-stu-id="c22ab-831">This currently only happens with one type: System.DateTime.</span></span> <span data-ttu-id="c22ab-832">請改用 Objective C 對等項目 (NSDate)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-832">Use the Objective-C equivalent (NSDate) instead.</span></span>

<a name="MT4103" />

### <a name="mt4103-the-registrar-found-an-invalid-type--in-signature-for-method--the-type-implements-inativeobject-but-does-not-have-a-constructor-that-takes-two-intptr-bool-arguments"></a><span data-ttu-id="c22ab-833">MT4103:在註冊機構找到無效的型別`*`方法的簽章中`*`:型別會實作 INativeObject，但並沒有會採用兩個建構函式 (IntPtr，bool) 引數</span><span class="sxs-lookup"><span data-stu-id="c22ab-833">MT4103: The registrar found an invalid type `*` in signature for method `*`: The type implements INativeObject, but does not have a constructor that takes two (IntPtr, bool) arguments</span></span>

<span data-ttu-id="c22ab-834">發生這種情況時註冊機構會遇到中所述的特性的簽章的類型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-834">This occurs when the registrar encounter a type in a signature with the mentioned characteristics.</span></span> <span data-ttu-id="c22ab-835">在註冊機構可能需要建立新的執行個體的型別，而且在此情況下需要 (IntPtr，bool) 的建構函式簽章-的第一個引數 (IntPtr) 指定的受管理的控制代碼，如果呼叫端傳遞原生的擁有權，第二個（如果此值為 false 將會在物件上呼叫 '保留'） 處理。</span><span class="sxs-lookup"><span data-stu-id="c22ab-835">The registrar might need to create new instances of the type, and in this case it requires a constructor with the (IntPtr, bool) signature - the first argument (IntPtr) specifies the managed handle, while the second if the caller hands over ownership of the native handle (if this value is false 'retain' will be called on the object).</span></span>

<a name="MT4104" />

### <a name="mt4104-the-registrar-cannot-marshal-the-return-value-for-type--in-signature-for-method-"></a><span data-ttu-id="c22ab-836">MT4104:在註冊機構無法封送處理類型的傳回值`*`方法的簽章中`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-836">MT4104: The registrar cannot marshal the return value for type `*` in signature for method `*`.</span></span>

<span data-ttu-id="c22ab-837">在執行階段不知道如何封送處理從 OBJECTIVE-C 的匯出 API 中找不到型別</span><span class="sxs-lookup"><span data-stu-id="c22ab-837">A type was found in exported API that the runtime doesn't know how to marshal to/from Objective-C.</span></span>

<span data-ttu-id="c22ab-838">如果您認為 Xamarin.iOS 應該支援的類型有問題，請提出的增強功能要求[ http://bugzilla.xamarin.com ](http://bugzilla.xamarin.com)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-838">If you believe Xamarin.iOS should support the type in question, please file an enhancement request at [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com).</span></span>

<a name="MT4105" />

### <a name="mt4105-the-registrar-cannot-marshal-the-parameter-of-type--in-signature-for-method-"></a><span data-ttu-id="c22ab-839">MT4105:在註冊機構無法封送處理的型別參數`*`方法的簽章中`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-839">MT4105: The registrar cannot marshal the parameter of type `*` in signature for method `*`.</span></span>

<span data-ttu-id="c22ab-840">如果您認為 Xamarin.iOS 應該支援的類型有問題，請提出的增強功能要求[ http://bugzilla.xamarin.com ](http://bugzilla.xamarin.com)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-840">If you believe Xamarin.iOS should support the type in question, please file an enhancement request at [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com).</span></span>

<a name="MT4106" />

### <a name="mt4106-the-registrar-cannot-marshal-the-return-value-for-structure--in-signature-for-method-"></a><span data-ttu-id="c22ab-841">MT4106:在註冊機構無法封送處理結構的傳回值`*`方法的簽章中`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-841">MT4106: The registrar cannot marshal the return value for structure `*` in signature for method `*`.</span></span>

<span data-ttu-id="c22ab-842">在執行階段不知道如何封送處理從 OBJECTIVE-C 的匯出 API 中找不到型別</span><span class="sxs-lookup"><span data-stu-id="c22ab-842">A type was found in exported API that the runtime doesn't know how to marshal to/from Objective-C.</span></span>

<span data-ttu-id="c22ab-843">如果您認為 Xamarin.iOS 應該支援的類型有問題，請提出的增強功能要求[ http://bugzilla.xamarin.com ](http://bugzilla.xamarin.com)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-843">If you believe Xamarin.iOS should support the type in question, please file an enhancement request at [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com).</span></span>

<a name="MT4107" />

### <a name="mt4107-the-registrar-cannot-marshal-the-parameter-of-type--in-signature-for-method-"></a><span data-ttu-id="c22ab-844">MT4107:在註冊機構無法封送處理的型別參數`*`方法的簽章中`+`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-844">MT4107: The registrar cannot marshal the parameter of type `*` in signature for method `+`.</span></span>

<span data-ttu-id="c22ab-845">在執行階段不知道如何封送處理從 OBJECTIVE-C 的匯出 API 中找不到型別</span><span class="sxs-lookup"><span data-stu-id="c22ab-845">A type was found in exported API that the runtime doesn't know how to marshal to/from Objective-C.</span></span>

<span data-ttu-id="c22ab-846">如果您認為 Xamarin.iOS 應該支援的類型有問題，請提出的增強功能要求[ http://bugzilla.xamarin.com ](http://bugzilla.xamarin.com)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-846">If you believe Xamarin.iOS should support the type in question, please file an enhancement request at [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com).</span></span>

<a name="MT4108" />

### <a name="mt4108-the-registrar-cannot-get-the-objectivec-type-for-managed-type-"></a><span data-ttu-id="c22ab-847">MT4108:在註冊機構無法取得 managed 類型的 ObjectiveC 類型`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-847">MT4108: The registrar cannot get the ObjectiveC type for managed type `*`.</span></span>

<span data-ttu-id="c22ab-848">在執行階段不知道如何封送處理從 OBJECTIVE-C 的匯出 API 中找不到型別</span><span class="sxs-lookup"><span data-stu-id="c22ab-848">A type was found in exported API that the runtime doesn't know how to marshal to/from Objective-C.</span></span>

<span data-ttu-id="c22ab-849">如果您認為 Xamarin.iOS 應該支援的類型有問題，請提出的增強功能要求[ http://bugzilla.xamarin.com ](http://bugzilla.xamarin.com)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-849">If you believe Xamarin.iOS should support the type in question, please file an enhancement request at [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com).</span></span>

<a name="MT4109" />

### <a name="mt4109-failed-to-compile-the-generated-registrar-code-please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-850">MT4109:無法編譯產生的註冊機構的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c22ab-850">MT4109: Failed to compile the generated registrar code.</span></span> <span data-ttu-id="c22ab-851">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-851">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<span data-ttu-id="c22ab-852">無法編譯產生的程式碼的註冊機構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-852">Failed to compile the generated code for the registrar.</span></span> <span data-ttu-id="c22ab-853">組建記錄檔會包含原生編譯器，解釋為何不進行編譯的程式碼的輸出。</span><span class="sxs-lookup"><span data-stu-id="c22ab-853">The build log will contain the output from the native compiler, explaining why the code isn't compiling.</span></span>

<span data-ttu-id="c22ab-854">這一律是 Xamarin.iOS; 中的 bug請提出錯誤報告在 [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com) 與您的專案或測試案例。</span><span class="sxs-lookup"><span data-stu-id="c22ab-854">This is always a bug in Xamarin.iOS; please file a bug report at [http://bugzilla.xamarin.com](http://bugzilla.xamarin.com) with your project or a test case.</span></span>

<a name="MT4110" />

### <a name="mt4110-the-registrar-cannot-marshal-the-out-parameter-of-type--in-signature-for-method-"></a><span data-ttu-id="c22ab-855">MT4110:在註冊機構無法封送處理類型的 out 參數`*`方法的簽章中`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-855">MT4110: The registrar cannot marshal the out parameter of type `*` in signature for method `*`.</span></span>

<a name="MT4111" />

### <a name="mt4111-the-registrar-cannot-build-a-signature-for-type--in-method-"></a><span data-ttu-id="c22ab-856">MT4111:在註冊機構的版本無法建立類型的簽章`*`方法中`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-856">MT4111: The registrar cannot build a signature for type `*` in method `*`.</span></span>

<a name="MT4112" />

### <a name="mt4112-the-registrar-found-an-invalid-type--registering-generic-types-with-objective-c-is-not-supported-and-may-lead-to-random-behavior-andor-crashes-for-backwards-compatibility-with-older-versions-of-xamarinios-it-is-possible-to-ignore-this-error-by-passing---unsupported--enable-generics-in-registrar-as-an-additional-mtouch-argument-in-the-projects-ios-build-options-page-see-developerxamarincomguidesiosadvancedtopicsregistrarhttpsdeveloperxamarincomguidesiosadvancedtopicsregistrar-for-more-information"></a><span data-ttu-id="c22ab-857">MT4112:在註冊機構找到無效的型別`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-857">MT4112: The registrar found an invalid type `*`.</span></span> <span data-ttu-id="c22ab-858">向 OBJECTIVE-C 中的泛型型別不支援，且可能會導致隨機的行為和/或損毀 (用於回溯相容性與舊版 Xamarin.iOS 就可以忽略此錯誤，藉由傳遞`--unsupported--enable-generics-in-registrar`為其他 mtouch專案的 iOS 組建選項 頁面中的引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-858">Registering generic types with Objective-C is not supported, and may lead to random behavior and/or crashes (for backwards compatibility with older versions of Xamarin.iOS it is possible to ignore this error by passing `--unsupported--enable-generics-in-registrar` as an additional mtouch argument in the project's iOS Build options page.</span></span> <span data-ttu-id="c22ab-859">請參閱[developer.xamarin.com/guides/ios/advanced_topics/registrar](https://developer.xamarin.com/guides/ios/advanced_topics/registrar)如需詳細資訊)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-859">See [developer.xamarin.com/guides/ios/advanced_topics/registrar](https://developer.xamarin.com/guides/ios/advanced_topics/registrar) for more information).</span></span>

<a name="MT4113" />

### <a name="mt4113-the-registrar-found-a-generic-method--exporting-generic-methods-is-not-supported-and-will-lead-to-random-behavior-andor-crashes"></a><span data-ttu-id="c22ab-860">MT4113:在註冊機構找到泛型的方法: '\*。\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-860">MT4113: The registrar found a generic method: '\*.\*'.</span></span> <span data-ttu-id="c22ab-861">匯出泛型方法不支援，並會導致隨機的行為和/或損毀。</span><span class="sxs-lookup"><span data-stu-id="c22ab-861">Exporting generic methods is not supported, and will lead to random behavior and/or crashes.</span></span>

<a name="MT4114" />

### <a name="mt4114-unexpected-error-in-the-registrar-for-the-method----please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-862">MT4114:未預期的錯誤中的註冊機構方法 '\*。\*'-請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-862">MT4114: Unexpected error in the registrar for the method '\*.\*' - Please file a bug report at http://bugzilla.xamarin.com</span></span>

<a name="MT4116" />

### <a name="mt4116-could-not-register-the-assembly--"></a><span data-ttu-id="c22ab-863">MT4116:無法註冊組件 ' \*': \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-863">MT4116: Could not register the assembly '\*': \*</span></span>

<a name="MT4117" />

### <a name="mt4117-the-registrar-found-a-signature-mismatch-in-the-method----the-selector-indicates-the-method-takes--parameters-while-the-managed-method-has--parameters"></a><span data-ttu-id="c22ab-864">MT4117:註冊機構位於方法簽章不符合 '*。*'-選取器指出此方法會採用 \* 參數，而受管理的方法有 \* 參數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-864">MT4117: The registrar found a signature mismatch in the method '*.*' - the selector indicates the method takes \* parameters, while the managed method has \* parameters.</span></span>

<a name="MT4118" />

### <a name="mt4118-cannot-register-two-managed-types--and--with-the-same-native-name-"></a><span data-ttu-id="c22ab-865">MT4118:無法註冊兩個的 managed 的類型 ('\*'和'\*') 具有相同的原生名稱 ('\* ')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-865">MT4118: Cannot register two managed types ('\*' and '\*') with the same native name ('\*').</span></span>

<a name="MT4119" />

### <a name="mt4119-could-not-register-the-selector--of-the-member--because-the-selector-is-already-registered-on-a-different-member"></a><span data-ttu-id="c22ab-866">MT4119:無法註冊選取器 '\*'的成員'\*。 \*' 因為選取器已經登錄在不同的成員。</span><span class="sxs-lookup"><span data-stu-id="c22ab-866">MT4119: Could not register the selector '\*' of the member '\*.\*' because the selector is already registered on a different member.</span></span>

<a name="MT4120" />

### <a name="mt4120-the-registrar-found-an-unknown-field-type--in-field--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-867">MT4120:在註冊機構找了未知的欄位類型 '\*'中欄位'\*。 \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-867">MT4120: The registrar found an unknown field type '\*' in field '\*.\*'.</span></span> <span data-ttu-id="c22ab-868">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-868">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<span data-ttu-id="c22ab-869">此錯誤表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-869">This error indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-870">請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-870">Please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4121" />

### <a name="mt4121-cannot-use-gccg-to-compile-the-generated-code-from-the-static-registrar-when-using-the-accounts-framework-the-header-files-provided-by-apple-used-during-the-compilation-require-clang-either-use-clang---compilerclang-or-the-dynamic-registrar---registrardynamic"></a><span data-ttu-id="c22ab-871">MT4121:無法使用 GCC / G + + 編譯的靜態的註冊機構從產生的程式碼時使用帳戶架構 （在編譯期間使用的 Apple 提供的標頭檔需要 Clang）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-871">MT4121: Cannot use GCC/G++ to compile the generated code from the static registrar when using the Accounts framework (the header files provided by Apple used during the compilation require Clang).</span></span> <span data-ttu-id="c22ab-872">請使用 Clang (-編譯器： clang) 或動態的註冊機構 (-註冊機構： 動態)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-872">Either use Clang (--compiler:clang) or the dynamic registrar (--registrar:dynamic).</span></span>

<a name="MT4122" />

### <a name="mt4122-cannot-use-the-clang-compiler-provided-in-the--sdk-to-compile-the-generated-code-from-the-static-registrar-when-non-ascii-type-names--are-present-in-the-application-either-use-gccg---compilergccg-the-dynamic-registrar---registrardynamic-or-a-newer-sdk"></a><span data-ttu-id="c22ab-873">MT4122:無法使用提供的 Clang 編譯器 *。*</span><span class="sxs-lookup"><span data-stu-id="c22ab-873">MT4122: Cannot use the Clang compiler provided in the *.*</span></span> <span data-ttu-id="c22ab-874">SDK 編譯產生的程式碼，從靜態的註冊機構時非 ASCII 類型名稱 ('\* ') 會出現在應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-874">SDK to compile the generated code from the static registrar when non-ASCII type names ('\*') are present in the application.</span></span> <span data-ttu-id="c22ab-875">請使用 GCC / G + + (-gcc 編譯器: | g + +)、 動態註冊機構 (-註冊機構： 動態) 或更新版本的 SDK。</span><span class="sxs-lookup"><span data-stu-id="c22ab-875">Either use GCC/G++ (--compiler:gcc|g++), the dynamic registrar (--registrar:dynamic) or a newer SDK.</span></span>

<a name="MT4123" />

### <a name="mt4123-the-type-of-the-variadic-parameter-in-the-variadic-function--must-be-systemintptr"></a><span data-ttu-id="c22ab-876">MT4123:Variadic 函式中的 variadic 參數的型別 ' \*' 必須是 System.IntPtr。</span><span class="sxs-lookup"><span data-stu-id="c22ab-876">MT4123: The type of the variadic parameter in the variadic function '\*' must be System.IntPtr.</span></span>

<a name="MT4124" />

### <a name="mt4124-invalid--found-on--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-877">MT4124:無效 \* 上找到 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-877">MT4124: Invalid \* found on '\*'.</span></span> <span data-ttu-id="c22ab-878">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-878">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<span data-ttu-id="c22ab-879">此錯誤表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-879">This error indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-880">請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-880">Please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4125" />

### <a name="mt4125-the-registrar-found-an-invalid-type--in-signature-for-method--the-interface-must-have-a-protocol-attribute-specifying-its-wrapper-type"></a><span data-ttu-id="c22ab-881">MT4125:在註冊機構找到無效的類型 '\*'中方法簽章'\*':介面必須要有通訊協定屬性，指定其包裝函式型別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-881">MT4125: The registrar found an invalid type '\*' in signature for method '\*': The interface must have a Protocol attribute specifying its wrapper type.</span></span>

<a name="MT4126" />

### <a name="mt4126-cannot-register-two-managed-protocols--and--with-the-same-native-name-"></a><span data-ttu-id="c22ab-882">MT4126:無法註冊兩個受管理的通訊協定 ('\*'和'\*') 具有相同的原生名稱 ('\* ')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-882">MT4126: Cannot register two managed protocols ('\*' and '\*') with the same native name ('\*').</span></span>

<a name="MT4127" />

### <a name="mt4127-cannot-register-more-than-one-interface-method-for-the-method--which-is-implementing-"></a><span data-ttu-id="c22ab-883">MT4127:無法註冊方法的多個介面方法 '\*' (這實作 '\*')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-883">MT4127: Cannot register more than one interface method for the method '\*' (which is implementing '\*').</span></span>

<a name="MT4128" />

### <a name="mt4128-the-registrar-found-an-invalid-generic-parameter-type--in-the-method--the-generic-parameter-must-have-an-nsobject-constraint"></a><span data-ttu-id="c22ab-884">MT4128:在註冊機構找到無效的泛型參數類型 '\*'中方法'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-884">MT4128: The registrar found an invalid generic parameter type '\*' in the method '\*'.</span></span> <span data-ttu-id="c22ab-885">泛型參數都必須有 'NSObject' 條件約束。</span><span class="sxs-lookup"><span data-stu-id="c22ab-885">The generic parameter must have an 'NSObject' constraint.</span></span>

<a name="MT4129" />

### <a name="mt4129-the-registrar-found-an-invalid-generic-return-type--in-the-method--the-generic-return-type-must-have-an-nsobject-constraint"></a><span data-ttu-id="c22ab-886">MT4129:在註冊機構找到無效的泛型傳回類型 '\*'中方法'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-886">MT4129: The registrar found an invalid generic return type '\*' in the method '\*'.</span></span> <span data-ttu-id="c22ab-887">泛型傳回類型必須有 'NSObject' 條件約束。</span><span class="sxs-lookup"><span data-stu-id="c22ab-887">The generic return type must have an 'NSObject' constraint.</span></span>

<a name="MT4130" />

### <a name="mt4130-the-registrar-cannot-export-static-methods-in-generic-classes-"></a><span data-ttu-id="c22ab-888">MT4130:在註冊機構無法匯出中的泛用類別的靜態方法 ('\* ')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-888">MT4130: The registrar cannot export static methods in generic classes ('\*').</span></span>

<a name="MT4131" />

### <a name="mt4131-the-registrar-cannot-export-static-properties-in-generic-classes-"></a><span data-ttu-id="c22ab-889">MT4131:在註冊機構無法匯出泛型類別中的靜態屬性 ('\*。\*')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-889">MT4131: The registrar cannot export static properties in generic classes ('\*.\*').</span></span>

<a name="MT4132" />

### <a name="mt4132-the-registrar-found-an-invalid-generic-return-type--in-the-property--the-return-type-must-have-an-nsobject-constraint"></a><span data-ttu-id="c22ab-890">MT4132:在註冊機構找到無效的泛型傳回類型 '\*'中屬性'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-890">MT4132: The registrar found an invalid generic return type '\*' in the property '\*'.</span></span> <span data-ttu-id="c22ab-891">傳回的類型必須有 'NSObject' 條件約束。</span><span class="sxs-lookup"><span data-stu-id="c22ab-891">The return type must have an 'NSObject' constraint.</span></span>

<a name="MT4133" />

### <a name="mt4133-cannot-construct-an-instance-of-the-type--from-objective-c-because-the-type-is-generic-runtime-exception"></a><span data-ttu-id="c22ab-892">MT4133:無法建構類型的執行個體 ' \*' 從 OBJECTIVE-C 因為型別是泛型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-892">MT4133: Cannot construct an instance of the type '\*' from Objective-C because the type is generic.</span></span> <span data-ttu-id="c22ab-893">[執行階段例外狀況]</span><span class="sxs-lookup"><span data-stu-id="c22ab-893">[Runtime exception]</span></span>

<a name="MT4134" />

### <a name="mt4134-your-application-is-using-the--framework-which-isnt-included-in-the-ios-sdk-youre-using-to-build-your-app-this-framework-was-introduced-in-ios--while-youre-building-with-the-ios--sdk-please-select-a-newer-sdk-in-your-apps-ios-build-options"></a><span data-ttu-id="c22ab-894">MT4134:您的應用程式使用 ' \*' framework，不會包含於 iOS SDK 您用來建置您的應用程式 (iOS 中引進了此架構 \*，而您要建置使用 iOS \* SDK。)請在您的應用程式 iOS 組建 選項，選取較新的 SDK。</span><span class="sxs-lookup"><span data-stu-id="c22ab-894">MT4134: Your application is using the '\*' framework, which isn't included in the iOS SDK you're using to build your app (this framework was introduced in iOS \*, while you're building with the iOS \* SDK.) Please select a newer SDK in your app's iOS Build options.</span></span>

<a name="MT4135" />

### <a name="mt4135-the-member--has-an-export-attribute-that-doesnt-specify-a-selector-a-selector-is-required"></a><span data-ttu-id="c22ab-895">MT4135:成員 '\*。\*' 有未指定選取器的匯出屬性。</span><span class="sxs-lookup"><span data-stu-id="c22ab-895">MT4135: The member '\*.\*' has an Export attribute that doesn't specify a selector.</span></span> <span data-ttu-id="c22ab-896">需要選取器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-896">A selector is required.</span></span>

<a name="MT4136" />

### <a name="mt4136-the-registrar-cannot-marshal-the-parameter-type--of-the-parameter--in-the-method-"></a><span data-ttu-id="c22ab-897">MT4136:在註冊機構無法封送處理參數類型 '\*'的參數'\*'中方法'\*。 \*'</span><span class="sxs-lookup"><span data-stu-id="c22ab-897">MT4136: The registrar cannot marshal the parameter type '\*' of the parameter '\*' in the method '\*.\*'</span></span>

<!-- MT4137 is unused -->

<a name="MT4138" />

### <a name="mt4138-the-registrar-cannot-marshal-the-property-type--of-the-property-"></a><span data-ttu-id="c22ab-898">MT4138:在註冊機構無法封送處理屬性類型 '\*'的屬性'\*。 \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-898">MT4138: The registrar cannot marshal the property type '\*' of the property '\*.\*'.</span></span>

<a name="MT4139" />

### <a name="mt4139-the-registrar-cannot-marshal-the-property-type--of-the-property--properties-with-the-connect-attribute-must-have-a-property-type-of-nsobject-or-a-subclass-of-nsobject"></a><span data-ttu-id="c22ab-899">MT4139:在註冊機構無法封送處理屬性類型 '\*'的屬性'\*。 \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-899">MT4139: The registrar cannot marshal the property type '\*' of the property '\*.\*'.</span></span> <span data-ttu-id="c22ab-900">NSObject 的屬性類型 （或 NSObject 的子類別），必須使用 [連線] 屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="c22ab-900">Properties with the [Connect] attribute must have a property type of NSObject (or a subclass of NSObject).</span></span>

<a name="MT4140" />

### <a name="mt4140-the-registrar-found-a-signature-mismatch-in-the-method----the-selector-indicates-the-variadic-method-takes--parameters-while-the-managed-method-has--parameters"></a><span data-ttu-id="c22ab-901">MT4140:註冊機構位於方法簽章不符合 '*。*'-選取器可讓您表示 variadic 方法會採用 \* 參數，而受管理的方法有 \* 參數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-901">MT4140: The registrar found a signature mismatch in the method '*.*' - the selector indicates the variadic method takes \* parameters, while the managed method has \* parameters.</span></span>

<a name="MT4141" />

### <a name="mt4141-cannot-register-the-selector--on-the-member--because-xamarinios-implicitly-registers-this-selector"></a><span data-ttu-id="c22ab-902">MT4141:無法註冊選取器 '\*'上成員'\*' 因為 Xamarin.iOS 隱含註冊這個選取器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-902">MT4141: Cannot register the selector '\*' on the member '\*' because Xamarin.iOS implicitly registers this selector.</span></span>

<span data-ttu-id="c22ab-903">這發生在子類別化 framework 型別，並嘗試實作 '保留'，'版本' 或 'dealloc' 方法：</span><span class="sxs-lookup"><span data-stu-id="c22ab-903">This occurs when subclassing a framework type, and trying to implement a 'retain', 'release' or 'dealloc' method:</span></span>

```csharp
class MyNSObject : NSObject
{
    [Export ("retain")]
    new void Retain () {}

    [Export ("release")]
    new void Release () {}

    [Export ("dealloc")]
    new void Dealloc () {}
}
```

<span data-ttu-id="c22ab-904">它是架構的不過可覆寫這些方法，如果類別不是架構的第一個子類別類型：</span><span class="sxs-lookup"><span data-stu-id="c22ab-904">It is however possible to override these methods if the class isn't the first subclass of the framework type:</span></span>

```csharp
class MyNSObject : NSObject
{
}

class MyCustomNSObject : MyNSObject
{
    [Export ("retain")]
    new void Retain () {}

    [Export ("release")]
    new void Release () {}

    [Export ("dealloc")]
    new void Dealloc () {}
}
```

<span data-ttu-id="c22ab-905">在此情況下將會覆寫 Xamarin.iOS `retain`，`release`和`dealloc`上`MyNSObject`類別，而且沒有任何衝突。</span><span class="sxs-lookup"><span data-stu-id="c22ab-905">In this case Xamarin.iOS will override `retain`, `release` and `dealloc` on the `MyNSObject` class, and there is no conflict.</span></span>

<a name="MT4142" />

### <a name="mt4142-failed-to-register-the-type-"></a><span data-ttu-id="c22ab-906">MT4142:無法註冊類型 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-906">MT4142: Failed to register the type '\*'.</span></span>

<a name="MT4143" />

### <a name="mt4143-the-objectivec-class--could-not-be-registered-it-does-not-seem-to-derive-from-any-known-objectivec-class-including-nsobject"></a><span data-ttu-id="c22ab-907">MT4143:ObjectiveC 類別 ' \*' 無法註冊，它似乎並沒有衍生自任何已知的 ObjectiveC 類別 （包括 NSObject）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-907">MT4143: The ObjectiveC class '\*' could not be registered, it does not seem to derive from any known ObjectiveC class (including NSObject).</span></span>

<a name="MT4144" />

### <a name="mt4144-cannot-register-the-method--since-it-does-not-have-an-associated-trampoline-please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-908">MT4144:無法將方法註冊 ' \*' 因為沒有相關聯的 trampoline。</span><span class="sxs-lookup"><span data-stu-id="c22ab-908">MT4144: Cannot register the method '\*' since it does not have an associated trampoline.</span></span> <span data-ttu-id="c22ab-909">請提出錯誤報告在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-909">Please file a bug report at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-910">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-910">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-911">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-911">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4145" />

### <a name="mt4145-invalid-enum--enums-with-the-native-attribute-must-have-a-underlying-enum-type-of-either-long-or-ulong"></a><span data-ttu-id="c22ab-912">MT4145:無效的列舉 ' \*': 具有 [原生] 屬性的列舉必須有基礎的列舉型別 'long' 或 'ulong'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-912">MT4145: Invalid enum '\*': enums with the [Native] attribute must have a underlying enum type of either 'long' or 'ulong'.</span></span>

<a name="MT4146" />

### <a name="mt4146-the-name-parameter-of-the-registrar-attribute-on-the-class---contains-an-invalid-character--"></a><span data-ttu-id="c22ab-913">MT4146:註冊機構上的屬性類別的 Name 參數\*'('\*') 包含無效的字元:'\*' (\*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-913">MT4146: The Name parameter of the Registrar attribute on the class '\*' ('\*') contains an invalid character: '\*' (\*).</span></span>

<span data-ttu-id="c22ab-914">Objectice C 類別的名稱不能包含空白字元，這表示`Register`相對應的 managed 類別上的屬性不能有`Name`參數不能是包含空白字元。</span><span class="sxs-lookup"><span data-stu-id="c22ab-914">The name of an Objectice-C class can't contain whitespace, which means that the `Register` attribute on the corresponding managed class can't have a `Name` parameter can't contain whitespace either.</span></span>

<span data-ttu-id="c22ab-915">請確認`Register`上錯誤訊息中所述之 managed 類別的屬性不包含任何空白字元。</span><span class="sxs-lookup"><span data-stu-id="c22ab-915">Please verify that the `Register` attribute on the managed class mentioned in the error message does not contain any whitespace.</span></span>

<a name="MT4147" />

### <a name="mt4147-detected-a-protocol-inheriting-from-the-jsexport-protocol-while-using-the-dynamic-registrar-it-is-not-possible-to-export-protocols-to-javascriptcore-dynamically-the-static-registrar-must-be-used-add---registrarstatic-to-the-additional-mtouch-arguments-in-the-projects-ios-build-options-to-select-the-static-registrar"></a><span data-ttu-id="c22ab-916">MT4147:偵測到繼承 JSExport 通訊協定，同時使用動態的註冊機構的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-916">MT4147: Detected a protocol inheriting from the JSExport protocol while using the dynamic registrar.</span></span> <span data-ttu-id="c22ab-917">不可能將通訊協定動態; 匯出至 JavaScriptCore必須使用靜態的註冊機構 (新增 '-其他 mtouch 引數，在專案的 iOS 建置選項以選取靜態註冊機構的註冊機構： 靜態)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-917">It is not possible to export protocols to JavaScriptCore dynamically; the static registrar must be used (add '--registrar:static to the additional mtouch arguments in the project's iOS Build options to select the static registrar).</span></span>

<a name="MT4148" />

### <a name="mt4148-the-registrar-found-a-generic-protocol--exporting-generic-protocols-is-not-supported"></a><span data-ttu-id="c22ab-918">MT4148:在註冊機構找泛用的通訊協定: ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-918">MT4148: The registrar found a generic protocol: '\*'.</span></span> <span data-ttu-id="c22ab-919">不支援匯出一般通訊協定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-919">Exporting generic protocols is not supported.</span></span>

<a name="MT4149" />

### <a name="mt4149-cannot-register-the-method--because-the-type-of-the-first-parameter--does-not-match-the-category-type-"></a><span data-ttu-id="c22ab-920">MT4149:無法註冊方法 '\*。\*' 因為第一個參數的型別 ('\*') 不符合類別類型 ('\*')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-920">MT4149: Cannot register the method '\*.\*' because the type of the first parameter ('\*') does not match the category type ('\*').</span></span>

<a name="MT4150" />

### <a name="mt4150-cannot-register-the-type--because-the-type-property--in-its-category-attribute-does-not-inherit-from-nsobject"></a><span data-ttu-id="c22ab-921">MT4150:無法註冊類型 '\*' 因為型別屬性 ('\*') 在其類別屬性不是繼承自 NSObject。</span><span class="sxs-lookup"><span data-stu-id="c22ab-921">MT4150: Cannot register the type '\*' because the Type property ('\*') in its Category attribute does not inherit from NSObject.</span></span>

<a name="MT4151" />

### <a name="mt4151-cannot-register-the-type--because-the-type-property-in-its-category-attribute-isnt-set"></a><span data-ttu-id="c22ab-922">MT4151:無法註冊類型 ' \*' 因為其類別屬性中的 [類型] 屬性未設定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-922">MT4151: Cannot register the type '\*' because the Type property in its Category attribute isn't set.</span></span>

<a name="MT4152" />

### <a name="mt4152-cannot-register-the-type--as-a-category-because-it-implements-inativeobject-or-subclasses-nsobject"></a><span data-ttu-id="c22ab-923">MT4152:無法註冊類型 ' \*' 做為類別目錄因為它會實作 INativeObject 或 NSObject 的子類別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-923">MT4152: Cannot register the type '\*' as a category because it implements INativeObject or subclasses NSObject.</span></span>

<a name="MT4153" />

### <a name="mt4153-cannot-register-the-type--as-a-category-because-its-generic"></a><span data-ttu-id="c22ab-924">MT4153:無法註冊類型 '\*' 做為類別目錄因為它是泛型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-924">MT4153: Cannot register the type '\*' as a category because it's generic.</span></span>

<a name="MT4154" />

### <a name="mt4154-cannot-register-the-method--as-a-category-method-because-its-generic"></a><span data-ttu-id="c22ab-925">MT4154:無法將方法註冊 '\*' 做為類別方法因為它是泛型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-925">MT4154: Cannot register the method '\*' as a category method because it's generic.</span></span>

<a name="MT4155" />

### <a name="mt4155-cannot-register-the-method--with-the-selector--as-a-category-method-on--because-the-objective-c-already-has-an-implementation-for-this-selector"></a><span data-ttu-id="c22ab-926">MT4155:無法註冊方法 '\*'與選取器'\*' 上的分類方法為 ' \*' 因為 Objective C 已經有這個選取器的實作。</span><span class="sxs-lookup"><span data-stu-id="c22ab-926">MT4155: Cannot register the method '\*' with the selector '\*' as a category method on '\*' because the Objective-C already has an implementation for this selector.</span></span>

<a name="MT4156" />

### <a name="mt4156-cannot-register-two-categories--and--with-the-same-native-name-"></a><span data-ttu-id="c22ab-927">MT4156:無法註冊兩個類別 ('\*'和'\*') 具有相同的原生名稱 ('\* ')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-927">MT4156: Cannot register two categories ('\*' and '\*') with the same native name ('\*').</span></span>

<a name="MT4157" />

### <a name="mt4157-cannot-register-the-category-method--because-at-least-one-parameter-is-required-and-its-type-must-match-the-category-type-"></a><span data-ttu-id="c22ab-928">MT4157:無法註冊類別方法 '\*' 因為至少一個參數是必要的 (且其類型必須符合類別類型 '\*')</span><span class="sxs-lookup"><span data-stu-id="c22ab-928">MT4157: Cannot register the category method '\*' because at least one parameter is required (and its type must match the category type '\*')</span></span>

<a name="MT4158" />

### <a name="mt4158-cannot-register-the-constructor--in-the-category--because-constructors-in-categories-are-not-supported"></a><span data-ttu-id="c22ab-929">MT4158:無法註冊建構函式 \* 類別 \* 因為不支援類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-929">MT4158: Cannot register the constructor \* in the category \* because constructors in categories are not supported.</span></span>

<a name="MT4159" />

### <a name="mt4159-cannot-register-the-method--as-a-category-method-because-category-methods-must-be-static"></a><span data-ttu-id="c22ab-930">MT4159:無法將方法註冊 ' \*' 做為類別方法因為類別方法必須是靜態。</span><span class="sxs-lookup"><span data-stu-id="c22ab-930">MT4159: Cannot register the method '\*' as a category method because category methods must be static.</span></span>

<a name="MT4160" />

### <a name="mt4160-invalid-character---found-in-selector--for-"></a><span data-ttu-id="c22ab-931">MT4160:無效的字元 '\*' (\*) 中選取器找到 '\*'for'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-931">MT4160: Invalid character '\*' (\*) found in selector '\*' for '\*'.</span></span>

<a name="MT4161" />

### <a name="mt4161-the-registrar-found-an-unsupported-structure--all-fields-in-a-structure-must-also-be-structures-field--with-type-2-is-not-a-structure"></a><span data-ttu-id="c22ab-932">MT4161:在註冊機構找到不支援的結構 '\*':在結構中的所有欄位也必須都是結構 (欄位 '\*'與 type'{2}' 不是結構)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-932">MT4161: The registrar found an unsupported structure '\*': All fields in a structure must also be structures (field '\*' with type '{2}' is not a structure).</span></span>

<span data-ttu-id="c22ab-933">在註冊機構會找到不支援欄位的結構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-933">The registrar found a structure with unsupported fields.</span></span>

<span data-ttu-id="c22ab-934">結構，其會公開以 OBJECTIVE-C 中的所有欄位也必須都是結構 （不是類別）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-934">All fields in a structure that is exposed to Objective-C must also be structures (not classes).</span></span>

<a name="MT4162" />

### <a name="mt4162-the-type--used-as--2-is-not-available-in---it-was-introduced-in---please-build-with-a-newer--sdk-usually-done-by-using-the-most-recent-version-of-xcode"></a><span data-ttu-id="c22ab-935">MT4162:類型 '\*' (做為 \* {2}) 不適用於 \* \* (首見於 \* \*)\*請使用較新建置 \* SDK （通常是使用最新版的 Xcode 來完成。</span><span class="sxs-lookup"><span data-stu-id="c22ab-935">MT4162: The type '\*' (used as \* {2}) is not available in \* \* (it was introduced in \* \*)\* Please build with a newer \* SDK (usually done by using the most recent version of Xcode.</span></span>

<span data-ttu-id="c22ab-936">在註冊機構找到的類型不包含在目前的 SDK。</span><span class="sxs-lookup"><span data-stu-id="c22ab-936">The registrar found a type which is not included in the current SDK.</span></span>

<span data-ttu-id="c22ab-937">請先升級 Xcode。</span><span class="sxs-lookup"><span data-stu-id="c22ab-937">Please upgrade Xcode.</span></span>

<a name="MT4163" />

### <a name="mt4163-internal-error-in-the-registrar--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-938">MT4163:註冊機構 （\*） 發生內部錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-938">MT4163: Internal error in the registrar (\*).</span></span> <span data-ttu-id="c22ab-939">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-939">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<span data-ttu-id="c22ab-940">此錯誤表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-940">This error indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-941">請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-941">Please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4164" />

### <a name="mt4164-cannot-export-the-property--because-its-selector--is-an-objective-c-keyword-please-use-a-different-name"></a><span data-ttu-id="c22ab-942">MT4164:無法匯出的屬性 '\*' 因為其選取器 '\*' Objective C 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c22ab-942">MT4164: Cannot export the property '\*' because its selector '\*' is an Objective-C keyword.</span></span> <span data-ttu-id="c22ab-943">請使用不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-943">Please use a different name.</span></span>

<span data-ttu-id="c22ab-944">選取器所討論的屬性不是有效的 Objective C 識別項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-944">The selector for the property in question is not a valid Objective-C identifer.</span></span>

<span data-ttu-id="c22ab-945">請為選取器，使用有效的 Objective C 識別項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-945">Please use a valid Objective-C identifier as selectors.</span></span>

<a name="MT4165" />

### <a name="mt4165-the-registrar-couldnt-find-the-type-systemvoid-in-any-of-the-referenced-assemblies"></a><span data-ttu-id="c22ab-946">MT4165:在註冊機構任何參考的組件中找不到類型 'System.Void'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-946">MT4165: The registrar couldn't find the type 'System.Void' in any of the referenced assemblies.</span></span>

<span data-ttu-id="c22ab-947">此錯誤最可能表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-947">This error most likely indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-948">請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-948">Please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4166" />

### <a name="mt4166-cannot-register-the-method--because-the-signature-contains-a-type--that-isnt-a-reference-type"></a><span data-ttu-id="c22ab-949">MT4166:無法註冊方法 '\*' 因為簽章包含的類型 (\*) 不是參考型別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-949">MT4166: Cannot register the method '\*' because the signature contains a type (\*) that isn't a reference type.</span></span>

<span data-ttu-id="c22ab-950">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-950">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4167" />

### <a name="mt4167-cannot-register-the-method--because-the-signature-contains-a-generic-type--with-a-generic-argument-type-that-isnt-an-nsobject-subclass-"></a><span data-ttu-id="c22ab-951">MT4167:無法註冊方法 '\*' 因為簽章包含泛型型別 (\*) 不是 NSObject 子類別 （\*） 的泛型引數類型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-951">MT4167: Cannot register the method '\*' because the signature contains a generic type (\*) with a generic argument type that isn't an NSObject subclass (\*).</span></span>

<span data-ttu-id="c22ab-952">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-952">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT4168" />

### <a name="mt4168-cannot-register-the-type-managedname-because-its-objective-c-name-exportedname-is-an-objective-c-keyword-please-use-a-different-name"></a><span data-ttu-id="c22ab-953">MT4168:無法註冊類型 '{受控\_名稱}' 因為其 Objective C 的名稱' {匯出\_名稱}' 的 Objective C 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c22ab-953">MT4168: Cannot register the type '{managed\_name}' because its Objective-C name '{exported\_name}' is an Objective-C keyword.</span></span> <span data-ttu-id="c22ab-954">請使用不同的名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-954">Please use a different name.</span></span>

<span data-ttu-id="c22ab-955">討論中類型的 Objective C 名稱不是有效的 Objective C 識別項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-955">The Objective-C name for the type in question is not a valid Objective-C identifier.</span></span>

<span data-ttu-id="c22ab-956">請使用有效的 Objective C 識別項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-956">Please use a valid Objective-C identifier.</span></span>

<a name="MT4169" />

### <a name="mt4169-failed-to-generate-a-pinvoke-wrapper-for-method-message"></a><span data-ttu-id="c22ab-957">MT4169:無法產生的 P/Invoke 包裝函式 {方法}: {message}</span><span class="sxs-lookup"><span data-stu-id="c22ab-957">MT4169: Failed to generate a P/Invoke wrapper for {method}: {message}</span></span>

<span data-ttu-id="c22ab-958">Xamarin.iOS 無法產生 P/Invoke 包裝函式的函式所述。</span><span class="sxs-lookup"><span data-stu-id="c22ab-958">Xamarin.iOS failed to generate a P/Invoke wrapper function for the mentioned.</span></span>
<span data-ttu-id="c22ab-959">請檢查根本原因的報告的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="c22ab-959">Please check the reported error message for the underlying cause.</span></span>

<a name="MT4170" />

### <a name="mt4170-the-registrar-cant-convert-from-managed-type-to-native-type-for-the-return-value-in-the-method-method"></a><span data-ttu-id="c22ab-960">MT4170:在 {方法} 方法的傳回值的註冊機構無法從 '{managed type}' 轉換為 '{原生類型}'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-960">MT4170: The registrar can't convert from '{managed type}' to '{native type}' for the return value in the method {method}.</span></span>

<span data-ttu-id="c22ab-961">請參閱錯誤的描述<a href="#MT4172">MT4172</a>。</span><span class="sxs-lookup"><span data-stu-id="c22ab-961">See the description of error <a href="#MT4172">MT4172</a>.</span></span>

<a name="MT4171" />

### <a name="mt4171-the-bindas-attribute-on-the-member-member-is-invalid-the-bindas-type-type-is-different-from-the-property-type-type"></a><span data-ttu-id="c22ab-962">MT4171:在成員 {成員} BindAs 屬性無效： BindAs 型別 {type} 是 {type} 屬性類型不同。</span><span class="sxs-lookup"><span data-stu-id="c22ab-962">MT4171: The BindAs attribute on the member {member} is invalid: the BindAs type {type} is different from the property type {type}.</span></span>

<span data-ttu-id="c22ab-963">請確定 BindAs 屬性中的型別符合它附加到成員的型別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-963">Please make sure the type in the BindAs attribute matches the type of the member it's attached to.</span></span>

<a name="MT4172" />

### <a name="mt4172-the-registrar-cant-convert-from-native-type-to-managed-type-for-the-parameter-parameter-name-in-the-method-method"></a><span data-ttu-id="c22ab-964">MT4172:方法 {方法} 中的參數 '{parameter name}' 的註冊機構無法從 '{原生 type}' 轉換為 '{managed type}'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-964">MT4172: The registrar can't convert from '{native type}' to '{managed type}' for the parameter '{parameter name}' in the method {method}.</span></span>

<span data-ttu-id="c22ab-965">在註冊機構不支援上述類型之間轉換。</span><span class="sxs-lookup"><span data-stu-id="c22ab-965">The registrar does not support converting between the mentioned types.</span></span>

<span data-ttu-id="c22ab-966">如果有問題的 API 由 Xamarin.iOS; 提供，這會是 Xamarin.iOS 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com][1]。</span><span class="sxs-lookup"><span data-stu-id="c22ab-966">This is a bug in Xamarin.iOS if the API in question is provided by Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com][1].</span></span>

<span data-ttu-id="c22ab-967">如果您遇到這個開發原生程式庫的繫結專案時，我們開啟新增支援新類型的組合。</span><span class="sxs-lookup"><span data-stu-id="c22ab-967">If you run into this while developing a binding project for a native library, we're open to adding support for new combinations of types.</span></span> <span data-ttu-id="c22ab-968">如果發生這種情況，請提出要求的增強功能 ([http://bugzilla.xamarin.com][2]) 與測試案例，我們將會評估它。</span><span class="sxs-lookup"><span data-stu-id="c22ab-968">If this is the case, please file an enhancement request ([http://bugzilla.xamarin.com][2]) with a test case and we'll evaluate it.</span></span>

[1]: https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS
[2]: https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS&component=General&bug_severity=enhancement

## <a name="mt5xxx-gcc-and-toolchain-error-messages"></a><span data-ttu-id="c22ab-969">MT5xxx:GCC 和工具鏈的錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-969">MT5xxx: GCC and toolchain error messages</span></span>

### <a name="mt51xx-compilation"></a><span data-ttu-id="c22ab-970">MT51xx:編譯</span><span class="sxs-lookup"><span data-stu-id="c22ab-970">MT51xx: Compilation</span></span>

<!--
 MT5xxx GCC and toolchain
  MT51xx compilation
  -->

<a name="MT5101" />

### <a name="mt5101-missing--compiler-please-install-xcode-command-line-tools-component"></a><span data-ttu-id="c22ab-971">MT5101:遺漏 ' \*' 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-971">MT5101: Missing '\*' compiler.</span></span> <span data-ttu-id="c22ab-972">請安裝 Xcode '命令列工具 」 元件</span><span class="sxs-lookup"><span data-stu-id="c22ab-972">Please install Xcode 'Command-Line Tools' component</span></span>

<a name="MT5102" />

### <a name="mt5102-failed-to-assemble-the-file--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-973">MT5102:無法組合檔案 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-973">MT5102: Failed to assemble the file '\*'.</span></span> <span data-ttu-id="c22ab-974">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-974">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<a name="MT5103" />

### <a name="mt5103-failed-to-compile-the-file--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-975">MT5103:無法編譯檔案 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-975">MT5103: Failed to compile the file '\*'.</span></span> <span data-ttu-id="c22ab-976">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-976">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<a name="MT5104" />

### <a name="mt5104-could-not-find-neither-the--nor-the--compiler-please-install-xcode-command-line-tools-component"></a><span data-ttu-id="c22ab-977">MT5104:找不到 '\*'和'\*' 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-977">MT5104: Could not find neither the '\*' nor the '\*' compiler.</span></span> <span data-ttu-id="c22ab-978">請安裝 Xcode '命令列工具 」 元件</span><span class="sxs-lookup"><span data-stu-id="c22ab-978">Please install Xcode 'Command-Line Tools' component</span></span>

<!-- 5105 is used by mmp -->

<a name="MT5106" />

### <a name="mt5106-could-not-compile-the-files--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-979">MT5106:可能不會編譯檔案 ' \*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-979">MT5106: Could not compile the file(s) '\*'.</span></span> <span data-ttu-id="c22ab-980">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-980">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<span data-ttu-id="c22ab-981">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-981">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

### <a name="mt52xx-linking"></a><span data-ttu-id="c22ab-982">MT52xx:連結</span><span class="sxs-lookup"><span data-stu-id="c22ab-982">MT52xx: Linking</span></span>

<!--
  MT52xx linking
  -->

<a name="MT5201" />

### <a name="mt5201-native-linking-failed-please-review-the-build-log-and-the-user-flags-provided-to-gcc-"></a><span data-ttu-id="c22ab-983">MT5201:原生連結失敗。</span><span class="sxs-lookup"><span data-stu-id="c22ab-983">MT5201: Native linking failed.</span></span> <span data-ttu-id="c22ab-984">請檢閱建置記錄檔和提供給 gcc 使用者旗標: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-984">Please review the build log and the user flags provided to gcc: \*</span></span>

<a name="MT5202" />

### <a name="mt5202-native-linking-failed-please-review-the-build-log"></a><span data-ttu-id="c22ab-985">MT5202:原生連結失敗。</span><span class="sxs-lookup"><span data-stu-id="c22ab-985">MT5202: Native linking failed.</span></span> <span data-ttu-id="c22ab-986">請檢閱建置記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-986">Please review the build log.</span></span>

<a name="MT5203" />

### <a name="mt5203-native-linking-warning-"></a><span data-ttu-id="c22ab-987">MT5203:原生連結警告: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-987">MT5203: Native linking warning: \*</span></span>

<!--- 5204-5208 are not used -->

<a name="MT5209" />

### <a name="mt5209-native-linking-error-"></a><span data-ttu-id="c22ab-988">MT5209:原生連結錯誤: \*</span><span class="sxs-lookup"><span data-stu-id="c22ab-988">MT5209: Native linking error: \*</span></span>

<a name="MT5210" />

### <a name="mt5210-native-linking-failed-undefined-symbol--please-verify-that-all-the-necessary-frameworks-have-been-referenced-and-native-libraries-are-properly-linked-in"></a><span data-ttu-id="c22ab-989">MT5210:原生連結失敗，未定義的符號: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-989">MT5210: Native linking failed, undefined symbol: \*.</span></span> <span data-ttu-id="c22ab-990">請確認已參考的所有必要的架構，並在會正確地連結到原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-990">Please verify that all the necessary frameworks have been referenced and native libraries are properly linked in.</span></span>

<span data-ttu-id="c22ab-991">會發生這種情況是當原生連結器找不到參考位置的符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-991">This happens when the native linker cannot find a symbol that is referenced somewhere.</span></span> <span data-ttu-id="c22ab-992">有幾個原因，這可能是：</span><span class="sxs-lookup"><span data-stu-id="c22ab-992">There are several reasons this may happen:</span></span>

* <span data-ttu-id="c22ab-993">第三方繫結需要一個架構，但繫結未指定在其`[LinkWith]`屬性。</span><span class="sxs-lookup"><span data-stu-id="c22ab-993">A third-party binding requires a framework, but the binding does not specify this in its `[LinkWith]` attribute.</span></span> <span data-ttu-id="c22ab-994">解決方案：</span><span class="sxs-lookup"><span data-stu-id="c22ab-994">Solutions:</span></span>
  - <span data-ttu-id="c22ab-995">如果您的第三方繫結、 作者或能夠存取其來源，修改繫結的`[LinkWith]`屬性來包含它所需要的架構：</span><span class="sxs-lookup"><span data-stu-id="c22ab-995">If you're the author of the third-party binding, or have access to its source, modify the binding's `[LinkWith]` attribute to include the framework it needs:</span></span>

            [LinkWith ("mylib.a", Frameworks = "SystemConfiguration")]

  - <span data-ttu-id="c22ab-996">如果您無法修改第三方繫結，您可以手動連結與必要的 framework 藉由傳遞`-gcc_flags '-framework SystemFramework'`至`mtouch`（這是藉由修改專案的 iOS 組建選項 頁面中的其他 mtouch 引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-996">If you can't modify the third-party binding, you can manually link with the required framework by passing `-gcc_flags '-framework SystemFramework'` to `mtouch` (this is done by modifying the additional mtouch arguments in the project's iOS Build options page.</span></span> <span data-ttu-id="c22ab-997">請記住，這必須針對每個專案組態）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-997">Remember that this must be done for every project configuration).</span></span>
* <span data-ttu-id="c22ab-998">在某些情況下，受管理的繫結組成多個原生程式庫，以及所有必須包含在繫結。</span><span class="sxs-lookup"><span data-stu-id="c22ab-998">In some cases a managed binding is composed of several native libraries, and all must be included in the bindings.</span></span> <span data-ttu-id="c22ab-999">可以有一個以上的原生程式庫，每個繫結專案，因此解決方案是只要將所有的必要原生程式庫新增至繫結專案。</span><span class="sxs-lookup"><span data-stu-id="c22ab-999">It is possible to have more than one native library in each binding project, so the solution is to just add all the required native libraries to the binding project.</span></span></li>
* <span data-ttu-id="c22ab-1000">受管理的繫結是指不存在於原生程式庫中的原生符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1000">A managed binding refers to native symbols that don't exist in the native library.</span></span>
    <span data-ttu-id="c22ab-1001">當繫結已存在一些時間，而且原生程式碼已修改在這段時間，讓特定的原生類別已移除或重新命名，而尚未更新繫結時，就會發生這種情形。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1001">This usually happens when a binding has existed for some time, and the native code has been modified during that time so that a particular native class has either been removed or renamed, while the binding has not been updated.</span></span>
* <span data-ttu-id="c22ab-1002">P/Invoke 指的是原生的符號不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1002">A P/Invoke refers to a native symbol that does not exist.</span></span> <span data-ttu-id="c22ab-1003">從 Xamarin.iOS 7.4 <a href="#MT5214">MT5214</a>將報告錯誤，在此情況下 （如需詳細資訊，請參閱 MT5214）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1003">Starting with Xamarin.iOS 7.4 an <a href="#MT5214">MT5214</a> error will be reported for this case (see MT5214 for more information).</span></span>
* <span data-ttu-id="c22ab-1004">第三方繫結 / 程式庫是使用C++，但繫結未指定在其`[LinkWith]`屬性。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1004">A third-party binding / library was built using C++, but the binding does not specify this in its `[LinkWith]` attribute.</span></span> <span data-ttu-id="c22ab-1005">這通常是很容易就能辨識，因為符號有輸出期間損壞C++符號 (其中一個例子`__ZNKSt9exception4whatEv`)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1005">This is usually fairly easy to recognize, because the symbols have are mangled C++ symbols (one common example is `__ZNKSt9exception4whatEv`).</span></span>
  - <span data-ttu-id="c22ab-1006">如果您的第三方繫結、 作者或能夠存取其來源，修改的繫結`[LinkWith]`屬性，設定`IsCxx`旗標：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1006">If you're the author of the third-party binding, or have access to its source, modify the binding's `[LinkWith]` attribute to set the `IsCxx` flag:</span></span>

            [LinkWith ("mylib.a", IsCxx = true)]

  - <span data-ttu-id="c22ab-1007">如果您無法修改的第三方繫結，或您手動連結與協力廠商程式庫，您可以藉由傳遞設定的對等的旗標<code>-cxx</code>至 mtouch （這是藉由修改 [其他 mtouch 引數，在專案的 iOS 組建] 選項頁面.</span><span class="sxs-lookup"><span data-stu-id="c22ab-1007">If you can't modify the third-party binding, or you're linking manually with a third-party library, you can set the equivalent flag by passing <code>-cxx</code> to mtouch (this is done by modifying the additional mtouch arguments in the project's iOS Build options page.</span></span> <span data-ttu-id="c22ab-1008">請記住，這必須針對每個專案組態）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1008">Remember that this must be done for every project configuration).</span></span>

<a name="MT5211" />

### <a name="mt5211-native-linking-failed-undefined-objective-c-class--the-symbol--could-not-be-found-in-any-of-the-libraries-or-frameworks-linked-with-your-application"></a><span data-ttu-id="c22ab-1009">MT5211:原生連結失敗，未定義的 Objective C 類別： \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1009">MT5211: Native linking failed, undefined Objective-C class: \*.</span></span> <span data-ttu-id="c22ab-1010">符號 '\*' 找不到的任何程式庫或架構與您的應用程式連結。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1010">The symbol '\*' could not be found in any of the libraries or frameworks linked with your application.</span></span>

<span data-ttu-id="c22ab-1011">會發生這種情況是當原生連結器找不到某處參考 OBJECTIVE-C 類別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1011">This happens when the native linker cannot find an Objective-C class that is referenced somewhere.</span></span> <span data-ttu-id="c22ab-1012">有幾個原因發生此情形： 相同[MT5210](#MT5210) ，此外：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1012">There are several reasons this may happen: the same as for [MT5210](#MT5210) and in addition:</span></span>

* <span data-ttu-id="c22ab-1013">第三方繫結繫結 OBJECTIVE-C 通訊協定，但沒有不加上註解與<code>[Protocol]</code>其 api 定義中的屬性。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1013">A third-party binding bound an Objective-C protocol, but did not annotate it with the <code>[Protocol]</code> attribute in its api definition.</span></span> <span data-ttu-id="c22ab-1014">解決方案：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1014">Solutions:</span></span>
  - <span data-ttu-id="c22ab-1015">新增遺漏`[Protocol]`屬性：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1015">Add the missing `[Protocol]` attribute:</span></span>

              [BaseType (typeof (NSObject))]
              [Protocol] // Add this
              public interface MyProtocol
              {
              }

<a name="MT5212" />

### <a name="mt5212-native-linking-failed-duplicate-symbol-"></a><span data-ttu-id="c22ab-1016">MT5212:原生連結失敗，重複的符號: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1016">MT5212: Native linking failed, duplicate symbol: \*.</span></span>

<span data-ttu-id="c22ab-1017">會發生這種情況是當原生連結器遭遇重複所有原生程式庫之間的符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1017">This happens when the native linker encounters duplicated symbols between all the native libraries.</span></span> <span data-ttu-id="c22ab-1018">遵循此錯誤可能有一或多個[MT5213](#MT5213)錯誤的每個項目符號的位置。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1018">Following this error there may be one or more [MT5213](#MT5213) errors with the location for each occurrence of the symbol.</span></span> <span data-ttu-id="c22ab-1019">此錯誤的可能原因：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1019">Possible reasons for this error:</span></span>

* <span data-ttu-id="c22ab-1020">相同的原生程式庫是包含兩次。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1020">The same native library is included twice.</span></span>
* <span data-ttu-id="c22ab-1021">若要定義相同的符號，就會發生兩個不同的原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1021">Two distinct native libraries happen to define the same symbols.</span></span>
* <span data-ttu-id="c22ab-1022">原生程式庫未正確建置，並多次包含相同的符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1022">A native library is not correctly built, and contains the same symbol more than once.</span></span>
  <span data-ttu-id="c22ab-1023">您可以使用下列命令，從終端機的確認 （將 i386 取代 x86_64/armv7/armv7s/arm64 根據哪一個架構中，您要建置的）：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1023">You can confirm this by using the following set of commands from a terminal (replace i386 with x86_64/armv7/armv7s/arm64 according to which architecture you're building for):</span></span>

        # Native libraries are usually fat libraries, containing binary code for
        # several architectures in the same file. First we extract the binary
        # code for the architecture we're interested in.
        lipo libNative.a -thin i386 -output libNative.i386.a

        # Now query the native library for the duplicated symbol.
        nm libNative.i386.a | fgrep 'SYMBOL'

        # You can also list the object files inside the native library.
        # In most cases this will reveal duplicated object files.
        ar -t libNative.i386.a

  <span data-ttu-id="c22ab-1024">有幾個可能的方式，修正此問題：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1024">There are a few possible ways to fix this:</span></span>

  - <span data-ttu-id="c22ab-1025">要求的提供者的原生程式庫修正此問題，並提供更新的版本。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1025">Request that the provider of the native library fix it and provide the updated version.</span></span>
  - <span data-ttu-id="c22ab-1026">它自行修正藉由移除額外的物件檔案 （這只適用於問題實際上是重複的目的檔）</span><span class="sxs-lookup"><span data-stu-id="c22ab-1026">Fix it yourself by removing the extra object files (this only works if the problem is in fact duplicated object files)</span></span>

            # Find out if the library is a fat library, and which
            # architectures it contains.
            lipo -info libNative.a

            # Extract each architecture (i386/x86_64/armv7/armv7s/arm64) to a separate file
            lipo libNative.a -thin ARCH -output libNative.ARCH.a

            # Extract the object files for the offending architecture
            # This will remove the duplicates by overwriting them
            # (since they have the same filename)
            mkdir -p ARCH
            cd ARCH
            ar -x ../libNative.ARCH.a

            # Reassemble the object files in an .a
            ar -r ../libNative.ARCH.a *.o
            cd ..

            # Reassemble the fat library
            lipo *.a -create -output libNative.a

  - <span data-ttu-id="c22ab-1027">要求的連結器，以移除未使用的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1027">Ask the linker to remove unused code.</span></span> <span data-ttu-id="c22ab-1028">Xamarin.iOS 會自動執行此動作如果符合所有下列條件：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1028">Xamarin.iOS will do this automatically if all of the following conditions are met:</span></span>
    - <span data-ttu-id="c22ab-1029">所有第三方繫結`[LinkWith]`屬性已啟用 SmartLink:</span><span class="sxs-lookup"><span data-stu-id="c22ab-1029">All third-party bindings' `[LinkWith]` attributes have enabled SmartLink:</span></span>

            [assembly: LinkWith ("libNative.a", SmartLink = true)]

    - <span data-ttu-id="c22ab-1030">否`-gcc_flags`傳遞給 mtouch （在專案的 iOS 組建 選項的 其他 mtouch 引數 欄位）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1030">No `-gcc_flags` is passed to mtouch (in the additional mtouch arguments field of the project's iOS Build options).</span></span>
    - <span data-ttu-id="c22ab-1031">您也可向連結器直接移除未使用的程式碼，藉由新增`-gcc_flags -dead_strip`其他 mtouch 引數，在 iOS 中專案的建置選項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1031">It's also possible to ask the linker directly to remove unused code by adding `-gcc_flags -dead_strip` to the additional mtouch arguments in the project's iOS Build options.</span></span>

<a name="MT5213" />

### <a name="mt5213-duplicate-symbol-in--location-related-to-previous-error"></a><span data-ttu-id="c22ab-1032">MT5213:中有重複的符號: \* （與之前錯誤相關的位置）</span><span class="sxs-lookup"><span data-stu-id="c22ab-1032">MT5213: Duplicate symbol in: \* (Location related to previous error)</span></span>

<span data-ttu-id="c22ab-1033">會報告此錯誤只搭配[MT5212](#MT5212)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1033">This error is reported only together with [MT5212](#MT5212).</span></span> <span data-ttu-id="c22ab-1034">請參閱[MT5212](#MT5212)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1034">Please see [MT5212](#MT5212) for more information.</span></span>

<a name="MT5214" />

### <a name="mt5214-native-linking-failed-undefined-symbol--this-symbol-was-referenced-the-managed-member--please-verify-that-all-the-necessary-frameworks-have-been-referenced-and-native-libraries-linked"></a><span data-ttu-id="c22ab-1035">MT5214:原生連結失敗，未定義的符號: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1035">MT5214: Native linking failed, undefined symbol: \*.</span></span> <span data-ttu-id="c22ab-1036">參考這個符號的受管理的成員 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1036">This symbol was referenced the managed member \*.</span></span> <span data-ttu-id="c22ab-1037">請確認所有必要的架構已連結的參考和原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1037">Please verify that all the necessary frameworks have been referenced and native libraries linked.</span></span>

<span data-ttu-id="c22ab-1038">當 managed 程式碼包含不存在的原生方法 P/Invoke 時，會報告此錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1038">This error is reported when the managed code contains a P/Invoke to a native method that does not exist.</span></span> <span data-ttu-id="c22ab-1039">例如: </span><span class="sxs-lookup"><span data-stu-id="c22ab-1039">For example:</span></span>

```csharp
using System.Runtime.InteropServices;
class MyImports {
   [DllImport ("__Internal")]
   public static extern void MyInexistentFunc ();
}
```

<span data-ttu-id="c22ab-1040">有幾個可能的解決方案：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1040">There are a few possible solutions:</span></span>

  -  <span data-ttu-id="c22ab-1041">從原始程式檔中移除有問題 P/Invoke。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1041">Remove the P/Invokes in question from the source code.</span></span>
  -  <span data-ttu-id="c22ab-1042">啟用受管理的連結器 （這是在專案的 iOS 組建 選項中，藉由將 「 連結器行為 」 設定為 「 所有組件 」） 的所有組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1042">Enable the managed linker for all assemblies (this is done in the project's iOS Build options, by setting "Linker Behavior" to "All assemblies").</span></span> <span data-ttu-id="c22ab-1043">這會有效地移除所有 P/Invokes 不使用應用程式 （自動，而不是以手動方式像前一個點）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1043">This will effectively remove all the P/Invokes you don't use from the app (automatically, instead of manually like the previous point).</span></span> <span data-ttu-id="c22ab-1044">缺點是，這會讓您的模擬器組建略慢，而且如果它使用反映-可以找到連結器的詳細資訊，它可能會中斷您的應用程式[此處](~/ios/deploy-test/linker.md))</span><span class="sxs-lookup"><span data-stu-id="c22ab-1044">The downside is that this will make your simulator builds somewhat slower, and it may break your app if it's using reflection - more information about the linker can be found  [here](~/ios/deploy-test/linker.md) )</span></span>
  -  <span data-ttu-id="c22ab-1045">建立第二個的原生程式庫包含遺失的原生符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1045">Create a second native library which contains the missing native symbols.</span></span> <span data-ttu-id="c22ab-1046">請注意，這只是因應措施 （如果您嘗試呼叫這些函式，您的應用程式會當機）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1046">Note that this is merely a workaround (if you happen to try to call those functions, your app will crash).</span></span>

<a name="MT5215" />

### <a name="mt5215-references-to--might-require-additional--frameworkxxx-or--lxxx-instructions-to-the-native-linker"></a><span data-ttu-id="c22ab-1047">MT5215:參考 ' \*' 可能會需要額外-framework = XXX 或-lXXX 指示原生連結器</span><span class="sxs-lookup"><span data-stu-id="c22ab-1047">MT5215: References to '\*' might require additional -framework=XXX or -lXXX instructions to the native linker</span></span>

<span data-ttu-id="c22ab-1048">這是警告，表示參考的程式庫，偵測到 P/Invoke，但不是與其連結的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1048">This is a warning, indicating that a P/Invoke was detected to reference the library in question, but the app is not linking with it.</span></span>

<a name="MT5216" />

### <a name="mt5216-native-linking-failed-for--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1049">MT5216:設定連結的原生失敗 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1049">MT5216: Native linking failed for \*.</span></span> <span data-ttu-id="c22ab-1050">請提出錯誤報告在 http://bugzilla.xamarin.com</span><span class="sxs-lookup"><span data-stu-id="c22ab-1050">Please file a bug report at http://bugzilla.xamarin.com</span></span>

<span data-ttu-id="c22ab-1051">連結 AOT 編譯器的輸出時，會報告此錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1051">This error is reported when linking the output from the AOT compiler.</span></span>

<span data-ttu-id="c22ab-1052">此錯誤最可能表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1052">This error most likely indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1053">請提出錯誤報告在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1053">Please file a bug report at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT5217" />

### <a name="mt5217-native-linking-possibly-failed-because-the-linker-command-line-was-too-long--characters"></a><span data-ttu-id="c22ab-1054">MT5217:原生連結可能會失敗，因為連結器命令列太長 (\* 字元)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1054">MT5217: Native linking possibly failed because the linker command line was too long (\* characters).</span></span>

<span data-ttu-id="c22ab-1055">原生連結失敗，您也可以連結器命令太長，所以發生此。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1055">Native linking failed, and it's possible this occured because the linker command was too long.</span></span>

<span data-ttu-id="c22ab-1056">Xamarin.iOS 專案會經常參考原生的符號，以動態方式表示原生連結器可能會移除這類原生的符號，在原生的連結過程中，因為原生連結器不會看到，會使用這些符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1056">Xamarin.iOS projects will often reference native symbols dynamically, which means that the native linker might remove such native symbols during the native linking process, because the native linker does not see that these symbols are used.</span></span>

<span data-ttu-id="c22ab-1057">通常是 Xamarin.iOS 的原生連結器將使用這類符號會被要求`-u symbol`連結器旗標，但如果有許多這類符號，整個命令列可能會超過最大的命令列長度所指定的作業系統。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1057">Usually Xamarin.iOS will ask the native linker to keep such symbols using the `-u symbol` linker flag, but if there are many such symbols, the entire command-line might exceed the maximum command-line length as specified by the operating system.</span></span>

<span data-ttu-id="c22ab-1058">有幾個可能的來源，這類動態符號：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1058">There are a few possible sources for such dynamic symbols:</span></span>

* <span data-ttu-id="c22ab-1059">P/Invokes 移到靜態連結程式庫中的方法 (dll 名稱的所在`__Internal`DllImport 屬性中`[DllImport ("__Internal")]`)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1059">P/Invokes to methods in statically linked libraries (where the dll name is `__Internal` in the DllImport attribute `[DllImport ("__Internal")]`).</span></span>
* <span data-ttu-id="c22ab-1060">欄位參考靜態連結程式庫中的記憶體位置，從繫結專案 (`[Field]`屬性)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1060">Field references to memory locations in statically linked libraries from binding projects (`[Field]` attributes).</span></span>
* <span data-ttu-id="c22ab-1061">從繫結專案 （使用累加建置時或在不使用靜態的註冊機構） 的靜態連結程式庫中所參考的 objective C 類別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1061">Objective-C classes referenced in statically linked libraries from binding projects (when using incremental builds or when not using the static registrar).</span></span>

<span data-ttu-id="c22ab-1062">可能的解決方案：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1062">Possible solutions:</span></span>

* <span data-ttu-id="c22ab-1063">（如果可進行的所有組件，而不是唯一的 SDK 組件），請讓受管理的連結器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1063">Enable the managed linker (if possible for all assemblies instead of only SDK assemblies).</span></span> <span data-ttu-id="c22ab-1064">動態符號，以便連結器的命令列不超過最大值，這可能會移除足夠的來源。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1064">This might remove enough of the sources for dynamic symbols so that the linker's command-line doesn't exceeded the maximum.</span></span>
* <span data-ttu-id="c22ab-1065">減少 P/Invokes、 欄位參考和/或 OBJECTIVE-C 類別的數目。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1065">Reduce the number of P/Invokes, field references and/or Objective-C classes.</span></span>
* <span data-ttu-id="c22ab-1066">請重寫要較短的名稱的動態符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1066">Rewrite the dynamic symbols to have shorter names.</span></span>
* <span data-ttu-id="c22ab-1067">傳遞`-dlsym:false`做為其他 mtouch 引數，在 iOS 中專案的建置選項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1067">Pass `-dlsym:false` as an additional mtouch argument in the project's iOS Build options.</span></span> <span data-ttu-id="c22ab-1068">使用此選項時，Xamarin.iOS 將產生的原生參考 AOT 編譯的程式碼，和不需要向連結器將保留這個符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1068">With this option, Xamarin.iOS will generate a native reference in the AOT-compiled code, and won't need to ask the linker to keep this symbol.</span></span> <span data-ttu-id="c22ab-1069">不過，這只適用於裝置組建，而且有 P/Invokes 不存在於靜態程式庫中的函式，它會導致連結器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1069">However, this only works for device builds, and it will cause linker errors if there are P/Invokes to functions that don't exist in the static library.</span></span>
* <span data-ttu-id="c22ab-1070">傳遞`--dynamic-symbol-mode=code`做為其他 mtouch 引數，在專案的 iOS 組建選項。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1070">Pass `--dynamic-symbol-mode=code` as an additional mtouch arguments in the project's iOS Build options.</span></span> <span data-ttu-id="c22ab-1071">使用此選項時，Xamarin.iOS 將產生額外的原生程式碼會參考這些符號，而不是要求原生連結器將這些符號使用命令列引數。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1071">With this option, Xamarin.iOS will generate additional native code that references these symbols instead of asking the native linker to keep these symbols using command-line arguments.</span></span> <span data-ttu-id="c22ab-1072">這種方法的缺點是，它將會稍微增加可執行檔的大小。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1072">The downside to this approach is that it will increase the size of the executable somewhat.</span></span>
* <span data-ttu-id="c22ab-1073">藉由傳遞啟用靜態註冊機構`--registrar:static`做為其他 mtouch 引數，在 iOS 中的專案組建選項 （對於模擬器組建，因為靜態註冊機構已經預設針對裝置組建）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1073">Enable the static registrar by passing `--registrar:static` as an additional mtouch argument in the project's iOS Build options (for simulator builds, since the static registrar is already the default for device builds).</span></span> <span data-ttu-id="c22ab-1074">靜態註冊機構會產生靜態方式參考 Objective C 類別的程式碼，因此不需要向原生的連結器，以保留這類類別。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1074">The static registrar will generate code that references Objective-C classes statically, so there is no need to ask the native linker to keep such classes.</span></span>
* <span data-ttu-id="c22ab-1075">停用累加建置 （針對裝置組建）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1075">Disable incremental builds (for device builds).</span></span> <span data-ttu-id="c22ab-1076">增量組建已啟用，靜態的註冊機構所產生的程式碼不會視為原生連結器，也就是說，Xamarin.iOS 仍然必須要求連結器，以保留參考 OBJECTIVE-C 類別中。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1076">When incremental builds are enabled, the code generated by the static registrar won't be considered by the native linker, which means that Xamarin.iOS must still ask the linker to keep referenced Objective-C classes.</span></span> <span data-ttu-id="c22ab-1077">因此停用累加建置，將導致這項需求。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1077">Thus disabling incremental builds will prevent this need.</span></span>

<a name="MT5218" />

### <a name="mt5218-cant-ignore-the-dynamic-symbol-symbol---ignore-dynamic-symbolsymbol-because-it-was-not-detected-as-a-dynamic-symbol"></a><span data-ttu-id="c22ab-1078">MT5218:不能忽視 {符號} 的動態符號 (-略過動態符號 = {符號}) 因為它沒有偵測到為動態的符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1078">MT5218: Can't ignore the dynamic symbol {symbol} (--ignore-dynamic-symbol={symbol}) because it was not detected as a dynamic symbol.</span></span>

<span data-ttu-id="c22ab-1079">命令列引數`--ignore-dynamic-symbol=symbol`已通過，但這個符號不是動態的符號必須以手動方式保留與已辨識符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1079">The command-line argument `--ignore-dynamic-symbol=symbol` was passed, but this symbol is not a symbol that was recognized as a dynamic symbol that must be manually preserved.</span></span>

<span data-ttu-id="c22ab-1080">有兩個主要的原因：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1080">There are two main reasons for this:</span></span>

* <span data-ttu-id="c22ab-1081">符號名稱不正確。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1081">The symbol name is incorrect.</span></span>
    * <span data-ttu-id="c22ab-1082">不在前面加上底線的符號名稱。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1082">Don't prepend an underscore to the symbol name.</span></span>
    * <span data-ttu-id="c22ab-1083">Objective C 類別的符號是`OBJC_CLASS_$_<classname>`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1083">The symbol for Objective-C classes is `OBJC_CLASS_$_<classname>`.</span></span>
* <span data-ttu-id="c22ab-1084">符號是正確的但已經保留以正常方式 （一些建置選項的原因來變更的動態符號的確切清單） 的符號。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1084">The symbol is correct, but it's a symbol that's already preserved by normal means (some build options causes the exact list of dynamic symbols to vary).</span></span>

### <a name="mt53xx-other-tools"></a><span data-ttu-id="c22ab-1085">MT53xx:其他工具</span><span class="sxs-lookup"><span data-stu-id="c22ab-1085">MT53xx: Other tools</span></span>

<!--
  MT53xx other tools
  -->

<a name="MT5301" />

### <a name="mt5301-missing-strip-tool-please-install-xcode-command-line-tools-component"></a><span data-ttu-id="c22ab-1086">MT5301:遺漏 '移除' 工具。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1086">MT5301: Missing 'strip' tool.</span></span> <span data-ttu-id="c22ab-1087">請安裝 Xcode '命令列工具 」 元件</span><span class="sxs-lookup"><span data-stu-id="c22ab-1087">Please install Xcode 'Command-Line Tools' component</span></span>

<a name="MT5302" />

### <a name="mt5302-missing-dsymutil-tool-please-install-xcode-command-line-tools-component"></a><span data-ttu-id="c22ab-1088">MT5302:遺漏 'dsymutil' 工具。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1088">MT5302: Missing 'dsymutil' tool.</span></span> <span data-ttu-id="c22ab-1089">請安裝 Xcode '命令列工具 」 元件</span><span class="sxs-lookup"><span data-stu-id="c22ab-1089">Please install Xcode 'Command-Line Tools' component</span></span>

<a name="MT5303" />

### <a name="mt5303-failed-to-generate-the-debug-symbols-dsym-directory-please-review-the-build-log"></a><span data-ttu-id="c22ab-1090">MT5303:無法產生偵錯符號 （dSYM 目錄）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1090">MT5303: Failed to generate the debug symbols (dSYM directory).</span></span> <span data-ttu-id="c22ab-1091">請檢閱建置記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1091">Please review the build log.</span></span>

<span data-ttu-id="c22ab-1092">若要建立偵錯符號的最終的.app 目錄上執行 dsymutil 時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1092">An error occurred when running dsymutil on the final .app directory to create the debug symbols.</span></span> <span data-ttu-id="c22ab-1093">請檢閱建置記錄檔，請參閱 dsymutil 的輸出，並查看如何修正它。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1093">Please review the build log to see dsymutil's output and see how it can be fixed.</span></span>

<a name="MT5304" />

### <a name="mt5304-failed-to-strip-the-final-binary-please-review-the-build-log"></a><span data-ttu-id="c22ab-1094">MT5304:無法刪除最終二進位檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1094">MT5304: Failed to strip the final binary.</span></span> <span data-ttu-id="c22ab-1095">請檢閱建置記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1095">Please review the build log.</span></span>

<span data-ttu-id="c22ab-1096">執行 '帶狀' 工具來移除應用程式的偵錯資訊時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1096">An error occurred when running the 'strip' tool to remove debugging information from the application.</span></span>

<a name="MT5305" />

### <a name="mt5305-missing-lipo-tool-please-install-xcode-command-line-tools-component"></a><span data-ttu-id="c22ab-1097">MT5305:遺漏 'lipo' 工具。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1097">MT5305: Missing 'lipo' tool.</span></span> <span data-ttu-id="c22ab-1098">請安裝 Xcode '命令列工具 」 元件</span><span class="sxs-lookup"><span data-stu-id="c22ab-1098">Please install Xcode 'Command-Line Tools' component</span></span>

<a name="MT5306" />

### <a name="mt5306-failed-to-create-the-a-fat-library-please-review-the-build-log"></a><span data-ttu-id="c22ab-1099">MT5306:無法建立 fat 程式庫。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1099">MT5306: Failed to create the a fat library.</span></span> <span data-ttu-id="c22ab-1100">請檢閱建置記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1100">Please review the build log.</span></span>

<span data-ttu-id="c22ab-1101">執行 'lipo' 工具時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1101">An error occurred when running the 'lipo' tool.</span></span> <span data-ttu-id="c22ab-1102">請檢閱組建記錄檔，以 'lipo' 回報的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1102">Please review the build log to see the error reported by 'lipo'.</span></span>

<a name="MT5307" />

### <a name="mt5307-failed-to-sign-the-executable-please-review-the-build-log"></a><span data-ttu-id="c22ab-1103">MT5307:無法簽署可執行檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1103">MT5307: Failed to sign the executable.</span></span> <span data-ttu-id="c22ab-1104">請檢閱建置記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1104">Please review the build log.</span></span>

<span data-ttu-id="c22ab-1105">登入應用程式時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1105">An error occurred when signing the application.</span></span> <span data-ttu-id="c22ab-1106">請檢閱組建記錄檔，以 'codesign' 回報的錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1106">Please review the build log to see the error reported by 'codesign'.</span></span>

<!-- 5308 is used by mmp -->
<!-- 5309 is used by mmp -->
<!-- 5310 is used by mmp -->

## <a name="mt6xxx-mtouch-internal-tools-error-messages"></a><span data-ttu-id="c22ab-1107">MT6xxx: mtouch 內部工具錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-1107">MT6xxx: mtouch internal tools error messages</span></span>

### <a name="mt600x-stripper"></a><span data-ttu-id="c22ab-1108">MT600x:清除</span><span class="sxs-lookup"><span data-stu-id="c22ab-1108">MT600x: Stripper</span></span>

<!--
 MT6xxx mtouch internal tools
  MT600x Stripper
  -->

<a name="MT6001" />

### <a name="mt6001-running-version-of-cecil-doesnt-support-assembly-stripping"></a><span data-ttu-id="c22ab-1109">MT6001:Cecil 執行版本不支援移除的組件</span><span class="sxs-lookup"><span data-stu-id="c22ab-1109">MT6001: Running version of Cecil doesn't support assembly stripping</span></span>

<a name="MT6002" />

### <a name="mt6002-could-not-strip-assembly-"></a><span data-ttu-id="c22ab-1110">MT6002:無法移除組件`*`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1110">MT6002: Could not strip assembly `*`.</span></span>

<span data-ttu-id="c22ab-1111">移除應用程式中的 managed 程式碼 （移除的 IL 程式碼） 的組件時，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1111">An error occurred when stripping managed code(removing the IL code) from the assemblies in the application.</span></span>

<a name="MT6003" />

### <a name="mt6003-unauthorizedaccessexception-message"></a><span data-ttu-id="c22ab-1112">MT6003: [UnauthorizedAccessException 訊息]</span><span class="sxs-lookup"><span data-stu-id="c22ab-1112">MT6003: [UnauthorizedAccessException message]</span></span>

<span data-ttu-id="c22ab-1113">安全性時發生錯誤移除偵錯符號，從應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1113">A security error ocurred while stripping debugging symbols from the application.</span></span>

## <a name="mt7xxx-msbuild-error-messages"></a><span data-ttu-id="c22ab-1114">MT7xxx:MSBuild 錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-1114">MT7xxx: MSBuild error messages</span></span>

<!--
 MT7xxx msbuild errors
  -->

<a name="MT7001" />

### <a name="mt7001-could-not-resolve-host-ips-for-wifi-debugger-settings"></a><span data-ttu-id="c22ab-1115">MT7001:無法解析主機 Ip WiFi 偵錯工具設定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1115">MT7001: Could not resolve host IPs for WiFi debugger settings.</span></span>

<span data-ttu-id="c22ab-1116">*MSBuild 工作：DetectDebugNetworkConfigurationTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1116">*MSBuild task: DetectDebugNetworkConfigurationTaskBase*</span></span>

<span data-ttu-id="c22ab-1117">疑難排解步驟：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1117">Troubleshooting steps:</span></span>

- <span data-ttu-id="c22ab-1118">嘗試執行`csharp -e 'System.Net.Dns.GetHostEntry (System.Net.Dns.GetHostName ()).AddressList'`（這將使您的 IP 位址而非錯誤很明顯地）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1118">try to run `csharp -e 'System.Net.Dns.GetHostEntry (System.Net.Dns.GetHostName ()).AddressList'` (that should give you an IP address and not an error obviously).</span></span>
- <span data-ttu-id="c22ab-1119">嘗試執行 「 ping \`hostname\`」 這可能會讓您的詳細資訊，例如： `cannot resolve MyHost.local: Unknown host`</span><span class="sxs-lookup"><span data-stu-id="c22ab-1119">try to run "ping \`hostname\`" which might give you more information, like: `cannot resolve MyHost.local: Unknown host`</span></span>

<span data-ttu-id="c22ab-1120">在某些情況下，它是 「 區域網路 」 問題，並藉由新增未知的主機可解決`127.0.0.1   MyHost.local`在`/etc/hosts`。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1120">In some cases, it's a "local network" issue and it can be addressed by adding the unknown host `127.0.0.1   MyHost.local` in `/etc/hosts`.</span></span>

<a name="MT7002" />

### <a name="mt7002-this-machine-does-not-have-any-network-adapters-this-is-required-when-debugging-or-profiling-on-device-over-wifi"></a><span data-ttu-id="c22ab-1121">MT7002:這部電腦沒有任何網路介面卡。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1121">MT7002: This machine does not have any network adapters.</span></span> <span data-ttu-id="c22ab-1122">偵錯或分析裝置上透過 WiFi 時，這是必要的。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1122">This is required when debugging or profiling on device over WiFi.</span></span>

<span data-ttu-id="c22ab-1123">*MSBuild 工作：DetectDebugNetworkConfigurationTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1123">*MSBuild task: DetectDebugNetworkConfigurationTaskBase*</span></span>

<a name="MT7003" />

### <a name="mt7003-the-app-extension--does-not-contain-an-infoplist"></a><span data-ttu-id="c22ab-1124">MT7003:應用程式擴充功能 ' \*' 不包含 Info.plist。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1124">MT7003: The App Extension '\*' does not contain an Info.plist.</span></span>

<span data-ttu-id="c22ab-1125">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1125">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7004" />

### <a name="mt7004-the-app-extension--does-not-specify-a-cfbundleidentifier"></a><span data-ttu-id="c22ab-1126">MT7004:應用程式擴充功能 ' \*' 未指定 CFBundleIdentifier。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1126">MT7004: The App Extension '\*' does not specify a CFBundleIdentifier.</span></span>

<span data-ttu-id="c22ab-1127">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1127">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7005" />

### <a name="mt7005-the-app-extension--does-not-specify-a-cfbundleexecutable"></a><span data-ttu-id="c22ab-1128">MT7005:應用程式擴充功能 ' \*' 未指定 CFBundleExecutable。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1128">MT7005: The App Extension '\*' does not specify a CFBundleExecutable.</span></span>

<span data-ttu-id="c22ab-1129">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1129">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7006" />

### <a name="mt7006-the-app-extension--has-an-invalid-cfbundleidentifier--it-does-not-begin-with-the-main-app-bundles-cfbundleidentifier-"></a><span data-ttu-id="c22ab-1130">MT7006:應用程式擴充功能 '\*' 具有無效的 CFBundleIdentifier (\*)，它不是主要的應用程式套件組合的 CFBundleIdentifier （\*）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1130">MT7006: The App Extension '\*' has an invalid CFBundleIdentifier (\*), it does not begin with the main app bundle's CFBundleIdentifier (\*).</span></span>

<span data-ttu-id="c22ab-1131">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1131">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7007" />

### <a name="mt7007-the-app-extension--has-a-cfbundleidentifier--that-ends-with-the-illegal-suffix-key"></a><span data-ttu-id="c22ab-1132">MT7007:應用程式擴充功能 '\*' 具有 CFBundleIdentifier (\*)，結尾是不合法的後置詞".key 」。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1132">MT7007: The App Extension '\*' has a CFBundleIdentifier (\*) that ends with the illegal suffix ".key".</span></span>

<span data-ttu-id="c22ab-1133">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1133">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7008" />

### <a name="mt7008-the-app-extension--does-not-specify-a-cfbundleshortversionstring"></a><span data-ttu-id="c22ab-1134">MT7008:應用程式擴充功能 ' \*' 未指定 CFBundleShortVersionString。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1134">MT7008: The App Extension '\*' does not specify a CFBundleShortVersionString.</span></span>

<span data-ttu-id="c22ab-1135">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1135">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7009" />

### <a name="mt7009-the-app-extension--has-an-invalid-infoplist-it-does-not-contain-an-nsextension-dictionary"></a><span data-ttu-id="c22ab-1136">MT7009:應用程式擴充功能 ' \*' 有無效的 Info.plist： 它不包含 NSExtension 字典。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1136">MT7009: The App Extension '\*' has an invalid Info.plist: it does not contain an NSExtension dictionary.</span></span>

<span data-ttu-id="c22ab-1137">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1137">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7010" />

### <a name="mt7010-the-app-extension--has-an-invalid-infoplist-the-nsextension-dictionary-does-not-contain-an-nsextensionpointidentifier-value"></a><span data-ttu-id="c22ab-1138">MT7010:應用程式擴充功能 ' \*' 有無效的 Info.plist: NSExtension 字典不包含 NSExtensionPointIdentifier 值。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1138">MT7010: The App Extension '\*' has an invalid Info.plist: the NSExtension dictionary does not contain an NSExtensionPointIdentifier value.</span></span>

<span data-ttu-id="c22ab-1139">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1139">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7011" />

### <a name="mt7011-the-watchkit-extension--has-an-invalid-infoplist-the-nsextension-dictionary-does-not-contain-an-nsextensionattributes-dictionary"></a><span data-ttu-id="c22ab-1140">MT7011:WatchKit 擴充功能 ' \*' 有無效的 Info.plist: NSExtension 字典不包含 NSExtensionAttributes 字典。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1140">MT7011: The WatchKit Extension '\*' has an invalid Info.plist: the NSExtension dictionary does not contain an NSExtensionAttributes dictionary.</span></span>

<span data-ttu-id="c22ab-1141">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1141">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7012" />

### <a name="mt7012-the-watchkit-extension--does-not-have-exactly-one-watch-app"></a><span data-ttu-id="c22ab-1142">MT7012:WatchKit 擴充功能 ' \*' 沒有剛好一個 watch 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1142">MT7012: The WatchKit Extension '\*' does not have exactly one watch app.</span></span>

<span data-ttu-id="c22ab-1143">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1143">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7013" />

### <a name="mt7013-the-watchkit-extension--has-an-invalid-infoplist-uirequireddevicecapabilities-must-contain-the-watch-companion-capability"></a><span data-ttu-id="c22ab-1144">MT7013:WatchKit 擴充功能 ' \*' 有無效的 Info.plist:UIRequiredDeviceCapabilities 必須包含 '監看式隨附' 功能。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1144">MT7013: The WatchKit Extension '\*' has an invalid Info.plist: UIRequiredDeviceCapabilities must contain the 'watch-companion' capability.</span></span>

<span data-ttu-id="c22ab-1145">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1145">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7014" />

### <a name="mt7014-the-watch-app--does-not-contain-an-infoplist"></a><span data-ttu-id="c22ab-1146">MT7014:Watch 應用程式 ' \*' 不包含 Info.plist。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1146">MT7014: The Watch App '\*' does not contain an Info.plist.</span></span>

<span data-ttu-id="c22ab-1147">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1147">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7015" />

### <a name="mt7015-the-watch-app--does-not-specify-a-cfbundleidentifier"></a><span data-ttu-id="c22ab-1148">MT7015:Watch 應用程式 ' \*' 未指定 CFBundleIdentifier。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1148">MT7015: The Watch App '\*' does not specify a CFBundleIdentifier.</span></span>

<span data-ttu-id="c22ab-1149">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1149">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7016" />

### <a name="mt7016-the-watch-app--has-an-invalid-cfbundleidentifier--it-does-not-begin-with-the-main-app-bundles-cfbundleidentifier-"></a><span data-ttu-id="c22ab-1150">MT7016:Watch 應用程式 '\*' 具有無效的 CFBundleIdentifier (\*)，它不是主要的應用程式套件組合的 CFBundleIdentifier （\*）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1150">MT7016: The Watch App '\*' has an invalid CFBundleIdentifier (\*), it does not begin with the main app bundle's CFBundleIdentifier (\*).</span></span>

<span data-ttu-id="c22ab-1151">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1151">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7017" />

### <a name="mt7017-the-watch-app--does-not-have-a-valid-uidevicefamily-value-expected-watch-4-but-found--"></a><span data-ttu-id="c22ab-1152">MT7017:Watch 應用程式 '\*' 沒有有效的 UIDeviceFamily 值。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1152">MT7017: The Watch App '\*' does not have a valid UIDeviceFamily value.</span></span> <span data-ttu-id="c22ab-1153">預期的 '(4) 觀看' 卻找到 '\* （\*） '。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1153">Expected 'Watch (4)' but found '\* (\*)'.</span></span>

<span data-ttu-id="c22ab-1154">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1154">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7018" />

### <a name="mt7018-the-watch-app--does-not-specify-a-cfbundleexecutable"></a><span data-ttu-id="c22ab-1155">MT7018:Watch 應用程式 ' \*' 未指定 CFBundleExecutable</span><span class="sxs-lookup"><span data-stu-id="c22ab-1155">MT7018: The Watch App '\*' does not specify a CFBundleExecutable</span></span>

<span data-ttu-id="c22ab-1156">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1156">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7019" />

### <a name="mt7019-the-watch-app--has-an-invalid-wkcompanionappbundleidentifier-value--it-does-not-match-the-main-app-bundles-cfbundleidentifier-"></a><span data-ttu-id="c22ab-1157">MT7019:Watch 應用程式 '\*' 有無效的 WKCompanionAppBundleIdentifier 值 ('\*')，它不符合主要的應用程式套件組合的 CFBundleIdentifier ('\* ')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1157">MT7019: The Watch App '\*' has an invalid WKCompanionAppBundleIdentifier value ('\*'), it does not match the main app bundle's CFBundleIdentifier ('\*').</span></span>

<span data-ttu-id="c22ab-1158">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1158">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7020" />

### <a name="mt7020-the-watch-app--has-an-invalid-infoplist-the-wkwatchkitapp-key-must-be-present-and-have-a-value-of-true"></a><span data-ttu-id="c22ab-1159">MT7020:Watch 應用程式 ' \*' 有無效的 Info.plist： 必須要有 WKWatchKitApp 金鑰，並將其值為 'true'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1159">MT7020: The Watch App '\*' has an invalid Info.plist: the WKWatchKitApp key must be present and have a value of 'true'.</span></span>

<span data-ttu-id="c22ab-1160">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1160">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7021" />

### <a name="mt7021-the-watch-app--has-an-invalid-infoplist-the-lsrequiresiphoneos-key-must-not-be-present"></a><span data-ttu-id="c22ab-1161">MT7021:Watch 應用程式 ' \*' 有無效的 Info.plist: LSRequiresIPhoneOS 金鑰不能存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1161">MT7021: The Watch App '\*' has an invalid Info.plist: the LSRequiresIPhoneOS key must not be present.</span></span>

<span data-ttu-id="c22ab-1162">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1162">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7022" />

### <a name="mt7022-the-watch-app--does-not-contain-a-watch-extension"></a><span data-ttu-id="c22ab-1163">MT7022:Watch 應用程式 ' \*' 不包含監看式延伸模組。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1163">MT7022: The Watch App '\*' does not contain a Watch Extension.</span></span>

<span data-ttu-id="c22ab-1164">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1164">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7023" />

### <a name="mt7023-the-watch-extension--does-not-contain-an-infoplist"></a><span data-ttu-id="c22ab-1165">MT7023:監看式延伸模組 ' \*' 不包含 Info.plist。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1165">MT7023: The Watch Extension '\*' does not contain an Info.plist.</span></span>

<span data-ttu-id="c22ab-1166">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1166">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7024" />

### <a name="mt7024-the-watch-extension--does-not-specify-a-cfbundleidentifier"></a><span data-ttu-id="c22ab-1167">MT7024:監看式延伸模組 ' \*' 未指定 CFBundleIdentifier。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1167">MT7024: The Watch Extension '\*' does not specify a CFBundleIdentifier.</span></span>

<span data-ttu-id="c22ab-1168">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1168">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7025" />

### <a name="mt7025-the-watch-extension--does-not-specify-a-cfbundleexecutable"></a><span data-ttu-id="c22ab-1169">MT7025:監看式延伸模組 ' \*' 未指定 CFBundleExecutable。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1169">MT7025: The Watch Extension '\*' does not specify a CFBundleExecutable.</span></span>

<span data-ttu-id="c22ab-1170">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1170">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7026" />

### <a name="mt7026-the-watch-extension--has-an-invalid-cfbundleidentifier--it-does-not-begin-with-the-main-app-bundles-cfbundleidentifier-"></a><span data-ttu-id="c22ab-1171">MT7026:監看式延伸模組 '\*' 具有無效的 CFBundleIdentifier (\*)，它不是主要的應用程式套件組合的 CFBundleIdentifier （\*）。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1171">MT7026: The Watch Extension '\*' has an invalid CFBundleIdentifier (\*), it does not begin with the main app bundle's CFBundleIdentifier (\*).</span></span>

<span data-ttu-id="c22ab-1172">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1172">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7027" />

### <a name="mt7027-the-watch-extension--has-a-cfbundleidentifier--that-ends-with-the-illegal-suffix-key"></a><span data-ttu-id="c22ab-1173">MT7027:監看式延伸模組 '\*' 具有 CFBundleIdentifier (\*)，結尾是不合法的後置詞".key 」。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1173">MT7027: The Watch Extension '\*' has a CFBundleIdentifier (\*) that ends with the illegal suffix ".key".</span></span>

<span data-ttu-id="c22ab-1174">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1174">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7028" />

### <a name="mt7028-the-watch-extension--has-an-invalid-infoplist-it-does-not-contain-an-nsextension-dictionary"></a><span data-ttu-id="c22ab-1175">MT7028:監看式延伸模組 ' \*' 有無效的 Info.plist： 它不包含 NSExtension 字典。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1175">MT7028: The Watch Extension '\*' has an invalid Info.plist: it does not contain an NSExtension dictionary.</span></span>

<span data-ttu-id="c22ab-1176">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1176">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7029" />

### <a name="mt7029-the-watch-extension--has-an-invalid-infoplist-the-nsextensionpointidentifier-must-be-comapplewatchkit"></a><span data-ttu-id="c22ab-1177">MT7029:監看式延伸模組 ' \*' 有無效的 Info.plist: NSExtensionPointIdentifier 必須是"com.apple.watchkit 」。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1177">MT7029: The Watch Extension '\*' has an invalid Info.plist: the NSExtensionPointIdentifier must be "com.apple.watchkit".</span></span>

<span data-ttu-id="c22ab-1178">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1178">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7030" />

### <a name="mt7030-the-watch-extension--has-an-invalid-infoplist-the-nsextension-dictionary-must-contain-nsextensionattributes"></a><span data-ttu-id="c22ab-1179">MT7030:監看式延伸模組 ' \*' 有無效的 Info.plist: NSExtension 字典必須包含 NSExtensionAttributes。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1179">MT7030: The Watch Extension '\*' has an invalid Info.plist: the NSExtension dictionary must contain NSExtensionAttributes.</span></span>

<span data-ttu-id="c22ab-1180">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1180">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7031" />

### <a name="mt7031-the-watch-extension--has-an-invalid-infoplist-the-nsextensionattributes-dictionary-must-contain-a-wkappbundleidentifier"></a><span data-ttu-id="c22ab-1181">MT7031:監看式延伸模組 ' \*' 有無效的 Info.plist: NSExtensionAttributes 字典必須包含 WKAppBundleIdentifier。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1181">MT7031: The Watch Extension '\*' has an invalid Info.plist: the NSExtensionAttributes dictionary must contain a WKAppBundleIdentifier.</span></span>

<span data-ttu-id="c22ab-1182">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1182">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7032" />

### <a name="mt7032-the-watchkit-extension--has-an-invalid-infoplist-uirequireddevicecapabilities-should-not-contain-the-watch-companion-capability"></a><span data-ttu-id="c22ab-1183">MT7032:WatchKit 擴充功能 ' \*' 有無效的 Info.plist:UIRequiredDeviceCapabilities 不應包含 '監看式隨附' 功能。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1183">MT7032: The WatchKit Extension '\*' has an invalid Info.plist: UIRequiredDeviceCapabilities should not contain the 'watch-companion' capability.</span></span>

<span data-ttu-id="c22ab-1184">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1184">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7033" />

### <a name="mt7033-the-watch-app--does-not-contain-an-infoplist"></a><span data-ttu-id="c22ab-1185">MT7033:Watch 應用程式 ' \*' 不包含 Info.plist。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1185">MT7033: The Watch App '\*' does not contain an Info.plist.</span></span>

<span data-ttu-id="c22ab-1186">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1186">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7034" />

### <a name="mt7034-the-watch-app--does-not-specify-a-cfbundleidentifier"></a><span data-ttu-id="c22ab-1187">MT7034:Watch 應用程式 ' \*' 未指定 CFBundleIdentifier。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1187">MT7034: The Watch App '\*' does not specify a CFBundleIdentifier.</span></span>

<span data-ttu-id="c22ab-1188">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1188">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7035" />

### <a name="mt7035-the-watch-app--does-not-have-a-valid-uidevicefamily-value-expected--but-found--"></a><span data-ttu-id="c22ab-1189">MT7035:Watch 應用程式 '\*' 沒有有效的 UIDeviceFamily 值。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1189">MT7035: The Watch App '\*' does not have a valid UIDeviceFamily value.</span></span> <span data-ttu-id="c22ab-1190">必須是 '\*'但卻發現'\* (\*)'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1190">Expected '\*' but found '\* (\*)'.</span></span>

<span data-ttu-id="c22ab-1191">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1191">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7036" />

### <a name="mt7036-the-watch-app--does-not-specify-a-cfbundleexecutable"></a><span data-ttu-id="c22ab-1192">MT7036:Watch 應用程式 ' \*' 未指定 CFBundleExecutable。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1192">MT7036: The Watch App '\*' does not specify a CFBundleExecutable.</span></span>

<span data-ttu-id="c22ab-1193">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1193">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7037" />

### <a name="mt7037-the-watchkit-extension-extensionname-has-an-invalid-wkappbundleidentifier-value--it-does-not-match-the-watch-apps-cfbundleidentifier-"></a><span data-ttu-id="c22ab-1194">MT7037:WatchKit 延伸模組 '{extensionName}' 有無效的 WKAppBundleIdentifier 值 ('\*')，它不符合監看式應用程式的 CFBundleIdentifier ('\*')。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1194">MT7037: The WatchKit Extension '{extensionName}' has an invalid WKAppBundleIdentifier value ('\*'), it does not match the Watch App's CFBundleIdentifier ('\*').</span></span>

<span data-ttu-id="c22ab-1195">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1195">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7038" />

### <a name="mt7038-the-watch-app--has-an-invalid-infoplist-the-wkcompanionappbundleidentifier-must-exist-and-must-match-the-main-app-bundles-cfbundleidentifier"></a><span data-ttu-id="c22ab-1196">MT7038:Watch 應用程式 ' \*' 有無效的 Info.plist: WKCompanionAppBundleIdentifier 必須存在，且必須符合主要的應用程式套件組合的 CFBundleIdentifier。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1196">MT7038: The Watch App '\*' has an invalid Info.plist: the WKCompanionAppBundleIdentifier must exist and must match the main app bundle's CFBundleIdentifier.</span></span>

<span data-ttu-id="c22ab-1197">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1197">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7039" />

### <a name="mt7039-the-watch-app--has-an-invalid-infoplist-the-lsrequiresiphoneos-key-must-not-be-present"></a><span data-ttu-id="c22ab-1198">MT7039:Watch 應用程式 ' \*' 有無效的 Info.plist: LSRequiresIPhoneOS 金鑰不能存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1198">MT7039: The Watch App '\*' has an invalid Info.plist: the LSRequiresIPhoneOS key must not be present.</span></span>

<span data-ttu-id="c22ab-1199">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1199">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7040" />

### <a name="mt7040-the-app-bundle-appbundlepath-does-not-contain-an-infoplist"></a><span data-ttu-id="c22ab-1200">MT7040:應用程式套件組合 {AppBundlePath} 不包含 Info.plist。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1200">MT7040: The app bundle {AppBundlePath} does not contain an Info.plist.</span></span>

<span data-ttu-id="c22ab-1201">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1201">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7041" />

### <a name="mt7041-main-infoplist-path-does-not-specify-a-cfbundleidentifier"></a><span data-ttu-id="c22ab-1202">MT7041:Main Info.plist 路徑未指定 CFBundleIdentifier。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1202">MT7041: Main Info.plist path does not specify a CFBundleIdentifier.</span></span>

<span data-ttu-id="c22ab-1203">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1203">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7042" />

### <a name="mt7042-main-infoplist-path-does-not-specify-a-cfbundleexecutable"></a><span data-ttu-id="c22ab-1204">MT7042:Main Info.plist 路徑未指定 CFBundleExecutable。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1204">MT7042: Main Info.plist path does not specify a CFBundleExecutable.</span></span>

<span data-ttu-id="c22ab-1205">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1205">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7043" />

### <a name="mt7043-main-infoplist-path-does-not-specify-a-cfbundlesupportedplatforms"></a><span data-ttu-id="c22ab-1206">MT7043:Main Info.plist 路徑未指定 CFBundleSupportedPlatforms。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1206">MT7043: Main Info.plist path does not specify a CFBundleSupportedPlatforms.</span></span>

<span data-ttu-id="c22ab-1207">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1207">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7044" />

### <a name="mt7044-main-infoplist-path-does-not-specify-a-uidevicefamily"></a><span data-ttu-id="c22ab-1208">MT7044:Main Info.plist 路徑未指定 UIDeviceFamily。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1208">MT7044: Main Info.plist path does not specify a UIDeviceFamily.</span></span>

<span data-ttu-id="c22ab-1209">*MSBuild 工作：ValidateAppBundleTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1209">*MSBuild task: ValidateAppBundleTaskBase*</span></span>

<a name="MT7045" />

### <a name="mt7045-unrecognized-format-"></a><span data-ttu-id="c22ab-1210">MT7045:無法辨認的格式: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1210">MT7045: Unrecognized Format: \*.</span></span>

<span data-ttu-id="c22ab-1211">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1211">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<span data-ttu-id="c22ab-1212">其中 \* 可以是：</span><span class="sxs-lookup"><span data-stu-id="c22ab-1212">Where \* can be:</span></span>

- <span data-ttu-id="c22ab-1213">字串</span><span class="sxs-lookup"><span data-stu-id="c22ab-1213">string</span></span>
- <span data-ttu-id="c22ab-1214">array</span><span class="sxs-lookup"><span data-stu-id="c22ab-1214">array</span></span>
- <span data-ttu-id="c22ab-1215">dict</span><span class="sxs-lookup"><span data-stu-id="c22ab-1215">dict</span></span>
- <span data-ttu-id="c22ab-1216">bool</span><span class="sxs-lookup"><span data-stu-id="c22ab-1216">bool</span></span>
- <span data-ttu-id="c22ab-1217">實數</span><span class="sxs-lookup"><span data-stu-id="c22ab-1217">real</span></span>
- <span data-ttu-id="c22ab-1218">整數</span><span class="sxs-lookup"><span data-stu-id="c22ab-1218">integer</span></span>
- <span data-ttu-id="c22ab-1219">date</span><span class="sxs-lookup"><span data-stu-id="c22ab-1219">date</span></span>
- <span data-ttu-id="c22ab-1220">資料</span><span class="sxs-lookup"><span data-stu-id="c22ab-1220">data</span></span>

<a name="MT7046" />

### <a name="mt7046-add-entry--incorrectly-specified"></a><span data-ttu-id="c22ab-1221">MT7046:加入:項目，\*，正確指定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1221">MT7046: Add: Entry, \*, Incorrectly Specified.</span></span>

<span data-ttu-id="c22ab-1222">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1222">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7047" />

### <a name="mt7047-add-entry--contains-invalid-array-index"></a><span data-ttu-id="c22ab-1223">MT7047:加入:項目，\*，包含無效的陣列索引。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1223">MT7047: Add: Entry, \*, Contains Invalid Array Index.</span></span>

<span data-ttu-id="c22ab-1224">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1224">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7048" />

### <a name="mt7048-add--entry-already-exists"></a><span data-ttu-id="c22ab-1225">MT7048:新增: \* 項目已經存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1225">MT7048: Add: \* Entry Already Exists.</span></span>

<span data-ttu-id="c22ab-1226">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1226">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7049" />

### <a name="mt7049-add-cant-add-entry--to-parent"></a><span data-ttu-id="c22ab-1227">MT7049:加入:無法新增項目，\*，以父代。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1227">MT7049: Add: Can't Add Entry, \*, to Parent.</span></span>

<span data-ttu-id="c22ab-1228">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1228">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7050" />

### <a name="mt7050-delete-cant-delete-entry--from-parent"></a><span data-ttu-id="c22ab-1229">MT7050:刪除：無法刪除項目，\*，從父代。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1229">MT7050: Delete: Can't Delete Entry, \*, from Parent.</span></span>

<span data-ttu-id="c22ab-1230">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1230">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7051" />

### <a name="mt7051-delete-entry--contains-invalid-array-index"></a><span data-ttu-id="c22ab-1231">MT7051:刪除：項目，\*，包含無效的陣列索引。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1231">MT7051: Delete: Entry, \*, Contains Invalid Array Index.</span></span>

<span data-ttu-id="c22ab-1232">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1232">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7052" />

### <a name="mt7052-delete-entry--does-not-exist"></a><span data-ttu-id="c22ab-1233">MT7052:刪除：項目，\*，不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1233">MT7052: Delete: Entry, \*, Does Not Exist.</span></span>

<span data-ttu-id="c22ab-1234">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1234">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7053" />

### <a name="mt7053-import-entry--incorrectly-specified"></a><span data-ttu-id="c22ab-1235">MT7053:匯入：項目，\*，正確指定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1235">MT7053: Import: Entry, \*, Incorrectly Specified.</span></span>

<span data-ttu-id="c22ab-1236">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1236">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7054" />

### <a name="mt7054-import-entry--contains-invalid-array-index"></a><span data-ttu-id="c22ab-1237">MT7054:匯入：項目，\*，包含無效的陣列索引。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1237">MT7054: Import: Entry, \*, Contains Invalid Array Index.</span></span>

<span data-ttu-id="c22ab-1238">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1238">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7055" />

### <a name="mt7055-import-error-reading-file-"></a><span data-ttu-id="c22ab-1239">MT7055:匯入：讀取檔案時發生錯誤: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1239">MT7055: Import: Error Reading File: \*.</span></span>

<span data-ttu-id="c22ab-1240">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1240">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7056" />

### <a name="mt7056-import-cant-add-entry--to-parent"></a><span data-ttu-id="c22ab-1241">MT7056:匯入：無法新增項目，\*，以父代。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1241">MT7056: Import: Can't Add Entry, \*, to Parent.</span></span>

<span data-ttu-id="c22ab-1242">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1242">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7057" />

### <a name="mt7057-merge-cant-add-array-entries-to-dict"></a><span data-ttu-id="c22ab-1243">MT7057:合併：無法將陣列項目加入至 dict.</span><span class="sxs-lookup"><span data-stu-id="c22ab-1243">MT7057: Merge: Can't Add array Entries to dict.</span></span>

<span data-ttu-id="c22ab-1244">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1244">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7058" />

### <a name="mt7058-merge-specified-entry-must-be-a-container"></a><span data-ttu-id="c22ab-1245">MT7058:合併：指定的項目必須是一個容器。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1245">MT7058: Merge: Specified Entry Must Be a Container.</span></span>

<span data-ttu-id="c22ab-1246">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1246">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7059" />

### <a name="mt7059-merge-entry--contains-invalid-array-index"></a><span data-ttu-id="c22ab-1247">MT7059:合併：項目，\*，包含無效的陣列索引。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1247">MT7059: Merge: Entry, \*, Contains Invalid Array Index.</span></span>

<span data-ttu-id="c22ab-1248">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1248">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7060" />

### <a name="mt7060-merge-entry--does-not-exist"></a><span data-ttu-id="c22ab-1249">MT7060:合併：項目，\*，不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1249">MT7060: Merge: Entry, \*, Does Not Exist.</span></span>

<span data-ttu-id="c22ab-1250">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1250">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7061" />

### <a name="mt7061-merge-error-reading-file-"></a><span data-ttu-id="c22ab-1251">MT7061:合併：讀取檔案時發生錯誤: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1251">MT7061: Merge: Error Reading File: \*.</span></span>

<span data-ttu-id="c22ab-1252">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1252">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7062" />

### <a name="mt7062-set-entry--incorrectly-specified"></a><span data-ttu-id="c22ab-1253">MT7062:設定：項目，\*，正確指定。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1253">MT7062: Set: Entry, \*, Incorrectly Specified.</span></span>

<span data-ttu-id="c22ab-1254">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1254">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7063" />

### <a name="mt7063-set-entry--contains-invalid-array-index"></a><span data-ttu-id="c22ab-1255">MT7063:設定：項目，\*，包含無效的陣列索引。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1255">MT7063: Set: Entry, \*, Contains Invalid Array Index.</span></span>

<span data-ttu-id="c22ab-1256">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1256">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7064" />

### <a name="mt7064-set-entry--does-not-exist"></a><span data-ttu-id="c22ab-1257">MT7064:設定：項目，\*，不存在。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1257">MT7064: Set: Entry, \*, Does Not Exist.</span></span>

<span data-ttu-id="c22ab-1258">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1258">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7065" />

### <a name="mt7065-unknown-propertylist-editor-action-"></a><span data-ttu-id="c22ab-1259">MT7065:未知的 PropertyList 編輯器動作: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1259">MT7065: Unknown PropertyList editor action: \*.</span></span>

<span data-ttu-id="c22ab-1260">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1260">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7066" />

### <a name="mt7066-error-loading--"></a><span data-ttu-id="c22ab-1261">MT7066:載入時發生錯誤 ' \*': \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1261">MT7066: Error loading '\*': \*.</span></span>

<span data-ttu-id="c22ab-1262">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1262">*MSBuild task: PropertyListEditorTaskBase*</span></span>

<a name="MT7067" />

### <a name="mt7067-error-saving--"></a><span data-ttu-id="c22ab-1263">MT7067:錯誤節約 ' \*': \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1263">MT7067: Error saving '\*': \*.</span></span>

<span data-ttu-id="c22ab-1264">*MSBuild 工作：PropertyListEditorTaskBase*</span><span class="sxs-lookup"><span data-stu-id="c22ab-1264">*MSBuild task: PropertyListEditorTaskBase*</span></span>

## <a name="mt8xxx-runtime-error-messages"></a><span data-ttu-id="c22ab-1265">MT8xxx:執行階段錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="c22ab-1265">MT8xxx: Runtime error messages</span></span>

<!--
 MT8xxx runtime
  MT800x misc
  -->

<a name="MT8001" />

### <a name="mt8001-version-mismatch-between-the-native-xamarinios-runtime-and-monotouchdll-please-reinstall-xamarinios"></a><span data-ttu-id="c22ab-1266">MT8001:原生的 Xamarin.iOS 執行階段與 monotouch.dll 的版本不符。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1266">MT8001: Version mismatch between the native Xamarin.iOS runtime and monotouch.dll.</span></span> <span data-ttu-id="c22ab-1267">請重新安裝 Xamarin.iOS。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1267">Please reinstall Xamarin.iOS.</span></span>

<a name="MT8002" />

### <a name="mt8002-could-not-find-the-method--in-the-type-"></a><span data-ttu-id="c22ab-1268">MT8002:找不到方法 '\*'中類型'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1268">MT8002: Could not find the method '\*' in the type '\*'.</span></span>

<a name="MT8003" />

### <a name="mt8003-failed-to-find-the-closed-generic-method--on-the-type-"></a><span data-ttu-id="c22ab-1269">MT8003:封閉式泛型方法中找不到 '\*'在類型'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1269">MT8003: Failed to find the closed generic method '\*' on the type '\*'.</span></span>

<a name="MT8004" />

### <a name="mt8004-cannot-create-an-instance-of--for-the-native-object-0x-of-type--because-another-instance-already-exists-for-this-native-object-of-type-"></a><span data-ttu-id="c22ab-1270">MT8004:無法建立的執行個體 \* 的原生物件 0 x \* (類型的 ' \*')，因為另一個執行個體已經存在於此原生的物件 (類型的 \*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1270">MT8004: Cannot create an instance of \* for the native object 0x\* (of type '\*'), because another instance already exists for this native object (of type \*).</span></span>

<a name="MT8005" />

### <a name="mt8005-wrapper-type--is-missing-its-native-objectivec-class-"></a><span data-ttu-id="c22ab-1271">MT8005:包裝函式類型 '\*'遺漏其原生 ObjectiveC 類別'\*'。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1271">MT8005: Wrapper type '\*' is missing its native ObjectiveC class '\*'.</span></span>

<a name="MT8006" />

### <a name="mt8006-failed-to-find-the-selector--on-the-type-"></a><span data-ttu-id="c22ab-1272">MT8006:選取器找不到 '\*'在類型'\*'</span><span class="sxs-lookup"><span data-stu-id="c22ab-1272">MT8006: Failed to find the selector '\*' on the type '\*'</span></span>

<a name="MT8007" />

### <a name="mt8007-cannot-get-the-method-descriptor-for-the-selector--on-the-type--because-the-selector-does-not-correspond-to-a-method"></a><span data-ttu-id="c22ab-1273">MT8007:無法選取器取得方法描述元 '\*'在類型'\*'，因為選取器未對應至方法</span><span class="sxs-lookup"><span data-stu-id="c22ab-1273">MT8007: Cannot get the method descriptor for the selector '\*' on the type '\*', because the selector does not correspond to a method</span></span>

<a name="MT8008" />

### <a name="mt8008-the-loaded-version-of-xamariniosdll-was-compiled-for--bits-while-the-process-is--bits-please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1274">MT8008:Xamarin.iOS.dll 載入的版本所編譯的 \* 位元，而處理程序是 \* 位元。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1274">MT8008: The loaded version of Xamarin.iOS.dll was compiled for \* bits, while the process is \* bits.</span></span> <span data-ttu-id="c22ab-1275">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1275">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1276">這表示有問題發生在建置程序。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1276">This indicates something is wrong in the build process.</span></span> <span data-ttu-id="c22ab-1277">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1277">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8009" />

### <a name="mt8009-unable-to-locate-the-block-to-delegate-conversion-method-for-the-method-s-parameter--please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1278">MT8009:找不到要委派之方法的轉換方法的區塊 *。*'s 參數 # \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1278">MT8009: Unable to locate the block to delegate conversion method for the method *.*'s parameter #\*.</span></span> <span data-ttu-id="c22ab-1279">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1279">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1280">這表示未正確繫結 API。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1280">This indicates an API wasn't bound correctly.</span></span> <span data-ttu-id="c22ab-1281">如果這是 Xamarin 所公開的 API，請提報 bug 中我們 bugzilla ([http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS))，則為第三方繫結，請連絡廠商。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1281">If this is an API exposed by Xamarin, please file a bug in our bugzilla ([http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)), if it's a third-party binding, please contact the vendor.</span></span>

<a name="MT8010" />

### <a name="mt8010-native-type-size-mismatch-between-xamariniosmacdll-and-the-executing-architecture-xamariniosmacdll-was-built-for--bit-while-the-current-process-is--bit"></a><span data-ttu-id="c22ab-1282">MT8010:Xamarin 之間的原生類型大小不符。[iOS |Mac].dll 和執行的架構。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1282">MT8010: Native type size mismatch between Xamarin.[iOS|Mac].dll and the executing architecture.</span></span> <span data-ttu-id="c22ab-1283">Xamarin。[iOS |專為 Mac].dll \*-位元，而目前的處理程序 \* 位元。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1283">Xamarin.[iOS|Mac].dll was built for \*-bit, while the current process is \*-bit.</span></span>

<span data-ttu-id="c22ab-1284">這表示有問題發生在建置程序。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1284">This indicates something is wrong in the build process.</span></span> <span data-ttu-id="c22ab-1285">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1285">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8011" />

### <a name="mt8011-unable-to-locate-the-delegate-to-block-conversion-attribute-delegateproxy-for-the-return-value-for-the-method--please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1286">MT8011:找不到方法的傳回值的區塊轉換屬性 ([DelegateProxy]) 的委派 *。*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1286">MT8011: Unable to locate the delegate to block conversion attribute ([DelegateProxy]) for the return value for the method *.*.</span></span> <span data-ttu-id="c22ab-1287">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1287">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1288">Xamarin.iOS 找不到所需的方法在執行階段 （若要將委派轉換至區塊） 項目。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1288">Xamarin.iOS was unable to locate a required method at runtime (to convert a delegate to a block).</span></span>

<span data-ttu-id="c22ab-1289">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1289">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8012" />

### <a name="mt8012-invalid-delegateproxyattribute-for-the-return-value-for-the-method--delegatetype-is-null-please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1290">MT8012:方法的傳回值的無效 DelegateProxyAttribute *。*:委派是 null。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1290">MT8012: Invalid DelegateProxyAttribute for the return value for the method *.*: DelegateType is null.</span></span> <span data-ttu-id="c22ab-1291">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1291">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1292">討論中方法的 DelegateProxy 屬性無效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1292">The DelegateProxy attribute for the method in question is invalid.</span></span>

<span data-ttu-id="c22ab-1293">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1293">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8013" />

### <a name="mt8013-invalid-delegateproxyattribute-for-the-return-value-for-the-method--delegatetype-2-specifies-a-type-without-a-handler-field-please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1294">MT8013:方法的傳回值的無效 DelegateProxyAttribute *。*:委派 ({2}) 指定沒有 'Handler' 欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1294">MT8013: Invalid DelegateProxyAttribute for the return value for the method *.*: DelegateType ({2}) specifies a type without a 'Handler' field.</span></span> <span data-ttu-id="c22ab-1295">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1295">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1296">討論中方法的 DelegateProxy 屬性無效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1296">The DelegateProxy attribute for the method in question is invalid.</span></span>

<span data-ttu-id="c22ab-1297">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1297">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8014" />

### <a name="mt8014-invalid-delegateproxyattribute-for-the-return-value-for-the-method--the-delegatetypes-2-handler-field-is-null-please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1298">MT8014:方法的傳回值的無效 DelegateProxyAttribute *。*:委派 ({2}) 'Handler' 欄位為 null。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1298">MT8014: Invalid DelegateProxyAttribute for the return value for the method *.*: The DelegateType's ({2}) 'Handler' field is null.</span></span> <span data-ttu-id="c22ab-1299">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1299">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1300">討論中方法的 DelegateProxy 屬性無效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1300">The DelegateProxy attribute for the method in question is invalid.</span></span>

<span data-ttu-id="c22ab-1301">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1301">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8015" />

### <a name="mt8015-invalid-delegateproxyattribute-for-the-return-value-for-the-method--the-delegatetypes-2-handler-field-is-not-a-delegate-its-a--please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1302">MT8015:方法的傳回值的無效 DelegateProxyAttribute *。*:委派 ({2}) 'Handler' 欄位不是委派，它是 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1302">MT8015: Invalid DelegateProxyAttribute for the return value for the method *.*: The DelegateType's ({2}) 'Handler' field is not a delegate, it's a \*.</span></span> <span data-ttu-id="c22ab-1303">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1303">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1304">討論中方法的 DelegateProxy 屬性無效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1304">The DelegateProxy attribute for the method in question is invalid.</span></span>

<span data-ttu-id="c22ab-1305">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1305">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8016" />

### <a name="mt8016-unable-to-convert-delegate-to-block-for-the-return-value-for-the-method--because-the-input-isnt-a-delegate-its-a--please-file-a-bug-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1306">MT8016:無法轉換為封鎖方法的傳回值的委派 *。*，輸入不是委派，因為它是 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1306">MT8016: Unable to convert delegate to block for the return value for the method *.*, because the input isn't a delegate, it's a \*.</span></span> <span data-ttu-id="c22ab-1307">請將 bug 歸檔在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1307">Please file a bug at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1308">討論中方法的 DelegateProxy 屬性無效。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1308">The DelegateProxy attribute for the method in question is invalid.</span></span>

<span data-ttu-id="c22ab-1309">這通常表示 Xamarin.iOS; 中的 bug請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1309">This usually indicates a bug in Xamarin.iOS; please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<!-- 8017 is used by mmp -->

<a name="MT8018" />

### <a name="mt8018-internal-consistency-error-please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1310">MT8018:內部一致性錯誤。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1310">MT8018: Internal consistency error.</span></span> <span data-ttu-id="c22ab-1311">請提出錯誤報告在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1311">Please file a bug report at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1312">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1312">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1313">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1313">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8019" />

### <a name="mt8019-could-not-find-the-assembly--in-the-loaded-assemblies"></a><span data-ttu-id="c22ab-1314">MT8019:找不到組件 \* 中載入的組件。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1314">MT8019: Could not find the assembly \* in the loaded assemblies.</span></span>

<span data-ttu-id="c22ab-1315">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1315">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1316">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1316">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8020" />

### <a name="mt8020-could-not-find-the-module-with-metadatatoken--in-the-assembly-"></a><span data-ttu-id="c22ab-1317">MT8020:找不到與 MetadataToken 模組 \* 組件中 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1317">MT8020: Could not find the module with MetadataToken \* in the assembly \*.</span></span>

<span data-ttu-id="c22ab-1318">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1318">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1319">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1319">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8021" />

### <a name="mt8021-unknown-implicit-token-type-"></a><span data-ttu-id="c22ab-1320">MT8021:未知的隱含語彙基元型別: \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1320">MT8021: Unknown implicit token type: \*.</span></span>

<span data-ttu-id="c22ab-1321">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1321">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1322">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1322">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8022" />

### <a name="mt8022-expected-the-token-reference--to-be-a--but-its-a--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1323">MT8022:預期的語彙基元參考 \* 為 \*，但它是 \*。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1323">MT8022: Expected the token reference \* to be a \*, but it's a \*.</span></span> <span data-ttu-id="c22ab-1324">請提出錯誤報告在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1324">Please file a bug report at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1325">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1325">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1326">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1326">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8023" />

### <a name="mt8023-an-instance-object-is-required-to-construct-a-closed-generic-method-for-the-open-generic-method--token-reference--please-file-a-bug-report-at-httpbugzillaxamarincom"></a><span data-ttu-id="c22ab-1327">MT8023:執行個體物件，才能建構封閉式的泛型方法，在開啟的泛型方法: \* (權杖參考: \*)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1327">MT8023: An instance object is required to construct a closed generic method for the open generic method: \* (token reference: \*).</span></span> <span data-ttu-id="c22ab-1328">請提出錯誤報告在 http://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1328">Please file a bug report at http://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1329">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1329">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1330">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1330">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>

<a name="MT8024" />

### <a name="mt8024-could-not-find-a-valid-extension-type-for-the-smart-enum-smarttype-please-file-a-bug-at-httpsbugzillaxamarincom"></a><span data-ttu-id="c22ab-1331">MT8024:找不到智慧型的列舉 '{smart_type}' 的有效的延伸模組類型。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1331">MT8024: Could not find a valid extension type for the smart enum '{smart_type}'.</span></span> <span data-ttu-id="c22ab-1332">請將 bug 歸檔在 https://bugzilla.xamarin.com。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1332">Please file a bug at https://bugzilla.xamarin.com.</span></span>

<span data-ttu-id="c22ab-1333">這表示在 Xamarin.iOS 中的 bug。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1333">This indicates a bug in Xamarin.iOS.</span></span> <span data-ttu-id="c22ab-1334">請將 bug 歸檔在 [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS)。</span><span class="sxs-lookup"><span data-stu-id="c22ab-1334">Please file a bug at [http://bugzilla.xamarin.com](https://bugzilla.xamarin.com/enter_bug.cgi?product=iOS).</span></span>