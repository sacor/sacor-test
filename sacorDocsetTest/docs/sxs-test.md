---
title: Migrieren von der Sprachübersetzungs-API zum Spracherkennungsdienst
titleSuffix: Azure Cognitive Services
description: Erfahren Sie, wie Sie Ihre Anwendungen von der Sprachübersetzungs-API zum Spracherkennungsdienst migrieren.
services: cognitive-services
author: aahill
manager: nitinme
ms.service: cognitive-services
ms.subservice: speech-service
ms.topic: conceptual
ms.date: 10/01/2018
ms.author: aahi
ms.openlocfilehash: 35f970e81d27511bd35610bc2988a5ea4832906b
ms.sourcegitcommit: 5839af386c5a2ad46aaaeb90a13065ef94e61e74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "57898634"
---
# <a name="migrate-from-the-translator-speech-api-to-the-speech-service"></a>Migrieren von der Sprachübersetzungs-API zum Spracherkennungsdienst

Verwenden Sie diesen Artikel, um Ihre Anwendungen von der Sprachübersetzungs-API von Microsoft zum [Spracherkennungsdienst](index.yml) zu migrieren. Diese Anleitung beschreibt die Unterschiede zwischen der Sprachübersetzungs-API von Microsoft und dem Spracherkennungsdienst und schlägt Strategien für die Migration Ihrer Anwendungen vor.

> [!NOTE]
> Ihr Abonnementschlüssel für die Sprachübersetzungs-API wird nicht vom Spracherkennungsdienst akzeptiert. Sie müssen ein neues Spracherkennungsdienst-Abonnement erstellen.

## <a name="comparison-of-features"></a>Vergleich der Features

| Feature                                           | Sprachübersetzungs-API                                  | Sprachdienste | Details                                                                                                                                                                                                                                                                            |
|---------------------------------------------------|-----------------------------------------------------------------|------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Übersetzung in Text                               | :heavy_check_mark:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| Übersetzung in Sprache                             | :heavy_check_mark:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| Globaler Endpunkt                                   | :heavy_check_mark:                                              | :heavy_minus_sign:                 | Die Spracherkennungsdienste bieten keinen globalen Endpunkt. Ein globaler Endpunkt kann den Datenverkehr automatisch zum nächstgelegenen regionalen Endpunkt leiten, wodurch die Latenz in Ihrer Anwendung verringert wird.                                                    |
| Regionale Endpunkte                                | :heavy_minus_sign:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| Verbindungszeitlimit                             | 90 Minuten                                               | Mit SDK unbegrenzt 10 Minuten mit einer WebSockets-Verbindung.                                                                                                                                                                                                                                                                                   |
| Authentifizierungsschlüssel im Header                                | :heavy_check_mark:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| Mehrere Sprachen in einer einzelnen Anforderung übersetzt | :heavy_minus_sign:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| SDKs verfügbar                                    | :heavy_minus_sign:                                              | :heavy_check_mark:                 | Informationen zu verfügbaren SDKs finden Sie in der [Dokumentation zum Spracherkennungsdienst](index.yml).                                                                                                                                                    |
| WebSockets-Verbindungen                             | :heavy_check_mark:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| Sprachen-API                                     | :heavy_check_mark:                                              | :heavy_minus_sign:                 | Der Spracherkennungsdienst unterstützt denselben Sprachumfang, der im Artikel [Sprachenreferenz für Sprachübersetzungs-API](../translator-speech/languages-reference.md) beschrieben ist. |
| Filter und Markierung für Obszönitäten                       | :heavy_minus_sign:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| .WAV/PCM als Eingabe                                 | :heavy_check_mark:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| Andere Dateitypen als Eingabe                         | :heavy_minus_sign:                                              | :heavy_minus_sign:                 |                                                                                                                                                                                                                                                                                    |
| Teilergebnisse                                   | :heavy_check_mark:                                              | :heavy_check_mark:                 |                                                                                                                                                                                                                                                                                    |
| Informationen zur zeitlichen Steuerung                                       | :heavy_check_mark:                                              | :heavy_minus_sign:                 |                                                                                                                                                                 |
| Korrelations-ID                                    | :heavy_check_mark:                                              | :heavy_minus_sign:                 |                                                                                                                                                                                                                                                                                    |
| Benutzerdefinierte Spracherkennungsmodelle                              | :heavy_minus_sign:                                              | :heavy_check_mark:                 | Der Spracherkennungsdienst bietet benutzerdefinierte Sprachmodelle, mit denen Sie die Spracherkennung an das spezifische Vokabular Ihres Unternehmens anpassen können.                                                                                                                                           |
| Benutzerdefinierte Übersetzungsmodelle                         | :heavy_minus_sign:                                              | :heavy_check_mark:                 | Wenn Sie die Textübersetzungs-API von Microsoft abonnieren, können Sie den [benutzerdefinierten Translator](https://www.microsoft.com/translator/business/customization/) verwenden, um Ihre eigenen Daten für präzisere Übersetzungen zu verwenden.                                                 |

## <a name="migration-strategies"></a>Migrationsstrategien

Wenn Sie oder Ihr Unternehmen Anwendungen in der Entwicklungs- oder Produktionsumgebung verwenden, die die Sprachübersetzungs-API verwenden, sollten Sie diese aktualisieren, um den Spracherkennungsdienst zu nutzen. Informationen zu verfügbaren SDKs, Codebeispielen und Tutorials finden Sie in der Dokumentation zum [Spracherkennungsdienst](index.yml). Berücksichtigen Sie bei der Migration Folgendes:

* Die Spracherkennungsdienste bieten keinen globalen Endpunkt. Ermitteln Sie, ob Ihre Anwendung effizient funktioniert, wenn sie einen einzigen regionalen Endpunkt für den gesamten Datenverkehr verwendet. Wenn nicht, verwenden Sie die Geolokalisierung, um den effizientesten Endpunkt zu bestimmen.

* Wenn Ihre Anwendung langlebige Verbindungen verwendet und die verfügbaren SDKs nicht nutzen kann, können Sie eine WebSockets-Verbindung verwenden. Steuern Sie das Zeitlimit von 10 Minuten, indem Sie die Verbindung zum jeweils richtigen Zeitpunkt wiederherstellen.

* Wenn Ihre Anwendung die Textübersetzungs-API und die Sprachübersetzungs-API verwendet, um benutzerdefinierte Übersetzungsmodelle zu aktivieren, können Sie Kategorie-IDs direkt mithilfe des Spracherkennungsdiensts hinzufügen.

* Im Gegensatz zur Sprachübersetzungs-API kann der Spracherkennungsdienst Übersetzungen in mehrere Sprachen in einer einzigen Anforderung durchführen.

## <a name="next-steps"></a>Nächste Schritte

* [Kostenloses Testen des Spracherkennungsdiensts](get-started.md)
* [Schnellstart: Erkennen von Sprache in einer UWP-App mit dem Speech SDK](quickstart-csharp-uwp.md)

## <a name="see-also"></a>Weitere Informationen

* [Worum handelt es sich beim Speech-Dienst?](overview.md)
* [Dokumentation zum Spracherkennungsdienst und zum Spracherkennungsdienst-SDK](https://docs.microsoft.com/azure/cognitive-services/speech-service/speech-devices-sdk-qsg)