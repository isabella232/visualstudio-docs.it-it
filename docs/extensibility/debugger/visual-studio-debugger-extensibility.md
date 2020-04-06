---
title: Estensibilità del debugger di Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff4222b555fab73914776725fc79581f29fa5e53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712504"
---
# <a name="visual-studio-debugger-extensibility"></a>Estendibilità del debugger di Visual StudioVisual Studio debugger extensibility
Visual Studio include un debugger del codice sorgente completamente interattivo, che fornisce uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger dispone del supporto completo per Visual Basic, C, C/C, e JavaScript. Tuttavia, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]con l'oggetto , disponibile nell'Area [download Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è il front-end comune (ovvero l'interfaccia utente) ai componenti di debug che sono, a loro volta, specifici per il linguaggio in fase di debug. Per i nuovi linguaggi, tutto ciò che è necessario per il supporto da parte del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è quello di creare i componenti back-end necessari, ad esempio un motore di debug (DE). Questo punto è [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] dove entra in gioco il

 Il [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] include un riferimento [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] completo a tutti gli elementi necessari per creare un nuovo DE. Inoltre, ci sono esempi e tutorial che ti aiuteranno a iniziare.

 Per un esempio completo di un sistema di progetto di linguaggio con supporto per il debug, vedere [l'esempio IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Nelle sezioni seguenti viene descritto come [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]estendere il debugger utilizzando il metodo .

## <a name="in-this-section"></a>Contenuto della sezione
 [Guida introduttiva](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Vengono descritti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i prodotti per il debug e come installare l'SDK.

 [Creare un motore di debug personalizzatoCreate](../../extensibility/debugger/creating-a-custom-debug-engine.md) a custom debug engine Documenta il processo DE personalizzato, dalla preparazione del programma per un DE per scollegare il DE.

 [Scrivere un analizzatore di espressioni CLRWrite a CLR expression evaluator](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Viene illustrato se è necessario scrivere un analizzatore di espressioni.

 [Scegliere una strategia di implementazione](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) del motore di debugChoose a debug engine implementation strategy Viene illustrato come implementare il DE.

 [Riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documenta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'API di debug.

 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md) Contiene collegamenti a un esempio di analizzatore di espressioni di Common Language Runtime e un esempio di motore di debug.
