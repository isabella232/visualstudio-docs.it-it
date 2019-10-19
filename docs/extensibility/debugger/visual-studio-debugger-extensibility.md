---
title: Estensibilità del debugger di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f8a1c2148f25a1e97cfd1369770e056d1cb907d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568977"
---
# <a name="visual-studio-debugger-extensibility"></a>Estensibilità del debugger di Visual Studio
Visual Studio include un debugger completamente interattivo del codice sorgente, che offre uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger dispone del supporto completo per Visual Basic C#,, CC++/e JavaScript. Tuttavia, con il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], disponibile nell' [area download Microsoft](http://go.microsoft.com/fwlink/?LinkId=214453), altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.

 Il debugger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è il front-end comune, ovvero l'interfaccia utente, per i componenti di debug che, a loro volta, sono specifici del linguaggio di cui è in corso il debug. Per le nuove lingue, tutto ciò che è necessario per il supporto da parte del debugger [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] consiste nel creare i componenti back-end necessari, ad esempio un motore di debug (DE). Questo è il punto in cui viene fornita la [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

 Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] include un riferimento completo a tutti gli elementi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiesti per creare un nuovo DE. Sono inoltre disponibili esempi ed esercitazioni che consentono di iniziare.

 Per un esempio completo di un sistema di progetto di linguaggio con supporto per il debug, vedere l' [esempio IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Nelle sezioni seguenti viene descritto come estendere il debugger utilizzando il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].

## <a name="in-this-section"></a>In questa sezione
 [Inizia subito](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Descrive i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offerte di debug e come installare l'SDK.

 [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta il processo personalizzato DE, dalla preparazione del programma per un DE allo scollegamento della DE.

 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Viene illustrato se è necessario scrivere un analizzatore di espressioni.

 [Scegliere una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Viene illustrato come implementare il DE.

 Informazioni di [riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documenta l'API di debug [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md) di Contiene collegamenti a un esempio Common Language Runtime analizzatore di espressioni e un esempio di motore di debug.
