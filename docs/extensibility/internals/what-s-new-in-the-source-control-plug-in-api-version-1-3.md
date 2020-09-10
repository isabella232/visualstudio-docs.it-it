---
title: "&apos;Novità dell'API del plug-in del controllo del codice sorgente 1,3"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0eb580d018bbb858cd0214970bdba3d4ab4f391c
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741540"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>Novità dell'API del plug-in del controllo del codice sorgente versione 1,3&#39;
L'API del plug-in del controllo del codice sorgente versione 1,3 introduce le nuove funzioni seguenti per fornire un controllo più avanzato.

## <a name="changes"></a>Modifiche
 Le seguenti funzioni sono nuove per l'API del plug-in del controllo del codice sorgente versione 1,3:

|Function|Panoramica|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Consente di segnalare i bit aggiuntivi della funzionalità|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Consente di esaminare i file con versioni più recenti nel database di controllo della versione rispetto al disco locale|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Consente di esaminare lo stato delle modifiche dei nomi (Rinomina, aggiunte ed eliminazioni) per i file specificati|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Consente di esaminare le directory e i file nel database di controllo della versione|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco specificato di file dal database del controllo della versione al progetto corrente|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Esegue un'"Get" invisibile ai file specificati (non viene visualizzata alcuna interfaccia utente)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Consente l'accesso alle opzioni specifiche dell'utente|

## <a name="see-also"></a>Vedere anche
- [Per iniziare](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
