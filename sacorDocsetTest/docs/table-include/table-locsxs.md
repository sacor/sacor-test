---
title: Configurar Reporting Services para usar un nombre alternativo del asunto | Microsoft Docs
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
ms.openlocfilehash: 90649f491fac7d867ebad0516d1ccea5fc41d4a5
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2018
ms.locfileid: "48134175"
---
# <a name="configure-reporting-services-to-use-a-subject-alternative-name"></a><span data-ttu-id="cd75b-102">Configuración de Reporting Services para utilizar un nombre alternativo del asunto</span><span class="sxs-lookup"><span data-stu-id="cd75b-102">Configure Reporting Services to Use a Subject Alternative Name</span></span>
  <span data-ttu-id="cd75b-103">En este tema se explica cómo configurar [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) para usar un nombre alternativo del asunto (SAN) modificando el archivo rsreportserver.config y usando la herramienta Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="cd75b-103">This topic explains how to configure [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SSRS) to use a subject alternative name (SAN) by modifying the rsreportserver.config file and using the Netsh.exe tool.</span></span>  
  
||  
|-|  
|<span data-ttu-id="cd75b-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] </span><span class="sxs-lookup"><span data-stu-id="cd75b-104">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 <span data-ttu-id="cd75b-105">Las instrucciones son válidas para la dirección URL del servicio de generación de informes y para la dirección URL del servicio web.</span><span class="sxs-lookup"><span data-stu-id="cd75b-105">The instructions apply to the Reporting Service URL as well as a Web Service URL.</span></span>  
  
 <span data-ttu-id="cd75b-106">Para utilizar el SAN, el certificado SSL debe estar registrado en el servidor, firmado y tener la clave privada.</span><span class="sxs-lookup"><span data-stu-id="cd75b-106">To use a SAN, the SSL certificate must be registered on the server, signed, and have the private key.</span></span> <span data-ttu-id="cd75b-107">No puede utilizar un certificado autofirmado</span><span class="sxs-lookup"><span data-stu-id="cd75b-107">You cannot use a self-signed certificate</span></span>  
  
 <span data-ttu-id="cd75b-108">Las direcciones URL en [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] puede configurarse para usar un certificado SSL.</span><span class="sxs-lookup"><span data-stu-id="cd75b-108">URLs in [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] can be configured to use an SSL certificate.</span></span> <span data-ttu-id="cd75b-109">Normalmente, un certificado solo tiene un nombre de asunto, lo que permite solo una dirección URL para una sesión SSL (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="cd75b-109">A certificate normally has just a subject name, which allows only one URL for an SSL (Secure Sockets Layer) session.</span></span> <span data-ttu-id="cd75b-110">El SAN es un campo adicional del certificado que permite a un servicio SSL escuchar y ser válido para varias direcciones URL, y compartir el puerto SSL con otras aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="cd75b-110">The SAN is an additional field in the certificate that allows an SSL service to listen and be valid for many URLs, and to share the SSL port with other applications.</span></span> <span data-ttu-id="cd75b-111">El SAN es tiene un aspecto parecido a lo siguiente: www.s2.com.</span><span class="sxs-lookup"><span data-stu-id="cd75b-111">The SAN looks something like the following: www.s2.com.</span></span>  
  
 <span data-ttu-id="cd75b-112">Para obtener más información sobre la configuración de SSL para [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], consulte [configurar conexiones SSL en un servidor de informes de modo nativo](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span><span class="sxs-lookup"><span data-stu-id="cd75b-112">For more information about SSL settings for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], see [Configure SSL Connections on a Native Mode Report Server](security/configure-ssl-connections-on-a-native-mode-report-server.md).</span></span>  
  
### <a name="configure-ssrs-to-use-a-subject-alternative-name-for-web-service-url"></a><span data-ttu-id="cd75b-113">Configure SSRS para utilizar un nombre alternativo del asunto para la dirección URL del servicio web</span><span class="sxs-lookup"><span data-stu-id="cd75b-113">Configure SSRS to use a subject alternative name for Web Service URL</span></span>  
  
1.  <span data-ttu-id="cd75b-114">Inicie el Administrador de configuración de Reporting Services.</span><span class="sxs-lookup"><span data-stu-id="cd75b-114">Start Reporting Services Configuration Manager.</span></span>  
  
     <span data-ttu-id="cd75b-115">Para obtener más información, vea [Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span><span class="sxs-lookup"><span data-stu-id="cd75b-115">For more information, see [Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="cd75b-116">En la página **Dirección URL del servicio web** , seleccione un puerto SSL y un certificado SSL.</span><span class="sxs-lookup"><span data-stu-id="cd75b-116">On the **Web Service URL** page, select an SSL port and SSL Certificate.</span></span>  
  
     <span data-ttu-id="cd75b-117">![Administrador de configuración de Reporting Services](media/reportingservices-configurationmanager.png "Administrador de configuración de Reporting Services")</span><span class="sxs-lookup"><span data-stu-id="cd75b-117">![Reporting Services Configuration Manager](media/reportingservices-configurationmanager.png "Reporting Services Configuration Manager")</span></span>  
  
     <span data-ttu-id="cd75b-118">El administrador de configuración registra el certificado SSL para el puerto.</span><span class="sxs-lookup"><span data-stu-id="cd75b-118">The configuration manager registers the SSL certificate for the port.</span></span>  
  
3.  <span data-ttu-id="cd75b-119">Abra el archivo rsreportserver.config.</span><span class="sxs-lookup"><span data-stu-id="cd75b-119">Open the rsreportserver.config file.</span></span>  
  
     <span data-ttu-id="cd75b-120">Para SSRS en el modo nativo, el archivo se encuentra predeterminadamente en la carpeta siguiente.</span><span class="sxs-lookup"><span data-stu-id="cd75b-120">For SSRS Native mode, the file is located by default in the following folder.</span></span>  
  
    ```  
    \Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer  
    ```  
  
4.  <span data-ttu-id="cd75b-121">Copie la sección de la URL para la aplicación de servicios web del servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="cd75b-121">Copy the URL section for the Report Server Web Service application.</span></span>  
  
     <span data-ttu-id="cd75b-122">Por ejemplo, la siguiente es la sección URL original.</span><span class="sxs-lookup"><span data-stu-id="cd75b-122">For example, the following is the original URL section.</span></span>  
  
    ```  
        <URL>  
         <UrlString>https://localhost:443</UrlString>  
         <AccountSid>S-1-5-20</AccountSid>  
         <AccountName>NT Authority\NetworkService</AccountName>  
        </URL>  
  
    ```  
  
     <span data-ttu-id="cd75b-123">El siguiente es la sección URL modificada.</span><span class="sxs-lookup"><span data-stu-id="cd75b-123">The following is the modified URL section.</span></span>  
  
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
  
5.  <span data-ttu-id="cd75b-124">Guarde el archivo rsreportserver.config.</span><span class="sxs-lookup"><span data-stu-id="cd75b-124">Save the rsreportserver.config file.</span></span>  
  
6.  <span data-ttu-id="cd75b-125">Inicie un símbolo del sistema como administrador y ejecute la herramienta Netsh.exe.</span><span class="sxs-lookup"><span data-stu-id="cd75b-125">Start a command prompt as an administrator, and run the Netsh.exe tool.</span></span>  
  
    ```  
    C:\windows\system32\netsh  
    ```  
  
7.  <span data-ttu-id="cd75b-126">Cambie al contexto http escribiendo lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="cd75b-126">Switch to the http context by typing the following.</span></span>  
  
    ```  
    Netsh>http  
    ```  
  
8.  <span data-ttu-id="cd75b-127">Muestre las urlacls existentes escribiendo lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="cd75b-127">Show the existing urlacls by typing the following.</span></span>  
  
    ```  
    Netsh http>show urlacl  
    ```  
  
     <span data-ttu-id="cd75b-128">Aparece una entrada como la siguiente.</span><span class="sxs-lookup"><span data-stu-id="cd75b-128">An entry such as the following appears.</span></span>  
  
    ```  
    Reserved URL            : https:// www.s1.com:443/ReportServer/  
        User: NT SERVICE\ReportServer  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;S-1-5-80-1234567890-123456789-123456789-123456789-1234567890)  
    ```  
  
     <span data-ttu-id="cd75b-129">Una urlacl es una DACL (lista de control de acceso discrecional) para una dirección URL reservada.</span><span class="sxs-lookup"><span data-stu-id="cd75b-129">An urlacl is a DACL (Discretionary Access Control List) for a reserved URL.</span></span>  
  
9. <span data-ttu-id="cd75b-130">Cree una nueva entrada para el nombre alternativo del asunto, con el mismo usuario y SDDL que la entrada existente, escribiendo lo siguiente.</span><span class="sxs-lookup"><span data-stu-id="cd75b-130">Create a new entry for the subject alternative name, with the same user and SDDL as the existing entry, by typing the following.</span></span>  
  
    ```  
    netsh http>add urlacl  url=https://www.s2.com:443/ReportServer    
    user="NT Service\ReportServer" sddl=D:(A;;GX;;;S-1-5-80-1234567980-12346579-123456789-123456789-1234567890)  
  
    ```  
  
10. <span data-ttu-id="cd75b-131">En la página **Estado del servidor de informes** del Administrador de configuración de Reporting Services, haga clic en **Detener** y, a continuación, haga clic en **Iniciar** para reiniciar el servidor de informes.</span><span class="sxs-lookup"><span data-stu-id="cd75b-131">On the **Report Server Status** page of the Reporting Services Configuration Manager, Click **Stop** and then click **Start** to restart the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd75b-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="cd75b-132">See Also</span></span>  
 <span data-ttu-id="cd75b-133">[Archivo de configuración RSReportServer](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="cd75b-133">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="cd75b-134">[Administrador de configuración de Reporting Services &#40;modo nativo&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="cd75b-134">[Reporting Services Configuration Manager &#40;Native Mode&#41;](../sql-server/install/reporting-services-configuration-manager-native-mode.md) </span></span>  
 <span data-ttu-id="cd75b-135">[Modificar un archivo de configuración de Reporting Services &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="cd75b-135">[Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="cd75b-136">Configurar las direcciones URL del servidor de informes &#40;Administrador de configuración de SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cd75b-136">Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;</span></span>](install-windows/configure-report-server-urls-ssrs-configuration-manager.md)  
  
  