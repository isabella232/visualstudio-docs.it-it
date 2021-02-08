---
title: Supporto del servizio di linguaggio per il debug | Microsoft Docs
description: Informazioni sulle funzionalità dei servizi di linguaggio nell'interfaccia IVsLanguageDebugInfo che forniscono supporto per il debug in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b53eb738b695726cf86859ce83a8ee93440564a0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839703"
---
# <a name="language-service-support-for-debugging"></a>Supporto dei servizi di linguaggio per il debug
Un servizio di linguaggio può fornire funzionalità che supportano un debugger tramite l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaccia. Queste funzionalità includono la convalida dei punti di interruzione e la fornitura di un elenco di espressioni alla finestra **auto** .

 Tuttavia, è necessario disporre di un analizzatore di espressioni per eseguire il debug della lingua. L'analizzatore di espressioni è responsabile della valutazione delle espressioni per produrre valori durante il debug. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere:

- [Analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Esempio di analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Output del compilatore
 Il tipo di compilatore determina ciò che è necessario eseguire per implementare il debug per la lingua. Se il compilatore è destinato al sistema operativo Windows e scrive un file con estensione PDB, è possibile eseguire il debug dei programmi con il motore di debug del codice nativo integrato in Visual Studio. Se il compilatore produce Microsoft Intermediate Language (MSIL), è possibile eseguire il debug di programmi con il motore di debug del codice gestito, anch ' esso integrato in Visual Studio. Se il compilatore è destinato a un sistema operativo proprietario o a un ambiente di runtime diverso, è necessario scrivere un motore di debug personalizzato.

 Per ulteriori informazioni sull'implementazione del debug per il linguaggio, vedere [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging SDK.
