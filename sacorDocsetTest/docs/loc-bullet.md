---
title: Advanced Threat Analytics installeren - Stap 5 | Microsoft Docs
description: Stap 5 van de ATA-installatie helpt u bij het configureren van de ATA Gateway-instellingen.
keywords: ''
author: rkarlin
ms.author: rkarlin
manager: mbaldwin
ms.date: 3/21/2018
ms.topic: conceptual
ms.prod: advanced-threat-analytics
ms.service: ''
ms.technology: ''
ms.assetid: 2a5b6652-2aef-464c-ac17-c7e5f12f920f
ms.reviewer: bennyl
ms.suite: ems
ms.openlocfilehash: dbc89fc060fb10408edc5137ae0179d8711e7517
ms.sourcegitcommit: f86dc8ad3d1e75ba64b372d4d0ab5386e28f2e29
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2018
ms.locfileid: "51609653"
---
<span data-ttu-id="39518-103">*Is van toepassing op: Advanced Threat Analytics versie 1.9*</span><span class="sxs-lookup"><span data-stu-id="39518-103">*Applies to: Advanced Threat Analytics version 1.9*</span></span>



# <a name="install-ata---step-5"></a><span data-ttu-id="39518-104">ATA installeren - Stap 5</span><span class="sxs-lookup"><span data-stu-id="39518-104">Install ATA - Step 5</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="39518-105">[« Stap 4](install-ata-step4.md)
> [Stap 6 »](install-ata-step6.md)</span><span class="sxs-lookup"><span data-stu-id="39518-105">[« Step 4](install-ata-step4.md)
[Step 6 »](install-ata-step6.md)</span></span>


## <a name="step-5-configure-the-ata-gateway-settings"></a><span data-ttu-id="39518-106">Stap 5.</span><span class="sxs-lookup"><span data-stu-id="39518-106">Step 5.</span></span> <span data-ttu-id="39518-107">De ATA Gateway-instellingen configureren</span><span class="sxs-lookup"><span data-stu-id="39518-107">Configure the ATA Gateway settings</span></span>
<span data-ttu-id="39518-108">Nadat de ATA Gateway is geïnstalleerd, moet u de volgende stappen uitvoeren om de ATA Gateway-instellingen te configureren.</span><span class="sxs-lookup"><span data-stu-id="39518-108">After the ATA Gateway was installed, perform the following steps to configure the settings for the ATA Gateway.</span></span>

1.  <span data-ttu-id="39518-109">Ga in ATA Console naar **Configuratie** en klik bij **Systeem** op **Gateways**.</span><span class="sxs-lookup"><span data-stu-id="39518-109">In the ATA Console, go to **Configuration** and, under **System**, select **Gateways**.</span></span>
   
     ![Afbeelding gateway-instellingen configureren](media/ata-gw-config-1.png)


2.  <span data-ttu-id="39518-111">Selecteer de gateway die u wilt configureren en voer de volgende informatie in:</span><span class="sxs-lookup"><span data-stu-id="39518-111">Click on the Gateway you want to configure and enter the following information:</span></span>

    ![Afbeelding gateway-instellingen configureren](media/ATA-Gateways-config-2.png)

  - <span data-ttu-id="39518-113">**Beschrijving**: voer een beschrijving in voor de ATA Gateway (optioneel).</span><span class="sxs-lookup"><span data-stu-id="39518-113">**Description**: Enter a description for the ATA Gateway (optional).</span></span>
  - <span data-ttu-id="39518-114">**Domeincontrollers met poortspiegeling (FQDN)** (vereist voor de ATA Gateway; dit kan niet worden gewijzigd voor de ATA Lightweight Gateway): voer de volledige FQDN-naam van de domeincontroller in en klik op het plusteken om deze toe te voegen aan de lijst.</span><span class="sxs-lookup"><span data-stu-id="39518-114">**Port Mirrored Domain Controllers (FQDN)** (required for the ATA Gateway, this cannot be changed for the ATA Lightweight Gateway): Enter the complete FQDN of your domain controller and click the plus sign to add it to the list.</span></span> <span data-ttu-id="39518-115">Bijvoorbeeld **dc01.contoso.com**</span><span class="sxs-lookup"><span data-stu-id="39518-115">For example,  **dc01.contoso.com**</span></span>

  <span data-ttu-id="39518-116">De volgende informatie is van toepassing op de servers die u in de lijst **Domeincontrollers** invoert:</span><span class="sxs-lookup"><span data-stu-id="39518-116">The following information applies to the servers you enter in the **Domain Controllers** list:</span></span>  

  - <span data-ttu-id="39518-117">Alle domeincontrollers waarvan het verkeer via poortspiegeling door de ATA Gateway wordt bewaakt, moeten in de lijst **Domeincontrollers** staan.</span><span class="sxs-lookup"><span data-stu-id="39518-117">All domain controllers whose traffic is being monitored via port mirroring by the ATA Gateway must be listed in the **Domain Controllers** list.</span></span> <span data-ttu-id="39518-118">Als een domeincontroller niet wordt weergegeven in de lijst **Domeincontrollers**, werkt de detectie van verdachte activiteiten mogelijk niet zoals verwacht.</span><span class="sxs-lookup"><span data-stu-id="39518-118">If a domain controller is not listed in the **Domain Controllers** list, detection of suspicious activities might not function as expected.</span></span>  
   - <span data-ttu-id="39518-119">Ten minste één domeincontroller in de lijst moet een globale catalogus zijn.</span><span class="sxs-lookup"><span data-stu-id="39518-119">At least one domain controller in the list should be a global catalog.</span></span> <span data-ttu-id="39518-120">Hierdoor kan ATA computer- en gebruikersobjecten in andere domeinen in het forest omzetten.</span><span class="sxs-lookup"><span data-stu-id="39518-120">This enables ATA to resolve computer and user objects in other domains in the forest.</span></span>

  - <span data-ttu-id="39518-121">**Netwerkadapters vastleggen** (vereist):</span><span class="sxs-lookup"><span data-stu-id="39518-121">**Capture Network adapters** (required):</span></span>
    - <span data-ttu-id="39518-122">Voor een ATA-gateway op een toegewezen server selecteert u de netwerkadapters die zijn geconfigureerd als doelpoort voor de spiegeling.</span><span class="sxs-lookup"><span data-stu-id="39518-122">For an ATA Gateway on a dedicated server, select the network adapters that are configured as the destination mirror port.</span></span> <span data-ttu-id="39518-123">Deze ontvangen het verkeer gespiegelde domeincontroller.</span><span class="sxs-lookup"><span data-stu-id="39518-123">These receive the mirrored domain controller traffic.</span></span>
    - <span data-ttu-id="39518-124">Voor een ATA Lightweight-gateway zijn dit alle netwerkadapters die worden gebruikt voor de communicatie met andere computers in uw organisatie.</span><span class="sxs-lookup"><span data-stu-id="39518-124">For an ATA Lightweight Gateway, this should be all the network adapters that are used for communication with other computers in your organization.</span></span>
  
  - <span data-ttu-id="39518-125">**Kandidaat voor de domeinsynchronisatieroutine**: een ATA-gateway die is ingesteld als kandidaat voor een domeinsynchronisatieroutine, kan de synchronisatie tussen ATA en uw Active Directory-domein afhandelen.</span><span class="sxs-lookup"><span data-stu-id="39518-125">**Domain synchronizer candidate**: Any ATA Gateway set to be a domain synchronizer candidate can be responsible for synchronization between ATA and your Active Directory domain.</span></span> <span data-ttu-id="39518-126">Afhankelijk van de grootte van het domein, de initiële synchronisatie kan enige tijd duren en is resource-intensief.</span><span class="sxs-lookup"><span data-stu-id="39518-126">Depending on the size of the domain, the initial synchronization might take some time and is resource-intensive.</span></span> <span data-ttu-id="39518-127">Standaard worden alleen ATA Gateways ingesteld als kandidaat voor de domeinsynchronisatieroutine.</span><span class="sxs-lookup"><span data-stu-id="39518-127">By default, only ATA Gateways are set as Domain synchronizer candidates.</span></span>
   <span data-ttu-id="39518-128">Het is raadzaam dat u een externe site ATA-Gateways van domeinsynchronisatieroutine uitschakelen.</span><span class="sxs-lookup"><span data-stu-id="39518-128">It is recommended that you disable any remote site ATA Gateways from being Domain synchronizer candidates.</span></span>
   <span data-ttu-id="39518-129">Als uw domeincontroller alleen-lezen is, moet u deze niet instellen als kandidaat voor een domeinsynchronisatieroutine.</span><span class="sxs-lookup"><span data-stu-id="39518-129">If your domain controller is read-only, do not set it as a Domain synchronizer candidate.</span></span> <span data-ttu-id="39518-130">Zie [ATA-architectuur](ata-architecture.md#ata-lightweight-gateway-features) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="39518-130">For more information, see [ATA architecture](ata-architecture.md#ata-lightweight-gateway-features).</span></span>

  > [!NOTE] 
  > <span data-ttu-id="39518-131">Het duurt enkele minuten voordat de ATA Gateway-service na de installatie voor het eerst wordt gestart, omdat deze de cache van de netwerkopnameparser moet samenstellen.</span><span class="sxs-lookup"><span data-stu-id="39518-131">It will take a few minutes for the ATA Gateway service to start the first time after installation because it builds the cache of the network capture parsers.</span></span>
  > <span data-ttu-id="39518-132">Wijzigingen in de configuratie worden toegepast op de ATA-Gateway op de volgende geplande synchronisatie tussen de ATA-Gateway en ATA Center.</span><span class="sxs-lookup"><span data-stu-id="39518-132">The configuration changes are applied to the ATA Gateway on the next scheduled sync between the ATA Gateway and the ATA Center.</span></span>

3. <span data-ttu-id="39518-133">Eventueel kunt u de [Syslog-listener- en Windows Event Forwarding-verzameling](configure-event-collection.md) instellen.</span><span class="sxs-lookup"><span data-stu-id="39518-133">Optionally, you can set the [Syslog listener and Windows Event Forwarding Collection](configure-event-collection.md).</span></span> 
4. <span data-ttu-id="39518-134">Schakel **bijwerken van ATA-Gateway automatisch** , zodat deze in een toekomstige versierelease wanneer u het ATA Center bijwerkt, wordt deze ATA-Gateway wordt automatisch bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="39518-134">Enable **Update ATA Gateway automatically** so that in upcoming version releases when you update the ATA Center, this ATA Gateway is automatically updated.</span></span>

5. <span data-ttu-id="39518-135">Klik op **Opslaan**.</span><span class="sxs-lookup"><span data-stu-id="39518-135">Click **Save**.</span></span>


## <a name="validate-installations"></a><span data-ttu-id="39518-136">Installaties valideren</span><span class="sxs-lookup"><span data-stu-id="39518-136">Validate installations</span></span>
<span data-ttu-id="39518-137">Als u wilt valideren dat de ATA-Gateway met succes is geïmplementeerd, controleert u de volgende stappen uit:</span><span class="sxs-lookup"><span data-stu-id="39518-137">To validate that the ATA Gateway has been successfully deployed, check the following steps:</span></span>

1.  <span data-ttu-id="39518-138">Controleer of de service met de naam **Microsoft Advanced Threat Analytics Gateway** wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="39518-138">Check that the service named **Microsoft Advanced Threat Analytics Gateway** is running.</span></span> <span data-ttu-id="39518-139">Nadat u de ATA Gateway-instellingen hebt opgeslagen, kan het enkele minuten duren voordat de service wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="39518-139">After you save the ATA Gateway settings, it might take a few minutes for the service to start.</span></span>

2.  <span data-ttu-id="39518-140">Als de service niet wordt gestart, controleert u het bestand Microsoft.Tri.Gateway-Errors.log in de standaardmap %programfiles%\Microsoft Advanced Threat Analytics\Gateway\Logs. Zie [ATA-probleemoplossing](troubleshooting-ata-known-errors.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="39518-140">If the service does not start, review the “Microsoft.Tri.Gateway-Errors.log” file located in the following default folder, “%programfiles%\Microsoft Advanced Threat Analytics\Gateway\Logs” and Check [ATA Troubleshooting](troubleshooting-ata-known-errors.md) for help.</span></span>

3.  <span data-ttu-id="39518-141">Als dit de eerste ATA Gateway is die wordt geïnstalleerd, meldt u zich na een paar minuten aan bij de ATA Console en opent u het meldingsvenster door de rechterkant van het scherm door middel van vegen te openen.</span><span class="sxs-lookup"><span data-stu-id="39518-141">If this is the first ATA Gateway installed, after a few minutes, log into the ATA Console and open the notification pane by swiping the right side of the screen open.</span></span> <span data-ttu-id="39518-142">In de meldingsbalk rechts van de console staat een lijst met **Onlangs geleerde entiteiten**.</span><span class="sxs-lookup"><span data-stu-id="39518-142">You should see a list of **Entities Recently Learned** in the notification bar on the right side of the console.</span></span>

4.  <span data-ttu-id="39518-143">Klik op het bureaublad op de snelkoppeling van **Microsoft Advanced Threat Analytics** om verbinding te maken met de ATA-console.</span><span class="sxs-lookup"><span data-stu-id="39518-143">On the desktop, click the **Microsoft Advanced Threat Analytics** shortcut to connect to the ATA Console.</span></span> <span data-ttu-id="39518-144">Meld u aan met de gebruikersreferenties die u hebt gebruikt voor de installatie van het ATA Center.</span><span class="sxs-lookup"><span data-stu-id="39518-144">Log in with the same user credentials that you used to install the ATA Center.</span></span>
5.  <span data-ttu-id="39518-145">Zoek in de console iets in de zoekbalk, bijvoorbeeld een gebruiker of een groep op uw domein.</span><span class="sxs-lookup"><span data-stu-id="39518-145">In the console, search for something in the search bar, such as a user or a group on your domain.</span></span>
6.  <span data-ttu-id="39518-146">Open de Prestatiemeter.</span><span class="sxs-lookup"><span data-stu-id="39518-146">Open Performance Monitor.</span></span> <span data-ttu-id="39518-147">Klik in de prestatiestructuur op **Prestatiemeter** en klik vervolgens op het plusteken om **een item toe te voegen**.</span><span class="sxs-lookup"><span data-stu-id="39518-147">In the Performance tree, click on **Performance Monitor** and then click the plus icon to **Add a Counter**.</span></span> <span data-ttu-id="39518-148">Vouw **Microsoft ATA-gateway** uit en schuif omlaag naar **Met PEF vastgelegde netwerklistenerberichten per seconde** en voeg dit item toe.</span><span class="sxs-lookup"><span data-stu-id="39518-148">Expand **Microsoft ATA Gateway** and scroll down to **Network Listener PEF Captured Messages/Sec** and add it.</span></span> <span data-ttu-id="39518-149">Controleer vervolgens of er activiteit is in de grafiek.</span><span class="sxs-lookup"><span data-stu-id="39518-149">Then, make sure you see activity on the graph.</span></span>

    ![Afbeelding van prestatiemeteritems toevoegen](media/ATA-performance-monitoring-add-counters.png)


> [!div class="step-by-step"]
> <span data-ttu-id="39518-151">[« Stap 4](install-ata-step4.md)
> [Stap 6 »](install-ata-step6.md)</span><span class="sxs-lookup"><span data-stu-id="39518-151">[« Step 4](install-ata-step4.md)
[Step 6 »](install-ata-step6.md)</span></span>



## <a name="related-videos"></a><span data-ttu-id="39518-152">Gerelateerde video 's</span><span class="sxs-lookup"><span data-stu-id="39518-152">Related Videos</span></span>
- [<span data-ttu-id="39518-153">Overzicht van de ATA-implementatie</span><span class="sxs-lookup"><span data-stu-id="39518-153">ATA Deployment Overview</span></span>](https://channel9.msdn.com/Shows/Microsoft-Security/Overview-of-ATA-Deployment-in-10-Minutes)
- [<span data-ttu-id="39518-154">Het recht voor ATA-Gateway van het type kiezen</span><span class="sxs-lookup"><span data-stu-id="39518-154">Choosing the right ATA Gateway type</span></span>](https://channel9.msdn.com/Shows/Microsoft-Security/ATA-Deployment-Choose-the-Right-Gateway-Type)


## <a name="see-also"></a><span data-ttu-id="39518-155">Zie ook</span><span class="sxs-lookup"><span data-stu-id="39518-155">See Also</span></span>
- [<span data-ttu-id="39518-156">ATA POC-Implementatiehandleiding</span><span class="sxs-lookup"><span data-stu-id="39518-156">ATA POC deployment guide</span></span>](http://aka.ms/atapoc)
- [<span data-ttu-id="39518-157">ATA sizing tool</span><span class="sxs-lookup"><span data-stu-id="39518-157">ATA sizing tool</span></span>](http://aka.ms/atasizingtool)
- [<span data-ttu-id="39518-158">Bekijk het ATA-forum.</span><span class="sxs-lookup"><span data-stu-id="39518-158">Check out the ATA forum!</span></span>](https://social.technet.microsoft.com/Forums/security/home?forum=mata)
- [<span data-ttu-id="39518-159">Gebeurtenissen verzamelen configureren</span><span class="sxs-lookup"><span data-stu-id="39518-159">Configure event collection</span></span>](configure-event-collection.md)
- [<span data-ttu-id="39518-160">ATA-vereisten</span><span class="sxs-lookup"><span data-stu-id="39518-160">ATA prerequisites</span></span>](ata-prerequisites.md)

