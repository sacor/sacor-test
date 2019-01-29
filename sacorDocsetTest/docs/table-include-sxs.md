---
title: Configure Reporting Services to Use a Subject Alternative Name | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
  - reporting-services-native
ms.topic: conceptual
ms.assetid: ce458f9f-4b4f-4a58-aa75-9a90dda1e622
author: maggiesmsft
ms.author: douglasl
manager: craigg
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a><span data-ttu-id="730af-102">Configure Reporting Services to Use a Subject Alternative Name</span><span class="sxs-lookup"><span data-stu-id="730af-102">Configure Reporting Services to Use a Subject Alternative Name</span></span>
  <span data-ttu-id="730af-103">This topic explains how to configure ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) to use a subject alternative name (SAN) by modifying the rsreportserver.config file and using the Netsh.exe tool.</span><span class="sxs-lookup"><span data-stu-id="730af-103">This topic explains how to configure ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) to use a subject alternative name (SAN) by modifying the rsreportserver.config file and using the Netsh.exe tool.</span></span>  
  
||  
|-|  
|<span data-ttu-id="730af-104">**applies](../includes/applies-md.md)]**  ssRSnoversion](../includes/ssrsnoversion-md.md)] Native mode</span><span class="sxs-lookup"><span data-stu-id="730af-104">**applies](../includes/applies-md.md)]**  ssRSnoversion](../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 <span data-ttu-id="730af-105">The instructions apply to the Reporting Service URL as well as a Web Service URL.</span><span class="sxs-lookup"><span data-stu-id="730af-105">The instructions apply to the Reporting Service URL as well as a Web Service URL.</span></span>  
  
 <span data-ttu-id="730af-106">To use a SAN, the SSL certificate must be registered on the server, signed, and have the private key.</span><span class="sxs-lookup"><span data-stu-id="730af-106">To use a SAN, the SSL certificate must be registered on the server, signed, and have the private key.</span></span> <span data-ttu-id="730af-107">You cannot use a self-signed certificate</span><span class="sxs-lookup"><span data-stu-id="730af-107">You cannot use a self-signed certificate</span></span>  
  
 <span data-ttu-id="730af-108">URLs in ssRSnoversion](../includes/ssrsnoversion-md.md)] can be configured to use an SSL certificate.</span><span class="sxs-lookup"><span data-stu-id="730af-108">URLs in ssRSnoversion](../includes/ssrsnoversion-md.md)] can be configured to use an SSL certificate.</span></span> <span data-ttu-id="730af-109">A certificate normally has just a subject name, which allows only one URL for an SSL (Secure Sockets Layer) session.</span><span class="sxs-lookup"><span data-stu-id="730af-109">A certificate normally has just a subject name, which allows only one URL for an SSL (Secure Sockets Layer) session.</span></span> <span data-ttu-id="730af-110">The SAN is an additional field in the certificate that allows an SSL service to listen and be valid for many URLs, and to share the SSL port with other applications.</span><span class="sxs-lookup"><span data-stu-id="730af-110">The SAN is an additional field in the certificate that allows an SSL service to listen and be valid for many URLs, and to share the SSL port with other applications.</span></span> <span data-ttu-id="730af-111">The SAN looks something like the following: www.s2.com.</span><span class="sxs-lookup"><span data-stu-id="730af-111">The SAN looks something like the following: www.s2.com.</span></span>  
  
 <span data-ttu-id="730af-112">For more information about SSL settings for ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Configure SSL Connections on a Native Mode Report Server](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span><span class="sxs-lookup"><span data-stu-id="730af-112">For more information about SSL settings for ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Configure SSL Connections on a Native Mode Report Server](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>  
  
### <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a><span data-ttu-id="730af-113">Configure SSRS to use a subject alternative name for Web Service URL</span><span class="sxs-lookup"><span data-stu-id="730af-113">Configure SSRS to use a subject alternative name for Web Service URL</span></span>  
  
1.  <span data-ttu-id="730af-114">Start Reporting Services Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="730af-114">Start Reporting Services Configuration Manager.</span></span>  
  
     <span data-ttu-id="730af-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="730af-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="730af-116">On the **Web Service URL** page, select an SSL port and SSL Certificate.</span><span class="sxs-lookup"><span data-stu-id="730af-116">On the **Web Service URL** page, select an SSL port and SSL Certificate.</span></span>  
  
     <span data-ttu-id="730af-117">![Reporting Services Configuration Manager](media/reportingservices-configurationmanager.png "Reporting Services Configuration Manager")</span><span class="sxs-lookup"><span data-stu-id="730af-117">![Reporting Services Configuration Manager](media/reportingservices-configurationmanager.png "Reporting Services Configuration Manager")</span></span>  
  
     <span data-ttu-id="730af-118">The configuration manager registers the SSL certificate for the port.</span><span class="sxs-lookup"><span data-stu-id="730af-118">The configuration manager registers the SSL certificate for the port.</span></span>  
  
3.  <span data-ttu-id="730af-119">Open the rsreportserver.config file.</span><span class="sxs-lookup"><span data-stu-id="730af-119">Open the rsreportserver.config file.</span></span>  
  
     <span data-ttu-id="730af-120">For SSRS Native mode, the file is located by default in the following folder.</span><span class="sxs-lookup"><span data-stu-id="730af-120">For SSRS Native mode, the file is located by default in the following folder.</span></span>  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  <span data-ttu-id="730af-121">Copy the URL section for the Report Server Web Service application.</span><span class="sxs-lookup"><span data-stu-id="730af-121">Copy the URL section for the Report Server Web Service application.</span></span>  
  
     <span data-ttu-id="730af-122">For example, the following is the original URL section.</span><span class="sxs-lookup"><span data-stu-id="730af-122">For example, the following is the original URL section.</span></span>  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     <span data-ttu-id="730af-123">The following is the modified URL section.</span><span class="sxs-lookup"><span data-stu-id="730af-123">The following is the modified URL section.</span></span>  
  
    ```  
    <URL>  
         <UrlString>https://www.s1.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
        <URL>  
         <UrlString>https://www.s2.com:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
5.  <span data-ttu-id="730af-124">Save the rsreportserver.config file.</span><span class="sxs-lookup"><span data-stu-id="730af-124">Save the rsreportserver.config file.</span></span>  
  
6.  <span data-ttu-id="730af-125">Start a command prompt as an administrator, and run the Netsh.exe tool.</span><span class="sxs-lookup"><span data-stu-id="730af-125">Start a command prompt as an administrator, and run the Netsh.exe tool.</span></span>  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  <span data-ttu-id="730af-126">Switch to the http context by typing the following.</span><span class="sxs-lookup"><span data-stu-id="730af-126">Switch to the http context by typing the following.</span></span>  
  
    ```  
    Netsh>http  
    ```  
  
8.  <span data-ttu-id="730af-127">Show the existing urlacls by typing the following.</span><span class="sxs-lookup"><span data-stu-id="730af-127">Show the existing urlacls by typing the following.</span></span>  
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     <span data-ttu-id="730af-128">An entry such as the following appears.</span><span class="sxs-lookup"><span data-stu-id="730af-128">An entry such as the following appears.</span></span>  
  
    ```  
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     <span data-ttu-id="730af-129">An urlacl is a DACL (Discretionary Access Control List) for a reserved URL.</span><span class="sxs-lookup"><span data-stu-id="730af-129">An urlacl is a DACL (Discretionary Access Control List) for a reserved URL.</span></span>  
  
9. <span data-ttu-id="730af-130">Create a new entry for the subject alternative name, with the same user and SDDL as the existing entry, by typing the following.</span><span class="sxs-lookup"><span data-stu-id="730af-130">Create a new entry for the subject alternative name, with the same user and SDDL as the existing entry, by typing the following.</span></span>  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. <span data-ttu-id="730af-131">On the **Report Server Status** page of the Reporting Services Configuration Manager, Click **Stop** and then click **Start** to restart the report server.</span><span class="sxs-lookup"><span data-stu-id="730af-131">On the **Report Server Status** page of the Reporting Services Configuration Manager, Click **Stop** and then click **Start** to restart the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730af-132">See Also</span><span class="sxs-lookup"><span data-stu-id="730af-132">See Also</span></span>  
 <span data-ttu-id="730af-133">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="730af-133">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="730af-134">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="730af-134">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="730af-135">[Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="730af-135">[Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="730af-136">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span><span class="sxs-lookup"><span data-stu-id="730af-136">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  