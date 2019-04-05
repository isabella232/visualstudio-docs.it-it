---
title: I nodi di programma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966201"
---
# <a name="program-nodes"></a>Nodi di programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **nodo programma**:  
  
- È una semplice descrizione di un programma.  
  
- Possibile identificare se stesso e il processo in esecuzione in e può essere collegato per essere disconnesso da e viene descritto il motore di debug (DE) che ha creato, se presente.  
  
- È rappresentato da un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia, in genere creato da una porta o DE. Nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando viene aggiunto un nodo di programma a una porta, aggiungerlo al processo che contiene il programma che rappresenta questo nodo del programma.  
  
  Un certo punto dopo una sessione di debug viene avviata, a seconda dell'implementazione del pacchetto di debug, nodi di programma vengono usati per creare programmi corrispondenti. Quando un processo viene eseguita una query per i relativi programmi, vengono enumerati i programmi, uno per ogni nodo del programma.  
  
  Prima di un programma viene collegato, l'IDE deve solo una semplice descrizione del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta il programma viene collegato, l'IDE deve visualizzare informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione del programma. Queste informazioni vengono ottenute dal programma stesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
