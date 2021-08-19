---
title: Programmi | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un programma nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0fcbd1d6ac01d4d67ad03193c1fa2b2e75ded6d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160335"
---
# <a name="programs"></a>Programmi
Nell'architettura del debugger, un *programma*:

- Contenitore sia per un set di thread che per un set di moduli. Un programma non ha alcuna analogia nel sistema Windows operativo.

     Un programma è un tipo di processo secondario. Ad esempio, quando si esegue il debug di un sito Web, uno script può essere visto come programma. Mentre uno script viene eseguito nel processo del motore di scripting, indipendentemente da altri script, ha anche un proprio set di thread. Un motore di debug (DE) si collega a un programma e non a un processo o a un thread.

- Può identificare se stesso e il processo in cui è in esecuzione. Un programma può essere collegato, scollegato da e descrivere l'istanza di de che lo ha creato, se presente. Un programma può anche eseguire, arrestare, continuare e essere terminato.

- Può enumerare tutti i relativi thread. Un programma può anche fornire il proprio flusso di disassembly e può enumerare tutti i contesti di codice di una determinata posizione del documento.

- È rappresentato da [un'interfaccia IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) creata prima che il programma sia collegato o come parte del processo di connessione, a seconda dell'implementazione. Quando una porta enumera i programmi di un processo, ogni programma viene creato in base a [un'interfaccia IDebugProgramNode2 corrispondente](../../extensibility/debugger/reference/idebugprogramnode2.md) passata come argomento ad [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Anche se i motori di debug creano anche interfacce per rappresentare i programmi, questi programmi non vengono `IDebugProgram2` creati in base a un nodo di programma. Le interfacce create da un de vengono usate per il debug effettivo, mentre quelle create da una porta vengono usate solo per individuare i programmi `IDebugProgramNode2` in esecuzione in un processo.

## <a name="see-also"></a>Vedi anche
- [Processi](../../extensibility/debugger/processes.md)
- [Nodi di programma](../../extensibility/debugger/program-nodes.md)
- [Moduli](../../extensibility/debugger/modules.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Posizione del documento](../../extensibility/debugger/document-position.md)
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
