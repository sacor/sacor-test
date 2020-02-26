---
title: include file
description: include file
services: storage
author: tamram
ms.service: storage
ms.topic: include
ms.date: 05/06/2019
ms.author: tamram
ms.custom: include file
---

<span data-ttu-id="b8ac8-103">To create a general-purpose v2 storage account in the Azure portal, follow these steps:</span><span class="sxs-lookup"><span data-stu-id="b8ac8-103">To create a general-purpose v2 storage account in the Azure portal, follow these steps:</span></span>

1. <span data-ttu-id="b8ac8-104">On the Azure portal menu, select **All services**.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-104">On the Azure portal menu, select **All services**.</span></span> <span data-ttu-id="b8ac8-105">In the list of resources, type **Storage Accounts**.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-105">In the list of resources, type **Storage Accounts**.</span></span> <span data-ttu-id="b8ac8-106">As you begin typing, the list filters based on your input.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-106">As you begin typing, the list filters based on your input.</span></span> <span data-ttu-id="b8ac8-107">Select **Storage Accounts**.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-107">Select **Storage Accounts**.</span></span>
2. <span data-ttu-id="b8ac8-108">On the **Storage Accounts** window that appears, choose **Add**.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-108">On the **Storage Accounts** window that appears, choose **Add**.</span></span>
3. <span data-ttu-id="b8ac8-109">Select the subscription in which to create the storage account.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-109">Select the subscription in which to create the storage account.</span></span>
4. <span data-ttu-id="b8ac8-110">Under the **Resource group** field, select **Create new**.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-110">Under the **Resource group** field, select **Create new**.</span></span> <span data-ttu-id="b8ac8-111">Enter a name for your new resource group, as shown in the following image.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-111">Enter a name for your new resource group, as shown in the following image.</span></span>

    ![Screenshot showing how to create a resource group in the portal](./media/storage-create-account-portal-include/create-resource-group-for-storage.png)

5. <span data-ttu-id="b8ac8-113">Next, enter a name for your storage account.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-113">Next, enter a name for your storage account.</span></span> <span data-ttu-id="b8ac8-114">The name you choose must be unique across Azure.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-114">The name you choose must be unique across Azure.</span></span> <span data-ttu-id="b8ac8-115">The name also must be between 3 and 24 characters in length, and can include numbers and lowercase letters only.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-115">The name also must be between 3 and 24 characters in length, and can include numbers and lowercase letters only.</span></span>
6. <span data-ttu-id="b8ac8-116">Select a location for your storage account, or use the default location.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-116">Select a location for your storage account, or use the default location.</span></span>
7. <span data-ttu-id="b8ac8-117">Leave these fields set to their default values:</span><span class="sxs-lookup"><span data-stu-id="b8ac8-117">Leave these fields set to their default values:</span></span>

   |<span data-ttu-id="b8ac8-118">Field</span><span class="sxs-lookup"><span data-stu-id="b8ac8-118">Field</span></span>  |<span data-ttu-id="b8ac8-119">Value</span><span class="sxs-lookup"><span data-stu-id="b8ac8-119">Value</span></span>  |
   |---------|---------|
   |<span data-ttu-id="b8ac8-120">Deployment model</span><span class="sxs-lookup"><span data-stu-id="b8ac8-120">Deployment model</span></span>     |<span data-ttu-id="b8ac8-121">Resource Manager</span><span class="sxs-lookup"><span data-stu-id="b8ac8-121">Resource Manager</span></span>         |
   |<span data-ttu-id="b8ac8-122">Performance</span><span class="sxs-lookup"><span data-stu-id="b8ac8-122">Performance</span></span>     |<span data-ttu-id="b8ac8-123">Standard</span><span class="sxs-lookup"><span data-stu-id="b8ac8-123">Standard</span></span>         |
   |<span data-ttu-id="b8ac8-124">Account kind</span><span class="sxs-lookup"><span data-stu-id="b8ac8-124">Account kind</span></span>     |<span data-ttu-id="b8ac8-125">StorageV2 (general-purpose v2)</span><span class="sxs-lookup"><span data-stu-id="b8ac8-125">StorageV2 (general-purpose v2)</span></span>         |
   |<span data-ttu-id="b8ac8-126">Replication</span><span class="sxs-lookup"><span data-stu-id="b8ac8-126">Replication</span></span>     |<span data-ttu-id="b8ac8-127">Read-access geo-redundant storage (RA-GRS)</span><span class="sxs-lookup"><span data-stu-id="b8ac8-127">Read-access geo-redundant storage (RA-GRS)</span></span>         |
   |<span data-ttu-id="b8ac8-128">Access tier</span><span class="sxs-lookup"><span data-stu-id="b8ac8-128">Access tier</span></span>     |<span data-ttu-id="b8ac8-129">Hot</span><span class="sxs-lookup"><span data-stu-id="b8ac8-129">Hot</span></span>         |

8. <span data-ttu-id="b8ac8-130">If you plan to use [Azure Data Lake Storage](https://azure.microsoft.com/services/storage/data-lake-storage/), choose the **Advanced** tab, and then set **Hierarchical namespace** to **Enabled**.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-130">If you plan to use [Azure Data Lake Storage](https://azure.microsoft.com/services/storage/data-lake-storage/), choose the **Advanced** tab, and then set **Hierarchical namespace** to **Enabled**.</span></span>
9. <span data-ttu-id="b8ac8-131">Select **Review + Create** to review your storage account settings and create the account.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-131">Select **Review + Create** to review your storage account settings and create the account.</span></span>
10. <span data-ttu-id="b8ac8-132">Select **Create**.</span><span class="sxs-lookup"><span data-stu-id="b8ac8-132">Select **Create**.</span></span>

<span data-ttu-id="b8ac8-133">For more information about types of storage accounts and other storage account settings, see [Azure storage account overview](https://docs.microsoft.com/azure/storage/common/storage-account-overview).</span><span class="sxs-lookup"><span data-stu-id="b8ac8-133">For more information about types of storage accounts and other storage account settings, see [Azure storage account overview](https://docs.microsoft.com/azure/storage/common/storage-account-overview).</span></span> <span data-ttu-id="b8ac8-134">For more information on resource groups, see [Azure Resource Manager overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span><span class="sxs-lookup"><span data-stu-id="b8ac8-134">For more information on resource groups, see [Azure Resource Manager overview](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).</span></span> 