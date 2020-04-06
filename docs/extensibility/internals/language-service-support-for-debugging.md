---
title: Supporto del servizio di linguaggio per il debug . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8c80e8e1f584b1728f342cb596b689f6a22c9297
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707439"
---
# <a name="language-service-support-for-debugging"></a>Supporto dei servizi di linguaggio per il debug
Un servizio di linguaggio può fornire <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> funzionalità che supportano un debugger tramite l'interfaccia. Queste funzionalità includono la convalida dei punti di interruzione e la fornitura di un elenco di espressioni per il **Auto** finestra.

 Tuttavia, è necessario disporre di un analizzatore di espressioni per eseguire il debug del linguaggio. L'analizzatore di espressioni è responsabile della valutazione delle espressioni per produrre valori durante il debug. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere:For information about implementing CLR expression evaluators, please see:

- [Analizzatori di espressioni CLRCLR Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)

- [Esempio di analizzatore di espressioni gestiteManaged Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

## <a name="compiler-output"></a>Output del compilatore
 Il tipo di compilatore determina le operazioni da eseguire per implementare il debug per il linguaggio. Se il compilatore è destinato al sistema operativo Windows e scrive un file con estensione pdb, è possibile eseguire il debug di programmi con il motore di debug del codice nativo integrato in Visual Studio. Se il compilatore produce MSIL (Microsoft Intermediate Language), è possibile eseguire il debug di programmi con il motore di debug del codice gestito, anch'egli integrato in Visual Studio. Se il compilatore è destinato a un sistema operativo proprietario o a un ambiente di runtime diverso, è necessario scrivere un motore di debug personalizzato.

 Per ulteriori informazioni sull'implementazione del debug per il linguaggio, vedere [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging SDK.
