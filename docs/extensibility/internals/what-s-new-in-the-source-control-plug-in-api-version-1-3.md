---
title: Che cosa&#39;s nuovo nell'API del plug-in del controllo del codice sorgente versione 1.3 Documenti Microsoft
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
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703369"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>&#39;Novità dell'API del plug-in del controllo del codice sorgente versione 1.3
L'API plug-in del controllo del codice sorgente versione 1.3 introduce le nuove funzioni seguenti per fornire un controllo più avanzato.

## <a name="changes"></a>Modifiche
 Le seguenti funzioni sono nuove per l'API del plug-in del controllo del codice sorgente versione 1.3:

|Funzione|Panoramica|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Consente di segnalare ulteriori bit di funzionalità|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Consente l'esame dei file con versioni più recenti nel database di controllo della versione rispetto al disco locale|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Consente di esaminare lo stato delle modifiche dei nomi (rinominazioni, aggiunte ed eliminazioni) per i file specificati|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Consente l'esame di directory e file nel database di controllo della versione|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco specificato di file dal database del controllo della versione al progetto corrente|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Esegue un "Get" invisibile all'utente dei file specificati (non viene visualizzata alcuna interfaccia utente)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Consente l'accesso a opzioni specifiche dell'utente|

## <a name="see-also"></a>Vedere anche
- [Guida introduttiva](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
