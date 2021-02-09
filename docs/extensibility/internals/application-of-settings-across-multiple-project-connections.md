---
title: Applicare le impostazioni tra più connessioni di progetto
description: Informazioni su come applicare le impostazioni tra più connessioni di progetto tramite un plug-in del controllo del codice sorgente per eseguire un'operazione batch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 14b466112e3939756142a43568ddc3107e55d659
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906095"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Applicazione delle impostazioni tra più connessioni di progetto
Un plug-in del controllo del codice sorgente compilato con l'API del plug-in del controllo del codice sorgente versione 1,2, può usare un'operazione batch per eseguire la stessa operazione del controllo del codice sorgente tra più progetti o più contesti di connessione. I batch possono essere usati per eliminare le finestre di dialogo ridondanti per progetto dall'esperienza utente.

 Se un utente seleziona più elementi che appartengono a più di una connessione in un plug-in del controllo del codice sorgente compilato usando l'API del plug-in del controllo del codice sorgente versione 1,1 (ad esempio, due progetti Web in diversi computer con una condivisione file) e li estrae, l'utente visualizza ripetutamente la stessa finestra di dialogo. Questo scenario si verifica anche se l'utente fa clic sulla casella di controllo **applica a tutti** nella finestra di dialogo, perché l'IDE Reimposta lo stato per ogni contesto di connessione.

## <a name="new-capability-flag"></a>Nuovo flag funzionalità
 La `SccBeginBatch` funzione imposta il `SCC_CAP_BATCH` flag per indicare che è in corso un'operazione batch.

## <a name="new-functions"></a>Nuove funzioni
Le nuove funzioni seguenti supportano l'operazione batch:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

La `SCCBeginBatch` funzione avvia un gruppo di operazioni del controllo del codice sorgente. La `SccEndBatch` funzione chiude il gruppo. I gruppi non possono essere annidati.

## <a name="see-also"></a>Vedi anche
- [Novità dell'API del plug-in del controllo del codice sorgente versione 1,2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
