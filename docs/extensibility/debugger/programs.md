---
title: I programmi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8bd34f72f54fe068ff39b752ddbd6348e4970db
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252375"
---
# <a name="programs"></a>Programs
Nell'architettura di debugger, un *programma*:  
  
-   È un contenitore per un set di thread e un set di moduli. Un programma non ha nessuna analogia singolo nel sistema operativo Windows.  
  
     Un programma è un tipo di processo secondario. Ad esempio, quando si esegue il debug di un sito Web, uno script può essere considerato un programma. Mentre è in esecuzione uno script nel processo del motore di scripting, indipendente da altri script, include anche un proprio set di thread. Un motore di debug (DE) viene associato a un programma e non a un processo o un thread.  
  
-   Possibile identificare se stesso e il processo in che è in esecuzione. Un programma può essere collegato per essere disconnesso da e descrivere il DE cui è stato creato, se presente. Un programma può anche eseguire, arrestare, continuare ed essere terminato.  
  
-   Possibile enumerare tutti i relativi thread. Un programma può fornire anche il proprio flusso disassembly e possa enumerare tutti i contesti di codice di una posizione del documento specificato.  
  
-   È rappresentato da un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interfaccia, creata prima che il programma viene collegato o come parte del processo di collegamento, a seconda dell'implementazione. Quando una porta enumera i programmi di un processo, viene creato ogni programma in base a una corrispondente [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) passata come argomento a interfaccia [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Mentre i motori di debug anche creare `IDebugProgram2` interfacce per rappresentare i programmi, questi programmi non vengono create in base a un nodo di programma. Il `IDebugProgramNode2` interfacce create da un CRI vengono usate per eseguire il debug effettivi, mentre quelli creati da una porta sono utilizzati solo per l'individuazione dei quali programmi sono in esecuzione in un processo.  
  
## <a name="see-also"></a>Vedere anche  
 [Processi](../../extensibility/debugger/processes.md)   
 [Nodi di programma](../../extensibility/debugger/program-nodes.md)   
 [Moduli](../../extensibility/debugger/modules.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Posizione di documento](../../extensibility/debugger/document-position.md)   
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)