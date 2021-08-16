---
title: Visualizzare i contatori dotnet | Microsoft Docs
description: Informazioni sull'uso dello strumento Contatori .NET nel Visual Studio Profiler prestazioni.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 1eb8ce22a6271c10f7a5b0375958788a5f862bdbe51f2bc2759c67ea58399197
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368682"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visualizzare i contatori dotnet dal profiler Visual Studio


Lo strumento Contatori .NET consente di visualizzare i contatori [dotnet](/dotnet/core/diagnostics/dotnet-counters) nel tempo direttamente dall'interno Visual Studio profiler.


> [!NOTE]
> Lo strumento Contatori .NET richiede Visual Studio 2019 versione 16.7 o successiva e ha come destinazione .NET Core 3.0+.

## <a name="setup"></a>Eseguire la configurazione

1. Aprire il Profiler prestazioni (**ALT + F2** o **Debug -> Profiler prestazioni**) in Visual Studio.

2. Selezionare la **casella di controllo Contatori .NET.**

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Strumento Contatori selezionato.":::

3. Fare clic **sul pulsante** Start per eseguire lo strumento.

Per altre informazioni su come ottimizzare le prestazioni dello strumento, vedere [Ottimizzazione delle impostazioni del profiler.](../profiling/optimize-profiler-settings.md)


## <a name="understand-your-data"></a>Informazioni sui dati

Mentre lo strumento raccoglie inizialmente dati, è possibile visualizzare i valori live dei [contatori dotnet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Raccolta dello strumento contatore .NET.":::

È anche possibile visualizzare i grafici dei contatori selezionando la casella di controllo accanto ai nomi dei contatori. È possibile visualizzare i grafici di più contatori contemporaneamente.


Al termine dell'esercizio dell'app e della raccolta dei dati, è possibile interrompere la raccolta per un report ancora più dettagliato. A tale scopo, premere il **pulsante Arresta** raccolta.


Dopo il caricamento del report, verrà visualizzato un report finalizzato simile a quello illustrato di seguito.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Report dello strumento Contatore .NET.":::

Il report mostra i valori seguenti:

- Min: valore minimo per il contatore nell'intervallo di tempo selezionato.
- Max: valore massimo per il contatore nell'intervallo di tempo selezionato.
- Average : valore medio per il contatore nell'intervallo di tempo selezionato.

È possibile filtrare o aggiungere colonne nella tabella facendo clic con il pulsante destro del mouse sulle intestazioni di colonna e selezionando un'intestazione.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Colonne dello strumento Contatore .NET.":::

È anche possibile visualizzare i grafici nel report dettagliato selezionando le caselle di controllo accanto ai contatori. I dati nelle tabelle rappresentano i valori dell'intera durata della traccia raccolta per impostazione predefinita. Per filtrare i dati in base a un intervallo di tempo specifico, fare clic e trascinare i grafici.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Filtro temporale dello strumento Contatori .NET.":::

La tabella viene aggiornata ai valori rilevanti per l'ora selezionata nei grafici. Usare il **pulsante Cancella** selezione per reimpostare l'intervallo di tempo selezionato sull'intera traccia.


## <a name="see-also"></a>Vedi anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)
- [Contatori dotnet](/dotnet/core/diagnostics/dotnet-counters)
