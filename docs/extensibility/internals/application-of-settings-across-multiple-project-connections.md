---
title: Applicazione delle impostazioni su più connessioni di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710057"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Applicazione delle impostazioni su più connessioni di progetto
Un plug-in del controllo del codice sorgente compilato utilizzando l'API del plug-in del controllo del codice sorgente versione 1.2, può utilizzare un'operazione batch per eseguire la stessa operazione di controllo del codice sorgente tra più progetti o più contesti di connessione. I batch possono essere utilizzati per eliminare le finestre di dialogo ridondanti per progetto dall'esperienza utente.

 Se un utente seleziona più elementi che appartengono a più di una connessione in un plug-in del controllo del codice sorgente compilato utilizzando l'API del plug-in del controllo del codice sorgente versione 1.1 (ad esempio, due progetti Web in computer di condivisione file diversi) e li estrae, l'utente vede ripetutamente la stessa finestra di dialogo. Questo scenario si verifica anche se l'utente fa clic sulla casella di controllo **Applica a tutti** nella finestra di dialogo, perché l'IDE reimposta lo stato per ogni contesto di connessione.

## <a name="new-capability-flag"></a>Nuovo flag di funzionalità
 La `SccBeginBatch` funzione `SCC_CAP_BATCH` imposta il flag per indicare che è in corso un'operazione batch.

## <a name="new-functions"></a>Nuove funzioni
Le seguenti nuove funzioni supportano l'operazione batch:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

La `SCCBeginBatch` funzione avvia un gruppo di operazioni di controllo del codice sorgente. La `SccEndBatch` funzione chiude il gruppo. I gruppi non possono essere nidificati.

## <a name="see-also"></a>Vedere anche
- [Novità dell'API del plug-in del controllo del codice sorgente versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
