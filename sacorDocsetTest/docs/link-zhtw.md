---
title: 使用 Node.js 建立 Vue.js 應用程式
description: 您可以使用 Vue.js 架構在 Visual Studio 中建立 Node.js 應用程式
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: a4b912f523be0380858d639dbf43a4c53bc358c6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947019"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a><span data-ttu-id="fd710-103">使用適用於 Visual Studio 的 Node.js 工具建立 Vue.js 應用程式</span><span class="sxs-lookup"><span data-stu-id="fd710-103">Create a Vue.js application using Node.js Tools for Visual Studio</span></span>

<span data-ttu-id="fd710-104">Visual Studio 2017 包含改善的 [Vue.js](https://vuejs.org/) 架構支援，該架構可在使用 Vue.js、JavaScript 和 TypeScript 建立應用程式時改善開發體驗。</span><span class="sxs-lookup"><span data-stu-id="fd710-104">Visual Studio 2017 includes improved support for the [Vue.js](https://vuejs.org/) framework, which improves the development experience when creating an application with Vue.js, JavaScript and TypeScript.</span></span>

<span data-ttu-id="fd710-105">下列新功能支援 Visual Studio 中的 Vue.js 應用程式開發：</span><span class="sxs-lookup"><span data-stu-id="fd710-105">The following new features support Vue.js application development in Visual Studio:</span></span>

* <span data-ttu-id="fd710-106">支援 *.vue* 檔案中的指令碼、樣式和範本區塊</span><span class="sxs-lookup"><span data-stu-id="fd710-106">Support for Script, Style, and Template blocks in *.vue* files</span></span>
* <span data-ttu-id="fd710-107">辨識 *.vue* 檔案上的 `lang` 屬性</span><span class="sxs-lookup"><span data-stu-id="fd710-107">Recognition of the `lang` attribute on *.vue* files</span></span>
* <span data-ttu-id="fd710-108">Vue.js 專案和檔案範本</span><span class="sxs-lookup"><span data-stu-id="fd710-108">Vue.js project and file templates</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd710-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="fd710-109">Prerequisites</span></span>

* <span data-ttu-id="fd710-110">您必須安裝 Visual Studio 2017 15.8 版 Preview 3 和 **Node.js 開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="fd710-110">You must have Visual Studio 2017 version 15.8 Preview 3 or later installed and the **Node.js development** workload.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="fd710-111">本文需要的功能是從 Visual Studio 2017 15.8 版 Preview 3 開始提供。</span><span class="sxs-lookup"><span data-stu-id="fd710-111">This article requires features that are only available starting in Visual Studio 2017 version 15.8 Preview 3.</span></span>

    <span data-ttu-id="fd710-112">如果您尚未安裝 Visual Studio，請前往  [Visual Studio 下載](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) 頁面免費進行安裝。</span><span class="sxs-lookup"><span data-stu-id="fd710-112">If you haven't already installed Visual Studio, go to the [Visual Studio downloads](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) page to install it for free.</span></span>

    <span data-ttu-id="fd710-113">如果您需要安裝工作負載，但已擁有 Visual Studio，請在 [新增專案] 對話方塊 (選取 [檔案] > [新增] > [專案]) 的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。</span><span class="sxs-lookup"><span data-stu-id="fd710-113">If you need to install the workload but already have Visual Studio, click the **Open Visual Studio Installer** link in the left pane of the **New Project** dialog box (select **File** > **New** > **Project**).</span></span> <span data-ttu-id="fd710-114">Visual Studio 安裝程式即會啟動。</span><span class="sxs-lookup"><span data-stu-id="fd710-114">The Visual Studio Installer launches.</span></span> <span data-ttu-id="fd710-115">選擇 [Node.js 開發] 工作負載，然後選擇 [修改]。</span><span class="sxs-lookup"><span data-stu-id="fd710-115">Choose the **Node.js development** workload, then choose **Modify**.</span></span>

* <span data-ttu-id="fd710-116">若要建立 ASP.NET Core 專案，您必須安裝 ASP.NET 與網頁程式開發工作負載，以及 .NET Core 跨平台開發工作負載。</span><span class="sxs-lookup"><span data-stu-id="fd710-116">To create the ASP.NET Core project, you must have the ASP.NET and web development and .NET Core cross-platform development workloads installed.</span></span>

* <span data-ttu-id="fd710-117">您必須安裝 Node.js 執行階段。</span><span class="sxs-lookup"><span data-stu-id="fd710-117">You must have the Node.js runtime installed.</span></span>

    <span data-ttu-id="fd710-118">如果您沒有安裝，請從 [Node.js](https://nodejs.org/en/download/) 網站安裝 LTS 版本。</span><span class="sxs-lookup"><span data-stu-id="fd710-118">If you don't have it installed, install the LTS version from the [Node.js](https://nodejs.org/en/download/) website.</span></span> <span data-ttu-id="fd710-119">一般而言，Visual Studio 會自動偵測已安裝的 Node.js 執行階段。</span><span class="sxs-lookup"><span data-stu-id="fd710-119">In general, Visual Studio automatically detects the installed Node.js runtime.</span></span> <span data-ttu-id="fd710-120">如果它沒有偵測到已安裝的執行階段，您可以將專案設定為參考屬性頁面中已安裝的執行階段。</span><span class="sxs-lookup"><span data-stu-id="fd710-120">If it does not detect an installed runtime, you can configure your project to reference the installed runtime in the properties page.</span></span> <span data-ttu-id="fd710-121">(建立專案之後，請以滑鼠右鍵按一下專案節點，然後選擇 [屬性])。</span><span class="sxs-lookup"><span data-stu-id="fd710-121">(After you create a project, right-click the project node and choose **Properties**).</span></span>

## <a name="create-a-vuejs-project-using-a-template"></a><span data-ttu-id="fd710-122">使用範本建立 Vue.js 專案</span><span class="sxs-lookup"><span data-stu-id="fd710-122">Create a Vue.js project using a template</span></span>

<span data-ttu-id="fd710-123">您可以使用新的 Vue.js 範本來建立新專案。</span><span class="sxs-lookup"><span data-stu-id="fd710-123">You can use the new Vue.js templates to create a new project.</span></span> <span data-ttu-id="fd710-124">使用範本是最簡單的使用者入門方式。</span><span class="sxs-lookup"><span data-stu-id="fd710-124">Use of the template is the easiest way to get started.</span></span> <span data-ttu-id="fd710-125">如需詳細步驟，請參閱[使用 Visual Studio 建立您的第一個 Vue.js 應用程式](../javascript/quickstart-vuejs-with-nodejs.md)。</span><span class="sxs-lookup"><span data-stu-id="fd710-125">For detailed steps, see [Use Visual Studio to create your first Vue.js app](../javascript/quickstart-vuejs-with-nodejs.md).</span></span>

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a><span data-ttu-id="fd710-126">使用 ASP.NET Core 和 Vue CLI 建立 Vue.js 專案</span><span class="sxs-lookup"><span data-stu-id="fd710-126">Create a Vue.js project with ASP.NET Core and the Vue CLI</span></span>

<span data-ttu-id="fd710-127">Vue.js 提供正式的 CLI 以快速 Scaffolding 專案。</span><span class="sxs-lookup"><span data-stu-id="fd710-127">Vue.js provides an official CLI for quickly scaffolding projects.</span></span> <span data-ttu-id="fd710-128">如果您想要使用 CLI 來建立應用程式，請遵循本文中的步驟以設定您的開發環境。</span><span class="sxs-lookup"><span data-stu-id="fd710-128">If you would like to use the CLI to create your application, follow the steps in this article to set up your development environment.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fd710-129">這些步驟假設您已經有一些使用 Vue.js 架構的體驗。</span><span class="sxs-lookup"><span data-stu-id="fd710-129">These steps assume that you already have some experience with the Vue.js framework.</span></span> <span data-ttu-id="fd710-130">如果沒有，請瀏覽 [Vue.js](https://vuejs.org/) 以深入了解此架構。</span><span class="sxs-lookup"><span data-stu-id="fd710-130">If not, please visit [Vue.js](https://vuejs.org/) to learn more about the framework.</span></span>

### <a name="create-a-new-aspnet-core-project"></a><span data-ttu-id="fd710-131">建立新的 ASP.NET Core 專案</span><span class="sxs-lookup"><span data-stu-id="fd710-131">Create a new ASP.NET Core project</span></span>

<span data-ttu-id="fd710-132">在此範例中，請使用空白的 ASP.NET Core 應用程式 (C#)。</span><span class="sxs-lookup"><span data-stu-id="fd710-132">For this example, you use an empty ASP.NET Core Application (C#).</span></span> <span data-ttu-id="fd710-133">不過，您可以從各種專案和程式設計語言中進行選擇。</span><span class="sxs-lookup"><span data-stu-id="fd710-133">However, you can choose from a variety of projects and programming languages.</span></span>

#### <a name="create-an-empty-project"></a><span data-ttu-id="fd710-134">建立空白專案</span><span class="sxs-lookup"><span data-stu-id="fd710-134">Create an Empty project</span></span>

1. <span data-ttu-id="fd710-135">開啟 Visual Studio，然後從主功能表選擇 [檔案] > [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="fd710-135">Open Visual Studio and choose **File** > **New** > **Project** from the main menu.</span></span>

1. <span data-ttu-id="fd710-136">在 [Visual C#] > [Web] 底下，選擇 [ASP.NET Core Web 應用程式]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="fd710-136">Under **Visual C#** > **Web**, choose **ASP.NET Core Web Application**, and then click **OK**.</span></span>

    <span data-ttu-id="fd710-137">如果您看不到 [ASP.NET Core Web 應用程式] 專案範本，則必須先安裝 **ASP.NET 與網頁程式開發** 工作負載和 **.NET Core** 程式開發工作負載。</span><span class="sxs-lookup"><span data-stu-id="fd710-137">If you don't see the **ASP.NET Core Web Application** project template, you must install the **ASP.NET and web development** workload and the .**NET Core** development workload first.</span></span> <span data-ttu-id="fd710-138">若要安裝工作負載，請在 [新增專案] 對話方塊 (選取 [檔案] > [新增] > [專案]) 的左窗格中，按一下 [開啟 Visual Studio 安裝程式]。</span><span class="sxs-lookup"><span data-stu-id="fd710-138">To install the workload(s), click the **Open Visual Studio Installer** link in the left pane of the **New Project** dialog box (select **File** > **New** > **Project**).</span></span> <span data-ttu-id="fd710-139">Visual Studio 安裝程式即會啟動。</span><span class="sxs-lookup"><span data-stu-id="fd710-139">The Visual Studio Installer launches.</span></span> <span data-ttu-id="fd710-140">選取所需的工作負載。</span><span class="sxs-lookup"><span data-stu-id="fd710-140">Select the required workloads.</span></span>

1. <span data-ttu-id="fd710-141">選取 [空白]，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="fd710-141">Select **Empty**, and then click **OK**.</span></span>

    <span data-ttu-id="fd710-142">Visual Studio 隨即建立專案，而專案會在 [方案總管] (右窗格) 中開啟。</span><span class="sxs-lookup"><span data-stu-id="fd710-142">Visual Studio creates the project, which opens in Solution Explorer (right pane).</span></span>

#### <a name="configure-the-project-startup-file"></a><span data-ttu-id="fd710-143">設定專案啟動檔案</span><span class="sxs-lookup"><span data-stu-id="fd710-143">Configure the project startup file</span></span>

* <span data-ttu-id="fd710-144">開啟檔案 *./Startup.cs*，並將下列幾行新增至 Configure 方法：</span><span class="sxs-lookup"><span data-stu-id="fd710-144">Open the file *./Startup.cs*, and add the following lines to the Configure method:</span></span>

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a><span data-ttu-id="fd710-145">安裝 vue CLI</span><span class="sxs-lookup"><span data-stu-id="fd710-145">Install the vue CLI</span></span>

<span data-ttu-id="fd710-146">若要安裝 vue-cli npm 模組，請開啟命令提示字元，並鍵入 `npm install --g vue-cli` 或 `npm install -g @vue/cli` (適用於 3.0 版，其目前處於搶鮮版 (Beta) 階段)。</span><span class="sxs-lookup"><span data-stu-id="fd710-146">To install the vue-cli npm module, open a command prompt and type `npm install --g vue-cli` or `npm install -g @vue/cli` for version 3.0 (currently in beta).</span></span>

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a><span data-ttu-id="fd710-147">使用 vue CLI 來 Scaffold 新的用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="fd710-147">Scaffold a new client application using the vue CLI</span></span>

1. <span data-ttu-id="fd710-148">移至命令提示字元，並將目前的目錄變更為專案根資料夾。</span><span class="sxs-lookup"><span data-stu-id="fd710-148">Go to your command prompt and change the current directory to your project root folder.</span></span>

1. <span data-ttu-id="fd710-149">鍵入 `vue init webpack ClientApp`，並在系統提示您回答其他問題時遵循步驟。</span><span class="sxs-lookup"><span data-stu-id="fd710-149">Type `vue init webpack ClientApp` and follow steps when prompted to answer additional questions.</span></span>

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a><span data-ttu-id="fd710-150">修改 Webpack 組態以將建置的檔案輸出至 wwwroot</span><span class="sxs-lookup"><span data-stu-id="fd710-150">Modify the webpack configuration to output the built files to wwwroot</span></span>

* <span data-ttu-id="fd710-151">開啟檔案 *./ClientApp/config/index.js*，並將 `build.index` 和 `build.assetsRoot` 變更為 wwwroot 路徑：</span><span class="sxs-lookup"><span data-stu-id="fd710-151">Open the file *./ClientApp/config/index.js*, and change the `build.index` and `build.assetsRoot` to wwwroot path:</span></span>

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a><span data-ttu-id="fd710-152">表示專案會在每次觸發組建時建置 ClientApp</span><span class="sxs-lookup"><span data-stu-id="fd710-152">Indicate the project to build the ClientApp each time that a build is triggered</span></span>

1. <span data-ttu-id="fd710-153">在 Visual Studio 中，移至 [專案] > [屬性] > [建置事件]。</span><span class="sxs-lookup"><span data-stu-id="fd710-153">In Visual Studio, go to **Project** > **Properties** > **Build Events**.</span></span>

1. <span data-ttu-id="fd710-154">在 [建置前事件命令列] 上鍵入 `npm --prefix ./ClientApp run build`。</span><span class="sxs-lookup"><span data-stu-id="fd710-154">On **Pre-build event command line**, type `npm --prefix ./ClientApp run build`.</span></span>

#### <a name="configure-webpacks-output-module-names"></a><span data-ttu-id="fd710-155">設定 Webpack 的輸出模組名稱</span><span class="sxs-lookup"><span data-stu-id="fd710-155">Configure webpack's output module names</span></span>

* <span data-ttu-id="fd710-156">開啟檔案 *./ClientApp/build/webpack.base.conf.js*，並將下列屬性新增至 output 屬性：</span><span class="sxs-lookup"><span data-stu-id="fd710-156">Open the file *./ClientApp/build/webpack.base.conf.js*, and add the following properties to the output property:</span></span>

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a><span data-ttu-id="fd710-157">使用 Vue CLI 新增 TypeScript 支援</span><span class="sxs-lookup"><span data-stu-id="fd710-157">Add TypeScript support with the Vue CLI</span></span>

<span data-ttu-id="fd710-158">這些步驟需要 vue-cli 3.0，它目前仍處於搶鮮版 (Beta) 階段。</span><span class="sxs-lookup"><span data-stu-id="fd710-158">These steps require vue-cli 3.0, which is currently in beta.</span></span>

1. <span data-ttu-id="fd710-159">移至命令提示字元，並將目前的目錄變更為專案根資料夾。</span><span class="sxs-lookup"><span data-stu-id="fd710-159">Go to your command prompt and change the current directory to the project root folder.</span></span>

1. <span data-ttu-id="fd710-160">鍵入 `vue create ClientApp`，然後選擇 [手動選取功能]。</span><span class="sxs-lookup"><span data-stu-id="fd710-160">Type `vue create ClientApp`, and then choose **Manually select features**.</span></span>

1. <span data-ttu-id="fd710-161">選擇 [Typescript]，然後選取其他所需的選項。</span><span class="sxs-lookup"><span data-stu-id="fd710-161">Choose **Typescript**, and then select other desired options.</span></span>

1. <span data-ttu-id="fd710-162">遵循其餘的步驟並回應問題。</span><span class="sxs-lookup"><span data-stu-id="fd710-162">Follow the remaining steps and respond to the questions.</span></span>

#### <a name="configure-a-vuejs-project-for-typescript"></a><span data-ttu-id="fd710-163">設定 TypeScript 的 Vue.js 專案</span><span class="sxs-lookup"><span data-stu-id="fd710-163">Configure a Vue.js project for TypeScript</span></span>

1. <span data-ttu-id="fd710-164">開啟檔案 *./ClientApp/tsconfig.json*，並將 `noEmit:true` 新增至編譯器選項。</span><span class="sxs-lookup"><span data-stu-id="fd710-164">Open the file *./ClientApp/tsconfig.json* and add `noEmit:true` to the compiler options.</span></span>

    <span data-ttu-id="fd710-165">藉由設定此選項，您可以避免每次在 Visual Studio 中建置時造成專案雜亂。</span><span class="sxs-lookup"><span data-stu-id="fd710-165">By setting this option, you avoid cluttering your project each time that you build in Visual Studio.</span></span>

1. <span data-ttu-id="fd710-166">接下來，在 *./ClientApp/* 中建立 *vue.config.js* 檔案，並新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="fd710-166">Next, create a *vue.config.js* file in *./ClientApp/* and add the following code.</span></span>

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    <span data-ttu-id="fd710-167">上述程式碼會設定 Webpack，並設定 wwwroot 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fd710-167">The preceding code configures webpack and sets the wwwroot folder.</span></span>

#### <a name="build-with-vue-cli-30"></a><span data-ttu-id="fd710-168">使用 vue-cli 3.0 建置</span><span class="sxs-lookup"><span data-stu-id="fd710-168">Build with vue-cli 3.0</span></span>

<span data-ttu-id="fd710-169">vue-cli 3.0 的未知問題會阻止自動化建置流程。</span><span class="sxs-lookup"><span data-stu-id="fd710-169">An unknown issue with the vue-cli 3.0 prevents automating the build process.</span></span> <span data-ttu-id="fd710-170">每次嘗試重新整理 wwwroot 資料夾時，您都需要在 ClientApp 資料夾上執行命令 `npm run build`。</span><span class="sxs-lookup"><span data-stu-id="fd710-170">Each time that you try to refresh the wwwroot folder, you need to run the command `npm run build` on the ClientApp folder.</span></span>

## <a name="limitations"></a><span data-ttu-id="fd710-171">限制</span><span class="sxs-lookup"><span data-stu-id="fd710-171">Limitations</span></span>

* <span data-ttu-id="fd710-172">`lang` 屬性僅支援 JavaScript 和 TypeScript 語言。</span><span class="sxs-lookup"><span data-stu-id="fd710-172">`lang` attribute only supports JavaScript and TypeScript languages.</span></span> <span data-ttu-id="fd710-173">接受的值包括：js、jsx、ts 和 tsx。</span><span class="sxs-lookup"><span data-stu-id="fd710-173">The accepted values are: js, jsx, ts, and tsx.</span></span>
* <span data-ttu-id="fd710-174">`lang` 屬性不適用於範本或樣式標籤。</span><span class="sxs-lookup"><span data-stu-id="fd710-174">`lang` attribute doesn't work with template or style tags.</span></span>
* <span data-ttu-id="fd710-175">由於其前置處理本質，不支援對 *.vue* 檔案中的指令碼區塊進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="fd710-175">Debugging script blocks in *.vue* files isn't supported due to its preprocessed nature.</span></span>
* <span data-ttu-id="fd710-176">TypeScript 無法將 *.vue* 檔案辨識為模組。</span><span class="sxs-lookup"><span data-stu-id="fd710-176">TypeScript doesn't recognize *.vue* files as modules.</span></span> <span data-ttu-id="fd710-177">您需要包含如下程式碼的檔案，以告知 TypeScript *.vue* 檔案的外觀 (vue-cli 3.0 範本已經包含此檔案)。</span><span class="sxs-lookup"><span data-stu-id="fd710-177">You need a file that contains code such as the following to tell TypeScript what *.vue* files look like (vue-cli 3.0 template already includes this file).</span></span>

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* <span data-ttu-id="fd710-178">使用 vue-cli 3.0 時，執行命令 `npm run build` 作為專案屬性的建置前事件無法運作。</span><span class="sxs-lookup"><span data-stu-id="fd710-178">Running the command `npm run build` as a pre-build event on the project properties doesn't work when using vue-cli 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd710-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd710-179">See also</span></span>

- <span data-ttu-id="fd710-180">https://vuejs.org/v2/guide - Vue 使用者入門指南。</span><span class="sxs-lookup"><span data-stu-id="fd710-180">https://vuejs.org/v2/guide - Vue get started guide.</span></span>
- <span data-ttu-id="fd710-181">https://github.com/vuejs/vue-cli - Vue CLI 專案。</span><span class="sxs-lookup"><span data-stu-id="fd710-181">https://github.com/vuejs/vue-cli - Vue CLI project.</span></span>
- <span data-ttu-id="fd710-182">https://webpack.js.org/configuration/ - Webpack 組態文件。</span><span class="sxs-lookup"><span data-stu-id="fd710-182">https://webpack.js.org/configuration/ - Webpack configuration documentation.</span></span>