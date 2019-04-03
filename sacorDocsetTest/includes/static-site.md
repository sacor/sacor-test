---
ms.openlocfilehash: eced0b220a3e02b25a784acce081841360774d69
ms.sourcegitcommit: 0c819d1def4ad0284725e7019c1b21b7648656c3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58542360"
---
<span data-ttu-id="a2b75-101">Azure Blob Storage は、静的ファイルをホストする際に使用できる、低コストで非常にスケーラブルなサービスです。</span><span class="sxs-lookup"><span data-stu-id="a2b75-101">Azure Blob storage is a low-cost and massively scalable service that can be used to host static files.</span></span> <span data-ttu-id="a2b75-102">このチュートリアルでは、Blob Storage を使用して、構築した Web アプリの静的コンテンツ (HTML、JavaScript、CSS など) を提供します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-102">For this tutorial, you use it to serve static content (for example, HTML, JavaScript, CSS) for the web app that you build.</span></span>

## <a name="create-a-storage-account"></a><span data-ttu-id="a2b75-103">ストレージ アカウントの作成</span><span class="sxs-lookup"><span data-stu-id="a2b75-103">Create a Storage account</span></span>

<span data-ttu-id="a2b75-104">ストレージ アカウントは、テーブル、キュー、ファイル、BLOB (オブジェクト)、および仮想マシン ディスクを格納できる Azure リソースです。</span><span class="sxs-lookup"><span data-stu-id="a2b75-104">A Storage account is an Azure resource that allows you to store tables, queues, files, blobs (objects), and virtual machine disks.</span></span>

1. <span data-ttu-id="a2b75-105">**[Enter focus mode]\(フォーカス モードにする\)** ボタンをクリックして、Cloud Shell (Bash) にログインします。</span><span class="sxs-lookup"><span data-stu-id="a2b75-105">Log in to the Cloud Shell (Bash), by selecting the **Enter focus mode** button.</span></span> <span data-ttu-id="a2b75-106">このボタンは、ブラウザー ウィンドウサイズに応じて、ページの右上または下部に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2b75-106">This button is at the top right or the bottom of the page, depending on how wide your browser window is.</span></span> <span data-ttu-id="a2b75-107">フォーカス モードでは、ブラウザー ウィンドウの右側に Cloud Shell ウィンドウがドッキングされるので、このチュートリアルで示すコマンドを簡単に実行できます。</span><span class="sxs-lookup"><span data-stu-id="a2b75-107">Focus mode docks a Cloud Shell window on the right side of your browser window, so you can easily execute commands that are shown in the tutorial.</span></span>

2. <span data-ttu-id="a2b75-108">Azure では、リソース グループは、管理を容易にするために関連する Azure リソースをまとめるコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="a2b75-108">In Azure, a Resource Group is a container that holds related Azure resources for ease of management.</span></span> <span data-ttu-id="a2b75-109">**first-serverless-app** という名前の新しいリソース グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-109">Create a new resource group named **first-serverless-app**.</span></span>

    ```azurecli
    az group create -n first-serverless-app -l westcentralus
    ```

3. <span data-ttu-id="a2b75-110">このチュートリアルの静的コンテンツ (HTML、CSS、および JavaScript ファイル) は Blob Storage でホストされます。</span><span class="sxs-lookup"><span data-stu-id="a2b75-110">The static content (HTML, CSS, and JavaScript files) for this tutorial is hosted in Blob Storage.</span></span> <span data-ttu-id="a2b75-111">Blob Storage にはストレージ アカウントが必要です。</span><span class="sxs-lookup"><span data-stu-id="a2b75-111">Blob Storage requires a Storage account.</span></span> <span data-ttu-id="a2b75-112">リソース グループにストレージ アカウント (汎用 V2) を作成します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-112">Create a Storage account (general purpose V2) in the resource group.</span></span> <span data-ttu-id="a2b75-113">`<storage account name>` を一意の名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a2b75-113">Replace `<storage account name>` with a unique name.</span></span>

    ```azurecli
    az storage account create -n <storage account name> -g first-serverless-app --kind StorageV2 -l westcentralus --https-only true --sku Standard_LRS
    ```

4. <span data-ttu-id="a2b75-114">[Azure portal](https://portal.azure.com) の上部にある検索バーを使用して、先ほど作成したストレージ アカウントを検索し、開きます。</span><span class="sxs-lookup"><span data-stu-id="a2b75-114">Using the Search bar at the top of the [Azure portal](https://portal.azure.com), find the storage account you just created and open it.</span></span>

5. <span data-ttu-id="a2b75-115">左側のナビゲーションで、**[静的な Web サイト (プレビュー)]** を選択し、静的な Web サイトを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a2b75-115">On the left navigation, select **Static website (preview)** to configure a container for static website hosting.</span></span>
   - <span data-ttu-id="a2b75-116">**[有効]** を選択して、静的な Web サイトを有効にします。</span><span class="sxs-lookup"><span data-stu-id="a2b75-116">Select **Enabled** to enable static website.</span></span>
   - <span data-ttu-id="a2b75-117">インデックス ドキュメント名に「*index.html*」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-117">Enter *index.html* as the index document name.</span></span> <span data-ttu-id="a2b75-118">このフィールドには、グレースケールフォントで *index.html* が既に入力されていますが、これはサンプル テキストに過ぎません。フィールドに値を入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2b75-118">The field already has *index.html* in a gray font but this is only example text; you still have to enter that value in the field.</span></span>
   - <span data-ttu-id="a2b75-119">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2b75-119">Click **Save**.</span></span>
    
     ![静的な Web サイトの設定を入力する](media/functions-first-serverless-web-app/1-storage-static-website.png)

6. <span data-ttu-id="a2b75-121">このチュートリアルの作業中に簡単にコピーできる場所に**プライマリ エンドポイント**を保存します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-121">Save the **Primary Endpoint** somewhere you can conveniently copy it from while working through the tutorial.</span></span> <span data-ttu-id="a2b75-122">これは作成する Web アプリケーションの URL です。</span><span class="sxs-lookup"><span data-stu-id="a2b75-122">This is the URL of your web application.</span></span>

## <a name="upload-the-web-application"></a><span data-ttu-id="a2b75-123">Web アプリケーションをアップロードする</span><span class="sxs-lookup"><span data-stu-id="a2b75-123">Upload the web application</span></span>

1. <span data-ttu-id="a2b75-124">このチュートリアルで構築するアプリケーションのソース ファイルは、[GitHub リポジトリ](https://github.com/Azure-Samples/functions-first-serverless-web-application)にあります。</span><span class="sxs-lookup"><span data-stu-id="a2b75-124">The source files for the application that you build in this tutorial are located in a [GitHub repository](https://github.com/Azure-Samples/functions-first-serverless-web-application).</span></span> <span data-ttu-id="a2b75-125">Cloud Shell のホーム ディレクトリから、このリポジトリをクローンします。</span><span class="sxs-lookup"><span data-stu-id="a2b75-125">Make sure that you are in your home directory in Cloud Shell and clone this repository.</span></span>

    ```azurecli
    cd ~
    git clone https://github.com/Azure-Samples/functions-first-serverless-web-application
    ```

    <span data-ttu-id="a2b75-126">リポジトリは `/home/<username>/functions-first-serverless-web-application` にクローンされます。</span><span class="sxs-lookup"><span data-stu-id="a2b75-126">The repository is cloned to `/home/<username>/functions-first-serverless-web-application`.</span></span>

1. <span data-ttu-id="a2b75-127">クライアント側の Web アプリケーションは **www** フォルダーにあり、 JavaScript の Vue.js フレームワークを使用して構築されています。</span><span class="sxs-lookup"><span data-stu-id="a2b75-127">The client-side web application is located in the **www** folder and is built using the Vue.js JavaScript framework.</span></span> <span data-ttu-id="a2b75-128">このフォルダーに移動し、 npm コマンドを実行してアプリケーションの依存関係をインストールし、アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="a2b75-128">Change into the folder and run npm commands to install the application's dependencies and build the application.</span></span> <span data-ttu-id="a2b75-129">最後のコマンドは、完了に数分かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="a2b75-129">The last of these commands might take several minutes to complete.</span></span>

    ```azurecli
    cd ~/functions-first-serverless-web-application/www
    npm install
    npm run generate
    ```

    <span data-ttu-id="a2b75-130">アプリケーションが **dist** フォルダーに生成されます。</span><span class="sxs-lookup"><span data-stu-id="a2b75-130">The application is generated in the **dist** folder.</span></span>

1. <span data-ttu-id="a2b75-131">カレントディレクトリを **dist** に変更し、アプリケーションを **$web** Blob コンテナーにアップロードします。</span><span class="sxs-lookup"><span data-stu-id="a2b75-131">Change the current directory to **dist** and upload the application to the **$web** Blob container.</span></span>

    ```azurecli
    cd dist
    az storage blob upload-batch -s . -d \$web --account-name <storage account name>
    ```

1. <span data-ttu-id="a2b75-132">Web ブラウザーで Storage の静的 Web サイトのプライマリ エンドポイント URL を開き、アプリケーションを表示します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-132">Open the Storage static websites primary endpoint URL in a web browser to view the application.</span></span>

    ![最初のサーバーレス Web アプリのホーム ページ](media/functions-first-serverless-web-app/1-app-screenshot-new.png)


## <a name="summary"></a><span data-ttu-id="a2b75-134">まとめ</span><span class="sxs-lookup"><span data-stu-id="a2b75-134">Summary</span></span>

<span data-ttu-id="a2b75-135">本章では、ストレージ アカウントを含む **first-serverless-app** という名前のリソース グループを作成しました。</span><span class="sxs-lookup"><span data-stu-id="a2b75-135">In this module, you created a resource group named **first-serverless-app** containing a Storage account.</span></span> <span data-ttu-id="a2b75-136">ストレージ アカウント内の **$web** という名前の Blob コンテナーでは、 Web アプリケーションの静的コンテンツを格納し、コンテンツを公開します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-136">A blob container named **$web** in the Storage account stores the static content for your web application and makes the content available publicly.</span></span> <span data-ttu-id="a2b75-137">次に、サーバレスである Azure Functions を使用し、この Web アプリケーションから Blob Storage に画像をアップロードする方法を学習します。</span><span class="sxs-lookup"><span data-stu-id="a2b75-137">Next, you learn how to use a serverless function to upload images to Blob storage from this web application.</span></span>