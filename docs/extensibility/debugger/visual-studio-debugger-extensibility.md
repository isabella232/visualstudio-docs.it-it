---
title: Estensibilità del debugger di Visual Studio | Microsoft Docs
description: Questo articolo descrive l'estensibilità del debugger di Visual Studio e fornisce collegamenti ad articoli sul debug di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ebc884d36260ec3a057f75951cdbc4e7cc811079
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965447"
---
# <a name="visual-studio-debugger-extensibility"></a>Estensibilità del debugger di Visual Studio
Visual Studio include un debugger completamente interattivo del codice sorgente, che offre uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger dispone del supporto completo per Visual Basic, C#, C/C++ e JavaScript. Tuttavia, con [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , disponibile nell' [area download Microsoft](https://www.microsoft.com/download/details.aspx?id=21835), altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è il front-end comune, ovvero l'interfaccia utente, per i componenti di debug che, a loro volta, sono specifici del linguaggio di cui è in corso il debug. Per i nuovi linguaggi, tutto ciò che è necessario per il supporto del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger consiste nel creare i componenti back-end necessari, ad esempio un motore di debug (de). Questo è il punto [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] in cui entra in arrivo.

 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Include un riferimento completo a tutti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gli elementi necessari per creare un nuovo de. Sono inoltre disponibili esempi ed esercitazioni che consentono di iniziare.

 Per un esempio completo di un sistema di progetto di linguaggio con supporto per il debug, vedere l' [esempio IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Nelle sezioni seguenti viene descritto come estendere il debugger utilizzando [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
 [Inizia subito](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Descrive [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] le offerte di debug e come installare l'SDK.

 [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta il processo personalizzato DE, dalla preparazione del programma per un DE allo scollegamento della DE.

 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Viene illustrato se è necessario scrivere un analizzatore di espressioni.

 [Scegliere una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Viene illustrato come implementare il DE.

 Informazioni di [riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documenta l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] API di debug.

 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md) di Contiene collegamenti a un esempio Common Language Runtime analizzatore di espressioni e un esempio di motore di debug.
