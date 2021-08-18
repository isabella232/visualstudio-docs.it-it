---
title: Analizzare le prestazioni del codice asincrono .NET | Microsoft Docs
description: Usare lo strumento .NET Async per analizzare le prestazioni del codice asincrono. È disponibile un intervallo per ogni attività elencata. Per visualizzare il codice, usare Vai al file di origine.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: f6d688706fbc26013badea2beb06a534bbf5932245879dfbaede609a325434d8
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121427302"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Analizzare le prestazioni del codice asincrono .NET

Usare lo .NET Async per analizzare le prestazioni del codice asincrono nell'app.

> [!NOTE]
> Lo .NET Async richiede Visual Studio 2019 versione 16.7 o successiva e un progetto .NET che usa **async** **e await.**

## <a name="setup"></a>Eseguire la configurazione

1. Premere **ALT+F2** per aprire il profiler delle prestazioni in Visual Studio.

1. Selezionare la **.NET Async** di controllo.

   ![.NET Async strumento selezionato](../profiling/media/async-tool-selected.png ".NET Async strumento selezionato")

1. Fare clic **sul pulsante** Start per eseguire lo strumento.

1. Dopo l'avvio dell'esecuzione dello strumento, eseguire lo scenario che si vuole profilare nell'app. Selezionare quindi **Interrompi raccolta** o chiudere l'app per visualizzare i dati.

1. Dopo l'arresto della raccolta, viene visualizzata una tabella delle attività che si sono verificate durante la sessione di profilatura.

   ![.NET Async stato arrestato](../profiling/media/async-tool-opened.png ".NET Async stato arrestato")

Gli eventi asincroni sono organizzati in attività in ordine cronologico. Ognuno visualizza l'ora di inizio, l'ora di fine e la durata.

Ogni riga che corrisponde a [un'attività](/dotnet/api/system.threading.tasks) viene etichettata nella **colonna** Nome . Per qualsiasi nome di attività che non può essere risolto, viene visualizzata **un'attività nell'etichetta.** È seguito dal nome del metodo in cui si verifica l'attività. Se un'attività asincrona non viene completata all'interno della sessione di raccolta, **nella** colonna Ora di fine viene visualizzata **un'etichetta Incompleta.**

Per analizzare ulteriormente un'attività o un'attività specifica, fare clic con il pulsante destro del mouse sulla riga. Selezionare quindi **Vai al file di origine per** vedere dove si è verificata l'attività nel codice.

![.NET Async con l'opzione Vai al file di origine selezionata](../profiling/media/async-tool-gotosource.png ".NET Async con l'opzione Vai al file di origine selezionata")

## <a name="see-also"></a>Vedi anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)