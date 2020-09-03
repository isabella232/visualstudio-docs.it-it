---
title: Programmi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738203"
---
# <a name="programs"></a>Programmi
Nell'architettura del debugger, un *programma*:

- È un contenitore per un set di thread e un set di moduli. Un programma non ha una singola analogia nel sistema operativo Windows.

     Un programma è un tipo di sottoprocesso. Ad esempio, quando si esegue il debug di un sito Web, uno script può essere considerato come un programma. Mentre uno script viene eseguito nel processo del motore di script, indipendentemente da altri script, dispone anche di un proprio set di thread. Un motore di debug (DE) si connette a un programma e non a un processo o a un thread.

- Consente di identificare se stesso e il processo in cui è in esecuzione. Un programma può essere collegato a, essere scollegato da e descrivere il DE che lo ha creato, se disponibile. Un programma può anche eseguire, arrestare, continuare ed essere terminato.

- Consente di enumerare tutti i relativi thread. Un programma può anche fornire il proprio flusso di Disassembly ed è in grado di enumerare tutti i contesti di codice di una determinata posizione del documento.

- È rappresentato da un'interfaccia [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , creata prima che il programma venga collegato o come parte del processo di connessione, a seconda dell'implementazione. Quando una porta enumera i programmi di un processo, ogni programma viene creato in base a un'interfaccia [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) corrispondente passata come argomento a [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Sebbene i motori di debug creino anche `IDebugProgram2` interfacce per rappresentare i programmi, questi programmi non vengono creati in base a un nodo del programma. Le `IDebugProgramNode2` interfacce create da un de vengono usate per il debug effettivo, mentre quelle create da una porta vengono usate solo per individuare i programmi in esecuzione in un processo.

## <a name="see-also"></a>Vedere anche
- [Processi](../../extensibility/debugger/processes.md)
- [Nodi del programma](../../extensibility/debugger/program-nodes.md)
- [Moduli](../../extensibility/debugger/modules.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Posizione del documento](../../extensibility/debugger/document-position.md)
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
