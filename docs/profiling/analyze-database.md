---
title: Analizzare l'utilizzo del database per i progetti .NET Core | Microsoft Docs
description: Usare lo strumento database per registrare le query del database dell'app, quindi analizzarle per trovare modi per migliorare le prestazioni.
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
ms.openlocfilehash: a8518e3f43bec3a9d5f696a07613dee84829dbc2
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205463"
---
# <a name="analyze-database-performance-using-the-database-tool"></a>Analizzare le prestazioni del database tramite lo strumento database

Usare lo strumento database per registrare le query del database eseguite dall'app durante una sessione di diagnostica. È quindi possibile analizzare le informazioni sulle singole query per trovare le posizioni per migliorare le prestazioni dell'app.

> [!NOTE]
> Lo strumento database richiede Visual Studio 2019 versione 16,3 o successiva e un progetto .NET Core in Windows con [ADO.NET]( https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) o [Entity Framework Core](/ef/core/).

## <a name="setup"></a>Configurazione

1. Selezionare **ALT + F2** per aprire il profiler delle prestazioni in Visual Studio.

1. Selezionare la casella di controllo **database** .

   ![Strumento database selezionato](./media/db-launch.png "Strumento database selezionato")

   > [!NOTE]
   > Se lo strumento non è disponibile per la selezione, deselezionare la casella di controllo di ogni altro strumento, perché alcuni strumenti devono essere eseguiti da soli. Per ulteriori informazioni sull'esecuzione di strumenti insieme, vedere l'articolo relativo all' [utilizzo degli strumenti di profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md).
   >
   > Se lo strumento non è ancora disponibile, verificare che il progetto soddisfi i requisiti precedenti. Verificare che il progetto sia in modalità versione per acquisire i dati più accurati.

1. Selezionare il pulsante **Avvia** per eseguire lo strumento.

1. Dopo l'avvio dell'esecuzione dello strumento, esaminare lo scenario che si vuole profilare nell'app. Quindi selezionare **Arresta raccolta** o Chiudi l'app per visualizzare i dati.

1. Dopo l'arresto della raccolta, viene visualizzata una tabella delle query eseguite durante la sessione di profilatura.

   ![Lo strumento di database è stato arrestato](./media/db-after.png "Lo strumento di database è stato arrestato")

Le query sono organizzate in ordine cronologico, ma è possibile ordinarle in base a qualsiasi colonna. È possibile visualizzare più colonne facendo clic con il pulsante destro del mouse sui titoli delle colonne. Se si seleziona la colonna **durata** , le query vengono ordinate dalla più lunga durata alla più breve.

Dopo aver individuato una query che si desidera analizzare, fare clic con il pulsante destro del mouse sulla query. Selezionare quindi **Vai a file di origine** per vedere quale codice è responsabile per la query.

![Vai a file di origine selezionato](./media/db-gotosource.png "Vai a file di origine selezionato")

Se si seleziona un intervallo di tempo in un grafico, nella tabella query vengono mostrate solo le query che si sono verificate durante tale intervallo di tempo. Questo comportamento è particolarmente utile quando si esegue anche lo [strumento utilizzo CPU](./cpu-usage.md?view=vs-2019&preserve-view=true).

## <a name="see-also"></a>Vedere anche

- [Ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md)