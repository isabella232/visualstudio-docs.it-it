---
title: Confrontare la cartella di progetto di origine controllo Store | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ac710fd3994dca24d8e15e3d15c18d9f456a744
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56614194"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale con l'archivio del controllo del codice sorgente
In origine controllare il confronto tra la cartella di progetto locale e il controllo del codice sorgente viene eseguito usando le funzioni di plug-in API 1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 All'interno **Esplora soluzioni**, se si seleziona una cartella anziché un singolo file, il **confrontare le versioni** richiama il nuovo menu di scelta rapida [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e[ SccDirDiff](../../extensibility/sccdirdiff-function.md) nel plug-in del controllo del codice sorgente.

## <a name="new-capability-flags"></a>Nuovi flag funzionalità
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Nuove funzioni
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 Il `SccDirQueryInfo` funzione viene chiamata prima `SccDirDiff` per determinare se la directory di lavoro è controllato dal codice sorgente. Il `SccDirDiff` funzione consente di visualizzare le differenze tra la directory corrente e la cartella di controllo di origine corrispondente. Questo comando richiede il controllo del codice sorgente del plug-in per visualizzare l'elenco delle modifiche alla directory. Un plug-in del controllo del codice sorgente fornisce la propria interfaccia utente per visualizzare le differenze.

> [!NOTE]
>  Questa funzione Usa gli stessi flag di comando come [SccDiff](../../extensibility/sccdiff-function.md). Un provider di plug-in del controllo codice sorgente, è possibile scegliere di non supportare l'operazione "diff veloce" per le directory.

## <a name="see-also"></a>Vedere anche
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)