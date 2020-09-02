---
title: Gestione debug sessione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157835"
---
# <a name="session-debug-manager"></a>Gestione del debug delle sessioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gestione debug sessione (SDM) gestisce un numero qualsiasi di motori di debug (DE) che esegue il debug di un numero qualsiasi di programmi in più processi in un numero qualsiasi di computer. Oltre a essere un motore di debug multiplexer, SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.  
  
## <a name="session-debug-manager-operation"></a>Operazione di gestione del debug della sessione  
 Gestione debug sessione (SDM) gestisce il DE. In un computer può essere in esecuzione contemporaneamente più di un motore di debug. Per eseguire il multiplexing delle DEs, il SDM esegue il wrapping di un numero di interfacce dal DEs e le espone all'IDE come una singola interfaccia.  
  
 Per migliorare le prestazioni, alcune interfacce non vengono multiplexate. Vengono invece utilizzati direttamente da DE e le chiamate a queste interfacce non passano attraverso la SDM. Ad esempio, le interfacce usate con i contesti di memoria, di codice e di documento non sono multiplex, perché fanno riferimento a un'istruzione, a una memoria o a un documento specifico in un programma specifico sottoposto a debug da uno specifico DE. Non è necessario che altre richieste siano necessarie per questo livello di comunicazione.  
  
 Questa operazione non è valida per tutti i contesti. Le chiamate all'interfaccia del contesto di valutazione dell'espressione passano attraverso l'SDM. Durante la valutazione dell'espressione, il SDM esegue il wrapping dell'interfaccia [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) che fornisce all'IDE perché, quando tale espressione viene valutata, può coinvolgere più des che eseguono il debug di programmi nello stesso processo che potrebbe essere in esecuzione nello stesso thread.  
  
 Il SDM funge in genere da meccanismo di delega, ma può fungere da meccanismo di trasmissione. Ad esempio, durante la valutazione dell'espressione, SDM funge da meccanismo di trasmissione per notificare a tutti i DEs che possono eseguire codice in un thread specificato. Analogamente, quando SDM riceve un evento di arresto, trasmette a tutti i programmi che dovrebbero arrestare l'esecuzione. Quando viene chiamato un passaggio, il SDM trasmette a tutti i programmi che possono continuare l'esecuzione. I punti di interruzione vengono trasmessi anche a ogni DE.  
  
 SDM non rileva il programma, il thread o la stack frame corrente. Le informazioni relative al processo, al programma e al thread vengono inviate all'SDM insieme a eventi di debug specifici.  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)
