---
title: Estensibilità del debugger di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b8d37954bf238b2ed1323bf021fded94ec0c584
ms.sourcegitcommit: 3a19319e2599bd193fb2ca32020ca53942974bfd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/13/2019
ms.locfileid: "73983664"
---
# <a name="visual-studio-debugger-extensibility"></a>Estendibilità del debugger di Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Visual Studio include un debugger completamente interattivo del codice sorgente, che offre uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger dispone del supporto completo Visual Basic C#,, CC++/e JavaScript. Tuttavia, con il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], disponibile nell' [area download Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.  
  
 Il debugger [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è il front-end comune, ovvero l'interfaccia utente, per i componenti di debug che, a loro volta, sono specifici del linguaggio di cui è in corso il debug. Per le nuove lingue, tutto ciò che è necessario per il supporto da parte del debugger [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] consiste nel creare i componenti back-end necessari, ad esempio un motore di debug (DE). Qui viene fornita la [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
 Il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] include un riferimento completo a tutti gli elementi [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] richiesti per creare un nuovo DE. Sono inoltre disponibili esempi ed esercitazioni che consentono di iniziare.  
  
 Per un esempio end-to-end di un sistema di progetto di linguaggio con supporto per il debug, vedere l' [esempio IronPython](https://msdn.microsoft.com/4c41695c-12c1-4670-b43b-d8d84c9e4089).  
  
 Nelle sezioni seguenti viene descritto come estendere il debugger utilizzando il [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)  
 Descrive i [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] offerte di debug e come installare l'SDK.  
  
 [Creazione di un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Documenta il processo personalizzato DE, dalla preparazione del programma per un DE allo scollegamento della DE.  
  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
 Viene illustrato se è necessario scrivere un analizzatore di espressioni.  
  
 [Scelta di una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md)  
 Viene illustrato come implementare il DE.  
  
 [Reference](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md)  
 Documenta l'API di debug [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md)  
 Contiene collegamenti a un esempio Common Language Runtime analizzatore di espressioni e un esempio di motore di debug.
