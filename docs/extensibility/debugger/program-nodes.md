---
title: Nodi del programma | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un nodo di programma nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 65a97a32baab159ad2c0bd1ac189dedbf09fe98e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948439"
---
# <a name="program-nodes"></a>Nodi del programma
Nell'architettura del debugger, un *nodo di programma*:

- È una descrizione semplificata di un programma.

- Consente di identificare se stesso e il processo in cui è in esecuzione. Un nodo del programma può essere collegato a, essere scollegato da e descrivere il motore di debug (DE) che l'ha creata, se disponibile.

- È rappresentato da un'interfaccia [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , in genere creata da un de o una porta. I nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando si aggiunge un nodo di programma a una porta, questo viene aggiunto al processo che contiene il programma rappresentato da questo nodo del programma.

  Una volta avviata una sessione di debug, a seconda dell'implementazione del pacchetto di debug, i nodi di programma vengono utilizzati per creare i programmi corrispondenti. Quando viene eseguita una query su un processo per i relativi programmi, vengono enumerati i programmi, uno per ogni nodo del programma.

  Prima che un programma venga collegato a, l'IDE necessita solo di una descrizione semplice del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta che il programma è collegato a, nell'IDE vengono visualizzate informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione nel programma. Queste informazioni vengono ottenute dal programma stesso.

## <a name="see-also"></a>Vedi anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Processi](../../extensibility/debugger/processes.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
