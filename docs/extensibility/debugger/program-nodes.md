---
title: Nodi di programma Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738212"
---
# <a name="program-nodes"></a>Nodi di programma
Nell'architettura del debugger, un *nodo di programma*:

- È una descrizione leggera di un programma.

- Può identificare se stesso e il processo in cui è in esecuzione. Un nodo di programma può essere collegato, essere scollegato da e descrivere il motore di debug (DE) che lo ha creato, se presente.

- È rappresentato da un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia, in genere creato da un DE o una porta. I nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando un nodo di programma viene aggiunto a una porta, viene aggiunto al processo contenente il programma rappresentato da questo nodo di programma.

  Qualche volta dopo l'avvio di una sessione di debug, a seconda dell'implementazione del pacchetto di debug, i nodi di programma vengono utilizzati per creare i programmi corrispondenti. Quando un processo viene interrogato per i suoi programmi, i programmi vengono enumerati, uno per ogni nodo di programma.

  Prima di un programma è collegato, l'IDE richiede solo una descrizione leggera del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta collegato il programma, l'IDE visualizza informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione nel programma. Queste informazioni vengono ottenute dal programma stesso.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Processi](../../extensibility/debugger/processes.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
