---
title: Thread | Microsoft Docs
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
- debugging [Debugging SDK], threads
- threading [Debugging SDK]
ms.assetid: 2243d24a-c3d2-41d1-abbb-6db21a2db9ee
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8070107a1befab999f2edd47d32e25e84266b86d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526446"
---
# <a name="threads"></a>Thread
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [thread](https://docs.microsoft.com/visualstudio/extensibility/debugger/threads).  
  
In termini di architettura del debugger, un **thread**:  
  
-   È l'unità fondamentale di calcolo. Un thread viene eseguito in modo sequenziale le proprie istruzioni all'interno del contesto di uno stack di chiamate singolo, lo spostamento dal contesto di un codice a quella successiva.  
  
-   Possibile identificare se stesso e il programma è in esecuzione in e può essere denominato, sospesa e ripresa. Un thread può inoltre enumerare relativo frame dello stack associata e, in alcune condizioni, può essere spostato in un altro stack frame. Dato il contesto di un frame dello stack, un thread può restituire il thread logico associato, se presente. Un thread dispone di proprietà, ad esempio un conteggio di sospensione, che possono essere visualizzati nella finestra thread dell'IDE.  
  
-   È rappresentato da un [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) interfaccia, in genere creato da un motore di debug (DE) o una macchina virtuale di conseguenza l'esecuzione di un programma.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Gestione del debug delle sessioni](../../extensibility/debugger/session-debug-manager.md)

