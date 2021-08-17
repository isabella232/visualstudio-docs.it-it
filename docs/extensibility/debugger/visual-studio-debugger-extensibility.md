---
title: Visual Studio Estendibilità del debugger | Microsoft Docs
description: Questo articolo descrive l Visual Studio estendibilità del debugger e fornisce collegamenti ad articoli Visual Studio debug.
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
ms.openlocfilehash: 153b5006db591ca12cf4e27e6715ccb8cd0fcb37
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042647"
---
# <a name="visual-studio-debugger-extensibility"></a>Visual Studio estendibilità del debugger
Visual Studio include un debugger del codice sorgente completamente interattivo, che offre uno strumento potente e facile da usare per tenere traccia dei bug nel programma. Il debugger include il supporto completo per Visual Basic, C#, C/C++ e JavaScript. Tuttavia, con , disponibile nell'Area download Microsoft, altri linguaggi di programmazione possono essere supportati nel [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] debugger con le stesse funzionalità avanzate. [](https://www.microsoft.com/download/details.aspx?id=21835)

 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger è il front-end comune, ovvero l'interfaccia utente, ai componenti di debug specifici del linguaggio di cui viene eseguito il debug. Per i nuovi linguaggi, tutto ciò che è necessario per il supporto da parte del debugger è creare i componenti back-end necessari, ad esempio un motore di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debug (DE). Questo è il punto in [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] cui entra in campo.

 include [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] un riferimento completo a tutti gli elementi necessari per creare un nuovo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de. Sono inoltre disponibili esempi ed esercitazioni che consentono di iniziare.

 Per un esempio completo di un sistema di progetto di linguaggio con supporto per il debug, vedere [l'esempio IronPython](https://www.microsoft.com/download/details.aspx?id=55984).

 Le sezioni seguenti descrivono come estendere il debugger usando [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] .

## <a name="in-this-section"></a>Contenuto della sezione
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md) Descrive le funzionalità [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] offerte dal debug e come installare l'SDK.

 [Creare un motore di debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md) Documenta il processo DE personalizzato, dalla preparazione del programma per un de alla disconnessione del de.

 [Scrivere un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) Spiega se è necessario scrivere un analizzatore di espressioni.

 [Scegliere una strategia di implementazione del motore di debug](../../extensibility/debugger/choosing-a-debug-engine-implementation-strategy.md) Viene illustrato come implementare il DE.

 [Informazioni di riferimento](../../extensibility/debugger/reference/reference-visual-studio-debugging-apis.md) Documenta [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'API di debug.

 [Esempi](../../extensibility/debugger/visual-studio-debugging-samples.md) Contiene collegamenti a un esempio di analizzatore di espressioni di Common Language Runtime e a un esempio di motore di debug.
