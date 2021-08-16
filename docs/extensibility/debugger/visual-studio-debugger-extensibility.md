---
title: Visual Studio Debugger Extensibility | Microsoft Docs
description: Questo articolo descrive Visual Studio estensibilità del debugger e fornisce collegamenti ad articoli Visual Studio debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], Debugging SDK
- Debugging SDK
ms.assetid: c088b6a2-c3ad-446b-830d-9c6f41b2934b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 3949777d22f6cb47469e035a84dbbc484ab210a663420f31bd4a67c4a21cd487
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306036"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio estensibilità del debugger
Visual Studio include un debugger del codice sorgente completamente interattivo, che offre uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger include il supporto completo per Visual Basic, C#, C/C++ e JavaScript. Tuttavia, con [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , disponibile nell'Area [download Microsoft,](https://www.microsoft.com/download/details.aspx?id=21835)altri linguaggi di programmazione possono essere supportati nel debugger con le stesse funzionalità avanzate.

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è il front-end comune, ovvero l'interfaccia utente, ai componenti di debug che sono, a loro volta, specifici del linguaggio di cui viene eseguito il debug. Per i nuovi linguaggi, per il supporto da parte del debugger è necessario creare i componenti back-end necessari, ad esempio un motore di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug. Questo è il punto in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] cui entra in campo .

 include [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] un riferimento completo a tutti gli elementi necessari per creare un nuovo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DE. Sono inoltre disponibili esempi ed esercitazioni utili per iniziare.

 Per un esempio completo di un sistema di progetto di linguaggio con supporto per il debug, vedere [l'esempio IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Nelle sezioni seguenti viene descritto come estendere il debugger utilizzando [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Descrive le funzionalità [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offerte dal debug e come installare l'SDK.

 [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta il processo DE personalizzato, dalla preparazione del programma per un de alla disconnessione del de.

 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Viene illustrato se è necessario scrivere un analizzatore di espressioni.

 [Scegliere una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Viene illustrato come implementare derelimentazione.

 [Informazioni di riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documenta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'API di debug.

 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md) Contiene collegamenti a un esempio di analizzatore di espressioni di Common Language Runtime e a un esempio di motore di debug.
