---
title: Guida di orientamento per l'estensione del Debugger | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f9272728f79e402800c56f6e8c9ce0fc008e3ad
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370869"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guida di orientamento per l'estensione del debugger
Questa documentazione vengono fornite informazioni di riferimento e Guida per l'estensione di [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] del debugger con la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug documentazione include esempi, un riferimento completo e numerosi scenari rappresentativi che illustrano i modi tipici per personalizzare il debugger.  
  
 Il compilatore e il relativo output determinare i requisiti per l'impostazione del debug nel prodotto. Se il compilatore:  
  
-   Ha come destinazione di Windows nativo del sistema operativo e scrive un *. PDB* file, eseguire il debug di programmi con il motore di debug di codice nativo (DE), integrata in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Non è necessario implementare un analizzatore DE o un'espressione. L'analizzatore di espressioni viene scritto per la sintassi del linguaggio di programmazione C++.  
  
-   Produce Microsoft intermediate language (MSIL) di output, è possibile eseguire il debug di programmi con il motore di debug di codice gestito, DE, che è anche integrato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Di conseguenza, è necessario implementare solo un analizzatore di espressioni. Un analizzatore di espressioni di esempio viene fornito automaticamente. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [La valutazione delle espressioni](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Valutazione dell'espressione in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Scrivere un analizzatore di espressioni di common language runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Destinato a un proprietario o un altro ambiente di runtime del sistema operativo, è necessario scrivere il proprio DE. Viene fornita un'esercitazione che crea un semplice DE utilizzando ATL COM. Per altre informazioni, vedere i seguenti argomenti:  
  
     [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [Esercitazione: Creare un motore di debug tramite COM ATL](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)