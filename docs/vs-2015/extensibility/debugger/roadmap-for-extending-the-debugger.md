---
title: Guida di orientamento per l'estensione del debugger | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 89a07bc5a5c4c8b7a6054b53610325c654355bc8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695963"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guida di orientamento per l'estensione del debugger
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In questa documentazione vengono fornite informazioni di riferimento e guida per estendere il [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] debugger con il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] .  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la documentazione di debug include esempi, un riferimento completo e diversi scenari rappresentativi che illustrano le modalità tipiche di personalizzazione del debugger.  
  
 Il compilatore e l'output determinano gli elementi necessari per implementare il debug nel prodotto. Se il compilatore:  
  
- Ha come destinazione il sistema operativo nativo di Windows e scrive un. File PDB, è possibile eseguire il debug di programmi con il motore di debug del codice nativo (DE), integrato in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Non è necessario implementare un analizzatore di espressioni o. L'analizzatore di espressioni viene scritto per la sintassi del linguaggio di programmazione C++.  
  
- Produce l'output Microsoft Intermediate Language (MSIL), è possibile eseguire il debug di programmi con il motore di debug del codice gestito DE, che è integrato anche in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Pertanto, è necessario implementare solo un analizzatore di espressioni. Viene fornito un analizzatore di espressioni di esempio. Per altre informazioni, vedere gli argomenti seguenti:  
  
     [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Valutazione di espressioni](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contesto di valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Valutazione delle espressioni in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Scrittura di un analizzatore di espressioni di Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
- La destinazione è un sistema operativo proprietario o un altro ambiente di runtime, ma è necessario scrivere il proprio DE. Viene fornita un'esercitazione che crea una semplice DE usando ATL COM. Per altre informazioni, vedere gli argomenti seguenti:  
  
     [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Esercitazione: creazione di un motore di debug con ATL COM](https://msdn.microsoft.com/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementazione di un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Per iniziare](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
