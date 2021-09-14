---
title: Applicare le impostazioni tra più connessioni di progetto
description: Informazioni su come applicare le impostazioni tra più connessioni di progetto usando un plug-in di controllo del codice sorgente per eseguire un'operazione batch.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 21c1486855dba6906937f95f10cae2f323ff0383
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711766"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Applicazione delle impostazioni tra più connessioni di progetto
Un plug-in del controllo del codice sorgente compilato usando l'API plug-in del controllo del codice sorgente versione 1.2 può usare un'operazione batch per eseguire la stessa operazione di controllo del codice sorgente in più progetti o più contesti di connessione. I batch possono essere usati per eliminare dall'esperienza utente le finestre di dialogo ridondanti per ogni progetto.

 Se un utente seleziona più elementi che appartengono a più di una connessione in un plug-in del controllo del codice sorgente compilato usando l'API plug-in del controllo del codice sorgente versione 1.1 (ad esempio, due progetti Web in computer con condivisione file diversi) e li esemplifica, l'utente visualizza ripetutamente la stessa finestra di dialogo. Questo scenario si verifica anche  se l'utente fa clic sulla casella di controllo Applica a tutti nella finestra di dialogo, perché l'IDE reimposta il proprio stato per ogni contesto di connessione.

## <a name="new-capability-flag"></a>Nuovo flag di funzionalità
 La funzione imposta il flag per indicare che è in corso `SccBeginBatch` `SCC_CAP_BATCH` un'operazione batch.

## <a name="new-functions"></a>Nuove funzioni
Le nuove funzioni seguenti supportano l'operazione batch:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

La `SCCBeginBatch` funzione avvia un gruppo di operazioni di controllo del codice sorgente. La `SccEndBatch` funzione chiude il gruppo. I gruppi potrebbero non essere annidati.

## <a name="see-also"></a>Vedi anche
- [Novità dell'API del plug-in del controllo del codice sorgente versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
