---
title: Confrontare Project cartella con l'archivio del controllo del codice sorgente | Microsoft Docs
description: Nell'API plug-in del controllo del codice sorgente il confronto tra la cartella del progetto locale e il controllo del codice sorgente viene eseguito usando SccDirQueryInfo e SccDirDiff.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 76d57b288a221b2b7e89494605aaccd4df752821
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063109"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale con l'archivio del controllo del codice sorgente
Nell'API plug-in del controllo del codice sorgente 1.2 il confronto tra la cartella del progetto locale e il controllo del codice sorgente viene eseguito usando le funzioni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).

 In **Esplora soluzioni**, se è selezionata una cartella anziché  un singolo file, il menu di scelta rapida Confronta versioni richiama i nuovi [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) nel plug-in del controllo del codice sorgente.

## <a name="new-capability-flags"></a>Nuovi flag di funzionalità
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>Funzioni nuove
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 La `SccDirQueryInfo` funzione viene chiamata prima di per `SccDirDiff` determinare se la directory di lavoro è controllata dal codice sorgente. La `SccDirDiff` funzione visualizza le differenze tra la directory locale corrente e la cartella del controllo del codice sorgente corrispondente. Questo comando chiede al plug-in del controllo del codice sorgente di visualizzare l'elenco delle modifiche alla directory. Un plug-in del controllo del codice sorgente fornisce la propria interfaccia utente per visualizzare le differenze.

> [!NOTE]
> Questa funzione usa gli stessi flag di comando di [SccDiff](../../extensibility/sccdiff-function.md). Come provider di plug-in del controllo del codice sorgente, è possibile scegliere di non supportare l'operazione di "diff rapido" per le directory.

## <a name="see-also"></a>Vedi anche
- [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
