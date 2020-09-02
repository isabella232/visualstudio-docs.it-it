---
title: Ovverride di Gestione contenuto della Guida | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 95fe6396-276b-4ee5-b03d-faacec42765f
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 70c0044a0436dcf27a3b087b3f11a5f759824735
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645555"
---
# <a name="help-content-manager-overrides"></a>Ovverride di Gestione contenuto della Guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile modificare il Registro di sistema per modificare il comportamento predefinito del visualizzatore della Guida e le funzionalità correlate alla Guida nell'IDE di Visual Studio.

|Attività|Chiave del Registro di sistema|Valore e definizione|
|----------|------------------|--------------------------|
|Definire l'endpoint di servizio univoco|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|NewContentAndUpdateService--*HTTPValueForTheServiceEndpoint*.|
|Definire l'impostazione predefinita online/offline|HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help|UseOnlineHelp--Immettere `0` per specificare la Guida locale e `1` per specificare la Guida online.|
|Definire l'endpoint univoco F1|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VSWinExpress\14.0\Help|OnlineBaseUrl--*HTTPValueForTheServiceEndpoint*|
|Eseguire l'override della priorità del processo BITS|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\Help\v2.2|BITSPriority--Usare uno dei valori seguenti: **foreground**, **high**, **normal** o **low**.|
|Disabilitare la guida online (e l'opzione online dell'IDE)|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\VisualStudio\14.0\Help|OnlineHelpPreferenceDisabled--Impostare su 1 per disabilitare l'accesso al contenuto della Guida online.|
|Disabilitare la gestione del contenuto|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\VisualStudio\14.0\Help|ContentManagementDisabled--Impostare su 1 per disabilitare la scheda **Gestisci contenuto** in Help Viewer.|
|Puntare all'archivio del contenuto locale nella condivisione di rete|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio11|LocationPath="*ContentStoreNetworkShare*"|
|Disabilitare l'installazione del contenuto al primo avvio della funzionalità di Visual Studio.|HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node (nei computer a 64 bit)\Microsoft\VisualStudio\14.0\Help|DisableFirstRunHelpSelection--Impostare su 1 per disabilitare le funzionalità della guida configurate la prima volta che si esegue Visual Studio.|

## <a name="see-also"></a>Vedere anche
 [Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md)
