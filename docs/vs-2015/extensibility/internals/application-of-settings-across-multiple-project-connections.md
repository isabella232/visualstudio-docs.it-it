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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203843"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Applicazione delle impostazioni attraverso più connessioni di progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un plug-in del controllo del codice sorgente compilato utilizzando l'API del plug-in del controllo del codice sorgente 1,2, può utilizzare un'operazione batch per eseguire la stessa operazione del controllo del codice sorgente tra più progetti o più contesti di connessione. I batch possono essere usati per eliminare le finestre di dialogo ridondanti per progetto dall'esperienza utente.  
  
 Se un utente seleziona più elementi che appartengono a più di una connessione in un plug-in del controllo del codice sorgente compilato utilizzando l'API del plug-in del controllo del codice sorgente 1,1, ad esempio due progetti Web in diversi computer di condivisione file, e li estrae, l'utente visualizza ripetutamente la stessa finestra di dialogo. Ciò si verifica anche se l'utente fa clic sulla casella di controllo **applica a tutti** nella finestra di dialogo, perché l'IDE Reimposta lo stato per ogni contesto di connessione.  
  
## <a name="new-capability-flag"></a>Nuovo flag funzionalità  
 `SccBeginBatch` Function imposta il `SCC_CAP_BATCH` flag per indicare che è in corso un'operazione batch  
  
## <a name="new-functions"></a>Funzioni nuove  
 Le nuove funzioni seguenti supportano l'operazione batch:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  La `SCCBeginBatch` funzione avvia un gruppo di operazioni del controllo del codice sorgente. `SccEndBatch` chiude il gruppo. I gruppi non possono essere annidati.  
  
## <a name="see-also"></a>Vedere anche  
 [Novità della versione 1.2 dell'API del plug-in del controllo del codice sorgente](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
