---
title: Nodi di programma | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un nodo di programma nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: da57e9379d46bfbb5194b59d91baa7a2ef342f74
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080169"
---
# <a name="program-nodes"></a>Nodi di programma
Nell'architettura del debugger, un *nodo di programma*:

- Descrizione leggera di un programma.

- Può identificare se stesso e il processo in cui è in esecuzione. Un nodo di programma può essere collegato, scollegato e descritto il motore di debug (DE) che lo ha creato, se presente.

- È rappresentato da [un'interfaccia IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) in genere creata da un de o da una porta. I nodi del programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando un nodo di programma viene aggiunto a una porta, viene aggiunto al processo contenente il programma rappresentato da questo nodo di programma.

  A volte dopo l'avvio di una sessione di debug, a seconda dell'implementazione del pacchetto di debug, i nodi di programma vengono usati per creare programmi corrispondenti. Quando viene eseguita una query su un processo per i relativi programmi, i programmi vengono enumerati, uno per ogni nodo del programma.

  Prima che un programma sia collegato a , l'IDE necessita solo di una descrizione leggera del programma. Queste informazioni possono essere ottenute dal nodo del programma. Dopo aver collegato il programma, l'IDE visualizza informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione nel programma. Queste informazioni vengono ottenute dal programma stesso.

## <a name="see-also"></a>Vedi anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Processi](../../extensibility/debugger/processes.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
