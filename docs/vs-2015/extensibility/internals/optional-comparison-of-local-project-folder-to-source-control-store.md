---
title: Confronto facoltativo della cartella di progetto locale a origine controllo Store | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b6806a01127250b2376fee0aa77d55554eeba9bc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530628"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>Confronto facoltativo della cartella di progetto locale con l'archivio del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [confrontare cartella del progetto di origine controllo Store](https://docs.microsoft.com/visualstudio/extensibility/internals/optional-comparison-of-local-project-folder-to-source-control-store).  
  
In origine controllare il confronto tra la cartella di progetto locale e il controllo del codice sorgente viene eseguito usando le funzioni di plug-in API 1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e [SccDirDiff](../../extensibility/sccdirdiff-function.md).  
  
 All'interno **Esplora soluzioni**, se si seleziona una cartella anziché un singolo file, il **confrontare le versioni** richiama il nuovo menu di scelta rapida [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) e[ SccDirDiff](../../extensibility/sccdirdiff-function.md) nel plug-in del controllo del codice sorgente.  
  
## <a name="new-capability-flags"></a>Nuovi flag funzionalità  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>Nuove funzioni  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 Il `SccDirQueryInfo` funzione viene chiamata prima `SccDirDiff` per determinare se la directory di lavoro è controllato dal codice sorgente. Il `SccDirDiff` funzione consente di visualizzare le differenze tra la directory corrente e la cartella di controllo di origine corrispondente. Questo comando richiede il controllo del codice sorgente del plug-in per visualizzare l'elenco delle modifiche alla directory. Un plug-in del controllo del codice sorgente fornisce la propria interfaccia utente per visualizzare le differenze.  
  
> [!NOTE]
>  Questa funzione Usa gli stessi flag di comando come [SccDiff](../../extensibility/sccdiff-function.md). Un provider di plug-in del controllo codice sorgente, è possibile scegliere di non supportare l'operazione "diff veloce" per le directory.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

