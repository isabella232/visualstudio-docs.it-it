---
title: Roadmap for Extending the Debugger | Microsoft Docs
description: Visual Studio documentazione di debug include esempi, un riferimento e diversi scenari che illustrano i metodi tipici per personalizzare il debugger.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], roadmap
- Debugging SDK, roadmap
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 00da6cede11993e0b498978bc9a18ec0e21781b4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063642"
---
# <a name="roadmap-for-extending-the-debugger"></a>Roadmap per l'estensione del debugger
Questa documentazione fornisce informazioni di riferimento e guida per l'estensione del [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] debugger con [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] La documentazione di debug include esempi, un riferimento completo e diversi scenari rappresentativi che illustrano i metodi tipici per personalizzare il debugger.

 Il compilatore e il relativo output determinano ciò che è necessario per configurare il debug nel prodotto. Se il compilatore:

- La destinazione è Windows sistema operativo nativo e scrive un oggetto *. File PDB,* è possibile eseguire il debug di programmi con il motore di debug del codice nativo (DE), integrato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Non è necessario implementare un analizzatore di espressioni o DE. L'analizzatore di espressioni viene scritto per la sintassi del linguaggio di programmazione C++.

- Produce l'output MSIL (Microsoft Intermediate Language), è possibile eseguire il debug dei programmi con il motore di debug del codice gestito DE, integrato anche in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Di conseguenza, è necessario implementare solo un analizzatore di espressioni. Viene fornito un analizzatore di espressioni di esempio. Per altre informazioni, vedere i seguenti argomenti:

   [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)

   [Valutazione delle espressioni](../../extensibility/debugger/evaluating-expressions.md)

   [Contesto di valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-context.md)

   [Valutazione delle espressioni in modalità di interruzione](../../extensibility/debugger/expression-evaluation-in-break-mode.md)

   [Scrivere un analizzatore di espressioni di Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

- Destinato a un sistema operativo proprietario o a un altro ambiente di run-time, è necessario scrivere il proprio DE. Viene fornita un'esercitazione che crea una semplice de usando ATL COM. Per altre informazioni, vedere i seguenti argomenti:

   [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)

   [Esercitazione: Compilare un motore di debug con ATL COM](/previous-versions/bb147024(v=vs.90))

   [Implementare un fornitore di porte](../../extensibility/debugger/implementing-a-port-supplier.md)

   [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)

## <a name="see-also"></a>Vedi anche
- [Operazioni preliminari](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)