---
title: Guida di orientamento per l'estensione del debugger | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e809eeb6a1a5d2c24368932713d69c7199b5af38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713140"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guida di orientamento per l'estensione del debugger
In questa documentazione vengono fornite informazioni di riferimento e guida per estendere il [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] debugger con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la documentazione di debug include esempi, un riferimento completo e diversi scenari rappresentativi che illustrano le modalità tipiche di personalizzazione del debugger.

 Il compilatore e il relativo output determinano gli elementi necessari per impostare il debug nel prodotto. Se il compilatore:

- Ha come destinazione il sistema operativo nativo di Windows e scrive un *. File PDB* , è possibile eseguire il debug di programmi con il motore di debug del codice nativo (de), integrato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Non è necessario implementare un analizzatore di espressioni o. L'analizzatore di espressioni viene scritto per la sintassi del linguaggio di programmazione C++.

- Produce l'output Microsoft Intermediate Language (MSIL), è possibile eseguire il debug di programmi con il motore di debug del codice gestito DE, che è integrato anche in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Pertanto, è necessario implementare solo un analizzatore di espressioni. Viene fornito un analizzatore di espressioni di esempio. Per altre informazioni, vedere gli argomenti seguenti:

   [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Valutazione delle espressioni](../../extensibility/debugger/evaluating-expressions.md)

   [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)

   [Valutazione delle espressioni in modalità di interruzioni](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Scrivere un analizzatore di espressioni Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- La destinazione è un sistema operativo proprietario o un altro ambiente di runtime, ma è necessario scrivere il proprio DE. Viene fornita un'esercitazione che crea una semplice DE usando ATL COM. Per altre informazioni, vedere gli argomenti seguenti:

   [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Esercitazione: creare un motore di debug con ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Vedere anche
- [Operazioni preliminari](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
