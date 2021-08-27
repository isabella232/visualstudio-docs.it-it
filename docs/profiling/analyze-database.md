---
title: Analizzare l'utilizzo del database per i progetti .NET Core | Microsoft Docs
description: Usare lo strumento Database per registrare le query di database dell'app e quindi analizzarle per trovare modi per migliorare le prestazioni.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- database, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 758fad160bad89b5e8a4305bf4757302b05732e1
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/26/2021
ms.locfileid: "122981086"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Analizzare le prestazioni del database con lo strumento Database

Usare lo strumento Database per registrare le query di database eseguite dall'app durante una sessione di diagnostica. È quindi possibile analizzare le informazioni sulle singole query per trovare posizioni per migliorare le prestazioni dell'app.

> [!NOTE]
> Lo strumento Database richiede Visual Studio 2019 versione 16.3 o successiva e un progetto .NET Core in Windows usando [ADO.NET](/dotnet/framework/data/adonet/ado-net-overview) o [Entity Framework Core](/ef/core/).

## <a name="setup"></a>Configurazione

1. Premere **ALT+F2** per aprire il profiler delle prestazioni in Visual Studio.

1. Selezionare la **casella di** controllo Database .

   ![Strumento database selezionato](./media/db-launch.png "Strumento database selezionato")

   > [!NOTE]
   > Se lo strumento non è disponibile per la selezione, deselezionare la casella di controllo di tutti gli altri strumenti perché alcuni strumenti devono essere eseguiti da soli. Per altre informazioni sull'esecuzione di strumenti insieme, vedere [Uso degli strumenti di profilatura dalla riga di comando.](../profiling/using-the-profiling-tools-from-the-command-line.md)
   >
   > Se lo strumento non è ancora disponibile, verificare che il progetto soddisfi i requisiti precedenti. Assicurarsi che il progetto sia in modalità di rilascio per acquisire i dati più accurati.

1. Selezionare il **pulsante Start** per eseguire lo strumento.

1. Dopo l'avvio dell'esecuzione dello strumento, eseguire lo scenario che si vuole profilare nell'app. Selezionare quindi **Interrompi raccolta** o chiudere l'app per visualizzare i dati.

1. Dopo l'arresto della raccolta, viene visualizzata una tabella delle query eseguite durante la sessione di profilatura.

   ![Strumento di database arrestato](./media/db-after.png "Strumento di database arrestato")

Le query sono organizzate in ordine cronologico, ma è possibile ordinarle in base a qualsiasi colonna. È possibile visualizzare più colonne facendo clic con il pulsante destro del mouse sui titoli delle colonne. Selezionando la **colonna Durata** le query vengono ordinate dalla più lunga alla più breve.

Dopo aver trovato una query da analizzare, fare clic con il pulsante destro del mouse sulla query. Selezionare quindi **Vai al file di origine** per visualizzare il codice responsabile della query.

![Vai al file di origine selezionato](./media/db-gotosource.png "Vai al file di origine selezionato")

Se si seleziona un intervallo di tempo in un grafico, la tabella di query mostra solo le query che si sono verificate durante tale intervallo di tempo. Questo comportamento è particolarmente utile quando si esegue anche lo strumento [Utilizzo CPU](./cpu-usage.md?view=vs-2019&preserve-view=true).

## <a name="see-also"></a>Vedi anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)