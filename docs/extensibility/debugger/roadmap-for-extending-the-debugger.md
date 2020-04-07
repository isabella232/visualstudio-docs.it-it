---
title: Guida di orientamento per l'estensione del debugger Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713140"
---
# <a name="roadmap-for-extending-the-debugger"></a>Guida di orientamento per l'estensione del debugger
In questa documentazione vengono fornite [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] informazioni [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]di riferimento e di guida per l'estensione del debugger con l'oggetto .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]la documentazione di debug include esempi, un riferimento completo e diversi scenari rappresentativi che illustrano modi tipici per personalizzare il debugger.

 Il compilatore e il relativo output determinano gli elementi necessari per configurare il debug nel prodotto. Se il compilatore:

- È destinato al sistema operativo nativo di Windows e scrive un file *. PDB,* è possibile eseguire il debug di programmi con il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]motore di debug del codice nativo (DE), che è integrato in . Non è necessario implementare un analizzatore di espressioni o DE. L'analizzatore di espressioni viene scritto per la sintassi del linguaggio di programmazione C.

- Produce l'output MSIL (Microsoft Intermediate Language), è possibile eseguire il debug [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]di programmi con il motore di debug del codice gestito DE, anch'egli integrato in . Pertanto, è necessario implementare solo un analizzatore di espressioni. Viene fornito un analizzatore di espressioni di esempio. Per altre informazioni, vedere gli argomenti seguenti:

   [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Valutazione delle espressioni](../../extensibility/debugger/evaluating-expressions.md)

   [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)

   [Valutazione dell'espressione in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Scrivere un analizzatore di espressioni di Common Language RuntimeWrite a common language runtime expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Targets un sistema operativo proprietario o qualche altro ambiente di runtime, è necessario scrivere il proprio DE. Viene fornita un'esercitazione che crea un semplice DE utilizzando ATL COM. Per altre informazioni, vedere gli argomenti seguenti:

   [Creare un motore di debug personalizzatoCreate a custom debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Esercitazione: Creare un motore di debug usando COM ATLTutorial: Build a debug engine using ATL COM](https://msdn.microsoft.com/library/9097b71e-1fe7-48f7-bc00-009e25940c24)

   [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Vedere anche
- [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
