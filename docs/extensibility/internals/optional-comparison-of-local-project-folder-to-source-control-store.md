---
title: Confrontare la cartella del progetto con l'archivio del controllo del codice sorgente | Microsoft Docs
description: Nell'API del plug-in del controllo del codice sorgente, il confronto tra la cartella del progetto locale e il controllo del codice sorgente viene eseguito usando SccDirQueryInfo e SccDirDiff.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f7b334bb6e1b73dd31060020378e91b74e5af102
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063045"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale con l'archivio del controllo del codice sorgente
Nell'API del plug-in del controllo del codice sorgente 1,2 il confronto tra la cartella del progetto locale e il controllo del codice sorgente viene eseguito usando le funzioni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 All'interno **Esplora soluzioni**, se è stata selezionata una cartella anziché un singolo file, il menu di scelta rapida **Confronta versioni** richiama i nuovi [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) nel plug-in del controllo del codice sorgente.

## <a name="new-capability-flags"></a>Nuovi flag funzionalità
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Funzioni nuove
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 La `SccDirQueryInfo` funzione viene chiamata prima `SccDirDiff` di per determinare se la directory di lavoro è controllata dal codice sorgente. La `SccDirDiff` funzione Visualizza le differenze tra la directory locale corrente e la cartella del controllo del codice sorgente corrispondente. Questo comando chiede al plug-in del controllo del codice sorgente di visualizzare l'elenco delle modifiche apportate alla directory. Un plug-in del controllo del codice sorgente fornisce una propria interfaccia utente per visualizzare le differenze.

> [!NOTE]
> Questa funzione usa gli stessi flag di comando di [SccDiff](../../extensibility/sccdiff-function.md). Come provider del plug-in del controllo del codice sorgente, è possibile scegliere di non supportare l'operazione "diff veloce" per le directory.

## <a name="see-also"></a>Vedi anche
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
