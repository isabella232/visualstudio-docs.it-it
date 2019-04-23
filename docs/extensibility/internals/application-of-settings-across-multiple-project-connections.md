---
title: Applicazione delle impostazioni tra più connessioni di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6dbc2638fa23a1e0c7bf1301c3c978a1ef864c75
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074099"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Applicazione delle impostazioni tra più connessioni di progetto
Un plug-in del controllo del codice sorgente compilati usando l'origine controllo plug-in API versione 1.2, può usare un'operazione batch per eseguire la stessa operazione di controllo di origine in più progetti o più contesti di connessione. Batch sono utilizzabile per eliminare le applicazioni ridondanti, finestre di dialogo dall'esperienza utente per ogni progetto.

 Se un utente seleziona più elementi che appartengono a più di una connessione in un plug-in del controllo del codice sorgente creata mediante origine controllo plug-in API versione 1.1 (ad esempio, due progetti web nei computer diversi con la condivisione file) e ne viene verificata l'uscita, l'utente vede lo stesso finestra di dialogo ripetutamente. Questo scenario si verifica anche se l'utente fa clic il **applica a tutti** casella di controllo nella finestra di dialogo, perché l'IDE Reimposta lo stato per ogni contesto di connessione.

## <a name="new-capability-flag"></a>Nuovo flag funzionalità
 Il `SccBeginBatch` viene impostata dalla funzione di `SCC_CAP_BATCH` flag per indicare che un'operazione batch è in corso.

## <a name="new-functions"></a>Nuove funzioni
Le nuove funzioni seguenti supportano l'operazione batch:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

Il `SCCBeginBatch` funzione inizia un gruppo di operazioni di controllo di origine. Il `SccEndBatch` funzione chiude il gruppo. I gruppi non possono essere annidati.

## <a name="see-also"></a>Vedere anche
- [Novità di plug-in origine controllo API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)