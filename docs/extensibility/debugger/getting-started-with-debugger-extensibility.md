---
title: Attività iniziali con l'estendibilità del debugger | Microsoft Docs
description: Introduzione alla creazione e alla personalizzazione dei componenti del debugger usati per eseguire il debug di programmi dall'Visual Studio ambiente.
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 87f6ff3bb423a32af3e5bf6fb1a25a016d367556
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043557"
---
# <a name="get-started-with-debugger-extensibility"></a>Introduzione all'estendibilità del debugger
fornisce [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] le informazioni necessarie per creare e personalizzare i componenti del debugger utilizzati per eseguire il debug di programmi dall'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug ha aggiunto miglioramenti derivati dai test di usabilità estesi eseguiti nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger precedenti. È possibile usare il debug per eseguire un'applicazione multilingue oppure implementare la modifica in tempo reale delle variabili durante il debug di applicazioni e soluzioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] multilingue.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Il debug viene eseguito out-of-process con il programma in fase di debug e pertanto è meno intrusivo nello spazio di elaborazione dell'applicazione. Di conseguenza, è più semplice scrivere componenti che interagiscono con il debugger senza influire sul programma di debug.

 Per usare al meglio [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , è necessario avere familiarità con gli elementi seguenti:

- Ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE)

- Linguaggio di programmazione C++

- ATL COM

## <a name="in-this-section"></a>Contenuto della sezione
 [Roadmap per l'estensione del debugger](../../extensibility/debugger/roadmap-for-extending-the-debugger.md) Descrive il processo di implementazione del debug nel prodotto, a seconda del compilatore e del relativo output.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di debug, tra cui il motore di debug (DE), l'analizzatore di espressioni (edizione Enterprise) e il gestore [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dei simboli (SH).

 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali dell'architettura di debug.

 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo del motore di debug all'interno di contesti di codice, documentazione e valutazione delle espressioni. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

 [Attività di debug](../../extensibility/debugger/debugging-tasks.md) Contiene collegamenti a varie attività di debug, ad esempio l'avvio di un programma e la valutazione di espressioni.
