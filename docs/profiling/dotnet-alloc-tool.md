---
title: Analizzare l'utilizzo della memoria per gli oggetti .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2020
ms.locfileid: "75898469"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analizzare l'utilizzo della memoria mediante lo strumento di allocazione oggetti .NET

È possibile visualizzare la quantità di memoria usata dall'app e i percorsi del codice che allocano la maggior parte della memoria usando lo strumento di allocazione oggetti .NET.

Dopo aver eseguito lo strumento, è possibile visualizzare i percorsi di esecuzione della funzione in cui vengono allocati gli oggetti in modo che sia possibile risalire alla radice dell'albero delle chiamate che sta occupando la maggior quantità di memoria.

## <a name="setup"></a>Programma di installazione

1. Aprire il profiler delle prestazioni (**ALT + F2)** in Visual Studio.
2.  Selezionare la casella di **controllo rilevamento allocazione oggetti .NET** .

![Hub diag](../profiling/media/diaghub.png "Hub diag")

> [!NOTE]
> Il progetto di avvio viene selezionato come **destinazione di analisi** per impostazione predefinita, ma può essere modificato nel processo in esecuzione, nei file eseguibili, nelle app in esecuzione e nelle app installate aprendo il menu a discesa **Modifica destinazione** e quindi selezionando una delle opzioni disponibili.

   Lo strumento di allocazione oggetti .NET attualmente non supporta i file eseguibili tramite il menu a discesa. Per usare lo strumento, sarà necessario esaminare il sistema di progetto exe. A tale scopo, chiudere la soluzione corrente (**file** -> **Chiudi soluzione**), quindi fare clic su **file** -> **aprire un progetto o una soluzione** > selezionare il file con estensione exe.

![Destinazione analisi](../profiling/media/analysistarget.png "Destinazione analisi")

3. Fare clic sul pulsante **Start** per eseguire lo strumento.

![Interrompi raccolta](../profiling/media/stopcollection.png "Arresta raccolta")

4. Una volta avviata l'esecuzione dello strumento, esaminare lo scenario desiderato nell'app, quindi premere **Stop Collection** o chiudere l'app per visualizzare i dati.
5. Fare clic sulla scheda **allocazione** . verrà visualizzata un'immagine simile a quella illustrata di seguito.

![Allocation](../profiling/media/allocation.png "Allocazione")

Congratulazioni! È ora possibile analizzare l'allocazione di memoria degli oggetti.

## <a name="understand-your-data"></a>Informazioni sui dati

### <a name="collection"></a>Raccolta

![Raccolta](../profiling/media/collection.png "Raccolta")

La visualizzazione raccolta consente di visualizzare il numero di oggetti raccolti durante Garbage Collection e il numero di oggetti conservati. Questa vista fornisce anche alcuni grafici a torta per visualizzare gli oggetti raccolti e superstiti in base al tipo.

- La colonna **raccolta** indica il numero di oggetti raccolti dal Garbage Collector.
- La colonna **superstite** Mostra il numero di oggetti rimasti dopo l'esecuzione del Garbage Collector.

### <a name="allocation"></a>Allocazione

![Allocazione espansa](../profiling/media/allocationexpanded.png "Allocazione espansa")

La visualizzazione Allocazione consente di visualizzare la posizione degli oggetti che allocano memoria e la quantità di memoria allocata dagli oggetti.

- La colonna **nome** è un elenco di varie classi e strutture che occupano memoria. Ogni elemento all'interno della colonna è un nodo che può essere espanso se nella categoria sono presenti elementi che occupano memoria. (Solo visualizzazione**allocazione** )
- La colonna **totale (allocazioni)** indica il numero di oggetti all'interno di un determinato tipo di allocazione che occupano memoria. (**Allocazione**, **albero delle chiamate**e visualizzazione **funzioni** )
- La colonna **self (Allocations)** Mostra il numero di oggetti all'interno di un singolo elemento che sta occupando memoria. (**Allocazione**, **albero delle chiamate**e visualizzazione **funzioni** )
- Tutte e tre le colonne sono ordinabili. Nel caso della colonna **nome** , gli elementi vengono ordinati in ordine alfabetico (avanti o indietro). Per il **totale** e l' **autonomia (allocazioni)** , è possibile ordinare numericamente, in modo crescente o decrescente.
- Le colonne **dimensioni totali (byte)** e **Dimensione automatica (byte)** non sono attivate per impostazione predefinita. Per abilitarli, fare clic con il pulsante destro del mouse sulle colonne **nome**, **totale** o **automatico (allocazioni)** , quindi fare clic su **dimensioni totali** e opzioni di **ridimensionamento automatico** per aggiungerle al grafico. Le due colonne sono simili a **totale (allocazioni)** e **self (allocazioni)** ad eccezione del fatto che, invece di visualizzare il numero di oggetti che occupano memoria, visualizzano la quantità totale di memoria in byte che tali oggetti sono in esecuzione. [Solo visualizzazione Allocazione]

### <a name="call-tree"></a>Albero delle chiamate

![Albero delle chiamate](../profiling/media/calltree.png "Albero delle chiamate")

La visualizzazione **albero delle chiamate** consente di visualizzare i percorsi di esecuzione della funzione che contengono oggetti che allocano una grande quantità di memoria.

- La colonna **nome funzione** Mostra il processo o il nome della funzione che contiene gli oggetti che allocano memoria in base al livello del nodo che si sta controllando.
- Le colonne **totale** e **auto (allocazioni)** mostrano le stesse informazioni della visualizzazione **allocazione** .
- Nella colonna **nome modulo** viene visualizzato il modulo che contiene la funzione o il processo che sta chiamando.

![Percorso critico](../profiling/media/hotpath.png "Percorso critico")

- Il pulsante **Espandi percorso critico** evidenzia un percorso di esecuzione della funzione che contiene numerosi oggetti che allocano memoria. L'algoritmo inizia da un nodo di interesse selezionato dall'utente ed evidenzia il percorso della maggior parte delle allocazioni, guidando un utente nella propria indagine.
- Il pulsante **Mostra percorso critico** consente di attivare o disattivare le icone della fiamma che indicano il nodo che fa parte del **percorso critico**.

### <a name="functions"></a>Funzioni

![Funzioni](../profiling/media/functions.png "Funzioni")

La visualizzazione **funzioni** Mostra i processi, i moduli e le funzioni che allocano memoria.

- Nella colonna **nome** vengono visualizzati i processi come nodi di livello più alto. I processi sotto sono moduli e in moduli sono funzioni.
- Le colonne **totale** e **auto (allocazioni)** mostrano le stesse informazioni della visualizzazione **allocazione** .

Le visualizzazioni **allocazioni**, **albero delle chiamate**e **funzioni** contengono tutte le opzioni **Mostra Just My Code**, **Mostra codice nativo**e **Cerca** :

![Barra del filtro](../profiling/media/filterbar.png "Barra del filtro")

- **Mostra Just My Code** comprime i sistemi, i Framework e altri codici non utente e nei frame **[codice esterno]** in modo che sia possibile concentrarsi sul codice utente. Per altre informazioni, vedere [eseguire il debug del codice utente con Just My Code](../debugger/just-my-code.md).
- **Mostra codice nativo** Mostra il codice nativo all'interno della destinazione di analisi, incluso il codice non utente, se selezionato.
- La **casella filtro** consente di filtrare la colonna nome **o** **nome funzione** in base al parametro fornito. È sufficiente digitare il campo e la tabella deve filtrare per visualizzare solo i tipi che contengono la stringa specificata.
