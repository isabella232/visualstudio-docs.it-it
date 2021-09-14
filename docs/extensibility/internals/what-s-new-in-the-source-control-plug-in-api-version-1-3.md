---
title: Novità &apos; dell'API del plug-in del controllo del codice sorgente 1.3
description: Informazioni sulle novità dell'API plug-in del controllo del codice sorgente versione 1.3, che introduce le nuove funzioni per fornire un controllo più avanzato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1b3ee614a0f754307c37e5d48dfb3d9f461ec432
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711730"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Novità&#39;'API del plug-in del controllo del codice sorgente versione 1.3
L'API plug-in del controllo del codice sorgente versione 1.3 introduce le nuove funzioni seguenti per fornire un controllo più avanzato.

## <a name="changes"></a>Modifiche
 Le funzioni seguenti sono una novità dell'API plug-in del controllo del codice sorgente versione 1.3:

|Funzione|Panoramica|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Consente di segnalar bit di funzionalità aggiuntivi|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Consente l'esame dei file con versioni più recenti nel database di controllo della versione rispetto al disco locale|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Consente di esaminare lo stato delle modifiche dei nomi (ridenominazioni, aggiunte ed eliminazioni) per i file specificati|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Consente l'esame di directory e file nel database di controllo della versione|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco specificato di file dal database del controllo della versione al progetto corrente|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Esegue un'operazione "Get" invisibile all'utente dei file specificati (non viene visualizzata alcuna interfaccia utente)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Consente l'accesso alle opzioni specifiche dell'utente|

## <a name="see-also"></a>Vedi anche
- [Per iniziare](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
