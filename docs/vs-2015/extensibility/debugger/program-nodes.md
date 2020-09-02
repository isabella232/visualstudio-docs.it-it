---
title: Nodi del programma | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153653"
---
# <a name="program-nodes"></a>Nodi di programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **nodo di programma**:  
  
- È una descrizione semplificata di un programma.  
  
- Può identificare se stesso e il processo in cui è in esecuzione e può essere collegato, essere scollegato da e descrivere il motore di debug (DE) che l'ha creata, se disponibile.  
  
- È rappresentato da un'interfaccia [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , in genere creata da un de o una porta. I nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando si aggiunge un nodo di programma a una porta, questo viene aggiunto al processo che contiene il programma rappresentato da questo nodo del programma.  
  
  Una volta avviata una sessione di debug, a seconda dell'implementazione del pacchetto di debug, i nodi di programma vengono utilizzati per creare i programmi corrispondenti. Quando viene eseguita una query su un processo per i relativi programmi, vengono enumerati i programmi, uno per ogni nodo del programma.  
  
  Prima che un programma venga collegato a, l'IDE necessita solo di una descrizione semplice del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta collegato il programma a, l'IDE deve visualizzare informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione nel programma. Queste informazioni vengono ottenute dal programma stesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
