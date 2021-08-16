---
title: Supporto del servizio di linguaggio per il debug | Microsoft Docs
description: Informazioni sulle funzionalità del servizio di linguaggio nell'interfaccia IVsLanguageDebugInfo che forniscono supporto per il debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 72cac3ff7768d49f66c87b569312253669d735fa2e64fdb895b51ff29aae2ca4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375896"
---
# <a name="language-service-support-for-debugging"></a>Supporto dei servizi di linguaggio per il debug
Un servizio di linguaggio può fornire funzionalità che supportano un debugger tramite <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> l'interfaccia . Queste funzionalità includono la convalida dei punti di interruzione e la fornitura di un elenco di espressioni **alla finestra Auto.**

 Tuttavia, è necessario disporre di un analizzatore di espressioni per eseguire il debug del linguaggio. L'analizzatore di espressioni è responsabile della valutazione delle espressioni per produrre valori durante il debug. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere:

- [Analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Esempio di analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Output del compilatore
 Il tipo di compilatore determina le operazioni da eseguire per implementare il debug per il linguaggio. Se il compilatore è destinato al sistema operativo Windows e scrive un file con estensione pdb, è possibile eseguire il debug dei programmi con il motore di debug del codice nativo integrato in Visual Studio. Se il compilatore produce Microsoft Intermediate Language (MSIL), è possibile eseguire il debug di programmi con il motore di debug del codice gestito, integrato anche in Visual Studio. Se il compilatore è destinato a un sistema operativo proprietario o a un ambiente di runtime diverso, è necessario scrivere un motore di debug personalizzato.

 Per altre informazioni sull'implementazione del debug per il linguaggio in [Attività iniziali,](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) vedere Visual Studio Debugging SDK.
