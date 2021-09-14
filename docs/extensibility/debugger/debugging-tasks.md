---
title: Attività di debug | Microsoft Docs
description: Informazioni sulle attività necessarie per eseguire il debug di un programma, ad esempio collegarlo a un motore di debug, generare eventi di avvio e raggiungere punti di interruzione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 960e87e629caca705d8dc8e8fd54de3731b9604e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710341"
---
# <a name="debug-tasks"></a>Eseguire il debug delle attività
Per eseguire il debug di un programma, è necessario avviarlo e associare un motore di debug (DE) oppure il de deve essere collegato a un programma avviato in precedenza. Dopo l'associazione, la dea deve generare determinati eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, si arresta e attende l'input dell'utente.

## <a name="in-this-section"></a>Contenuto della sezione
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md) Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.

 [Avviare un programma](../../extensibility/debugger/launching-a-program.md) Fornisce istruzioni dettagliate su come specificare un de, che chiama il sistema operativo per avviare il programma.

 [Collegarsi direttamente a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md) Descrive il processo utilizzato per eseguire il debug di un programma in un processo già in esecuzione.

 [Inviare eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Elenca gli eventi che si verificano dopo che il de è collegato al programma, fino a quando il programma non si trova nel punto di ingresso principale ed è pronto per il debug.

 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md) Spiega in genere come la derescita invia un evento del punto di ingresso, un evento di completamento del caricamento o un evento di arresto, a seconda delle circostanze.

 [Associare punti di interruzione](../../extensibility/debugger/binding-breakpoints.md) Descrive come, se l'utente imposta un punto di interruzione, l'IDE formula la richiesta e richiede alla sessione di debug di creare il punto di interruzione.

 [Valutare le espressioni](../../extensibility/debugger/evaluating-expressions.md) Illustra come vengono create le espressioni e cosa accade quando un'espressione viene valutata.

 [Visualizzare e visualizzare i dati](../../extensibility/debugger/visualizing-and-viewing-data.md) Viene illustrato come i visualizzatori di tipi e i visualizzatori personalizzati sono supportati dall'analizzatore di espressioni (edizione Enterprise).

## <a name="related-sections"></a>Sezioni correlate
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md) Vengono descritti i concetti principali dell'architettura di debug.

 [Componenti del debugger](../../extensibility/debugger/debugger-components.md) Viene fornita una panoramica dei componenti di Visual Studio debug, che includono de, edizione Enterprise e gestore di simboli (SH).

 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md) Viene illustrato il funzionamento simultaneo di DE all'interno di contesti di codice, documentazione e valutazione delle espressioni. Descrive, per ognuno dei tre contesti, la posizione, la posizione o la valutazione pertinente.

## <a name="see-also"></a>Vedi anche
 [Operazioni preliminari](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
