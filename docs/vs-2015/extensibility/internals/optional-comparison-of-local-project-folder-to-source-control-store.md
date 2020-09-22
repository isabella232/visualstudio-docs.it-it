---
title: Confronto facoltativo tra la cartella di progetto locale e l'archivio del controllo del codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: be26b4195e0db7b3b78fcc2223ff2a6f8bde47d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839947"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale con l'archivio del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nell'API del plug-in del controllo del codice sorgente 1,2 il confronto tra la cartella del progetto locale e il controllo del codice sorgente viene eseguito usando le funzioni [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 All'interno **Esplora soluzioni**, se è stata selezionata una cartella anziché un singolo file, il menu di scelta rapida **Confronta versioni** richiama i nuovi [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md) nel plug-in del controllo del codice sorgente.  
  
## <a name="new-capability-flags"></a>Nuovi flag funzionalità  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Funzioni nuove  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 La `SccDirQueryInfo` funzione viene chiamata prima `SccDirDiff` di per determinare se la directory di lavoro è controllata dal codice sorgente. La `SccDirDiff` funzione Visualizza le differenze tra la directory locale corrente e la cartella del controllo del codice sorgente corrispondente. Questo comando chiede al plug-in del controllo del codice sorgente di visualizzare l'elenco delle modifiche apportate alla directory. Un plug-in del controllo del codice sorgente fornisce una propria interfaccia utente per visualizzare le differenze.  
  
> [!NOTE]
> Questa funzione usa gli stessi flag di comando di [SccDiff](../../extensibility/sccdiff-function.md). Come provider del plug-in del controllo del codice sorgente, è possibile scegliere di non supportare l'operazione "diff veloce" per le directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
