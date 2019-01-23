---
title: Novinky ve verzi 1810
titleSuffix: Configuration Manager
description: Získáte podrobnosti o novinkách, počínaje 1810 verzi aktuální větve nástroje Configuration Manager.
ms.date: 12/20/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4812324b-e6aa-4431-bf1d-9fcd763a8caa
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 60d1c93acc2fcc2c04d09cd8f0ec0c083089a8ec
ms.sourcegitcommit: a3cec96a771eed69e58a29917d1a3fe1a5fb2e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2019
ms.locfileid: "54250591"
---
# <a name="whats-new-in-version-1810-of-configuration-manager-current-branch"></a><span data-ttu-id="9ad75-103">Co je nového v 1810 verzi aktuální větve nástroje Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="9ad75-103">What's new in version 1810 of Configuration Manager current branch</span></span>

<span data-ttu-id="9ad75-104">*Platí pro: System Center Configuration Manager (Current Branch)*</span><span class="sxs-lookup"><span data-stu-id="9ad75-104">*Applies to: System Center Configuration Manager (Current Branch)*</span></span>

<span data-ttu-id="9ad75-105">Aktualizace 1810 pro aktuální větev nástroje Configuration Manager je k dispozici jako aktualizace v konzole.</span><span class="sxs-lookup"><span data-stu-id="9ad75-105">Update 1810 for Configuration Manager current branch is available as an in-console update.</span></span> <span data-ttu-id="9ad75-106">Tato aktualizace na serverech, na kterých běží verze 1710, 1802 nebo 1806.</span><span class="sxs-lookup"><span data-stu-id="9ad75-106">Apply this update on sites that run version 1710, 1802, or 1806.</span></span> <!-- baseline only statement: When installing a new site, it's also available as a baseline version.-->

<span data-ttu-id="9ad75-107">Vždy zkontrolujte nejnovější kontrolní seznam pro instalaci této aktualizace.</span><span class="sxs-lookup"><span data-stu-id="9ad75-107">Always review the latest checklist for installing this update.</span></span> <span data-ttu-id="9ad75-108">Další informace najdete v tématu [kontrolní seznam pro instalaci aktualizace 1810](/sccm/core/servers/manage/checklist-for-installing-update-1810).</span><span class="sxs-lookup"><span data-stu-id="9ad75-108">For more information, see [Checklist for installing update 1810](/sccm/core/servers/manage/checklist-for-installing-update-1810).</span></span> <span data-ttu-id="9ad75-109">Po aktualizaci lokality také zkontrolujte [kontrolní seznam aktualizace po](/sccm/core/servers/manage/checklist-for-installing-update-1810#post-update-checklist).</span><span class="sxs-lookup"><span data-stu-id="9ad75-109">After you update a site, also review the [Post-update checklist](/sccm/core/servers/manage/checklist-for-installing-update-1810#post-update-checklist).</span></span>

> [!Note]  
> <span data-ttu-id="9ad75-110">Tento článek uvádí aktuálně všechny důležité funkce v této verzi.</span><span class="sxs-lookup"><span data-stu-id="9ad75-110">This article currently lists all significant features in this version.</span></span> <span data-ttu-id="9ad75-111">Ne všechny části však ještě propojit aktualizovaný obsah s další informace o nových funkcích.</span><span class="sxs-lookup"><span data-stu-id="9ad75-111">However, not all sections yet link to updated content with further information on the new features.</span></span> <span data-ttu-id="9ad75-112">Kontrolovat tuto stránku pravidelně aktualizací.</span><span class="sxs-lookup"><span data-stu-id="9ad75-112">Keep checking this page regularly for updates.</span></span> <span data-ttu-id="9ad75-113">Změny jsou označeny pomocí ***[aktualizovat]*** značky.</span><span class="sxs-lookup"><span data-stu-id="9ad75-113">Changes are noted with the ***[Updated]*** tag.</span></span> <span data-ttu-id="9ad75-114">Tato poznámka se odebere, když obsah se dokončuje.</span><span class="sxs-lookup"><span data-stu-id="9ad75-114">This note will be removed when the content is finalized.</span></span>  

<span data-ttu-id="9ad75-115">Kromě nových funkcí tato verze rovněž obsahuje další změny, jako jsou opravy chyb.</span><span class="sxs-lookup"><span data-stu-id="9ad75-115">Aside from new features, this release also includes additional changes such as bug fixes.</span></span> <span data-ttu-id="9ad75-116">Další informace najdete v tématu [souhrn změn v aktuální větvi nástroje Configuration Manager verze 1810](https://support.microsoft.com/help/4482169).</span><span class="sxs-lookup"><span data-stu-id="9ad75-116">For more information, see [Summary of changes in Configuration Manager current branch, version 1810](https://support.microsoft.com/help/4482169).</span></span>

<!--
For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [PowerShell 1810 Release Notes](https://docs.microsoft.com/powershell/sccm/1810_release_notes?view=sccm-ps).

The following additional updates to this release are also now available:
- [Update rollup for Configuration Manager current branch, version 1810](https://support.microsoft.com/help/4462978)
-->

> [!Important]  
> <span data-ttu-id="9ad75-117">Abyste mohli využívat nové funkce nástroje Configuration Manager, nejprve aktualizovat klienty na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="9ad75-117">To take advantage of new Configuration Manager features, first update clients to the latest version.</span></span> <span data-ttu-id="9ad75-118">Nové funkce se zobrazí v konzole nástroje Configuration Manager při aktualizaci lokality a konzoly, úplného scénáře nejsou funkční až do verze klienta je také na nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="9ad75-118">While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.</span></span>

<span data-ttu-id="9ad75-119">Tento článek shrnuje změny a nové funkce v Configuration Manageru verze 1810.</span><span class="sxs-lookup"><span data-stu-id="9ad75-119">This article summarizes the changes and new features in Configuration Manager, version 1810.</span></span>  



## <a name="bkmk_deprecated"></a> <span data-ttu-id="9ad75-120">Zastaralé funkce a operační systémy</span><span class="sxs-lookup"><span data-stu-id="9ad75-120">Deprecated features and operating systems</span></span>

<span data-ttu-id="9ad75-121">Další informace o podpoře změny předtím, než jsou v nich implementované v [odebrané a zastaralé položky](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated).</span><span class="sxs-lookup"><span data-stu-id="9ad75-121">Learn about support changes before they're implemented in [removed and deprecated items](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated).</span></span>

<span data-ttu-id="9ad75-122">Od 14. srpna 2018 se funkce správy mobilních zařízení hybridní je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="9ad75-122">Starting on August 14, 2018, the hybrid mobile device management feature is deprecated.</span></span> <span data-ttu-id="9ad75-123">Další informace najdete v tématu [hybridní MDM](/sccm/mdm/understand/hybrid-mobile-device-management).<!--Intune feature 2683117--></span><span class="sxs-lookup"><span data-stu-id="9ad75-123">For more information, see [What is hybrid MDM](/sccm/mdm/understand/hybrid-mobile-device-management).<!--Intune feature 2683117--></span></span>  

<span data-ttu-id="9ad75-124">Podpora pro System Center Endpoint Protection (SCEP) pro Mac a Linux (všechny verze) končí 31. prosince 2018.</span><span class="sxs-lookup"><span data-stu-id="9ad75-124">Support for System Center Endpoint Protection (SCEP) for Mac and Linux (all versions) ends on December 31, 2018.</span></span> <span data-ttu-id="9ad75-125">Po ukončení podpory může být pozastaveno dostupnost nových definic virů pro SCEP pro Mac a SCEP pro Linux.</span><span class="sxs-lookup"><span data-stu-id="9ad75-125">Availability of new virus definitions for SCEP for Mac and SCEP for Linux may be discontinued after the end of support.</span></span> <span data-ttu-id="9ad75-126">Další informace najdete v tématu [konec podpory blogový příspěvek](https://go.microsoft.com/fwlink/?linkid=870182).</span><span class="sxs-lookup"><span data-stu-id="9ad75-126">For more information, see [End of support blog post](https://go.microsoft.com/fwlink/?linkid=870182).</span></span>

<span data-ttu-id="9ad75-127">Nasazení Classic služby v Azure jsou už zastaralé v nástroji Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9ad75-127">Classic service deployments in Azure are now deprecated in Configuration Manager.</span></span> <span data-ttu-id="9ad75-128">Začněte používat nasazení Azure Resource Manageru pro bránu pro správu cloudu a distribuční bod cloudu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-128">Start using Azure Resource Manager deployments for the cloud management gateway and the cloud distribution point.</span></span> <span data-ttu-id="9ad75-129">Další informace najdete v tématu [plánování CMG](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager).</span><span class="sxs-lookup"><span data-stu-id="9ad75-129">For more information, see [Plan for CMG](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager).</span></span>
<!--
Version 1810 drops support for the following products:
-->



## <a name="bkmk_infra"></a> <span data-ttu-id="9ad75-130">Infrastruktura lokality</span><span class="sxs-lookup"><span data-stu-id="9ad75-130">Site infrastructure</span></span>

### <a name="support-for-windows-server-2019"></a><span data-ttu-id="9ad75-131">Podpora pro systém Windows Server. 2019</span><span class="sxs-lookup"><span data-stu-id="9ad75-131">Support for Windows Server 2019</span></span>
<span data-ttu-id="9ad75-132"><!--1359195--> Nástroj Configuration Manager teď podporuje 2019 serveru systému Windows a Windows Server verze 1809, jako systémy lokality.</span><span class="sxs-lookup"><span data-stu-id="9ad75-132"><!--1359195--> Configuration Manager now supports Windows Server 2019 and Windows Server, version 1809, as site systems.</span></span> 

<span data-ttu-id="9ad75-133">Další informace najdete v tématu [podporované operační systémy pro servery systému lokality](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).</span><span class="sxs-lookup"><span data-stu-id="9ad75-133">For more information, see [Supported operating systems for site system servers](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).</span></span>


### <a name="hierarchy-support-for-site-server-high-availability"></a><span data-ttu-id="9ad75-134">Hierarchie podporovat pro zajištění vysoké dostupnosti serveru lokality</span><span class="sxs-lookup"><span data-stu-id="9ad75-134">Hierarchy support for site server high availability</span></span>
<span data-ttu-id="9ad75-135"><!--1358224--> Lokality centrální správy a podřízených primárních lokalit můžete teď mít server další lokality v pasivním režimu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-135"><!--1358224--> Central administration sites and child primary sites can now have an additional site server in passive mode.</span></span> 

<!--For more information, see [Site server high availability](/sccm/core/servers/deploy/configure/site-server-high-availability).-->


### <a name="improvements-to-setup-prerequisites"></a><span data-ttu-id="9ad75-136">Vylepšení požadovaných součástí instalace</span><span class="sxs-lookup"><span data-stu-id="9ad75-136">Improvements to setup prerequisites</span></span>

<span data-ttu-id="9ad75-137">Při instalaci nebo aktualizaci na verzi 1810, instalační program nástroje Configuration Manager nyní zahrnuje nebo zlepšuje následující kontroly splnění podmínek:</span><span class="sxs-lookup"><span data-stu-id="9ad75-137">When you install or update to version 1810, Configuration Manager setup now includes or improves the following prerequisite checks:</span></span>

- <span data-ttu-id="9ad75-138">**Systém čeká se na restart**: Tato kontrola požadovaných součástí je nyní odolnější.</span><span class="sxs-lookup"><span data-stu-id="9ad75-138">**Pending system restart**: This prerequisite check is now more resilient.</span></span> <span data-ttu-id="9ad75-139">Zkontroluje další klíče registru pro funkce Windows.</span><span class="sxs-lookup"><span data-stu-id="9ad75-139">It checks additional registry keys for Windows features.</span></span> <span data-ttu-id="9ad75-140">Další informace najdete v tématu [systém čeká se na restart](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#pending-system-restart).</span><span class="sxs-lookup"><span data-stu-id="9ad75-140">For more information, see [Pending system restart](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#pending-system-restart).</span></span> <!--SCCMDocs-pr issue 3010-->  

- <span data-ttu-id="9ad75-141">**SQL změnit vyčištění sledování**: Novou kontrolu, pokud databáze lokality, má nevyřízené položky data sledování změn SQL.</span><span class="sxs-lookup"><span data-stu-id="9ad75-141">**SQL change tracking cleanup**: A new check if the site database has a backlog of SQL change tracking data.</span></span> <span data-ttu-id="9ad75-142">Další informace, včetně postupu pro ověření a zrušte zaškrtnutí těchto nevyřízených položek, naleznete v tématu [SQL změnit vyčištění sledování](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#bkmk_changetracking).</span><span class="sxs-lookup"><span data-stu-id="9ad75-142">For more information, including a procedure to verify and clear this backlog, see [SQL change tracking cleanup](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#bkmk_changetracking).</span></span> <!--SCCMDocs-pr issue 3023-->  

- <span data-ttu-id="9ad75-143">**Verze SQL Native Client**: Tato kontrola požadovaných součástí je aktualizována o verzích SQL Native Client, které podporují protokol TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="9ad75-143">**SQL Native Client version**: This prerequisite check is updated for versions of SQL Native Client that support TLS 1.2.</span></span> <span data-ttu-id="9ad75-144">Minimální verze je [SQL 2012 SP4](https://www.microsoft.com/download/details.aspx?id=50402).</span><span class="sxs-lookup"><span data-stu-id="9ad75-144">The minimum version is [SQL 2012 SP4](https://www.microsoft.com/download/details.aspx?id=50402).</span></span> <span data-ttu-id="9ad75-145">Další informace najdete v tématu [verze SQL Native Client](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#sql-native-client).</span><span class="sxs-lookup"><span data-stu-id="9ad75-145">For more information, see [SQL Native Client version](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#sql-native-client).</span></span> <!--SCCMDocs-pr issue 3094-->  

- <span data-ttu-id="9ad75-146">**V uzlu clusteru Windows serveru**: Proces instalace nástroje Configuration Manager už blokuje instalaci role serveru lokality na počítači s rolí Windows pro převzetí služeb při selhání.</span><span class="sxs-lookup"><span data-stu-id="9ad75-146">**Site system on Windows cluster node**: The Configuration Manager setup process no longer blocks installation of the site server role on a computer with the Windows role for Failover Clustering.</span></span> <span data-ttu-id="9ad75-147">SQL Always On vyžaduje tato role, takže dříve nelze společné umístění databáze lokality na serveru lokality.</span><span class="sxs-lookup"><span data-stu-id="9ad75-147">SQL Always On requires this role, so previously you couldn't colocate the site database on the site server.</span></span> <span data-ttu-id="9ad75-148">Díky této změně můžete vytvořit lokality s vysokou dostupností s menší počet serverů s použitím SQL Always On a server lokality v pasivním režimu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-148">With this change, you can create a highly available site with fewer servers by using SQL Always On and a site server in passive mode.</span></span> <span data-ttu-id="9ad75-149">Další informace najdete v tématu [clusteru převzetí služeb při selhání Windows](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#windows-failover-cluster).</span><span class="sxs-lookup"><span data-stu-id="9ad75-149">For more information, see [Windows Failover Cluster](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#windows-failover-cluster).</span></span> <!--1359132-->  




### <a name="new-permission-for-client-notification-actions"></a><span data-ttu-id="9ad75-150">Nová oprávnění pro klientské oznámení akce</span><span class="sxs-lookup"><span data-stu-id="9ad75-150">New permission for client notification actions</span></span>
<span data-ttu-id="9ad75-151"><!--SCCMDocs-pr issue #2972--> Klientské oznámení akce nyní vyžadovat, aby **oznámit prostředků** oprávnění ve třídě SMS_Collection.</span><span class="sxs-lookup"><span data-stu-id="9ad75-151"><!--SCCMDocs-pr issue #2972--> Client notification actions now require the **Notify Resource** permission on the SMS_Collection class.</span></span> <span data-ttu-id="9ad75-152">Následující předdefinované role mají toto oprávnění ve výchozím nastavení:</span><span class="sxs-lookup"><span data-stu-id="9ad75-152">The following built-in roles have this permission by default:</span></span>
- <span data-ttu-id="9ad75-153">Správce s úplnými oprávněními</span><span class="sxs-lookup"><span data-stu-id="9ad75-153">Full Administrator</span></span>  
- <span data-ttu-id="9ad75-154">Správce infrastruktury</span><span class="sxs-lookup"><span data-stu-id="9ad75-154">Infrastructure Administrator</span></span>  

<span data-ttu-id="9ad75-155">Přidáte toto oprávnění k žádné vlastní roli, které je potřeba použít klientské oznámení akce.</span><span class="sxs-lookup"><span data-stu-id="9ad75-155">Add this permission to any custom roles that need to use client notification actions.</span></span> 

<span data-ttu-id="9ad75-156">Další informace najdete v tématu [oznámení klienta](/sccm/core/clients/manage/client-notification).</span><span class="sxs-lookup"><span data-stu-id="9ad75-156">For more information, see [Client notifications](/sccm/core/clients/manage/client-notification).</span></span>



## <a name="bkmk_content"></a><span data-ttu-id="9ad75-157">Správa obsahu</span><span class="sxs-lookup"><span data-stu-id="9ad75-157">Content management</span></span>

### <a name="new-boundary-group-options"></a><span data-ttu-id="9ad75-158">Nové možnosti pro skupiny hranic</span><span class="sxs-lookup"><span data-stu-id="9ad75-158">New boundary group options</span></span>
<span data-ttu-id="9ad75-159"><!--1358749--> Hraniční skupiny teď obsahují následující dodatečná nastavení získáte větší kontrolu nad distribuce obsahu ve vašem prostředí:</span><span class="sxs-lookup"><span data-stu-id="9ad75-159"><!--1358749--> Boundary groups now include the following additional settings to give you more control over content distribution in your environment:</span></span>

- <span data-ttu-id="9ad75-160">**Preferovat distribučních bodů přes partnerské uzly pomocí stejné podsíti**: Ve výchozím nastavení bod správy upřednostňuje zdroje sdílené mezipaměti v horní části seznamu umístění obsahu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-160">**Prefer distribution points over peers with the same subnet**: By default, the management point prioritizes peer cache sources at the top of the list of content locations.</span></span> <span data-ttu-id="9ad75-161">Toto nastavení změní který tuto prioritu pro klienty, kteří jsou ve stejné podsíti jako zdroj sdílené mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9ad75-161">This setting reverses that priority for clients that are in the same subnet as the peer cache source.</span></span>  

- <span data-ttu-id="9ad75-162">**Preferovat cloudové distribuční body v distribučních bodech**: Pokud máte firemní pobočce s odkazem na Internetu rychlejší, můžete teď určit prioritu obsahu cloudové.</span><span class="sxs-lookup"><span data-stu-id="9ad75-162">**Prefer cloud distribution points over distribution points**: If you have a branch office with a faster internet link, you can now prioritize cloud content.</span></span>  

<span data-ttu-id="9ad75-163">Další informace najdete v tématu [možnosti skupiny hranic pro sdílené soubory ke stažení](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_bgoptions).</span><span class="sxs-lookup"><span data-stu-id="9ad75-163">For more information, see [Boundary group options for peer downloads](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_bgoptions).</span></span>


### <a name="management-insights-rule-for-peer-cache-source-client-version"></a><span data-ttu-id="9ad75-164">Přehledy správy pravidlo pro verze klienta zdroje sdílené mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9ad75-164">Management insights rule for peer cache source client version</span></span>
<span data-ttu-id="9ad75-165"><!-- 1358008 --> **Přehledy správy** uzel má nové pravidlo k identifikaci klientů, které bude sloužit jako zdroj sdílené mezipaměti, ale nebyla upgradována z verze pre-1806 klienta.</span><span class="sxs-lookup"><span data-stu-id="9ad75-165"><!-- 1358008 --> The **Management Insights** node has a new rule to identify clients that serve as a peer cache source but haven't upgraded from a pre-1806 client version.</span></span> <span data-ttu-id="9ad75-166">Nové pravidlo je **zdroje sdílené mezipaměti upgradovat na nejnovější verzi klienta nástroje Configuration Manager**, a je součástí nového **proaktivní údržby** skupiny pravidel.</span><span class="sxs-lookup"><span data-stu-id="9ad75-166">The new rule is **Upgrade peer cache sources to the latest version of the Configuration Manager client**, and is part of the new **Proactive Maintenance** rule group.</span></span> <span data-ttu-id="9ad75-167">Klienti Pre-1806 nelze použít jako zdroj sdílené mezipaměti pro klienty, kteří používají verzi 1806 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9ad75-167">Pre-1806 clients can't be used as a peer cache source for clients that run version 1806 or later.</span></span> <span data-ttu-id="9ad75-168">Vyberte **provést akci** otevření zobrazení zařízení, která zobrazí seznam klientů.</span><span class="sxs-lookup"><span data-stu-id="9ad75-168">Select **Take action** to open a device view that displays the list of clients.</span></span> 

<span data-ttu-id="9ad75-169">Další informace najdete v tématu [přehledy správy](/sccm/core/servers/manage/management-insights).</span><span class="sxs-lookup"><span data-stu-id="9ad75-169">For more information, see [Management insights](/sccm/core/servers/manage/management-insights).</span></span>



## <a name="bkmk_client"></a> <span data-ttu-id="9ad75-170">Správa klientů</span><span class="sxs-lookup"><span data-stu-id="9ad75-170">Client management</span></span>

### <a name="new-client-notification-action-to-wake-up-device"></a><span data-ttu-id="9ad75-171">Nová akce oznámení klienta k probuzení zařízení</span><span class="sxs-lookup"><span data-stu-id="9ad75-171">New client notification action to wake up device</span></span>
<span data-ttu-id="9ad75-172"><!--1317364--> Můžete teď probuzení klientů v konzole nástroje Configuration Manager i v případě, že klient není ve stejné podsíti jako server lokality.</span><span class="sxs-lookup"><span data-stu-id="9ad75-172"><!--1317364--> You can now wake up clients from the Configuration Manager console, even if the client isn't on the same subnet as the site server.</span></span> <span data-ttu-id="9ad75-173">Pokud potřebujete provést údržbu nebo dotaz zařízení, nejsou omezeny vzdálených klientů, kteří jsou v režimu spánku.</span><span class="sxs-lookup"><span data-stu-id="9ad75-173">If you need to do maintenance or query devices, you're not limited by remote clients that are asleep.</span></span> <span data-ttu-id="9ad75-174">Server lokality používá k identifikaci jiného klienta, který běží ve stejné podsíti vzdálené kanál.</span><span class="sxs-lookup"><span data-stu-id="9ad75-174">The site server uses the client notification channel to identify another client that's awake on the same remote subnet.</span></span> <span data-ttu-id="9ad75-175">Vzhůru Klient pak odešle probuzení na žádosti sítě LAN (magic paketů).</span><span class="sxs-lookup"><span data-stu-id="9ad75-175">The awake client then sends a wake on LAN request (magic packet).</span></span>

### <a name="new-option-to-perform-client-notification-from-devices-node"></a><span data-ttu-id="9ad75-176">Nová možnost provádět klientské oznámení z uzlu zařízení</span><span class="sxs-lookup"><span data-stu-id="9ad75-176">New option to perform client notification from devices node</span></span>
<span data-ttu-id="9ad75-177"><!--1317364--> Až 1810 **klientské oznámení** byla dostupná z uzlu kolekce zařízení nebo když jste zobrazili členství v kolekci zařízení jenom možnost.</span><span class="sxs-lookup"><span data-stu-id="9ad75-177"><!--1317364--> Up until 1810, the **Client Notification** option was only available from either the Device Collection node or when you viewed the membership of a Device Collection.</span></span> <span data-ttu-id="9ad75-178">Nyní je možné provést **klientské oznámení** z **zařízení** uzel přímo.</span><span class="sxs-lookup"><span data-stu-id="9ad75-178">It's now possible to perform a **Client Notification** from the **Devices** node directly.</span></span> <span data-ttu-id="9ad75-179">Požadavek bude v rámci zobrazení členství kolekce již není.</span><span class="sxs-lookup"><span data-stu-id="9ad75-179">There's no longer a requirement to be within a collection membership view.</span></span> 

<span data-ttu-id="9ad75-180">Další informace najdete v tématu [oznámení klienta](/sccm/core/clients/manage/client-notification).</span><span class="sxs-lookup"><span data-stu-id="9ad75-180">For more information, see [Client notifications](/sccm/core/clients/manage/client-notification).</span></span>


### <a name="improvements-to-collection-evaluation"></a><span data-ttu-id="9ad75-181">Vylepšení vyhodnocování kolekce</span><span class="sxs-lookup"><span data-stu-id="9ad75-181">Improvements to collection evaluation</span></span>
<span data-ttu-id="9ad75-182"><!--1358981--> Následující změny v chování při vyhodnocování kolekce může zlepšit výkon lokality:</span><span class="sxs-lookup"><span data-stu-id="9ad75-182"><!--1358981--> The following changes in collection evaluation behavior can improve site performance:</span></span>  
 
- <span data-ttu-id="9ad75-183">Dříve, při konfiguraci plánu na kolekce založené na dotazech webu by i nadále vyhodnotit dotaz, jestli jste povolili nastavení kolekce pro **naplánujte úplnou aktualizaci na této kolekci**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-183">Previously, when you configured a schedule on a query-based collection, the site would continue to evaluate the query whether or not you enabled the collection setting to **Schedule a full update on this collection**.</span></span> <span data-ttu-id="9ad75-184">Plně zakázat plán, musíte změnit plán **žádný**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-184">To fully disable the schedule, you had to change the schedule to **None**.</span></span> <span data-ttu-id="9ad75-185">Nyní webu vymaže plán když toto nastavení zakážete.</span><span class="sxs-lookup"><span data-stu-id="9ad75-185">Now the site clears the schedule when you disable this setting.</span></span> <span data-ttu-id="9ad75-186">K určení plánu pro vyhodnocování kolekce, povolte možnost **naplánujte úplnou aktualizaci na této kolekci**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-186">To specify a schedule for collection evaluation, enable the option to **Schedule a full update on this collection**.</span></span>  

- <span data-ttu-id="9ad75-187">Už se nedá vypnout hodnocení vestavěné kolekce jako **všechny systémy**, ale teď můžete nakonfigurovat plán.</span><span class="sxs-lookup"><span data-stu-id="9ad75-187">You can't disable the evaluation of built-in collections like **All Systems**, but now you can configure the schedule.</span></span> <span data-ttu-id="9ad75-188">Toto chování můžete upravit tuto akci v čase, který splňuje vaše podnikové požadavky.</span><span class="sxs-lookup"><span data-stu-id="9ad75-188">This behavior allows you to customize this action at a time that meets your business requirements.</span></span> 

<!--For more information, see [How to create collections](/sccm/core/clients/manage/collections/create-collections).-->


### <a name="improvement-to-client-installation"></a><span data-ttu-id="9ad75-189">Vylepšení instalace klienta</span><span class="sxs-lookup"><span data-stu-id="9ad75-189">Improvement to client installation</span></span>
<span data-ttu-id="9ad75-190"><!--1358840--> Při instalaci klienta nástroje Configuration Manager, proces ccmsetup kontaktuje bod správy k vyhledání nezbytné obsahu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-190"><!--1358840--> When installing the Configuration Manager client, the ccmsetup process contacts the management point to locate the necessary content.</span></span> <span data-ttu-id="9ad75-191">Dříve v tomto procesu bod správy vrátí pouze distribuční body v aktuální skupině hranic klienta.</span><span class="sxs-lookup"><span data-stu-id="9ad75-191">Previously in this process the management point only returns distribution points in the client's current boundary group.</span></span> <span data-ttu-id="9ad75-192">Pokud je k dispozici žádný obsah, proces instalace spadne zpět ke stažení obsahu z bodu správy.</span><span class="sxs-lookup"><span data-stu-id="9ad75-192">If no content is available, the setup process falls back to download content from the management point.</span></span> <span data-ttu-id="9ad75-193">Neexistuje žádná možnost vrátit zpět do distribučních bodů v jiných skupinách hranic, které může být nutný obsah.</span><span class="sxs-lookup"><span data-stu-id="9ad75-193">There's no option to fall back to distribution points in other boundary groups that might have the necessary content.</span></span> <span data-ttu-id="9ad75-194">Nyní bod správy vrátí distribučních bodů v závislosti na konfiguraci skupiny hranic.</span><span class="sxs-lookup"><span data-stu-id="9ad75-194">Now the management point returns distribution points based on boundary group configuration.</span></span> 

<span data-ttu-id="9ad75-195">Další informace najdete v tématu [konfiguraci skupin hranic](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_ccmsetup).</span><span class="sxs-lookup"><span data-stu-id="9ad75-195">For more information, see [Configure boundary groups](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_ccmsetup).</span></span>


### <a name="improvements-to-internet-based-client-setup"></a><span data-ttu-id="9ad75-196">Vylepšení nastavení internetových klientů</span><span class="sxs-lookup"><span data-stu-id="9ad75-196">Improvements to internet-based client setup</span></span>
<span data-ttu-id="9ad75-197"><!--1359181-->
<!--move this under co-management?--> Tato vydaná verze dále zjednodušuje proces instalace klienta nástroje Configuration Manager pro klienty na Internetu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-197"><!--1359181-->
<!--move this under co-management?--> This release further simplifies the Configuration Manager client setup process for clients on the internet.</span></span> <span data-ttu-id="9ad75-198">Další informace o Azure Active Directory (Azure AD) lokality publikuje do brány pro správu cloudu (CMG).</span><span class="sxs-lookup"><span data-stu-id="9ad75-198">The site publishes additional Azure Active Directory (Azure AD) information to the cloud management gateway (CMG).</span></span> <span data-ttu-id="9ad75-199">Azure připojená k AD získá klient tyto informace z CMG během procesu služby ccmsetup pomocí stejného tenanta, ke kterému je připojený.</span><span class="sxs-lookup"><span data-stu-id="9ad75-199">An Azure AD-joined client gets this information from the CMG during the ccmsetup process, using the same tenant to which it's joined.</span></span> <span data-ttu-id="9ad75-200">Toto chování dále usnadňuje registraci zařízení do spolusprávy v prostředí s více než jednoho tenanta Azure AD.</span><span class="sxs-lookup"><span data-stu-id="9ad75-200">This behavior further simplifies enrolling devices to co-management in an environment with more than one Azure AD tenant.</span></span> <span data-ttu-id="9ad75-201">Nyní jsou pouze dvě vlastnosti ccmsetup požadované **CCMHOSTNAME** a **SMSSiteCode**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-201">Now the only two required ccmsetup properties are **CCMHOSTNAME** and **SMSSiteCode**.</span></span>

<!--For more information, see [Prepare Windows 10 devices for co-management](https://docs.microsoft.com/en-us/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client).-->



## <a name="bkmk_comgmt"></a> <span data-ttu-id="9ad75-202">Společná správa</span><span class="sxs-lookup"><span data-stu-id="9ad75-202">Co-management</span></span>

### <a name="required-app-compliance-policy-for-co-managed-devices"></a><span data-ttu-id="9ad75-203">Požadované aplikace zásady dodržování předpisů pro spoluspravovaná zařízení</span><span class="sxs-lookup"><span data-stu-id="9ad75-203">Required app compliance policy for co-managed devices</span></span>
<span data-ttu-id="9ad75-204"><!--1358196--> Definujte pravidla zásad dodržování předpisů v Configuration Manageru pro požadované aplikace.</span><span class="sxs-lookup"><span data-stu-id="9ad75-204"><!--1358196--> Define compliance policy rules in Configuration Manager for required applications.</span></span> <span data-ttu-id="9ad75-205">Toto posouzení aplikací je součástí celkový stav dodržování předpisů pro spoluspravovaná zařízení odešlou do Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="9ad75-205">This app assessment is part of the overall compliance state sent to Microsoft Intune for co-managed devices.</span></span>

<!--For more information, see [Co-management for Windows 10 devices](/sccm/core/clients/manage/co-management-overview).-->


### <a name="improvement-to-co-management-dashboard"></a><span data-ttu-id="9ad75-206">Vylepšení řídicí panel pro spolusprávu</span><span class="sxs-lookup"><span data-stu-id="9ad75-206">Improvement to co-management dashboard</span></span>
<span data-ttu-id="9ad75-207"><!--1358980--> Rozšířená řídicí panel pro spolusprávu následujícím podrobnější informace:</span><span class="sxs-lookup"><span data-stu-id="9ad75-207"><!--1358980--> The co-management dashboard is enhanced with the following more detailed information:</span></span>  

- <span data-ttu-id="9ad75-208">**Stav registrace spolusprávy** dlaždice obsahuje další stavy</span><span class="sxs-lookup"><span data-stu-id="9ad75-208">The **Co-management enrollment status** tile includes additional states</span></span>

- <span data-ttu-id="9ad75-209">Nový **stav spolusprávy** dlaždice s trychtýřového grafu zobrazí stavy procesu registrace</span><span class="sxs-lookup"><span data-stu-id="9ad75-209">A new **Co-management status** tile with a funnel chart shows states of the enrollment process</span></span>

- <span data-ttu-id="9ad75-210">Nová dlaždice s počty **chyb registrace**</span><span class="sxs-lookup"><span data-stu-id="9ad75-210">A new tile with counts of **Enrollment errors**</span></span>

![Společná správa řídicího panelu snímek obrazovky s nejvyšší čtyři dlaždice](media/1358980-comgmt-dashboard.png)

<span data-ttu-id="9ad75-212">Další informace najdete v tématu [řídicí panel pro spolusprávu](/sccm/comanage/how-to-monitor#co-management-dashboard).</span><span class="sxs-lookup"><span data-stu-id="9ad75-212">For more information, see [Co-management dashboard](/sccm/comanage/how-to-monitor#co-management-dashboard).</span></span>



<!-- ## <a name="bkmk_compliance"></a> Compliance settings -->



## <a name="bkmk_app"></a> <span data-ttu-id="9ad75-213">Správa aplikací</span><span class="sxs-lookup"><span data-stu-id="9ad75-213">Application management</span></span>

### <a name="convert-applications-to-msix"></a><span data-ttu-id="9ad75-214">Převést aplikace MSIX</span><span class="sxs-lookup"><span data-stu-id="9ad75-214">Convert applications to MSIX</span></span>
<span data-ttu-id="9ad75-215"><!--1359029--> Počínaje verzí 1806, Configuration Manager podporuje nasazení na nový formát balíčku (.msix) aplikace Windows 10.</span><span class="sxs-lookup"><span data-stu-id="9ad75-215"><!--1359029--> Starting in version 1806, Configuration Manager supports deployment of the new Windows 10 app package (.msix) format.</span></span> <span data-ttu-id="9ad75-216">Nyní můžete převést do formátu MSIX existující aplikace Instalační služby systému Windows (.msi).</span><span class="sxs-lookup"><span data-stu-id="9ad75-216">Now you can convert your existing Windows Installer (.msi) applications to the MSIX format.</span></span>

<!--For more information, see [Create Windows applications](/sccm/apps/get-started/creating-windows-applications#bkmk_general).  this might move to a new section for msix-->


### <a name="repair-applications"></a><span data-ttu-id="9ad75-217">Oprava aplikací</span><span class="sxs-lookup"><span data-stu-id="9ad75-217">Repair applications</span></span>
<span data-ttu-id="9ad75-218"><!--1357866--> Určuje příkazový řádek opravy pro typy nasazení Instalační služby systému Windows a instalační služba skriptů.</span><span class="sxs-lookup"><span data-stu-id="9ad75-218"><!--1357866--> Specify a repair command line for Windows Installer and Script Installer deployment types.</span></span> <span data-ttu-id="9ad75-219">Pokud povolíte možnost v nasazení, nové tlačítko je k dispozici v centru softwaru na **opravit** aplikace.</span><span class="sxs-lookup"><span data-stu-id="9ad75-219">Then if you enable the option on the deployment, a new button is available in Software Center to **Repair** the application.</span></span> <span data-ttu-id="9ad75-220">Při konfiguraci aplikace s programem opravit, uživatelé mohou spustit příkaz z centra softwaru.</span><span class="sxs-lookup"><span data-stu-id="9ad75-220">When you configure an application with a repair program, users can start the command from Software Center.</span></span> 

<span data-ttu-id="9ad75-221">Další informace najdete v tématu [vytvářet aplikace](/sccm/apps/deploy-use/create-applications#bkmk_dt-content) a [nasazení aplikací](/sccm/apps/deploy-use/deploy-applications#bkmk_deploy-settings).</span><span class="sxs-lookup"><span data-stu-id="9ad75-221">For more information, see [Create applications](/sccm/apps/deploy-use/create-applications#bkmk_dt-content) and [Deploy applications](/sccm/apps/deploy-use/deploy-applications#bkmk_deploy-settings).</span></span>


### <a name="approve-application-requests-via-email"></a><span data-ttu-id="9ad75-222">Schválení žádosti o aplikace e-mailem</span><span class="sxs-lookup"><span data-stu-id="9ad75-222">Approve application requests via email</span></span>
<span data-ttu-id="9ad75-223"><!--1321550--> Konfigurace e-mailová oznámení pro žádosti o schválení aplikace.</span><span class="sxs-lookup"><span data-stu-id="9ad75-223"><!--1321550--> Configure email notifications for application approval requests.</span></span> <span data-ttu-id="9ad75-224">Když si uživatel vyžádá aplikace, obdržíte e-mailu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-224">When a user requests an application, you receive an email.</span></span> <span data-ttu-id="9ad75-225">Kliknutím na odkazy v e-mailu schválí nebo zamítne žádost, aniž by bylo nutné konzolu nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9ad75-225">Click links in the email to approve or deny the request, without requiring the Configuration Manager console.</span></span>

<span data-ttu-id="9ad75-226">Další informace najdete v tématu [schválit aplikace](/sccm/apps/deploy-use/app-approval).</span><span class="sxs-lookup"><span data-stu-id="9ad75-226">For more information, see [Approve applications](/sccm/apps/deploy-use/app-approval).</span></span>


### <a name="detection-methods-dont-load-windows-powershell-profiles"></a><span data-ttu-id="9ad75-227">Metody detekce Nenačítat profily Windows Powershellu</span><span class="sxs-lookup"><span data-stu-id="9ad75-227">Detection methods don't load Windows PowerShell profiles</span></span>
<span data-ttu-id="9ad75-228"><!--1359239--> Pro metody zjišťování na aplikace a nastavení v položkách konfigurace můžete použít skripty prostředí Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ad75-228"><!--1359239--> You can use Windows PowerShell scripts for detection methods on applications and settings in configuration items.</span></span> <span data-ttu-id="9ad75-229">Když tyto skripty spustí na klientských počítačích, klienta nástroje Configuration Manager teď volá prostředí PowerShell se službou `-NoProfile` parametru.</span><span class="sxs-lookup"><span data-stu-id="9ad75-229">When these scripts run on clients, the Configuration Manager client now calls PowerShell with the `-NoProfile` parameter.</span></span> <span data-ttu-id="9ad75-230">Tento parametr spustí Powershellu bez profilů.</span><span class="sxs-lookup"><span data-stu-id="9ad75-230">This option starts PowerShell without profiles.</span></span> 

<span data-ttu-id="9ad75-231">Profil prostředí PowerShell je skript, který se spustí při spuštění PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ad75-231">A PowerShell profile is a script that runs when PowerShell starts.</span></span> <span data-ttu-id="9ad75-232">Můžete vytvořit profil prostředí PowerShell k přizpůsobení prostředí a přidání prvků specifických pro relaci na každou relaci Powershellu, které spustíte.</span><span class="sxs-lookup"><span data-stu-id="9ad75-232">You can create a PowerShell profile to customize your environment and to add session-specific elements to every PowerShell session that you start.</span></span> 

> [!Note]  
> <span data-ttu-id="9ad75-233">Tuto změnu v chování netýká [skripty](/sccm/apps/deploy-use/create-deploy-scripts) nebo [CMPivot](/sccm/core/servers/manage/cmpivot).</span><span class="sxs-lookup"><span data-stu-id="9ad75-233">This change in behavior doesn't apply to [Scripts](/sccm/apps/deploy-use/create-deploy-scripts) or [CMPivot](/sccm/core/servers/manage/cmpivot).</span></span> <span data-ttu-id="9ad75-234">Obě tyto funkce už používáte tento parametr prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9ad75-234">Both of these features already use this PowerShell parameter.</span></span>    

<!--For more information, see []().-->


## <a name="bkmk_osd"></a> <span data-ttu-id="9ad75-235">Nasazení operačního systému</span><span class="sxs-lookup"><span data-stu-id="9ad75-235">OS deployment</span></span>

### <a name="task-sequence-support-of-windows-autopilot-for-existing-devices"></a><span data-ttu-id="9ad75-236">Podpora pořadí úloh systému Windows Autopilot existujících zařízení pracujících s</span><span class="sxs-lookup"><span data-stu-id="9ad75-236">Task sequence support of Windows Autopilot for existing devices</span></span>
<!--1358333-->

<span data-ttu-id="9ad75-237">[Windows Autopilotu pro stávající zařízení](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), je teď dostupná ve Windows 10 verze 1809 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9ad75-237">[Windows Autopilot for existing devices](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430), is now available with Windows 10, version 1809 or later.</span></span> <span data-ttu-id="9ad75-238">Tato nová funkce umožňuje obnovení z Image a zřízení zařízení pro Windows 7 [režimu řízeném uživatele Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) pomocí jednoho, nativní pořadí úloh nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9ad75-238">This new feature allows you to reimage and provision a Windows 7 device for [Windows Autopilot user-driven mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) using a single, native Configuration Manager task sequence.</span></span> 

<!--For more information, see []().--> 


### <a name="specify-the-drive-for-offline-os-image-servicing"></a><span data-ttu-id="9ad75-239">Určete taky jednotku, pro obsluhu offline bitové kopie operačního systému</span><span class="sxs-lookup"><span data-stu-id="9ad75-239">Specify the drive for offline OS image servicing</span></span>  
<span data-ttu-id="9ad75-240"><!--1358924--> Teď zadejte jednotky, které nástroj Configuration Manager používá při přidání aktualizací softwaru do bitové kopie operačního systému a balíčky s upgradem operačního systému.</span><span class="sxs-lookup"><span data-stu-id="9ad75-240"><!--1358924--> Now specify the drive that Configuration Manager uses when adding software updates to OS images and OS upgrade packages.</span></span> <span data-ttu-id="9ad75-241">Tento proces může spotřebovat velké množství místa na disku s dočasnými soubory, takže tato možnost vám poskytne flexibilitu pro výběr jednotky pro použití.</span><span class="sxs-lookup"><span data-stu-id="9ad75-241">This process can consume a large amount of disk space with temporary files, so this option gives you flexibility to select the drive to use.</span></span> 

<span data-ttu-id="9ad75-242">Další informace najdete v tématu [bitové kopie operačního systému spravovat](/sccm/osd/get-started/manage-operating-system-images#bkmk_servicing-drive) nebo [balíčky s upgradem operačního systému spravovat](/sccm/osd/get-started/manage-operating-system-upgrade-packages#bkmk_servicing-drive).</span><span class="sxs-lookup"><span data-stu-id="9ad75-242">For more information, see [Manage OS images](/sccm/osd/get-started/manage-operating-system-images#bkmk_servicing-drive) or [Manage OS upgrade packages](/sccm/osd/get-started/manage-operating-system-upgrade-packages#bkmk_servicing-drive).</span></span>


### <a name="task-sequence-support-for-boundary-groups"></a><span data-ttu-id="9ad75-243">Podpora pořadí úkolů pro skupiny hranic</span><span class="sxs-lookup"><span data-stu-id="9ad75-243">Task sequence support for boundary groups</span></span>
<span data-ttu-id="9ad75-244"><!--1359025--> Když se zařízení spustí pořadí úkolů a je potřeba získat obsah, teď používá chování skupiny hranic, podobně jako u klienta nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9ad75-244"><!--1359025--> When a device runs a task sequence and needs to acquire content, it now uses boundary group behaviors similar to the Configuration Manager client.</span></span>   

<span data-ttu-id="9ad75-245">Další informace najdete v tématu [skupiny hranic](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_bgr-osd).</span><span class="sxs-lookup"><span data-stu-id="9ad75-245">For more information, see [Boundary groups](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_bgr-osd).</span></span>


### <a name="improvements-to-driver-maintenance"></a><span data-ttu-id="9ad75-246">Vylepšení údržby ovladače</span><span class="sxs-lookup"><span data-stu-id="9ad75-246">Improvements to driver maintenance</span></span>
<span data-ttu-id="9ad75-247"><!--1358270--> Balíčky ovladačů nyní obsahovat další metadata pole pro **výrobce** a **modelu**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-247"><!--1358270--> Driver packages now have additional metadata fields for **Manufacturer** and **Model**.</span></span> <span data-ttu-id="9ad75-248">Pomocí těchto polí do balíčků ovladačů značky s informacemi o pomáhat při obecné údržbu nebo k identifikaci původní a duplicitní ovladače, které můžete odstranit.</span><span class="sxs-lookup"><span data-stu-id="9ad75-248">Use these fields to tag driver packages with information to assist in general housekeeping, or to identify old and duplicate drivers that you can delete.</span></span>


### <a name="new-task-sequence-variable-for-last-action-name"></a><span data-ttu-id="9ad75-249">Nové proměnné pořadí úloh pro poslední název akce</span><span class="sxs-lookup"><span data-stu-id="9ad75-249">New task sequence variable for last action name</span></span>
<span data-ttu-id="9ad75-250"><!--SCCMDocs-pr issue #2964--> Spolu s proměnnou _SMSTSLastActionRetCode pořadí úkolů nastaví pořadí úloh také nové proměnné **_SMSTSLastActionName**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-250"><!--SCCMDocs-pr issue #2964--> Along with the task sequence variable _SMSTSLastActionRetCode, the task sequence also sets a new variable **_SMSTSLastActionName**.</span></span> <span data-ttu-id="9ad75-251">Protokoluje také tuto hodnotu do souboru smsts.log.</span><span class="sxs-lookup"><span data-stu-id="9ad75-251">It also logs this value to the smsts.log file.</span></span> <span data-ttu-id="9ad75-252">Tato nová proměnná je vhodné při řešení potíží s sekvenci úloh.</span><span class="sxs-lookup"><span data-stu-id="9ad75-252">This new variable is beneficial when troubleshooting a task sequence.</span></span> <span data-ttu-id="9ad75-253">Když krok selže, vlastní skript může obsahovat název kroku spolu s návratovým kódem.</span><span class="sxs-lookup"><span data-stu-id="9ad75-253">When a step fails, a custom script can include the step name along with the return code.</span></span>

<span data-ttu-id="9ad75-254">Další informace najdete v tématu [proměnné pořadí úkolů](/sccm/osd/understand/task-sequence-variables#SMSTSLastActionName).</span><span class="sxs-lookup"><span data-stu-id="9ad75-254">For more information, see [Task sequence variables](/sccm/osd/understand/task-sequence-variables#SMSTSLastActionName).</span></span>



<!-- ## <a name="bkmk_userxp"></a> Software Center -->



## <a name="bkmk_sum"></a><span data-ttu-id="9ad75-255">Aktualizace softwaru</span><span class="sxs-lookup"><span data-stu-id="9ad75-255">Software updates</span></span>

### <a name="phased-deployment-of-software-updates"></a><span data-ttu-id="9ad75-256">Postupné nasazení aktualizací softwaru</span><span class="sxs-lookup"><span data-stu-id="9ad75-256">Phased deployment of software updates</span></span>
<span data-ttu-id="9ad75-257"><!--1358146--> Vytvoření postupného nasazení pro aktualizace softwaru.</span><span class="sxs-lookup"><span data-stu-id="9ad75-257"><!--1358146--> Create phased deployments for software updates.</span></span> <span data-ttu-id="9ad75-258">Postupná nasazení umožňují organizovat koordinované, postupné uvádění softwaru na základě přizpůsobitelných kritérii a skupiny.</span><span class="sxs-lookup"><span data-stu-id="9ad75-258">Phased deployments allow you to orchestrate a coordinated, sequenced rollout of software based on customizable criteria and groups.</span></span>

<span data-ttu-id="9ad75-259">Další informace najdete v tématu [vytvořit postupné nasazení](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/sccm/sum/toc.json&bc=/sccm/sum/breadcrumb/toc.json).</span><span class="sxs-lookup"><span data-stu-id="9ad75-259">For more information, see [Create phased deployments](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/sccm/sum/toc.json&bc=/sccm/sum/breadcrumb/toc.json).</span></span>


### <a name="improvement-to-maintenance-windows-for-software-updates"></a><span data-ttu-id="9ad75-260">Vylepšení časová období údržby pro aktualizace softwaru</span><span class="sxs-lookup"><span data-stu-id="9ad75-260">Improvement to maintenance windows for software updates</span></span>
<span data-ttu-id="9ad75-261"><!--vso2839307--> Následující nastavení klienta je v **aktualizace softwaru** skupiny k řízení chování při instalaci aktualizace softwaru v časová období údržby:</span><span class="sxs-lookup"><span data-stu-id="9ad75-261"><!--vso2839307--> The following client setting is in the **Software Updates** group to control the installation behavior of software updates in maintenance windows:</span></span> 

<span data-ttu-id="9ad75-262">**Povolit instalaci aktualizací v časové období údržby "Všechna nasazení" po "Aktualizaci softwaru" časové období údržby je k dispozici**</span><span class="sxs-lookup"><span data-stu-id="9ad75-262">**Enable installation of updates in "All deployments" maintenance window when "Software update" maintenance window is available**</span></span>

<span data-ttu-id="9ad75-263">Ve výchozím nastavení, tato možnost je **ne** k zachování konzistence se stávající chování.</span><span class="sxs-lookup"><span data-stu-id="9ad75-263">By default, this option is **No** to keep consistent with the existing behavior.</span></span> <span data-ttu-id="9ad75-264">Změňte ho na **Ano** povolit klientům použití jiných časových období údržby dostupná k instalaci aktualizací softwaru.</span><span class="sxs-lookup"><span data-stu-id="9ad75-264">Change it to **Yes** to allow clients to use other available maintenance windows to install software updates.</span></span>

<!--For more information, see []().-->



## <a name="bkmk_report"></a><span data-ttu-id="9ad75-265">Vytváření sestav</span><span class="sxs-lookup"><span data-stu-id="9ad75-265">Reporting</span></span>

### <a name="improvement-to-lifecycle-dashboard"></a><span data-ttu-id="9ad75-266">Zlepšení na řídicí panel životní cyklus</span><span class="sxs-lookup"><span data-stu-id="9ad75-266">Improvement to lifecycle dashboard</span></span>
<span data-ttu-id="9ad75-267"><!--1358702--> Řídicí panel životní cyklus produktu nyní obsahuje informace o **System Center 2012 Configuration Manager a novější**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-267"><!--1358702--> The product lifecycle dashboard now includes information for **System Center 2012 Configuration Manager and later**.</span></span> 

<span data-ttu-id="9ad75-268">K dispozici je také novou sestavu, **životního cyklu 05A – řídicí panel životní cyklus produktu**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-268">There's also a new report, **Lifecycle 05A - Product lifecycle dashboard**.</span></span> <span data-ttu-id="9ad75-269">Zahrnuje podobné informace jako řídicí panel v konzole.</span><span class="sxs-lookup"><span data-stu-id="9ad75-269">It includes similar information as the in-console dashboard.</span></span>

<span data-ttu-id="9ad75-270">Další informace na tomto řídicím panelu najdete v tématu [pomocí řídicího panelu životního cyklu produktu](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard).</span><span class="sxs-lookup"><span data-stu-id="9ad75-270">For more information on this dashboard, see [Use the Product Lifecycle dashboard](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard).</span></span>


### <a name="improvement-to-data-warehouse"></a><span data-ttu-id="9ad75-271">Vylepšení datového skladu</span><span class="sxs-lookup"><span data-stu-id="9ad75-271">Improvement to data warehouse</span></span>
<span data-ttu-id="9ad75-272"><!--1358870--> Teď můžete synchronizovat další tabulky z databáze lokality do datového skladu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-272"><!--1358870--> You can now synchronize more tables from the site database to the data warehouse.</span></span> <span data-ttu-id="9ad75-273">Tato změna umožňuje vytvořit další sestavy založené na vašich obchodních požadavcích.</span><span class="sxs-lookup"><span data-stu-id="9ad75-273">This change allows you to create more reports based on your business requirements.</span></span>

<span data-ttu-id="9ad75-274">Další informace najdete v tématu [datového skladu](/sccm/core/servers/manage/data-warehouse).</span><span class="sxs-lookup"><span data-stu-id="9ad75-274">For more information, see [Data warehouse](/sccm/core/servers/manage/data-warehouse).</span></span>



<!-- ## <a name="bkmk_inv"></a> Inventory -->




<!-- ## <a name="bkmk_protect"></a> Protect devices-->




## <a name="bkmk_admin"></a> <span data-ttu-id="9ad75-275">Konzola nástroje Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="9ad75-275">Configuration Manager console</span></span>

### <a name="configuration-manager-administrator-authentication"></a><span data-ttu-id="9ad75-276">Ověřování u správců nástroje Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="9ad75-276">Configuration Manager administrator authentication</span></span>
<span data-ttu-id="9ad75-277"><!--1357013--> Teď můžete určit úroveň minimální ověřování pro správce pro přístup k serverům nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9ad75-277"><!--1357013--> You can now specify the minimum authentication level for administrators to access Configuration Manager sites.</span></span> <span data-ttu-id="9ad75-278">Tato funkce zajišťuje správce pro přihlášení k Windows s požadovanou úrovní.</span><span class="sxs-lookup"><span data-stu-id="9ad75-278">This feature enforces administrators to sign in to Windows with the required level.</span></span> <span data-ttu-id="9ad75-279">Ke konfiguraci tohoto nastavení, najdete **ověřování** kartu **nastavení hierarchie**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-279">To configure this setting, find the **Authentication** tab in **Hierarchy Settings**.</span></span> 

<span data-ttu-id="9ad75-280">Další informace najdete v tématu [plánování poskytovatele serveru SMS](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_auth).</span><span class="sxs-lookup"><span data-stu-id="9ad75-280">For more information, see [Plan for the SMS Provider](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_auth).</span></span>


### <a name="support-center"></a><span data-ttu-id="9ad75-281">Support Center</span><span class="sxs-lookup"><span data-stu-id="9ad75-281">Support Center</span></span>
<span data-ttu-id="9ad75-282"><!--1357489--> Pomocí centra podpory pro řešení potíží, v reálném čase protokol klienta zobrazení nebo zaznamenání stavu klientského počítače Configuration Manageru pro pozdější analýzu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-282"><!--1357489--> Use Support Center for client troubleshooting, real-time log viewing, or capturing the state of a Configuration Manager client computer for later analysis.</span></span> <span data-ttu-id="9ad75-283">Support Center je jeden nástroj ke sloučení mnoha správce nástroje pro odstraňování potíží.</span><span class="sxs-lookup"><span data-stu-id="9ad75-283">Support Center is a single tool to combine many administrator troubleshooting tools.</span></span> <span data-ttu-id="9ad75-284">Najděte instalační program Support Center na serveru lokality v **cd.latest\SMSSETUP\Tools\SupportCenter** složky.</span><span class="sxs-lookup"><span data-stu-id="9ad75-284">Find the Support Center installer on the site server in the **cd.latest\SMSSETUP\Tools\SupportCenter** folder.</span></span>

<span data-ttu-id="9ad75-285">Další informace najdete v tématu [Support Center](/sccm/core/support/support-center).</span><span class="sxs-lookup"><span data-stu-id="9ad75-285">For more information, see [Support Center](/sccm/core/support/support-center).</span></span>


### <a name="management-insights-dashboard"></a><span data-ttu-id="9ad75-286">Řídicí panel přehledů správy</span><span class="sxs-lookup"><span data-stu-id="9ad75-286">Management insights dashboard</span></span>
<!--1357979-->

<span data-ttu-id="9ad75-287">**Přehledy správy** uzel nyní zahrnuje grafické řídicí panel.</span><span class="sxs-lookup"><span data-stu-id="9ad75-287">The **Management Insights** node now includes a graphical dashboard.</span></span> <span data-ttu-id="9ad75-288">Tento řídicí panel zobrazuje přehled stavy pravidel, což usnadňuje zobrazení pokroku ve studiu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-288">This dashboard displays an overview of the rule states, which makes it easier for you to show your progress.</span></span> <span data-ttu-id="9ad75-289">Řídicí panel obsahuje tyto dlaždice:</span><span class="sxs-lookup"><span data-stu-id="9ad75-289">The dashboard includes the following tiles:</span></span>

- <span data-ttu-id="9ad75-290">**Správa insights index**: Sleduje celkový průběh na pravidla přehledů správy.</span><span class="sxs-lookup"><span data-stu-id="9ad75-290">**Management insights index**: Tracks overall progress on management insights rules.</span></span> <span data-ttu-id="9ad75-291">Index je vážený průměr.</span><span class="sxs-lookup"><span data-stu-id="9ad75-291">The index is a weighted average.</span></span> <span data-ttu-id="9ad75-292">Kritických pravidel stojí na maximum.</span><span class="sxs-lookup"><span data-stu-id="9ad75-292">Critical rules are worth the most.</span></span> <span data-ttu-id="9ad75-293">Tento index poskytuje nejnižší váha volitelné pravidel.</span><span class="sxs-lookup"><span data-stu-id="9ad75-293">This index gives the least weight to optional rules.</span></span>  

- <span data-ttu-id="9ad75-294">**Přehled skupin pro správu**: Zobrazí procento pravidel v každé skupině.</span><span class="sxs-lookup"><span data-stu-id="9ad75-294">**Management insights groups**: Shows percent of rules in each group.</span></span>  

- <span data-ttu-id="9ad75-295">**Priorita přehledů správy**: Zobrazuje procento pravidla podle priority.</span><span class="sxs-lookup"><span data-stu-id="9ad75-295">**Management insights priority**: Shows percent of rules by priority.</span></span>  

- <span data-ttu-id="9ad75-296">**Všechny přehledy**: Tabulka s přehledy, včetně priority a stavu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-296">**All insights**: A table of insights including priority and state.</span></span>  

![Snímek obrazovky řídicí panel přehledů správy](media/1357979-management-insights-dashboard.png)

<span data-ttu-id="9ad75-298">Další informace najdete v tématu [přehledy správy](/sccm/core/servers/manage/management-insights).</span><span class="sxs-lookup"><span data-stu-id="9ad75-298">For more information, see [Management insights](/sccm/core/servers/manage/management-insights).</span></span>


### <a name="improvements-to-cmpivot"></a><span data-ttu-id="9ad75-299">Vylepšení CMPivot</span><span class="sxs-lookup"><span data-stu-id="9ad75-299">Improvements to CMPivot</span></span>
<span data-ttu-id="9ad75-300"><!--1359068--> CMPivot zahrnuje následující vylepšení:</span><span class="sxs-lookup"><span data-stu-id="9ad75-300"><!--1359068--> CMPivot includes the following improvements:</span></span>

- <span data-ttu-id="9ad75-301">Uložit **Oblíbené** dotazy</span><span class="sxs-lookup"><span data-stu-id="9ad75-301">Save **Favorite** queries</span></span>  

- <span data-ttu-id="9ad75-302">Na kartě dotazu Souhrn vyberte počet zařízení v režimu Offline nebo se nezdařilo a pak vyberte možnost **vytvořit kolekci**.</span><span class="sxs-lookup"><span data-stu-id="9ad75-302">On the Query Summary tab, select the count of Failed or Offline devices, and then select the option to **Create Collection**.</span></span> 

<span data-ttu-id="9ad75-303">Další informace o dalších výkonu a odstraňování potíží vylepšení CMPivot najdete v tématu [vylepšení skripty](#bkmk_scripts).</span><span class="sxs-lookup"><span data-stu-id="9ad75-303">For more information on additional performance and troubleshooting improvements to CMPivot, see [Improvements to scripts](#bkmk_scripts).</span></span>

<!--For more information on CMPivot, see [CMPivot](/sccm/core/servers/manage/cmpivot).-->


### <a name="bkmk_scripts"></a> <span data-ttu-id="9ad75-304">Vylepšení do skriptů</span><span class="sxs-lookup"><span data-stu-id="9ad75-304">Improvements to scripts</span></span>
<span data-ttu-id="9ad75-305"><!--1358239--> Nyní můžete zobrazit podrobný skript výstup ve formátu raw nebo strukturovaná JSON.</span><span class="sxs-lookup"><span data-stu-id="9ad75-305"><!--1358239--> You can now view detailed script output in raw or structured JSON format.</span></span> <span data-ttu-id="9ad75-306">Toto formátování usnadňuje výstup pro čtení a analýzu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-306">This formatting makes the output easier to read and analyze.</span></span> 

<span data-ttu-id="9ad75-307">Následující výkonem a odstraňováním problémů vylepšení použít CMPivot a skriptů:</span><span class="sxs-lookup"><span data-stu-id="9ad75-307">The following performance and troubleshooting improvements apply to both CMPivot and scripts:</span></span>

- <span data-ttu-id="9ad75-308">Aktualizované klienti vrátí výstupní méně než 80 KB k webu přes rychlé komunikační kanál.</span><span class="sxs-lookup"><span data-stu-id="9ad75-308">Updated clients return output less than 80 KB to the site over a fast communication channel.</span></span> <span data-ttu-id="9ad75-309">Tato změna zvyšuje výkon zobrazení výstupu skriptu či dotazu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-309">This change increases the performance of viewing script or query output.</span></span>  

- <span data-ttu-id="9ad75-310">Další protokoly pro řešení potíží</span><span class="sxs-lookup"><span data-stu-id="9ad75-310">Additional logs for troubleshooting</span></span>  

<!--For more information, see the following articles:  

- [Create and run PowerShell scripts from the Configuration Manager console](/sccm/apps/deploy-use/create-deploy-scripts)  

- [CMPivot](/sccm/core/servers/manage/cmpivot)  -->


### <a name="sms-provider-api"></a><span data-ttu-id="9ad75-311">Rozhraní API poskytovatele serveru SMS</span><span class="sxs-lookup"><span data-stu-id="9ad75-311">SMS Provider API</span></span>
<span data-ttu-id="9ad75-312"><!--1321523--> Poskytovatel serveru SMS teď poskytuje přístup jen pro čtení vzájemná funkční spolupráce rozhraní API k rozhraní WMI přes protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="9ad75-312"><!--1321523--> The SMS Provider now provides read-only API interoperability access to WMI over HTTPS.</span></span> <span data-ttu-id="9ad75-313">**Poskytovatele serveru SMS** se zobrazí jako role s možností povolit komunikaci přes bránu pro správu cloudu.</span><span class="sxs-lookup"><span data-stu-id="9ad75-313">The **SMS Provider** appears as a role with an option to allow communication over the cloud management gateway.</span></span> <span data-ttu-id="9ad75-314">Aktuální použití funkce pro toto nastavení je umožnit aplikaci schválení prostřednictvím e-mailu ze vzdáleného zařízení.</span><span class="sxs-lookup"><span data-stu-id="9ad75-314">The current use for this setting is to enable application approvals via email from a remote device.</span></span> <span data-ttu-id="9ad75-315">Další informace najdete v tématu [schvalovat žádosti o aplikace e-mailem](#approve-application-requests-via-email).</span><span class="sxs-lookup"><span data-stu-id="9ad75-315">For more information, see [Approve application requests via email](#approve-application-requests-via-email).</span></span>



## <a name="bkmk_opmdm"></a> <span data-ttu-id="9ad75-316">Místní správy MDM</span><span class="sxs-lookup"><span data-stu-id="9ad75-316">On-premises MDM</span></span>

### <a name="an-intune-connection-is-no-longer-required-for-on-premises-mdm"></a><span data-ttu-id="9ad75-317">Připojení k Intune se už nevyžaduje pro místní správy MDM</span><span class="sxs-lookup"><span data-stu-id="9ad75-317">An Intune connection is no longer required for on-premises MDM</span></span>
<span data-ttu-id="9ad75-318"><!--1359124--> Místní MDM předpokladů konfigurace odběru Microsoft Intune se už nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="9ad75-318"><!--1359124--> The on-premises MDM prerequisite to configure a Microsoft Intune subscription is no longer required.</span></span> <span data-ttu-id="9ad75-319">Vaše organizace pořád vyžaduje licence Intune k použití této funkce.</span><span class="sxs-lookup"><span data-stu-id="9ad75-319">Your organization still requires Intune licenses to use this feature.</span></span> 



## <a name="next-steps"></a><span data-ttu-id="9ad75-320">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9ad75-320">Next steps</span></span>

<span data-ttu-id="9ad75-321">Jakmile budete připraveni k instalaci této verze, najdete v článku [instalace aktualizací pro Configuration Manager](/sccm/core/servers/manage/updates) a [kontrolní seznam pro instalaci aktualizace 1810](/sccm/core/servers/manage/checklist-for-installing-update-1810).</span><span class="sxs-lookup"><span data-stu-id="9ad75-321">When you're ready to install this version, see [Installing updates for Configuration Manager](/sccm/core/servers/manage/updates) and [Checklist for installing update 1810](/sccm/core/servers/manage/checklist-for-installing-update-1810).</span></span>

> [!TIP]  
> <span data-ttu-id="9ad75-322">K instalaci nové lokality můžete použijte základní verzi nástroje Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="9ad75-322">To install a new site, use a baseline version of Configuration Manager.</span></span>  
>
>  <span data-ttu-id="9ad75-323">Další informace pro:</span><span class="sxs-lookup"><span data-stu-id="9ad75-323">Learn more about:</span></span>    
>   - [<span data-ttu-id="9ad75-324">Instalaci nové lokality</span><span class="sxs-lookup"><span data-stu-id="9ad75-324">Installing new sites</span></span>](/sccm/core/servers/deploy/install/installing-sites)  
>   - [<span data-ttu-id="9ad75-325">Základní a aktualizované verze</span><span class="sxs-lookup"><span data-stu-id="9ad75-325">Baseline and update versions</span></span>](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

<span data-ttu-id="9ad75-326">Známé, významné problémy, najdete v článku [poznámky k verzi](/sccm/core/servers/deploy/install/release-notes).</span><span class="sxs-lookup"><span data-stu-id="9ad75-326">For known, significant issues, see the [Release notes](/sccm/core/servers/deploy/install/release-notes).</span></span>

<span data-ttu-id="9ad75-327">Po aktualizaci lokality také zkontrolujte [kontrolní seznam aktualizace po](/sccm/core/servers/manage/checklist-for-installing-update-1810#post-update-checklist).</span><span class="sxs-lookup"><span data-stu-id="9ad75-327">After you update a site, also review the [Post-update checklist](/sccm/core/servers/manage/checklist-for-installing-update-1810#post-update-checklist).</span></span>