---
title: Cosa&#39;s nuove nell'origine del plug-in versione 1.3 dell'API di controllo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b61e56fcef8bbbe8e9f36a39580eae14ad582d5
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56645979"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Cosa&#39;plug-in versione 1.3 dell'API di controllo s nuove nell'origine
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
- [Introduzione](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)