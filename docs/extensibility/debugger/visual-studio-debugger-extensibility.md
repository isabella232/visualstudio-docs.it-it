---
title: Estendibilità del Debugger di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b0be4a96854315bcf8b83db86692758e198980cd
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370926"
---
# <a name="visual-studio-debugger-extensibility"></a>Estendibilità del debugger Visual Studio
Visual Studio include un debugger di codice sorgente completamente interattivi, che fornisce uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger ha supporto completo per Visual Basic, c#, C/C++ e JavaScript. Tuttavia, con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], vale a dire disponibile la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.  
  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è il front-end comune (vale a dire, l'interfaccia utente) per i componenti di debug che sono, a sua volta, a seconda della lingua in fase di debug. Per nuove lingue, è sufficiente per supportare dal [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger consiste nel creare i componenti necessari di back-end, ad esempio un motore di debug (DE). In questo punto è dove il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] è disponibile in.  
  
 Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] include un riferimento completo a tutti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementi necessari per creare un nuovo DE. Inoltre, esistono esempi ed esercitazioni utili per iniziare a usare.  
  
 Per un esempio completo di un sistema di progetto linguaggio con il supporto del debug, vedere la [esempio di IronPython](https://www.microsoft.com/download/details.aspx?id=55984).  
  
 Le sezioni seguenti viene descritto come estendere il debugger usando la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Descrive cosa [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug offerte e su come installare il SDK.  
  
 [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Illustra il processo DE personalizzato, dalla preparazione programma per un CRI per scollegare il DE.  
  
 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Viene spiegato se è necessario scrivere un analizzatore di espressioni.  
  
 [Scegliere una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Viene illustrato come implementare il DE.  
  
 [Riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API di debug.  
  
 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene collegamenti a un esempio dell'analizzatore di espressioni espressione di common language runtime e un esempio di motore di debug.
