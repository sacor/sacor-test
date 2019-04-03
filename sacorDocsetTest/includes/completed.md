---
title: インクルード ファイル
description: インクルード ファイル
services: functions
author: ggailey777
manager: jeconnoc
ms.service: multiple
ms.topic: include
ms.date: 06/25/2018
ms.author: glenga
ms.custom: include file
ms.openlocfilehash: a66fcc3a406c79fcf9881ddaaaf8330f5b373043
ms.sourcegitcommit: cafe4aa5c3a492cb85519411dc080b8e618d72d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/06/2018
ms.locfileid: "54141558"
---
<span data-ttu-id="d1eda-103">Azure サービスを使用して、多彩な機能を備えたサーバーレス アプリケーションを作成できました。</span><span class="sxs-lookup"><span data-stu-id="d1eda-103">You've successfully created a full-featured, serverless application using Azure services.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="d1eda-104">リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="d1eda-104">Clean up resources</span></span>

<span data-ttu-id="d1eda-105">このアプリケーションの作業が完了したら、次のコマンドを使用して、このチュートリアルで作成したすべてのリソースを削除できます。</span><span class="sxs-lookup"><span data-stu-id="d1eda-105">When you are done working with this application, you can use the following command to delete all resources created during the tutorial:</span></span>

```azurecli
az group delete --name first-serverless-app
```

<span data-ttu-id="d1eda-106">確認を求められたら `y` と入力します。</span><span class="sxs-lookup"><span data-stu-id="d1eda-106">Type `y` when prompted.</span></span>  

## <a name="next-steps"></a><span data-ttu-id="d1eda-107">次の手順</span><span class="sxs-lookup"><span data-stu-id="d1eda-107">Next steps</span></span>

<span data-ttu-id="d1eda-108">このチュートリアルでは、以下の内容を学習しました。</span><span class="sxs-lookup"><span data-stu-id="d1eda-108">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="d1eda-109">静的な Web サイトとアップロードされた画像がホストされるように Azure Blob Storage を構成する。</span><span class="sxs-lookup"><span data-stu-id="d1eda-109">Configure Azure Blob storage to host a static website and uploaded images.</span></span>
> * <span data-ttu-id="d1eda-110">Azure Functions を使用して、画像を Azure Blob Storage にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="d1eda-110">Upload images to Azure Blob storage using Azure Functions.</span></span>
> * <span data-ttu-id="d1eda-111">Azure Functions を使用して、画像のサイズを変更します。</span><span class="sxs-lookup"><span data-stu-id="d1eda-111">Resize images using Azure Functions.</span></span>
> * <span data-ttu-id="d1eda-112">画像のメタデータを Azure Cosmos DB に格納します。</span><span class="sxs-lookup"><span data-stu-id="d1eda-112">Store image metadata in Azure Cosmos DB.</span></span>
> * <span data-ttu-id="d1eda-113">Cognitive Services Vision API を使用して、画像のキャプションを自動生成します。</span><span class="sxs-lookup"><span data-stu-id="d1eda-113">Use Cognitive Services Vision API to auto-generate image captions.</span></span>
> * <span data-ttu-id="d1eda-114">Azure Active Directory を使用してユーザーを認証することにより、Web アプリをセキュリティで保護する。</span><span class="sxs-lookup"><span data-stu-id="d1eda-114">Use Azure Active Directory to secure the web app by authenticating users.</span></span>

<span data-ttu-id="d1eda-115">さらに多くのサービスを関数に接続する方法については、Logic Apps のチュートリアルに進んでください。</span><span class="sxs-lookup"><span data-stu-id="d1eda-115">To learn how to connect even more services to Functions, continue to the Logic Apps tutorial.</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="d1eda-116">Functions と Logic Apps</span><span class="sxs-lookup"><span data-stu-id="d1eda-116">Functions with Logic Apps</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-twitter-email)