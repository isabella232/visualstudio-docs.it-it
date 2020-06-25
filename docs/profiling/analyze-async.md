---
title: Analizzare le prestazioni del codice asincrono .NET | Microsoft Docs
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 49091ba472637d480c04c39f0170c2aee00595d2
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290671"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Analizzare le prestazioni del codice asincrono .NET

Usare lo strumento .NET Async per analizzare le prestazioni del codice asincrono nell'app.

> [!NOTE]
> Lo strumento .NET Async richiede Visual Studio 2019 versione 16,7 o successiva e un progetto .NET che usa **Async** e **await**.

## <a name="setup"></a>Configurazione

1. Selezionare **ALT + F2** per aprire il profiler delle prestazioni in Visual Studio.

1. Selezionare la casella di controllo **asincrona .NET** .

   ![Strumento asincrono .NET selezionato](../profiling/media/async-tool-selected.png "Strumento asincrono .NET selezionato")

1. Fare clic sul pulsante **Start** per eseguire lo strumento.

1. Dopo l'avvio dell'esecuzione dello strumento, esaminare lo scenario che si vuole profilare nell'app. Quindi selezionare **Arresta raccolta** o Chiudi l'app per visualizzare i dati.

1. Dopo l'arresto della raccolta, viene visualizzata una tabella delle attività che si sono verificate durante la sessione di profilatura.

   ![Lo strumento .NET Async è stato arrestato](../profiling/media/async-tool-opened.png "Lo strumento .NET Async è stato arrestato")

Gli eventi asincroni sono organizzati in attività in ordine cronologico. Ognuno Visualizza l'ora di inizio, l'ora di fine e la durata.

Ogni riga che corrisponde a un' [attività](https://docs.microsoft.com/dotnet/api/system.threading.tasks) è denominata nella colonna **nome** . Per qualsiasi nome di attività che non può essere risolto, viene visualizzata un' **attività nell'** etichetta. Segue il nome del metodo in cui si trova l'attività. Se un'attività asincrona non viene completata nella sessione di raccolta, viene visualizzata un'etichetta **incompleta** nella colonna **ora di fine** .

Per esaminare ulteriormente un'attività o un'attività specifica, fare clic con il pulsante destro del mouse sulla riga. Selezionare quindi **Vai a file di origine** per vedere dove si è verificato l'attività nel codice.

![Strumento asincrono .NET con Vai al file di origine selezionato](../profiling/media/async-tool-gotosource.png "Strumento asincrono .NET con Vai al file di origine selezionato")

## <a name="see-also"></a>Vedi anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)
