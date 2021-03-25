---
title: Introduzione con estensibilità del debugger | Microsoft Docs
description: Iniziare a creare e personalizzare i componenti del debugger usati per eseguire il debug dei programmi dall'ambiente Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 20591adffbfdfd21d1ff1a77eaade39c165b9c51
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059977"
---
# <a name="get-started-with-debugger-extensibility"></a>Introduzione all'estendibilità del debugger
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]Fornisce le informazioni necessarie per creare e personalizzare i componenti del debugger utilizzati per eseguire il debug dei programmi dall'interno dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug ha aggiunto miglioramenti derivati dall'ampio test di usabilità eseguito nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger precedenti. È possibile utilizzare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug per eseguire un'applicazione multilingua oppure implementare modifiche immediate delle variabili durante il debug di applicazioni e soluzioni multilingue.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug viene eseguito out-of-process con il programma di cui è in corso il debug ed è quindi meno intrusivo nello spazio di processo dell'applicazione. Di conseguenza, è più facile scrivere componenti che interagiscono con il debugger senza influire sul programma di debug.

 Per usare al meglio [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , è necessario avere familiarità con gli elementi seguenti:

- Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE)

- Linguaggio di programmazione C++

- COM ATL

## <a name="in-this-section"></a>Contenuto della sezione
 Guida [di orientamento per l'estensione del debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Descrive il processo di implementazione del debug nel prodotto, a seconda del compilatore e del relativo output.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componenti di debug, tra cui il motore di debug (de), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).

 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i principali concetti dell'architettura di debug.

 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Viene illustrato come il motore di debug (DE) opera simultaneamente nei contesti di codice, documentazione e valutazione delle espressioni. Viene descritto, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a diverse attività di debug, ad esempio l'avvio di un programma e la valutazione delle espressioni.
