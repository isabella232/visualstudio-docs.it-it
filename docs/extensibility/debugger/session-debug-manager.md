---
title: Sessione di Debug Manager | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321b0a7c7eb2a30465098da39abc49cbc9261e11
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947205"
---
# <a name="session-debug-manager"></a>Gestione del debug della sessione
Gestore di sessione di debug (SDM) gestisce un numero qualsiasi di motori di debug (DE) che esegue il debug di un numero qualsiasi di programmi in più processi in un numero qualsiasi di macchine. Oltre a essere un motore di debug multiplexer, il modello SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.  
  
## <a name="session-debug-manager-operation"></a>Operazione sessione di debug manager  
 Gestore di sessione di debug (SDM) gestisce il DE. Può essere presente più di un motore di debug in esecuzione in un computer nello stesso momento. Per moltiplicare la crittografia DEs, il modello SDM esegue il wrapping di un numero di interfacce dalla crittografia DEs e li espone all'IDE come un'unica interfaccia.  
  
 Per migliorare le prestazioni, non sono multiplex alcune interfacce. Al contrario, vengono utilizzati direttamente dal DE e le chiamate a queste interfacce non passano attraverso il modello SDM. Ad esempio, non sono multiplex interfacce usate con memoria, il codice e contesti di documento, perché fanno riferimento a un'istruzione specifica, memoria o documento in un programma specifico di debug da un CRI specifico. Nessun altro Germania dovrà essere coinvolti in tale livello di comunicazione.  
  
 Ciò non vale per tutti i contesti. Le chiamate all'interfaccia di contesto di valutazione di espressione passano attraverso il modello SDM. Durante la valutazione dell'espressione, il modello SDM esegue il wrapping di [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che consente a IDE perché quando tale espressione viene valutata e può comportare più DEs che sta eseguendo il debug di programmi nello stesso processo che potrebbero essere in esecuzione sullo stesso thread.  
  
 Il modello SDM funge in genere da un meccanismo di delega, ma può fungere da un meccanismo di trasmissione. Ad esempio, durante la valutazione dell'espressione, il modello SDM agisce come un meccanismo di trasmissione per notificare tutti DEs che possono eseguire codice su un thread specificato. Analogamente, quando il modello SDM riceve un evento di arresto, trasmette i programmi che non possono più in esecuzione. Quando viene chiamato un passaggio, il modello SDM trasmette ai programmi che è possibile continuare l'esecuzione. I punti di interruzione vengono anche trasmessi a ogni DE.  
  
 Il modello SDM non rileva il programma corrente, thread o dello stack frame. Il processo, programma e informazioni sul thread vengono inviati per il modello SDM in combinazione con eventi di debug specifici.  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)