---
title: Visualizzare i contatori DotNet | Microsoft Docs
description: Informazioni su come usare lo strumento contatori .NET nel profiler delle prestazioni di Visual Studio.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905027"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visualizzare i contatori DotNet dal profiler di Visual Studio


Lo strumento contatori .NET consente di visualizzare i [contatori DotNet](/dotnet/core/diagnostics/dotnet-counters) nel tempo direttamente dall'interno del profiler di Visual Studio.


> [!NOTE]
> Lo strumento contatori .NET richiede Visual Studio 2019 versione 16,7 o successiva e ha come destinazione .NET Core 3.0 +.

## <a name="setup"></a>Configurazione

1. Aprire il Profiler prestazioni (**ALT + F2** o **debug-> Performance Profiler**) in Visual Studio.

2. Selezionare la casella di controllo **contatori .NET** .

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Strumento contatori selezionato.":::

3. Fare clic sul pulsante **Start** per eseguire lo strumento.

Per ulteriori informazioni su come ottimizzare le prestazioni dello strumento, vedere [ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Informazioni sui dati

Mentre lo strumento raccoglie inizialmente i dati, è possibile visualizzare i valori attivi dei [contatori DotNet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Raccolta di strumenti per contatori .NET.":::

È anche possibile visualizzare i grafici dei contatori selezionando la casella di controllo accanto ai nomi dei contatori. È possibile visualizzare i grafici di più contatori alla volta.


Al termine dell'esercizio dell'app e della raccolta dei dati, è possibile arrestare la raccolta per un report ancora più dettagliato. A tale scopo, premere il pulsante **Interrompi raccolta** .


Una volta caricato il report, verrà visualizzato un report finalizzato simile a quello illustrato di seguito.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Report dello strumento contatore .NET.":::

Il report Mostra i valori seguenti:

- Min: valore minimo per il contatore nell'intervallo di tempo selezionato.
- Max: valore massimo per il contatore nell'intervallo di tempo selezionato.
- Average: valore medio per il contatore nell'intervallo di tempo selezionato.

È possibile filtrare o aggiungere colonne nella tabella facendo clic con il pulsante destro del mouse sulle intestazioni di colonna e selezionando un'intestazione.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Colonne dello strumento contatore .NET.":::

È anche possibile visualizzare i grafici nel report dettagliato selezionando le caselle di controllo accanto a contatori. I dati nelle tabelle rappresentano i valori dell'intera durata della traccia raccolta per impostazione predefinita. Per filtrare i dati in base a un intervallo di tempo specifico, fare clic e trascinare nei grafici.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Filtri per gli strumenti dei contatori .NET.":::

La tabella aggiorna i valori rilevanti per l'ora selezionata nei grafici. Utilizzare il pulsante **Cancella selezione** per reimpostare l'intervallo di tempo selezionato sull'intera traccia.


## <a name="see-also"></a>Vedere anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)
- [contatori DotNet](/dotnet/core/diagnostics/dotnet-counters)
