---
title: I nodi di programma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ecc87a24b35993f200c709ee033fffe6a4ecb120
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49903621"
---
# <a name="program-nodes"></a>Nodi di programma
Nell'architettura di debugger, un *nodo programma*:  
  
- È una semplice descrizione di un programma.  
  
- Possibile identificare se stesso e il processo in che è in esecuzione. Un nodo del programma può essere collegato per essere disconnesso da e descrivere il motore di debug (DE) cui è stato creato, se presente.  
  
- È rappresentato da un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia, in genere creato da una porta o DE. Nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando viene aggiunto un nodo di programma a una porta, aggiungerlo al processo che contiene il programma che rappresenta questo nodo del programma.  
  
  Un certo punto dopo una sessione di debug viene avviata, a seconda dell'implementazione del pacchetto di debug, nodi di programma vengono usati per creare programmi corrispondenti. Quando un processo viene eseguita una query per i relativi programmi, vengono enumerati i programmi, uno per ogni nodo del programma.  
  
  Prima di un programma viene collegato, l'IDE deve solo una semplice descrizione del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta il programma viene collegato, l'IDE visualizza le informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione del programma. Queste informazioni vengono ottenute dal programma stesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)