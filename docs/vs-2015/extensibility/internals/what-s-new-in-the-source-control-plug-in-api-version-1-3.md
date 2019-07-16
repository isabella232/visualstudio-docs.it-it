---
title: Cosa&#39;s nuove nell'origine del plug-in versione 1.3 dell'API di controllo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d5333a5b44e9c990843e66da357578e4a90d210
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200926"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Cosa&#39;plug-in versione 1.3 dell'API di controllo s nuove nell'origine
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'API dei plug-in del controllo origine versione 1.3 introduce le nuove funzioni seguenti per fornire un controllo più avanzato.  
  
## <a name="changes"></a>Modifiche  
 Le funzioni seguenti sono nuove per le API dei plug-in del controllo origine versione 1.3:  
  
|Funzione|Panoramica|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Consente di bits funzionalità aggiuntiva per essere segnalato|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Consente di esaminare i file con le versioni più recenti nel database di controllo della versione sul disco locale|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Consente di esaminare lo stato delle modifiche di nome (ridenominazioni, aggiunte ed eliminazioni) per i file specificati|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Consente di esaminare file e directory nel database di controllo della versione|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco di file specificato dal database di controllo di versione nel progetto corrente|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Esegue un invisibile all'utente "Get" dei file specificati (non è visualizzata alcuna interfaccia utente)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Consente di accedere alle opzioni specifiche dell'utente|  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
