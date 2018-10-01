---
title: I nodi di programma | Microsoft Docs
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
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: caff608b85dc8fc563ace8f5d582dba1cba427c0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530511"
---
# <a name="program-nodes"></a>Nodi di programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [nodi di programma](https://docs.microsoft.com/visualstudio/extensibility/debugger/program-nodes).  
  
In termini di architettura del debugger, un **nodo programma**:  
  
-   È una semplice descrizione di un programma.  
  
-   Possibile identificare se stesso e il processo in esecuzione in e può essere collegato per essere disconnesso da e viene descritto il motore di debug (DE) che ha creato, se presente.  
  
-   È rappresentato da un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia, in genere creato da una porta o DE. Nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando viene aggiunto un nodo di programma a una porta, aggiungerlo al processo che contiene il programma che rappresenta questo nodo del programma.  
  
 Un certo punto dopo una sessione di debug viene avviata, a seconda dell'implementazione del pacchetto di debug, nodi di programma vengono usati per creare programmi corrispondenti. Quando un processo viene eseguita una query per i relativi programmi, vengono enumerati i programmi, uno per ogni nodo del programma.  
  
 Prima di un programma viene collegato, l'IDE deve solo una semplice descrizione del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta il programma viene collegato, l'IDE deve visualizzare informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione del programma. Queste informazioni vengono ottenute dal programma stesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)

