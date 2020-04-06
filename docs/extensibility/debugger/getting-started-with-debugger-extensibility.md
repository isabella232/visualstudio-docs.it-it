---
title: Guida introduttiva all'estensibilità del debugger Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 153db8889c78890a31a2e8003e6aa95ed24a02eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738598"
---
# <a name="get-started-with-debugger-extensibility"></a>Introduzione all'estensibilità del debuggerGet started with debugger extensibility
Fornisce [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] le informazioni necessarie per creare e personalizzare i componenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del debugger utilizzati per eseguire il debug di programmi dall'interno dell'ambiente.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Il debug ha aggiunto miglioramenti derivati dall'ampia usabilità eseguita nei debugger precedenti. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] È possibile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzare il debug per eseguire un'applicazione in più lingue oppure implementare la modifica in tempo reale delle variabili durante il debug di applicazioni e soluzioni multilingue.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]il debug viene eseguito out-of-process con il programma in fase di debug ed è quindi meno intrusivo nello spazio di processo dell'applicazione. Di conseguenza, è più semplice scrivere componenti che interagiscono con il debugger senza influire sul programma di debug.

 Per utilizzare [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]al meglio , è necessario avere familiarità con i seguenti elementi:

- Ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE)

- Il linguaggio di programmazione C

- ATL COM

## <a name="in-this-section"></a>Contenuto della sezione
 [Guida di orientamento per l'estensione del debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Viene descritto il processo di implementazione del debug nel prodotto, a seconda del compilatore e del relativo output.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] panoramica dei componenti di debug, che includono il motore di debug (DE), l'analizzatore di espressioni (EE) e il gestore di simboli (SH).

 [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali relativi all'architettura di debug.

 [Contesti del debuggerDebugger contexts](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo del motore di debug (DE) all'interno di contesti di valutazione del codice, della documentazione e delle espressioni. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
