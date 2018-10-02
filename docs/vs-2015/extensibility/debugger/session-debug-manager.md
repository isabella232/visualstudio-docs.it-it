---
title: Sessione di Debug Manager | Microsoft Docs
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
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aaeac3a5e728d73700b5c2b12d68f5918fd6e658
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540892"
---
# <a name="session-debug-manager"></a>Gestione del debug delle sessioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [sessione di Debug Manager](https://docs.microsoft.com/visualstudio/extensibility/debugger/session-debug-manager).  
  
Gestore di sessione di debug (SDM) gestisce un numero qualsiasi di motori di debug (DE) il debug di un numero qualsiasi di programmi in più processi in qualsiasi numero di computer. Oltre a essere un motore di debug multiplexer, il modello SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.  
  
## <a name="session-debug-manager-operation"></a>Operazione sessione di Debug Manager  
 Gestore di sessione di debug (SDM) gestisce il DE. Potrebbero essere presenti più di un motore di debug in esecuzione in un computer nello stesso momento. Per moltiplicare la crittografia DEs, il modello SDM esegue il wrapping di un numero di interfacce dalla crittografia DEs e li espone all'IDE come un'unica interfaccia.  
  
 Per migliorare le prestazioni, non sono in multiplexing alcune interfacce. Al contrario, vengono utilizzati direttamente dal DE e le chiamate a queste interfacce non passano attraverso il modello SDM. Ad esempio, le interfacce utilizzate con memoria, il codice e contesti di documento non sono in multiplexing, perché fanno riferimento a un'istruzione specifica, memoria o documento in un programma specifico di debug da un CRI specifico. Nessun altro Germania dovrà essere coinvolti in tale livello di comunicazione.  
  
 Ciò non vale per tutti i contesti. Le chiamate all'interfaccia di contesto di valutazione di espressione passano attraverso il modello SDM. Durante la valutazione dell'espressione, il modello SDM esegue il wrapping di [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che consente a IDE perché quando tale espressione viene valutata e può comportare più DEs che sta eseguendo il debug di programmi nello stesso processo che potrebbero essere in esecuzione sullo stesso thread.  
  
 Il modello SDM funge in genere da un meccanismo di delega, ma può fungere da un meccanismo di trasmissione. Ad esempio, durante la valutazione dell'espressione, il modello SDM agisce come un meccanismo di trasmissione per notificare tutti DEs che possono eseguire codice su un thread specificato. Analogamente, quando il modello SDM riceve un evento di arresto, trasmette tutti i programmi che non possono più in esecuzione. Quando viene chiamato un passaggio, il modello SDM trasmette a tutti i programmi che è possibile continuare l'esecuzione. I punti di interruzione vengono anche trasmessi a ogni DE.  
  
 Il modello SDM non rileva il programma corrente, thread o dello stack frame. Il processo, programma e thread informazioni vengono inviate a SDM in combinazione con eventi di debug specifici.  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)

