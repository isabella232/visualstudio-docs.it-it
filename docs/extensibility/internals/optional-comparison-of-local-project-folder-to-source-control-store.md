---
title: Confronto tra la cartella del progetto e l'archivio del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706869"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale con l'archivio del controllo del codice sorgente
Nel controllo del codice sorgente Plug-in API 1.2 il confronto tra la cartella del progetto locale e il controllo del codice sorgente viene eseguito utilizzando le funzioni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 All'interno di **Esplora soluzioni**, se viene selezionata una cartella anziché un singolo file, il menu di scelta rapida **Confronta versioni** richiama i nuovi [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) nel plug-in del controllo del codice sorgente.

## <a name="new-capability-flags"></a>Nuovi flag di funzionalità
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Funzioni nuove
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 La `SccDirQueryInfo` funzione viene `SccDirDiff` chiamata prima per determinare se la directory di lavoro è controllata dal codice sorgente. La `SccDirDiff` funzione visualizza le differenze tra la directory locale corrente e la cartella del controllo del codice sorgente corrispondente. Questo comando chiede al plug-in del controllo del codice sorgente di visualizzare l'elenco delle modifiche apportate alla directory. Un plug-in del controllo del codice sorgente fornisce la propria interfaccia utente per visualizzare le differenze.

> [!NOTE]
> Questa funzione utilizza gli stessi flag di comando di [SccDiff](../../extensibility/sccdiff-function.md). In qualità di provider di plug-in del controllo del codice sorgente, è possibile scegliere di non supportare l'operazione "diff rapido" per le directory.

## <a name="see-also"></a>Vedere anche
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
