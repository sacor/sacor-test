---
title: 'Samouczek: Wykonywanie operacji ETL za pomocą usługi Azure Databricks'
description: 'Dowiedz się, jak wyodrębniać dane z usługi Data Lake Storage Gen2 do usługi Azure Databricks, przekształcać je, a następnie załadować do usługi Azure SQL Data Warehouse.'
author: mamccrea
ms.author: mamccrea
ms.reviewer: jasonh
ms.service: azure-databricks
ms.custom: mvc
ms.topic: tutorial
ms.date: 05/17/2019
ms.openlocfilehash: a6a681ace95f9bab3c77e4a0f9982a2281c778b8
ms.sourcegitcommit: e9a46b4d22113655181a3e219d16397367e8492d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: '65966432'
---
# <a name="tutorial-extract-transform-and-load-data-by-using-azure-databricks"></a><span data-ttu-id="6af7b-103">Samouczek: Wyodrębnianie, przekształcanie i ładowanie danych przy użyciu usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-103">Samouczek: Wyodrębnianie, przekształcanie i ładowanie danych przy użyciu usługi Azure Databricks</span></span>

<span data-ttu-id="6af7b-104">W ramach tego samouczka wykonasz operację ETL (wyodrębnianie, przekształcanie i ładowanie danych) przy użyciu usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-104">W ramach tego samouczka wykonasz operację ETL (wyodrębnianie, przekształcanie i ładowanie danych) przy użyciu usługi Azure Databricks.</span></span> <span data-ttu-id="6af7b-105">Wyodrębnianie danych z usługi Azure Data Lake Storage Gen2 do usługi Azure Databricks, uruchom przekształcenia na danych w usłudze Azure Databricks i ładowania przekształconych danych Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-105">Wyodrębnianie danych z usługi Azure Data Lake Storage Gen2 do usługi Azure Databricks, uruchom przekształcenia na danych w usłudze Azure Databricks i ładowania przekształconych danych Azure SQL Data Warehouse.</span></span>

<span data-ttu-id="6af7b-106">W procedurach opisanych w tym samouczku do przesyłania danych do usługi Azure Databricks służy łącznik SQL Data Warehouse dla usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-106">W procedurach opisanych w tym samouczku do przesyłania danych do usługi Azure Databricks służy łącznik SQL Data Warehouse dla usługi Azure Databricks.</span></span> <span data-ttu-id="6af7b-107">Ten łącznik z kolei używa usługi Azure Blob Storage jako magazynu tymczasowego dla danych przesyłanych między klastrem usługi Azure Databricks a usługą Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-107">Ten łącznik z kolei używa usługi Azure Blob Storage jako magazynu tymczasowego dla danych przesyłanych między klastrem usługi Azure Databricks a usługą Azure SQL Data Warehouse.</span></span>

<span data-ttu-id="6af7b-108">Poniższa ilustracja przedstawia przepływ aplikacji:</span><span class="sxs-lookup"><span data-stu-id="6af7b-108">Poniższa ilustracja przedstawia przepływ aplikacji:</span></span>

<span data-ttu-id="6af7b-109">![Usługa Azure Databricks z usługami Data Lake Store i SQL Data Warehouse](./media/databricks-extract-load-sql-data-warehouse/databricks-extract-transform-load-sql-datawarehouse.png "Usługa Azure Databricks z usługami Data Lake Store i SQL Data Warehouse")</span><span class="sxs-lookup"><span data-stu-id="6af7b-109">![Usługa Azure Databricks z usługami Data Lake Store i SQL Data Warehouse](./media/databricks-extract-load-sql-data-warehouse/databricks-extract-transform-load-sql-datawarehouse.png "Usługa Azure Databricks z usługami Data Lake Store i SQL Data Warehouse")</span></span>

<span data-ttu-id="6af7b-110">Ten samouczek obejmuje następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="6af7b-110">Ten samouczek obejmuje następujące zadania:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="6af7b-111">Tworzenie usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-111">Tworzenie usługi Azure Databricks.</span></span>
> * <span data-ttu-id="6af7b-112">Tworzenie klastra Spark w usłudze Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-112">Tworzenie klastra Spark w usłudze Azure Databricks.</span></span>
> * <span data-ttu-id="6af7b-113">Tworzenie systemu plików na koncie usługi Data Lake Storage Gen2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-113">Tworzenie systemu plików na koncie usługi Data Lake Storage Gen2.</span></span>
> * <span data-ttu-id="6af7b-114">Przekazywanie danych przykładowych na konto usługi Azure Data Lake Storage Gen2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-114">Przekazywanie danych przykładowych na konto usługi Azure Data Lake Storage Gen2.</span></span>
> * <span data-ttu-id="6af7b-115">Tworzenie jednostki usługi.</span><span class="sxs-lookup"><span data-stu-id="6af7b-115">Tworzenie jednostki usługi.</span></span>
> * <span data-ttu-id="6af7b-116">Wyodrębnianie danych z konta usługi Azure Data Lake Storage Gen2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-116">Wyodrębnianie danych z konta usługi Azure Data Lake Storage Gen2.</span></span>
> * <span data-ttu-id="6af7b-117">Przekształcanie danych w usłudze Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-117">Przekształcanie danych w usłudze Azure Databricks.</span></span>
> * <span data-ttu-id="6af7b-118">Ładowanie danych do usługi Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-118">Ładowanie danych do usługi Azure SQL Data Warehouse.</span></span>

<span data-ttu-id="6af7b-119">Jeśli nie masz subskrypcji platformy Azure, przed rozpoczęciem utwórz [bezpłatne konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).</span><span class="sxs-lookup"><span data-stu-id="6af7b-119">Jeśli nie masz subskrypcji platformy Azure, przed rozpoczęciem utwórz [bezpłatne konto](https://azure.microsoft.com/free/?WT.mc_id=A261C142F).</span></span>

> [!Note]
> <span data-ttu-id="6af7b-120">W tym samouczku nie może być przeprowadzone przy użyciu **subskrypcji bezpłatnej wersji próbnej platformy Azure**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-120">W tym samouczku nie może być przeprowadzone przy użyciu **subskrypcji bezpłatnej wersji próbnej platformy Azure**.</span></span>
> <span data-ttu-id="6af7b-121">Aby użyć bezpłatnego konta do utworzenia klastra usługi Azure Databricks, przed utworzeniem klastra przejdź do swojego profilu i zmień swoją subskrypcję na **płatność zgodnie z rzeczywistym użyciem**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-121">Aby użyć bezpłatnego konta do utworzenia klastra usługi Azure Databricks, przed utworzeniem klastra przejdź do swojego profilu i zmień swoją subskrypcję na **płatność zgodnie z rzeczywistym użyciem**.</span></span> <span data-ttu-id="6af7b-122">Aby uzyskać więcej informacji, zobacz [Bezpłatne konto platformy Azure](https://azure.microsoft.com/free/).</span><span class="sxs-lookup"><span data-stu-id="6af7b-122">Aby uzyskać więcej informacji, zobacz [Bezpłatne konto platformy Azure](https://azure.microsoft.com/free/).</span></span>
     
## <a name="prerequisites"></a><span data-ttu-id="6af7b-123">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="6af7b-123">Wymagania wstępne</span></span>

<span data-ttu-id="6af7b-124">Przed rozpoczęciem tego samouczka wykonaj następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="6af7b-124">Przed rozpoczęciem tego samouczka wykonaj następujące zadania:</span></span>

* <span data-ttu-id="6af7b-125">Utwórz magazyn danych Azure SQL Data Warehouse, utwórz regułę zapory na poziomie serwera i nawiąż połączenie z serwerem jako administrator serwera.</span><span class="sxs-lookup"><span data-stu-id="6af7b-125">Utwórz magazyn danych Azure SQL Data Warehouse, utwórz regułę zapory na poziomie serwera i nawiąż połączenie z serwerem jako administrator serwera.</span></span> <span data-ttu-id="6af7b-126">Zobacz [Szybki start: Tworzenie i wysyłanie zapytań usługi Azure SQL data warehouse w witrynie Azure portal](../sql-data-warehouse/create-data-warehouse-portal.md).</span><span class="sxs-lookup"><span data-stu-id="6af7b-126">Zobacz [Szybki start: Tworzenie i wysyłanie zapytań usługi Azure SQL data warehouse w witrynie Azure portal](../sql-data-warehouse/create-data-warehouse-portal.md).</span></span>

* <span data-ttu-id="6af7b-127">Utwórz klucz główny bazy danych dla magazynu danych Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-127">Utwórz klucz główny bazy danych dla magazynu danych Azure SQL Data Warehouse.</span></span> <span data-ttu-id="6af7b-128">Zobacz [Tworzenie klucza głównego bazy danych](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-a-database-master-key).</span><span class="sxs-lookup"><span data-stu-id="6af7b-128">Zobacz [Tworzenie klucza głównego bazy danych](https://docs.microsoft.com/sql/relational-databases/security/encryption/create-a-database-master-key).</span></span>

* <span data-ttu-id="6af7b-129">Utwórz konto usługi Azure Blob Storage i zawarty w nim kontener.</span><span class="sxs-lookup"><span data-stu-id="6af7b-129">Utwórz konto usługi Azure Blob Storage i zawarty w nim kontener.</span></span> <span data-ttu-id="6af7b-130">Ponadto pobierz klucz dostępu, aby uzyskać dostęp do konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-130">Ponadto pobierz klucz dostępu, aby uzyskać dostęp do konta magazynu.</span></span> <span data-ttu-id="6af7b-131">Zobacz [Szybki start: Przekazywanie, pobieranie i wyświetlanie listy obiektów blob w witrynie Azure portal](../storage/blobs/storage-quickstart-blobs-portal.md).</span><span class="sxs-lookup"><span data-stu-id="6af7b-131">Zobacz [Szybki start: Przekazywanie, pobieranie i wyświetlanie listy obiektów blob w witrynie Azure portal](../storage/blobs/storage-quickstart-blobs-portal.md).</span></span>

* <span data-ttu-id="6af7b-132">Utwórz konto usługi Azure Data Lake Storage Gen2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-132">Utwórz konto usługi Azure Data Lake Storage Gen2.</span></span> <span data-ttu-id="6af7b-133">Zobacz [Szybki start: Tworzenie konta magazynu Azure Data Lake Storage Gen2](../storage/blobs/data-lake-storage-quickstart-create-account.md).</span><span class="sxs-lookup"><span data-stu-id="6af7b-133">Zobacz [Szybki start: Tworzenie konta magazynu Azure Data Lake Storage Gen2](../storage/blobs/data-lake-storage-quickstart-create-account.md).</span></span>

* <span data-ttu-id="6af7b-134">Tworzenie jednostki usługi.</span><span class="sxs-lookup"><span data-stu-id="6af7b-134">Tworzenie jednostki usługi.</span></span> <span data-ttu-id="6af7b-135">Zobacz [Instrukcje: używanie portalu do tworzenia aplikacji usługi Azure AD i jednostki usługi w celu uzyskiwania dostępu do zasobów](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal).</span><span class="sxs-lookup"><span data-stu-id="6af7b-135">Zobacz [Instrukcje: używanie portalu do tworzenia aplikacji usługi Azure AD i jednostki usługi w celu uzyskiwania dostępu do zasobów](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal).</span></span>

   <span data-ttu-id="6af7b-136">Jest kilka rzeczy, o których należy pamiętać podczas wykonywania kroków przedstawionych w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="6af7b-136">Jest kilka rzeczy, o których należy pamiętać podczas wykonywania kroków przedstawionych w tym artykule.</span></span>

   * <span data-ttu-id="6af7b-137">Wykonując kroki opisane w [przypisywanie aplikacji do roli](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#assign-the-application-to-a-role) sekcji tego artykułu, upewnij się przypisać **Współautor danych obiektu Blob magazynu** roli do jednostki usługi w zakresie usługi Data Lake Konto magazynu, Gen2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-137">Wykonując kroki opisane w [przypisywanie aplikacji do roli](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#assign-the-application-to-a-role) sekcji tego artykułu, upewnij się przypisać **Współautor danych obiektu Blob magazynu** roli do jednostki usługi w zakresie usługi Data Lake Konto magazynu, Gen2.</span></span> <span data-ttu-id="6af7b-138">Jeśli ta rola została przypisana do nadrzędnej grupy zasobów lub subskrypcji, otrzymasz błędy związane z uprawnieniami do momentu przypisania tych ról są propagowane do konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-138">Jeśli ta rola została przypisana do nadrzędnej grupy zasobów lub subskrypcji, otrzymasz błędy związane z uprawnieniami do momentu przypisania tych ról są propagowane do konta magazynu.</span></span>

      <span data-ttu-id="6af7b-139">Jeśli wolisz używać listy kontroli dostępu (ACL) do skojarzenia z jednostki usługi przy użyciu określonego pliku lub katalogu, dokumentacja [kontrola dostępu w usługach Azure Data Lake Storage Gen2](../storage/blobs/data-lake-storage-access-control.md).</span><span class="sxs-lookup"><span data-stu-id="6af7b-139">Jeśli wolisz używać listy kontroli dostępu (ACL) do skojarzenia z jednostki usługi przy użyciu określonego pliku lub katalogu, dokumentacja [kontrola dostępu w usługach Azure Data Lake Storage Gen2](../storage/blobs/data-lake-storage-access-control.md).</span></span>

   * <span data-ttu-id="6af7b-140">Wykonując kroki opisane w [pobieranie wartości do logowania](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) części artykułu, wklej identyfikator dzierżawy, identyfikator aplikacji i wartości hasła do pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="6af7b-140">Wykonując kroki opisane w [pobieranie wartości do logowania](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) części artykułu, wklej identyfikator dzierżawy, identyfikator aplikacji i wartości hasła do pliku tekstowego.</span></span> <span data-ttu-id="6af7b-141">Wkrótce będą potrzebne.</span><span class="sxs-lookup"><span data-stu-id="6af7b-141">Wkrótce będą potrzebne.</span></span>

* <span data-ttu-id="6af7b-142">Zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).</span><span class="sxs-lookup"><span data-stu-id="6af7b-142">Zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).</span></span>

## <a name="gather-the-information-that-you-need"></a><span data-ttu-id="6af7b-143">Zbieranie potrzebnych informacji</span><span class="sxs-lookup"><span data-stu-id="6af7b-143">Zbieranie potrzebnych informacji</span></span>

<span data-ttu-id="6af7b-144">Upewnij się, że zostały spełnione wszystkie wymagania wstępne tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="6af7b-144">Upewnij się, że zostały spełnione wszystkie wymagania wstępne tego samouczka.</span></span>

   <span data-ttu-id="6af7b-145">Przed rozpoczęciem należy zebrać następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="6af7b-145">Przed rozpoczęciem należy zebrać następujące informacje:</span></span>

   <span data-ttu-id="6af7b-146"> :heavy_check_mark:  Nazwa bazy danych, nazwa serwera baz danych, nazwa użytkownika i hasło magazynu Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-146">:heavy_check_mark:  Nazwa bazy danych, nazwa serwera baz danych, nazwa użytkownika i hasło magazynu Azure SQL Data Warehouse.</span></span>

   <span data-ttu-id="6af7b-147"> :heavy_check_mark:  Klucz dostępu konta usługi Blob Storage.</span><span class="sxs-lookup"><span data-stu-id="6af7b-147">:heavy_check_mark:  Klucz dostępu konta usługi Blob Storage.</span></span>

   <span data-ttu-id="6af7b-148"> :heavy_check_mark:  Nazwa konta magazynu usługi Data Lake Storage Gen2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-148">:heavy_check_mark:  Nazwa konta magazynu usługi Data Lake Storage Gen2.</span></span>

   <span data-ttu-id="6af7b-149"> :heavy_check_mark:  Identyfikator dzierżawy subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="6af7b-149">:heavy_check_mark:  Identyfikator dzierżawy subskrypcji.</span></span>

   <span data-ttu-id="6af7b-150"> :heavy_check_mark:  Identyfikator aplikacji, która została zarejestrowana w usłudze Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="6af7b-150">:heavy_check_mark:  Identyfikator aplikacji, która została zarejestrowana w usłudze Azure Active Directory (Azure AD).</span></span>

   <span data-ttu-id="6af7b-151"> :heavy_check_mark:  Klucz uwierzytelniania aplikacji, która została zarejestrowana w usłudze Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6af7b-151">:heavy_check_mark:  Klucz uwierzytelniania aplikacji, która została zarejestrowana w usłudze Azure AD.</span></span>

## <a name="create-an-azure-databricks-service"></a><span data-ttu-id="6af7b-152">Tworzenie usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-152">Tworzenie usługi Azure Databricks</span></span>

<span data-ttu-id="6af7b-153">W tej sekcji utworzysz usługę Azure Databricks przy użyciu witryny Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="6af7b-153">W tej sekcji utworzysz usługę Azure Databricks przy użyciu witryny Azure Portal.</span></span>

1. <span data-ttu-id="6af7b-154">W witrynie Azure Portal wybierz pozycję **Utwórz zasób** > **Analiza** > **Azure Databricks**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-154">W witrynie Azure Portal wybierz pozycję **Utwórz zasób** > **Analiza** > **Azure Databricks**.</span></span>

    <span data-ttu-id="6af7b-155">![Usługa Databricks w witrynie Azure Portal](./media/databricks-extract-load-sql-data-warehouse/azure-databricks-on-portal.png "Usługa Databricks w witrynie Azure Portal")</span><span class="sxs-lookup"><span data-stu-id="6af7b-155">![Usługa Databricks w witrynie Azure Portal](./media/databricks-extract-load-sql-data-warehouse/azure-databricks-on-portal.png "Usługa Databricks w witrynie Azure Portal")</span></span>

2. <span data-ttu-id="6af7b-156">W obszarze **Usługa Azure Databricks** podaj następujące wartości, aby utworzyć usługę Databricks:</span><span class="sxs-lookup"><span data-stu-id="6af7b-156">W obszarze **Usługa Azure Databricks** podaj następujące wartości, aby utworzyć usługę Databricks:</span></span>

    |<span data-ttu-id="6af7b-157">Właściwość</span><span class="sxs-lookup"><span data-stu-id="6af7b-157">Właściwość</span></span>  |<span data-ttu-id="6af7b-158">Opis</span><span class="sxs-lookup"><span data-stu-id="6af7b-158">Opis</span></span>  |
    |---------|---------|
    |<span data-ttu-id="6af7b-159">**Nazwa obszaru roboczego**</span><span class="sxs-lookup"><span data-stu-id="6af7b-159">**Nazwa obszaru roboczego**</span></span>     | <span data-ttu-id="6af7b-160">Podaj nazwę obszaru roboczego usługi Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-160">Podaj nazwę obszaru roboczego usługi Databricks.</span></span>        |
    |<span data-ttu-id="6af7b-161">**Subskrypcja**</span><span class="sxs-lookup"><span data-stu-id="6af7b-161">**Subskrypcja**</span></span>     | <span data-ttu-id="6af7b-162">Z listy rozwijanej wybierz subskrypcję platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="6af7b-162">Z listy rozwijanej wybierz subskrypcję platformy Azure.</span></span>        |
    |<span data-ttu-id="6af7b-163">**Grupa zasobów**</span><span class="sxs-lookup"><span data-stu-id="6af7b-163">**Grupa zasobów**</span></span>     | <span data-ttu-id="6af7b-164">Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy.</span><span class="sxs-lookup"><span data-stu-id="6af7b-164">Określ, czy chcesz utworzyć nową grupę zasobów, czy użyć istniejącej grupy.</span></span> <span data-ttu-id="6af7b-165">Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="6af7b-165">Grupa zasobów to kontener, który zawiera powiązane zasoby dla rozwiązania platformy Azure.</span></span> <span data-ttu-id="6af7b-166">Aby uzyskać więcej informacji, zobacz [Omówienie usługi Azure Resource Manager](../azure-resource-manager/resource-group-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6af7b-166">Aby uzyskać więcej informacji, zobacz [Omówienie usługi Azure Resource Manager](../azure-resource-manager/resource-group-overview.md).</span></span> |
    |<span data-ttu-id="6af7b-167">**Lokalizacja**</span><span class="sxs-lookup"><span data-stu-id="6af7b-167">**Lokalizacja**</span></span>     | <span data-ttu-id="6af7b-168">Wybierz pozycję **Zachodnie stany USA 2**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-168">Wybierz pozycję **Zachodnie stany USA 2**.</span></span>  <span data-ttu-id="6af7b-169">Inne dostępne regiony podano na stronie [dostępności usług platformy Azure według regionów](https://azure.microsoft.com/regions/services/).</span><span class="sxs-lookup"><span data-stu-id="6af7b-169">Inne dostępne regiony podano na stronie [dostępności usług platformy Azure według regionów](https://azure.microsoft.com/regions/services/).</span></span>      |
    |<span data-ttu-id="6af7b-170">**Warstwa cenowa**</span><span class="sxs-lookup"><span data-stu-id="6af7b-170">**Warstwa cenowa**</span></span>     |  <span data-ttu-id="6af7b-171">Wybierz opcję **Standardowa**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-171">Wybierz opcję **Standardowa**.</span></span>     |

3. <span data-ttu-id="6af7b-172">Tworzenie konta potrwa kilka minut.</span><span class="sxs-lookup"><span data-stu-id="6af7b-172">Tworzenie konta potrwa kilka minut.</span></span> <span data-ttu-id="6af7b-173">Stan operacji można monitorować za pomocą paska postępu znajdującego się u góry.</span><span class="sxs-lookup"><span data-stu-id="6af7b-173">Stan operacji można monitorować za pomocą paska postępu znajdującego się u góry.</span></span>

4. <span data-ttu-id="6af7b-174">Wybierz pozycję **Przypnij do pulpitu nawigacyjnego**, a następnie pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-174">Wybierz pozycję **Przypnij do pulpitu nawigacyjnego**, a następnie pozycję **Utwórz**.</span></span>

## <a name="create-a-spark-cluster-in-azure-databricks"></a><span data-ttu-id="6af7b-175">Tworzenie klastra Spark w usłudze Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-175">Tworzenie klastra Spark w usłudze Azure Databricks</span></span>

1. <span data-ttu-id="6af7b-176">W witrynie Azure Portal przejdź do utworzonej usługi Databricks i wybierz pozycję **Uruchom obszar roboczy**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-176">W witrynie Azure Portal przejdź do utworzonej usługi Databricks i wybierz pozycję **Uruchom obszar roboczy**.</span></span>

2. <span data-ttu-id="6af7b-177">Nastąpi przekierowanie do portalu usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-177">Nastąpi przekierowanie do portalu usługi Azure Databricks.</span></span> <span data-ttu-id="6af7b-178">W portalu wybierz pozycję **Klaster**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-178">W portalu wybierz pozycję **Klaster**.</span></span>

    <span data-ttu-id="6af7b-179">![Usługa Databricks na platformie Azure](./media/databricks-extract-load-sql-data-warehouse/databricks-on-azure.png "Usługa Databricks na platformie Azure")</span><span class="sxs-lookup"><span data-stu-id="6af7b-179">![Usługa Databricks na platformie Azure](./media/databricks-extract-load-sql-data-warehouse/databricks-on-azure.png "Usługa Databricks na platformie Azure")</span></span>

3. <span data-ttu-id="6af7b-180">Na stronie **Nowy klaster** podaj wartości, aby utworzyć klaster.</span><span class="sxs-lookup"><span data-stu-id="6af7b-180">Na stronie **Nowy klaster** podaj wartości, aby utworzyć klaster.</span></span>

    <span data-ttu-id="6af7b-181">![Tworzenie klastra Spark usługi Databricks na platformie Azure](./media/databricks-extract-load-sql-data-warehouse/create-databricks-spark-cluster.png "Tworzenie klastra Spark usługi Databricks na platformie Azure")</span><span class="sxs-lookup"><span data-stu-id="6af7b-181">![Tworzenie klastra Spark usługi Databricks na platformie Azure](./media/databricks-extract-load-sql-data-warehouse/create-databricks-spark-cluster.png "Tworzenie klastra Spark usługi Databricks na platformie Azure")</span></span>

4. <span data-ttu-id="6af7b-182">Uzupełnij wartości następujących pól i zaakceptuj wartości domyślne w pozostałych polach:</span><span class="sxs-lookup"><span data-stu-id="6af7b-182">Uzupełnij wartości następujących pól i zaakceptuj wartości domyślne w pozostałych polach:</span></span>

    * <span data-ttu-id="6af7b-183">Wprowadź nazwę klastra.</span><span class="sxs-lookup"><span data-stu-id="6af7b-183">Wprowadź nazwę klastra.</span></span>

    * <span data-ttu-id="6af7b-184">Na potrzeby tego artykułu utwórz klaster ze środowiskiem uruchomieniowym w wersji **5.1**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-184">Na potrzeby tego artykułu utwórz klaster ze środowiskiem uruchomieniowym w wersji **5.1**.</span></span>

    * <span data-ttu-id="6af7b-185">Upewnij się, że jest zaznaczone pole wyboru **Zakończ po \_\_ min nieaktywności**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-185">Upewnij się, że jest zaznaczone pole wyboru **Zakończ po \_\_ min nieaktywności**.</span></span> <span data-ttu-id="6af7b-186">Podaj czas (w minutach), po jakim działanie klastra ma zostać zakończone, jeśli nie jest on używany.</span><span class="sxs-lookup"><span data-stu-id="6af7b-186">Podaj czas (w minutach), po jakim działanie klastra ma zostać zakończone, jeśli nie jest on używany.</span></span>

    * <span data-ttu-id="6af7b-187">Wybierz pozycję **Utwórz klaster**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-187">Wybierz pozycję **Utwórz klaster**.</span></span> <span data-ttu-id="6af7b-188">Po uruchomieniu klastra możesz dołączać do niego notesy i uruchamiać zadania Spark.</span><span class="sxs-lookup"><span data-stu-id="6af7b-188">Po uruchomieniu klastra możesz dołączać do niego notesy i uruchamiać zadania Spark.</span></span>

## <a name="create-a-file-system-in-the-azure-data-lake-storage-gen2-account"></a><span data-ttu-id="6af7b-189">Tworzenie systemu plików na koncie usługi Azure Data Lake Storage Gen2</span><span class="sxs-lookup"><span data-stu-id="6af7b-189">Tworzenie systemu plików na koncie usługi Azure Data Lake Storage Gen2</span></span>

<span data-ttu-id="6af7b-190">W tej sekcji utworzysz notes w obszarze roboczym usługi Azure Databricks, a następnie uruchomisz fragmenty kodu, aby skonfigurować konto magazynu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-190">W tej sekcji utworzysz notes w obszarze roboczym usługi Azure Databricks, a następnie uruchomisz fragmenty kodu, aby skonfigurować konto magazynu.</span></span>

1. <span data-ttu-id="6af7b-191">W witrynie [Azure Portal](https://portal.azure.com) przejdź do utworzonej usługi Azure Databricks i wybierz pozycję **Uruchom obszar roboczy**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-191">W witrynie [Azure Portal](https://portal.azure.com) przejdź do utworzonej usługi Azure Databricks i wybierz pozycję **Uruchom obszar roboczy**.</span></span>

2. <span data-ttu-id="6af7b-192">Po lewej stronie wybierz pozycję **Obszar roboczy**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-192">Po lewej stronie wybierz pozycję **Obszar roboczy**.</span></span> <span data-ttu-id="6af7b-193">Z listy rozwijanej **Obszar roboczy** wybierz pozycję **Utwórz** > **Notes**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-193">Z listy rozwijanej **Obszar roboczy** wybierz pozycję **Utwórz** > **Notes**.</span></span>

    <span data-ttu-id="6af7b-194">![Tworzenie notesu w usłudze Databricks](./media/databricks-extract-load-sql-data-warehouse/databricks-create-notebook.png "Tworzenie notesu w usłudze Databricks")</span><span class="sxs-lookup"><span data-stu-id="6af7b-194">![Tworzenie notesu w usłudze Databricks](./media/databricks-extract-load-sql-data-warehouse/databricks-create-notebook.png "Tworzenie notesu w usłudze Databricks")</span></span>

3. <span data-ttu-id="6af7b-195">W oknie dialogowym**Tworzenie notesu** wprowadź nazwę notesu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-195">W oknie dialogowym**Tworzenie notesu** wprowadź nazwę notesu.</span></span> <span data-ttu-id="6af7b-196">Jako język wybierz pozycję **Scala**, a następnie wybierz utworzony wcześniej klaster Spark.</span><span class="sxs-lookup"><span data-stu-id="6af7b-196">Jako język wybierz pozycję **Scala**, a następnie wybierz utworzony wcześniej klaster Spark.</span></span>

    <span data-ttu-id="6af7b-197">![Podawanie szczegółów dotyczących notesu w usłudze Databricks](./media/databricks-extract-load-sql-data-warehouse/databricks-notebook-details.png "Podawanie szczegółów dotyczących notesu w usłudze Databricks")</span><span class="sxs-lookup"><span data-stu-id="6af7b-197">![Podawanie szczegółów dotyczących notesu w usłudze Databricks](./media/databricks-extract-load-sql-data-warehouse/databricks-notebook-details.png "Podawanie szczegółów dotyczących notesu w usłudze Databricks")</span></span>

4. <span data-ttu-id="6af7b-198">Wybierz pozycję **Utwórz**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-198">Wybierz pozycję **Utwórz**.</span></span>

5. <span data-ttu-id="6af7b-199">Poniższy blok kodu ustawia domyślne poświadczenia nazwy głównej usługi dla dowolnego konta usługi ADLS Gen 2, dostępny w sesja platformy Spark.</span><span class="sxs-lookup"><span data-stu-id="6af7b-199">Poniższy blok kodu ustawia domyślne poświadczenia nazwy głównej usługi dla dowolnego konta usługi ADLS Gen 2, dostępny w sesja platformy Spark.</span></span> <span data-ttu-id="6af7b-200">Drugi blok kodu dołącza nazwę konta do ustawienia, aby określić poświadczenia dla określonego konta usługi ADLS generacji 2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-200">Drugi blok kodu dołącza nazwę konta do ustawienia, aby określić poświadczenia dla określonego konta usługi ADLS generacji 2.</span></span>  <span data-ttu-id="6af7b-201">Skopiuj i Wklej albo blok kodu do pierwszej komórki notesu usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-201">Skopiuj i Wklej albo blok kodu do pierwszej komórki notesu usługi Azure Databricks.</span></span>

   <span data-ttu-id="6af7b-202">**Konfiguracja sesji**</span><span class="sxs-lookup"><span data-stu-id="6af7b-202">**Konfiguracja sesji**</span></span>

   ```scala
   spark.conf.set("fs.azure.account.auth.type", "OAuth")
   spark.conf.set("fs.azure.account.oauth.provider.type", "org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider")
   spark.conf.set("fs.azure.account.oauth2.client.id", "<appID>")
   spark.conf.set("fs.azure.account.oauth2.client.secret", "<password>")
   spark.conf.set("fs.azure.account.oauth2.client.endpoint", "https://login.microsoftonline.com/<tenant-id>/oauth2/token")
   spark.conf.set("fs.azure.createRemoteFileSystemDuringInitialization", "true")
   dbutils.fs.ls("abfss://<file-system-name>@<storage-account-name>.dfs.core.windows.net/")
   spark.conf.set("fs.azure.createRemoteFileSystemDuringInitialization", "false")
   ```

   <span data-ttu-id="6af7b-203">**Konfiguracja konta**</span><span class="sxs-lookup"><span data-stu-id="6af7b-203">**Konfiguracja konta**</span></span>

   ```scala
   spark.conf.set("fs.azure.account.auth.type.<storage-account-name>.dfs.core.windows.net", "OAuth")
   spark.conf.set("fs.azure.account.oauth.provider.type.<storage-account-name>.dfs.core.windows.net", "org.apache.hadoop.fs.azurebfs.oauth2.ClientCredsTokenProvider")
   spark.conf.set("fs.azure.account.oauth2.client.id.<storage-account-name>.dfs.core.windows.net", "<appID>")
   spark.conf.set("fs.azure.account.oauth2.client.secret.<storage-account-name>.dfs.core.windows.net", "<password>")
   spark.conf.set("fs.azure.account.oauth2.client.endpoint.<storage-account-name>.dfs.core.windows.net", "https://login.microsoftonline.com/<tenant-id>/oauth2/token")
   spark.conf.set("fs.azure.createRemoteFileSystemDuringInitialization", "true")
   dbutils.fs.ls("abfss://<file-system-name>@<storage-account-name>.dfs.core.windows.net/")
   spark.conf.set("fs.azure.createRemoteFileSystemDuringInitialization", "false")
   ```

6. <span data-ttu-id="6af7b-204">W tym bloku kodu zamień symbole zastępcze `appID`, `password`, `tenant-id` i `storage-account-name` na wartości zebrane podczas wykonywania kroków wymagań wstępnych.</span><span class="sxs-lookup"><span data-stu-id="6af7b-204">W tym bloku kodu zamień symbole zastępcze `appID`, `password`, `tenant-id` i `storage-account-name` na wartości zebrane podczas wykonywania kroków wymagań wstępnych.</span></span> <span data-ttu-id="6af7b-205">Zastąp symbol zastępczy `file-system-name` dowolną nazwą, którą chcesz nadać systemowi plików.</span><span class="sxs-lookup"><span data-stu-id="6af7b-205">Zastąp symbol zastępczy `file-system-name` dowolną nazwą, którą chcesz nadać systemowi plików.</span></span>

   * <span data-ttu-id="6af7b-206">Parametry `appID` i `password` pochodzą z aplikacji zarejestrowanej w usłudze Active Directory podczas tworzenia jednostki usługi.</span><span class="sxs-lookup"><span data-stu-id="6af7b-206">Parametry `appID` i `password` pochodzą z aplikacji zarejestrowanej w usłudze Active Directory podczas tworzenia jednostki usługi.</span></span>

   * <span data-ttu-id="6af7b-207">Parametr `tenant-id` pochodzi z subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="6af7b-207">Parametr `tenant-id` pochodzi z subskrypcji.</span></span>

   * <span data-ttu-id="6af7b-208">Parametr `storage-account-name` to nazwa konta magazynu usługi Azure Data Lake Storage Gen2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-208">Parametr `storage-account-name` to nazwa konta magazynu usługi Azure Data Lake Storage Gen2.</span></span>

7. <span data-ttu-id="6af7b-209">Naciśnij klawisze **SHIFT+ENTER**, aby uruchomić kod w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="6af7b-209">Naciśnij klawisze **SHIFT+ENTER**, aby uruchomić kod w tym bloku.</span></span>

## <a name="ingest-sample-data-into-the-azure-data-lake-storage-gen2-account"></a><span data-ttu-id="6af7b-210">Pozyskiwanie danych przykładowych na konto usługi Azure Data Lake Storage Gen2</span><span class="sxs-lookup"><span data-stu-id="6af7b-210">Pozyskiwanie danych przykładowych na konto usługi Azure Data Lake Storage Gen2</span></span>

<span data-ttu-id="6af7b-211">Przed przystąpieniem do pracy z tą sekcją musisz zapewnić spełnienie następujących wymagań wstępnych:</span><span class="sxs-lookup"><span data-stu-id="6af7b-211">Przed przystąpieniem do pracy z tą sekcją musisz zapewnić spełnienie następujących wymagań wstępnych:</span></span>

<span data-ttu-id="6af7b-212">Wprowadź następujący kod w komórce notesu:</span><span class="sxs-lookup"><span data-stu-id="6af7b-212">Wprowadź następujący kod w komórce notesu:</span></span>

    %sh wget -P /tmp https://raw.githubusercontent.com/Azure/usql/master/Examples/Samples/Data/json/radiowebsite/small_radio_json.json

<span data-ttu-id="6af7b-213">W tej komórce naciśnij klawisze **SHIFT + ENTER**, aby uruchomić kod.</span><span class="sxs-lookup"><span data-stu-id="6af7b-213">W tej komórce naciśnij klawisze **SHIFT + ENTER**, aby uruchomić kod.</span></span>

<span data-ttu-id="6af7b-214">Teraz w nowej komórce pod tą komórką wprowadź następujący kod, zastępując wartości w nawiasach tymi samymi wartościami, których użyto wcześniej:</span><span class="sxs-lookup"><span data-stu-id="6af7b-214">Teraz w nowej komórce pod tą komórką wprowadź następujący kod, zastępując wartości w nawiasach tymi samymi wartościami, których użyto wcześniej:</span></span>

    dbutils.fs.cp("file:///tmp/small_radio_json.json", "abfss://<file-system>@<account-name>.dfs.core.windows.net/")

<span data-ttu-id="6af7b-215">W tej komórce naciśnij klawisze **SHIFT + ENTER**, aby uruchomić kod.</span><span class="sxs-lookup"><span data-stu-id="6af7b-215">W tej komórce naciśnij klawisze **SHIFT + ENTER**, aby uruchomić kod.</span></span>

## <a name="extract-data-from-the-azure-data-lake-storage-gen2-account"></a><span data-ttu-id="6af7b-216">Wyodrębnianie danych z konta usługi Azure Data Lake Storage Gen2</span><span class="sxs-lookup"><span data-stu-id="6af7b-216">Wyodrębnianie danych z konta usługi Azure Data Lake Storage Gen2</span></span>

1. <span data-ttu-id="6af7b-217">Teraz możesz załadować przykładowy plik json jako ramkę danych w usłudze Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-217">Teraz możesz załadować przykładowy plik json jako ramkę danych w usłudze Azure Databricks.</span></span> <span data-ttu-id="6af7b-218">Wklej następujący kod w nowej komórce.</span><span class="sxs-lookup"><span data-stu-id="6af7b-218">Wklej następujący kod w nowej komórce.</span></span> <span data-ttu-id="6af7b-219">Zastąp symbole zastępcze umieszczone w nawiasach ostrokątnych własnymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="6af7b-219">Zastąp symbole zastępcze umieszczone w nawiasach ostrokątnych własnymi wartościami.</span></span>

   ```scala
   val df = spark.read.json("abfss://<file-system-name>@<storage-account-name>.dfs.core.windows.net/small_radio_json.json")
   ```

   * <span data-ttu-id="6af7b-220">Zastąp wartość symbolu zastępczego `file-system-name` nazwą nadaną systemowi plików w Eksploratorze usługi Storage.</span><span class="sxs-lookup"><span data-stu-id="6af7b-220">Zastąp wartość symbolu zastępczego `file-system-name` nazwą nadaną systemowi plików w Eksploratorze usługi Storage.</span></span>

   * <span data-ttu-id="6af7b-221">Zastąp symbol zastępczy `storage-account-name` nazwą konta magazynu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-221">Zastąp symbol zastępczy `storage-account-name` nazwą konta magazynu.</span></span>

2. <span data-ttu-id="6af7b-222">Naciśnij klawisze **SHIFT+ENTER**, aby uruchomić kod w tym bloku.</span><span class="sxs-lookup"><span data-stu-id="6af7b-222">Naciśnij klawisze **SHIFT+ENTER**, aby uruchomić kod w tym bloku.</span></span>

3. <span data-ttu-id="6af7b-223">Uruchom poniższy kod, aby wyświetlić zawartość ramki danych:</span><span class="sxs-lookup"><span data-stu-id="6af7b-223">Uruchom poniższy kod, aby wyświetlić zawartość ramki danych:</span></span>

    ```scala
    df.show()
    ```
   <span data-ttu-id="6af7b-224">Zostaną wyświetlone dane wyjściowe podobne do następującego fragmentu kodu:</span><span class="sxs-lookup"><span data-stu-id="6af7b-224">Zostaną wyświetlone dane wyjściowe podobne do następującego fragmentu kodu:</span></span>

   ```bash
   +---------------------+---------+---------+------+-------------+----------+---------+-------+--------------------+------+--------+-------------+---------+--------------------+------+-------------+------+
   |               artist|     auth|firstName|gender|itemInSession|  lastName|   length|  level|            location|method|    page| registration|sessionId|                song|status|           ts|userId|
   +---------------------+---------+---------+------+-------------+----------+---------+-------+--------------------+------+--------+-------------+---------+--------------------+------+-------------+------+
   | El Arrebato         |Logged In| Annalyse|     F|            2|Montgomery|234.57914| free  |  Killeen-Temple, TX|   PUT|NextSong|1384448062332|     1879|Quiero Quererte Q...|   200|1409318650332|   309|
   | Creedence Clearwa...|Logged In|   Dylann|     M|            9|    Thomas|340.87138| paid  |       Anchorage, AK|   PUT|NextSong|1400723739332|       10|        Born To Move|   200|1409318653332|    11|
   | Gorillaz            |Logged In|     Liam|     M|           11|     Watts|246.17751| paid  |New York-Newark-J...|   PUT|NextSong|1406279422332|     2047|                DARE|   200|1409318685332|   201|
   ...
   ...
   ```

   <span data-ttu-id="6af7b-225">Masz teraz dane wyodrębnione z usługi Azure Data Lake Storage 2.</span><span class="sxs-lookup"><span data-stu-id="6af7b-225">Masz teraz dane wyodrębnione z usługi Azure Data Lake Storage 2.</span></span> <span data-ttu-id="6af7b-226">generacji do usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-226">generacji do usługi Azure Databricks.</span></span>

## <a name="transform-data-in-azure-databricks"></a><span data-ttu-id="6af7b-227">Przekształcanie danych w usłudze Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-227">Przekształcanie danych w usłudze Azure Databricks</span></span>

<span data-ttu-id="6af7b-228">Plik przykładowych danych pierwotnych, **small_radio_json.json**, przechwytuje odbiorców stacji radiowej i ma wiele kolumn.</span><span class="sxs-lookup"><span data-stu-id="6af7b-228">Plik przykładowych danych pierwotnych, **small_radio_json.json**, przechwytuje odbiorców stacji radiowej i ma wiele kolumn.</span></span> <span data-ttu-id="6af7b-229">W tej sekcji przekształcisz dane tak, aby z zestawu danych były pobierane tylko określone kolumny.</span><span class="sxs-lookup"><span data-stu-id="6af7b-229">W tej sekcji przekształcisz dane tak, aby z zestawu danych były pobierane tylko określone kolumny.</span></span>

1. <span data-ttu-id="6af7b-230">Zacznij od pobrania tylko kolumn **firstName**, **lastName**, **gender**, **location** i **level** z utworzonej ramki danych.</span><span class="sxs-lookup"><span data-stu-id="6af7b-230">Zacznij od pobrania tylko kolumn **firstName**, **lastName**, **gender**, **location** i **level** z utworzonej ramki danych.</span></span>

   ```scala
   val specificColumnsDf = df.select("firstname", "lastname", "gender", "location", "level")
   specificColumnsDf.show()
   ```

   <span data-ttu-id="6af7b-231">Otrzymasz dane wyjściowe pokazane w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="6af7b-231">Otrzymasz dane wyjściowe pokazane w poniższym fragmencie kodu:</span></span>

   ```bash
   +---------+----------+------+--------------------+-----+
   |firstname|  lastname|gender|            location|level|
   +---------+----------+------+--------------------+-----+
   | Annalyse|Montgomery|     F|  Killeen-Temple, TX| free|
   |   Dylann|    Thomas|     M|       Anchorage, AK| paid|
   |     Liam|     Watts|     M|New York-Newark-J...| paid|
   |     Tess|  Townsend|     F|Nashville-Davidso...| free|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...| free|
   |     Alan|     Morse|     M|Chicago-Napervill...| paid|
   |Gabriella|   Shelton|     F|San Jose-Sunnyval...| free|
   |   Elijah|  Williams|     M|Detroit-Warren-De...| paid|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...| free|
   |     Tess|  Townsend|     F|Nashville-Davidso...| free|
   |     Alan|     Morse|     M|Chicago-Napervill...| paid|
   |     Liam|     Watts|     M|New York-Newark-J...| paid|
   |     Liam|     Watts|     M|New York-Newark-J...| paid|
   |   Dylann|    Thomas|     M|       Anchorage, AK| paid|
   |     Alan|     Morse|     M|Chicago-Napervill...| paid|
   |   Elijah|  Williams|     M|Detroit-Warren-De...| paid|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...| free|
   |     Alan|     Morse|     M|Chicago-Napervill...| paid|
   |   Dylann|    Thomas|     M|       Anchorage, AK| paid|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...| free|
   +---------+----------+------+--------------------+-----+
   ```

2. <span data-ttu-id="6af7b-232">Możesz dalej przekształcać te dane, aby zmienić nazwę kolumny **level** na **subscription_type**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-232">Możesz dalej przekształcać te dane, aby zmienić nazwę kolumny **level** na **subscription_type**.</span></span>

   ```scala
   val renamedColumnsDF = specificColumnsDf.withColumnRenamed("level", "subscription_type")
   renamedColumnsDF.show()
   ```

   <span data-ttu-id="6af7b-233">Otrzymasz dane wyjściowe pokazane w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-233">Otrzymasz dane wyjściowe pokazane w poniższym fragmencie kodu.</span></span>

   ```bash
   +---------+----------+------+--------------------+-----------------+
   |firstname|  lastname|gender|            location|subscription_type|
   +---------+----------+------+--------------------+-----------------+
   | Annalyse|Montgomery|     F|  Killeen-Temple, TX|             free|
   |   Dylann|    Thomas|     M|       Anchorage, AK|             paid|
   |     Liam|     Watts|     M|New York-Newark-J...|             paid|
   |     Tess|  Townsend|     F|Nashville-Davidso...|             free|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...|             free|
   |     Alan|     Morse|     M|Chicago-Napervill...|             paid|
   |Gabriella|   Shelton|     F|San Jose-Sunnyval...|             free|
   |   Elijah|  Williams|     M|Detroit-Warren-De...|             paid|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...|             free|
   |     Tess|  Townsend|     F|Nashville-Davidso...|             free|
   |     Alan|     Morse|     M|Chicago-Napervill...|             paid|
   |     Liam|     Watts|     M|New York-Newark-J...|             paid|
   |     Liam|     Watts|     M|New York-Newark-J...|             paid|
   |   Dylann|    Thomas|     M|       Anchorage, AK|             paid|
   |     Alan|     Morse|     M|Chicago-Napervill...|             paid|
   |   Elijah|  Williams|     M|Detroit-Warren-De...|             paid|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...|             free|
   |     Alan|     Morse|     M|Chicago-Napervill...|             paid|
   |   Dylann|    Thomas|     M|       Anchorage, AK|             paid|
   |  Margaux|     Smith|     F|Atlanta-Sandy Spr...|             free|
   +---------+----------+------+--------------------+-----------------+
   ```

## <a name="load-data-into-azure-sql-data-warehouse"></a><span data-ttu-id="6af7b-234">Ładowanie danych do usługi Azure SQL Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="6af7b-234">Ładowanie danych do usługi Azure SQL Data Warehouse</span></span>

<span data-ttu-id="6af7b-235">W tej sekcji przekażesz przekształcone dane do magazynu danych Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-235">W tej sekcji przekażesz przekształcone dane do magazynu danych Azure SQL Data Warehouse.</span></span> <span data-ttu-id="6af7b-236">Używając łącznika usługi Azure SQL Data Warehouse dla usługi Azure Databricks, bezpośrednio przekażesz ramkę danych jako tabelę w usłudze SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-236">Używając łącznika usługi Azure SQL Data Warehouse dla usługi Azure Databricks, bezpośrednio przekażesz ramkę danych jako tabelę w usłudze SQL Data Warehouse.</span></span>

<span data-ttu-id="6af7b-237">Jak wspomniano wcześniej, łącznik magazynu danych SQL korzysta z usługi Azure Blob Storage jako magazynu tymczasowego do przekazywania danych między usługami Azure Databricks i Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-237">Jak wspomniano wcześniej, łącznik magazynu danych SQL korzysta z usługi Azure Blob Storage jako magazynu tymczasowego do przekazywania danych między usługami Azure Databricks i Azure SQL Data Warehouse.</span></span> <span data-ttu-id="6af7b-238">Możesz rozpocząć od podania konfiguracji umożliwiającej nawiązanie połączenia z kontem magazynu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-238">Możesz rozpocząć od podania konfiguracji umożliwiającej nawiązanie połączenia z kontem magazynu.</span></span> <span data-ttu-id="6af7b-239">Musisz już mieć utworzone konto w ramach wymagań wstępnych dotyczących tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-239">Musisz już mieć utworzone konto w ramach wymagań wstępnych dotyczących tego artykułu.</span></span>

1. <span data-ttu-id="6af7b-240">Podaj konfigurację umożliwiającą uzyskanie dostępu do konta usługi Azure Storage z usługi Azure Databricks.</span><span class="sxs-lookup"><span data-stu-id="6af7b-240">Podaj konfigurację umożliwiającą uzyskanie dostępu do konta usługi Azure Storage z usługi Azure Databricks.</span></span>

   ```scala
   val blobStorage = "<blob-storage-account-name>.blob.core.windows.net"
   val blobContainer = "<blob-container-name>"
   val blobAccessKey =  "<access-key>"
   ```

2. <span data-ttu-id="6af7b-241">Określ folder tymczasowy do użycia podczas przenoszenia danych między usługami Azure Databricks i Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-241">Określ folder tymczasowy do użycia podczas przenoszenia danych między usługami Azure Databricks i Azure SQL Data Warehouse.</span></span>

   ```scala
   val tempDir = "wasbs://" + blobContainer + "@" + blobStorage +"/tempDirs"
   ```

3. <span data-ttu-id="6af7b-242">Uruchom poniższy fragment kodu, aby zapisać klucze dostępu usługi Azure Blob Storage w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6af7b-242">Uruchom poniższy fragment kodu, aby zapisać klucze dostępu usługi Azure Blob Storage w konfiguracji.</span></span> <span data-ttu-id="6af7b-243">Dzięki tej akcji nie będzie trzeba przechowywać klucza dostępu w notesie w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-243">Dzięki tej akcji nie będzie trzeba przechowywać klucza dostępu w notesie w postaci zwykłego tekstu.</span></span>

   ```scala
   val acntInfo = "fs.azure.account.key."+ blobStorage
   sc.hadoopConfiguration.set(acntInfo, blobAccessKey)
   ```

4. <span data-ttu-id="6af7b-244">Podaj wartości, aby nawiązać połączenie z wystąpieniem usługi Azure SQL Data Warehouse.</span><span class="sxs-lookup"><span data-stu-id="6af7b-244">Podaj wartości, aby nawiązać połączenie z wystąpieniem usługi Azure SQL Data Warehouse.</span></span> <span data-ttu-id="6af7b-245">Musisz mieć magazyn danych SQL Data Warehouse utworzony w ramach wymagań wstępnych.</span><span class="sxs-lookup"><span data-stu-id="6af7b-245">Musisz mieć magazyn danych SQL Data Warehouse utworzony w ramach wymagań wstępnych.</span></span> <span data-ttu-id="6af7b-246">Użyj w pełni kwalifikowaną nazwę serwera dla **dwServer**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-246">Użyj w pełni kwalifikowaną nazwę serwera dla **dwServer**.</span></span> <span data-ttu-id="6af7b-247">Na przykład `<servername>.database.windows.net`.</span><span class="sxs-lookup"><span data-stu-id="6af7b-247">Na przykład `<servername>.database.windows.net`.</span></span>

   ```scala
   //SQL Data Warehouse related settings
   val dwDatabase = "<database-name>"
   val dwServer = "<database-server-name>"
   val dwUser = "<user-name>"
   val dwPass = "<password>"
   val dwJdbcPort =  "1433"
   val dwJdbcExtraOptions = "encrypt=true;trustServerCertificate=true;hostNameInCertificate=*.database.windows.net;loginTimeout=30;"
   val sqlDwUrl = "jdbc:sqlserver://" + dwServer + ":" + dwJdbcPort + ";database=" + dwDatabase + ";user=" + dwUser+";password=" + dwPass + ";$dwJdbcExtraOptions"
   val sqlDwUrlSmall = "jdbc:sqlserver://" + dwServer + ":" + dwJdbcPort + ";database=" + dwDatabase + ";user=" + dwUser+";password=" + dwPass
   ```

5. Uruchom poniższy fragment kodu, aby załadować przekształconą ramkę danych **renamedColumnsDF** jako tabelę w magazynie danych SQL Data Warehouse. <span data-ttu-id="6af7b-249">Ten fragment kodu tworzy tabelę o nazwie **SampleTable** w bazie danych SQL.</span><span class="sxs-lookup"><span data-stu-id="6af7b-249">Ten fragment kodu tworzy tabelę o nazwie **SampleTable** w bazie danych SQL.</span></span>

   ```scala
   spark.conf.set(
       "spark.sql.parquet.writeLegacyFormat",
       "true")

   renamedColumnsDF.write
       .format("com.databricks.spark.sqldw")
       .option("url", sqlDwUrlSmall) 
       .option("dbtable", "SampleTable")
       .option( "forward_spark_azure_storage_credentials","True")
       .option("tempdir", tempDir)
       .mode("overwrite")
       .save()
   ```

   > [!NOTE]
   > <span data-ttu-id="6af7b-250">W tym przykładzie użyto `forward_spark_azure_storage_credentials` flagi, co powoduje, że usługa SQL Data Warehouse na dostęp do danych z magazynu obiektów blob przy użyciu klucza dostępu.</span><span class="sxs-lookup"><span data-stu-id="6af7b-250">W tym przykładzie użyto `forward_spark_azure_storage_credentials` flagi, co powoduje, że usługa SQL Data Warehouse na dostęp do danych z magazynu obiektów blob przy użyciu klucza dostępu.</span></span> <span data-ttu-id="6af7b-251">Jest to jedyna obsługiwana metoda uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="6af7b-251">Jest to jedyna obsługiwana metoda uwierzytelniania.</span></span>
   >
   > <span data-ttu-id="6af7b-252">Jeśli usługi Azure Blob Storage jest ograniczone do wybrania sieci wirtualne, usługa SQL Data Warehouse wymaga [tożsamości usługi zarządzanej zamiast kluczy dostępu](../sql-database/sql-database-vnet-service-endpoint-rule-overview.md#impact-of-using-vnet-service-endpoints-with-azure-storage).</span><span class="sxs-lookup"><span data-stu-id="6af7b-252">Jeśli usługi Azure Blob Storage jest ograniczone do wybrania sieci wirtualne, usługa SQL Data Warehouse wymaga [tożsamości usługi zarządzanej zamiast kluczy dostępu](../sql-database/sql-database-vnet-service-endpoint-rule-overview.md#impact-of-using-vnet-service-endpoints-with-azure-storage).</span></span> <span data-ttu-id="6af7b-253">Spowoduje to błąd "to żądanie nie ma uprawnień do wykonania tej operacji."</span><span class="sxs-lookup"><span data-stu-id="6af7b-253">Spowoduje to błąd "to żądanie nie ma uprawnień do wykonania tej operacji."</span></span>

6. <span data-ttu-id="6af7b-254">Połącz się z usługą SQL Database i sprawdź, czy jest widoczna baza danych o nazwie **SampleTable**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-254">Połącz się z usługą SQL Database i sprawdź, czy jest widoczna baza danych o nazwie **SampleTable**.</span></span>

   <span data-ttu-id="6af7b-255">![Sprawdzanie przykładowej tabeli](./media/databricks-extract-load-sql-data-warehouse/verify-sample-table.png "Sprawdzanie przykładowej tabeli")</span><span class="sxs-lookup"><span data-stu-id="6af7b-255">![Sprawdzanie przykładowej tabeli](./media/databricks-extract-load-sql-data-warehouse/verify-sample-table.png "Sprawdzanie przykładowej tabeli")</span></span>

7. <span data-ttu-id="6af7b-256">Uruchom wybrane zapytanie, aby sprawdzić zawartość tabeli.</span><span class="sxs-lookup"><span data-stu-id="6af7b-256">Uruchom wybrane zapytanie, aby sprawdzić zawartość tabeli.</span></span> <span data-ttu-id="6af7b-257">Tabela powinna zawierać takie same dane jak ramka danych **renamedColumnsDF**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-257">Tabela powinna zawierać takie same dane jak ramka danych **renamedColumnsDF**.</span></span>

    <span data-ttu-id="6af7b-258">![Sprawdzanie zawartości przykładowej tabeli](./media/databricks-extract-load-sql-data-warehouse/verify-sample-table-content.png "Sprawdzanie zawartości przykładowej tabeli")</span><span class="sxs-lookup"><span data-stu-id="6af7b-258">![Sprawdzanie zawartości przykładowej tabeli](./media/databricks-extract-load-sql-data-warehouse/verify-sample-table-content.png "Sprawdzanie zawartości przykładowej tabeli")</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="6af7b-259">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="6af7b-259">Oczyszczanie zasobów</span></span>

<span data-ttu-id="6af7b-260">Po ukończeniu tego samouczka możesz przerwać działanie klastra.</span><span class="sxs-lookup"><span data-stu-id="6af7b-260">Po ukończeniu tego samouczka możesz przerwać działanie klastra.</span></span> <span data-ttu-id="6af7b-261">W obszarze roboczym usługi Azure Databricks wybierz pozycję **Klastry** po lewej stronie.</span><span class="sxs-lookup"><span data-stu-id="6af7b-261">W obszarze roboczym usługi Azure Databricks wybierz pozycję **Klastry** po lewej stronie.</span></span> <span data-ttu-id="6af7b-262">Aby przerwać działanie klastra, w obszarze **Akcje** wskaż wielokropek (...) i wybierz ikonę **Przerwij**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-262">Aby przerwać działanie klastra, w obszarze **Akcje** wskaż wielokropek (...) i wybierz ikonę **Przerwij**.</span></span>

<span data-ttu-id="6af7b-263">![Zatrzymywanie klastra usługi Databricks](./media/databricks-extract-load-sql-data-warehouse/terminate-databricks-cluster.png "Zatrzymywanie klastra usługi Databricks")</span><span class="sxs-lookup"><span data-stu-id="6af7b-263">![Zatrzymywanie klastra usługi Databricks](./media/databricks-extract-load-sql-data-warehouse/terminate-databricks-cluster.png "Zatrzymywanie klastra usługi Databricks")</span></span>

<span data-ttu-id="6af7b-264">Jeśli nie przerwiesz działania klastra ręcznie, zostanie on automatycznie zatrzymany, o ile podczas tworzenia klastra zaznaczono pole wyboru **Zakończ po \_\_ min nieaktywności**.</span><span class="sxs-lookup"><span data-stu-id="6af7b-264">Jeśli nie przerwiesz działania klastra ręcznie, zostanie on automatycznie zatrzymany, o ile podczas tworzenia klastra zaznaczono pole wyboru **Zakończ po \_\_ min nieaktywności**.</span></span> <span data-ttu-id="6af7b-265">W takim przypadku nieaktywny klaster automatycznie zatrzymuje się po określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="6af7b-265">W takim przypadku nieaktywny klaster automatycznie zatrzymuje się po określonym czasie.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6af7b-266">Kolejne kroki</span><span class="sxs-lookup"><span data-stu-id="6af7b-266">Kolejne kroki</span></span>

<span data-ttu-id="6af7b-267">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6af7b-267">W niniejszym samouczku zawarto informacje na temat wykonywania następujących czynności:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="6af7b-268">Tworzenie usługi Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-268">Tworzenie usługi Azure Databricks</span></span>
> * <span data-ttu-id="6af7b-269">Tworzenie klastra Spark w usłudze Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-269">Tworzenie klastra Spark w usłudze Azure Databricks</span></span>
> * <span data-ttu-id="6af7b-270">Tworzenie notesu w usłudze Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-270">Tworzenie notesu w usłudze Azure Databricks</span></span>
> * <span data-ttu-id="6af7b-271">Wyodrębnianie danych z konta usługi Data Lake Storage Gen2</span><span class="sxs-lookup"><span data-stu-id="6af7b-271">Wyodrębnianie danych z konta usługi Data Lake Storage Gen2</span></span>
> * <span data-ttu-id="6af7b-272">Przekształcanie danych w usłudze Azure Databricks</span><span class="sxs-lookup"><span data-stu-id="6af7b-272">Przekształcanie danych w usłudze Azure Databricks</span></span>
> * <span data-ttu-id="6af7b-273">Ładowanie danych do usługi Azure SQL Data Warehouse</span><span class="sxs-lookup"><span data-stu-id="6af7b-273">Ładowanie danych do usługi Azure SQL Data Warehouse</span></span>

<span data-ttu-id="6af7b-274">Przejdź do następnego samouczka, aby dowiedzieć się więcej na temat przesyłania strumieniowego danych w czasie rzeczywistym do usługi Azure Databricks przy użyciu usługi Azure Event Hubs.</span><span class="sxs-lookup"><span data-stu-id="6af7b-274">Przejdź do następnego samouczka, aby dowiedzieć się więcej na temat przesyłania strumieniowego danych w czasie rzeczywistym do usługi Azure Databricks przy użyciu usługi Azure Event Hubs.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="6af7b-275">Przesyłanie strumieniowe danych do usługi Azure Databricks przy użyciu usługi Event Hubs</span><span class="sxs-lookup"><span data-stu-id="6af7b-275">Przesyłanie strumieniowe danych do usługi Azure Databricks przy użyciu usługi Event Hubs</span></span>](databricks-stream-from-eventhubs.md)