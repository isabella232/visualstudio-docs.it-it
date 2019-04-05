---
title: Applicazione delle impostazioni tra più connessioni di progetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "58970333"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Applicazione delle impostazioni attraverso più connessioni di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un plug-in del controllo del codice sorgente compilati usando l'API 1.2 plug-in controllo di origine, può usare un'operazione batch per eseguire la stessa operazione di controllo di origine in più progetti o più contesti di connessione. Batch sono utilizzabile per eliminare le applicazioni ridondanti, finestre di dialogo dall'esperienza utente per ogni progetto.  
  
 Se un utente seleziona più elementi che appartengono a più di una connessione in un plug-in del controllo del codice sorgente creata mediante API dei plug-in origine controllo 1.1, (ad esempio, due progetti Web nei computer diversi con la condivisione file) e ne viene verificata l'uscita, l'utente visualizzerà la stessa finestra di dialogo più volte. Ciò avviene anche se l'utente fa clic il **applica a tutti** casella di controllo nella finestra di dialogo, perché l'IDE Reimposta lo stato per ogni contesto di connessione.  
  
## <a name="new-capability-flag"></a>Nuovo Flag funzionalità  
 `SccBeginBatch` Viene impostata dalla funzione di `SCC_CAP_BATCH` flag per indicare che un'operazione batch è in corso  
  
## <a name="new-functions"></a>Nuove funzioni  
 Le nuove funzioni seguenti supportano l'operazione batch:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  Il `SCCBeginBatch` funzione inizia un gruppo di operazioni di controllo di origine. `SccEndBatch` Chiude il gruppo. I gruppi non possono essere annidati.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
