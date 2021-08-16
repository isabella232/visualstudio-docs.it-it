---
title: Novità dell'API plug-in del controllo del codice sorgente &apos; 1.3
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
ms.openlocfilehash: 5b7b200a45dd0fe87ff399917e196e00b3c365cdff854c5caa01ba22ab30672d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359117"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Novità&#39;'API plug-in del controllo del codice sorgente versione 1.3
L'API plug-in del controllo del codice sorgente versione 1.3 introduce le nuove funzioni seguenti per fornire un controllo più avanzato.

## <a name="changes"></a>Modifiche
 Le funzioni seguenti non sono nuove dell'API plug-in del controllo del codice sorgente versione 1.3:

|Funzione|Panoramica|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Consente la notifica di bit di funzionalità aggiuntivi|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Consente l'esame dei file con versioni più recenti nel database di controllo della versione rispetto al disco locale|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Consente di esaminare lo stato delle modifiche del nome (ridenominazioni, aggiunte ed eliminazioni) per i file specificati|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Consente l'esame di directory e file nel database del controllo della versione|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco specificato di file dal database del controllo della versione al progetto corrente|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Esegue un'operazione "Get" invisibile all'utente dei file specificati (non viene visualizzata alcuna interfaccia utente)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Consente l'accesso alle opzioni specifiche dell'utente|

## <a name="see-also"></a>Vedi anche
- [Per iniziare](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
