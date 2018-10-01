---
title: Estendibilità del Debugger di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d4c3a9644e7150ea31cca2aba927bbdbacb8b0eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531053"
---
# <a name="visual-studio-debugger-extensibility"></a>Estendibilità del debugger di Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Extensibility di Visual Studio Debugger](https://docs.microsoft.com/visualstudio/extensibility/debugger/visual-studio-debugger-extensibility).  
  
Visual Studio include un debugger di codice sorgente completamente interattivi, che fornisce uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger ha supporto completo per Visual Basic, c#, C/C++ e JavaScript. Tuttavia, con il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], vale a dire disponibile la [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkId=214453), altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.  
  
 Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger è il front-end comune (vale a dire, l'interfaccia utente) per i componenti di debug che sono, a sua volta, a seconda della lingua in fase di debug. Per nuove lingue, è sufficiente per supportare dal [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debugger consiste nel creare i componenti necessari di back-end, ad esempio un motore di debug (DE). In questi casi il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] è disponibile in.  
  
 Il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] include un riferimento completo a tutti [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementi necessari per creare un nuovo DE. Inoltre, esistono esempi ed esercitazioni utili per iniziare a usare.  
  
 Per un esempio end-to-end di un sistema di progetto linguaggio con il supporto del debug, vedere la [esempio di IronPython](http://msdn.microsoft.com/en-us/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Le sezioni seguenti viene descritto come estendere il debugger usando la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>In questa sezione  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Descrive cosa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] debug offerte e su come installare il SDK.  
  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Illustra il processo DE personalizzato, dalla preparazione programma per un CRI per scollegare il DE.  
  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Viene spiegato se è necessario scrivere un analizzatore di espressioni.  
  
 [Scelta di una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Viene illustrato come implementare il DE.  
  
 [Riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] API di debug.  
  
 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene collegamenti a un esempio dell'analizzatore di espressioni espressione di common language runtime e un esempio di motore di debug.

