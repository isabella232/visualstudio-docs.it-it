---
title: Supporto del servizio del linguaggio per il debug | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugger, language support
- language services, debugging support
ms.assetid: 7a44067f-a410-4a6a-84d2-bda5184140bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c61f7fa7e698e2c01cadb1dbb36a321c6e656e35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194995"
---
# <a name="language-service-support-for-debugging"></a>Supporto dei servizi di linguaggio per il debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un servizio di linguaggio può fornire funzionalità che supportano un debugger tramite il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo> interfaccia. Queste funzionalità includono la convalida dei punti di interruzione e specificando un elenco di espressioni per il **Auto** finestra.  
  
 Tuttavia, è necessario disporre di un analizzatore di espressioni per eseguire il debug del linguaggio. L'analizzatore di espressioni è responsabile per la valutazione delle espressioni che producono valori durante il debug. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere:  
  
- [Analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators)  
  
- [Esempio analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)  
  
## <a name="compiler-output"></a>Output del compilatore  
 Il tipo di compilatore determina ciò che è necessario eseguire per implementare il debug per la propria lingua. Se il compilatore ha come destinazione il sistema operativo Windows e scrive un file con estensione pdb, che è possibile eseguire il debug di programmi con il codice nativo, debug del motore è integrato in Visual Studio. Se il compilatore produce Microsoft intermediate language (MSIL), è possibile eseguire il debug di programmi con il codice gestito, debug motore, è anche integrato in Visual Studio. Se il compilatore è destinato a un sistema operativo proprietario o un ambiente di runtime diverse, è necessario scrivere il proprio motore di debug.  
  
 Per altre informazioni sull'implementazione di debug per il linguaggio, vedere [introduttiva](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) in Visual Studio Debugging SDK.
