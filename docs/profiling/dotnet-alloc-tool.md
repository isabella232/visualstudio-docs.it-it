---
title: Analizzare l'utilizzo della memoria per gli oggetti .NET . Documenti Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75898469"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analizzare l'utilizzo della memoria utilizzando lo strumento di allocazione degli oggetti .NETAnalyze memory usage using the .NET Object Allocation tool

Puoi vedere quanta memoria usa l'app e quali percorsi di codice allocano la maggior parte della memoria usando lo strumento di allocazione degli oggetti .NET.

Dopo aver eseguito lo strumento, è possibile visualizzare i percorsi di esecuzione della funzione in cui gli oggetti vengono allocati in modo da poter risalire alla radice della struttura ad albero delle chiamate che occupa la maggior quantità di memoria.

## <a name="setup"></a>Configurazione

1. Aprire il Profiler prestazioni **(ALT e F2)** in Visual Studio.
2.  Selezionare la casella di **controllo Tracciabilità allocazione oggetti .NET.**

![Diag Hub](../profiling/media/diaghub.png "Diag Hub")

> [!NOTE]
> Il progetto di avvio è selezionato come **Destinazione analisi** per impostazione predefinita, ma questo può essere modificato nel processo in esecuzione, negli eseguibili, nelle app in esecuzione e nelle app installate aprendo il menu a discesa **Cambia destinazione** e quindi selezionando le opzioni disponibili.

   Lo strumento .NET Object Allocation attualmente non supporta gli eseguibili tramite il menu a discesa. Si dovrà passare attraverso il sistema di progetto exe per utilizzare lo strumento. A tale scopo, chiudere la soluzione corrente ( Soluzione di**chiusura****file** -> ) e quindi premere **File** -> **Aprire un progetto o una soluzione** > selezionare il file con estensione exe.

![Destinazione analisi](../profiling/media/analysistarget.png "Destinazione analisi")

3. Fare clic sul pulsante **Start** per eseguire lo strumento.

![Interrompi raccolta](../profiling/media/stopcollection.png "Arresta raccolta")

4. Quando l'esecuzione dello strumento viene avviata, passa attraverso lo scenario desiderato nell'app, quindi premi **Interrompi raccolta** o chiudi l'app per visualizzare i dati.
5. Fare clic sulla scheda **Allocazione** e si dovrebbe vedere un'immagine simile a quella mostrata di seguito.

![Allocation (Allocazione)](../profiling/media/allocation.png "Allocation (Allocazione)")

Congratulazioni. È ora possibile analizzare l'allocazione di memoria degli oggetti.

## <a name="understand-your-data"></a>Comprendere i dati

### <a name="collection"></a>Raccolta

![Collezione](../profiling/media/collection.png "Raccolta")

La visualizzazione di raccolta consente di visualizzare il numero di oggetti raccolti durante l'operazione di Garbage Collection e quanti sono stati conservati. Questa visualizzazione fornisce anche alcuni grafici a torta per visualizzare gli oggetti raccolti e sopravvissuti per tipo.

- La colonna **Collected** mostra il numero di oggetti raccolti dal Garbage Collector.
- La colonna **Sopravvissuto** mostra il numero di oggetti sopravvissuti dopo l'esecuzione del Garbage Collector.

### <a name="allocation"></a>Allocation (Allocazione)

![Allocazione espansa](../profiling/media/allocationexpanded.png "Allocazione espansa")

La visualizzazione di allocazione consente di visualizzare la posizione degli oggetti che allocano memoria e la quantità di memoria che tali oggetti stanno allocando.

- La colonna **Nome** è un elenco di varie classi e strutture che occupano memoria. Ogni elemento all'interno della colonna è un nodo che può essere espanso se sono presenti elementi all'interno di tale categoria che occupano memoria. ( Solo visualizzazione**di allocazione)**
- La colonna **Totale (allocazioni)** mostra il numero di oggetti all'interno di un particolare tipo di allocazione che occupano memoria. **(Allocazione**, **Struttura ad**albero delle chiamate e visualizzazione **Funzioni)**
- La colonna **Self (allocazioni)** mostra il numero di oggetti all'interno di un singolo elemento che occupa memoria. **(Allocazione**, **Struttura ad**albero delle chiamate e visualizzazione **Funzioni)**
- Tutte e tre queste colonne sono ordinabili. Nel caso della colonna **Nome,** gli elementi vengono ordinati alfabeticamente (in avanti o all'indietro). Per **Totale** e **Self (Allocazioni)**, è possibile eseguire l'ordinamento numerico (sempre più o in modo crescente).
- Le colonne **Dimensione totale (byte)** e **Dimensione automatica (byte)** non sono attivate per impostazione predefinita. Per abilitarli, fare clic con il pulsante destro del mouse sulle colonne **Nome,** **Totale** o **Auto (Allocazioni)** e quindi scegliere **Dimensioni totali** e **Dimensioni personalizzate** per aggiungerle al grafico. Le due colonne sono simili a **Totale (allocazioni)** e **Self (allocazioni)** ad eccezione del fatto che invece di mostrare il numero di oggetti che occupano memoria, mostrano la quantità totale di memoria in byte che tali oggetti stanno occupando. [Solo visualizzazione di allocazione]

### <a name="call-tree"></a>Albero delle chiamate

![Albero delle chiamate](../profiling/media/calltree.png "Albero delle chiamate")

La visualizzazione Struttura ad albero **delle chiamate** consente di visualizzare i percorsi di esecuzione delle funzioni che contengono oggetti allocando molta memoria.

- La colonna **Nome funzione** mostra il processo o il nome della funzione contenente oggetti che allocano memoria in base al livello del nodo che si sta controllando.
- Le colonne **Totale** e **Auto (allocazioni)** mostrano le stesse informazioni della visualizzazione **Allocazione.**
- La colonna **Nome modulo** mostra il modulo che contiene la funzione o il processo che sta chiamando.

![Percorso caldo](../profiling/media/hotpath.png "Percorso critico")

- Il pulsante **Espandi percorso critico** evidenzia un percorso di esecuzione della funzione che contiene molti oggetti che allocano memoria. L'algoritmo inizia in corrispondenza di un nodo di interesse selezionato dall'utente ed evidenzia il percorso della maggior parte delle allocazioni, guidando un utente nella propria indagine.
- Il pulsante **Mostra percorso critico** attiva o disattiva le icone di fiamma che indicano quale nodo fa parte del percorso **critico.**

### <a name="functions"></a>Funzioni

![Funzioni](../profiling/media/functions.png "Funzioni")

La visualizzazione **Funzioni** mostra i processi, i moduli e le funzioni che allocano memoria.

- La colonna **Nome** mostra i processi come nodi di livello più alto. Sotto i processi ci sono i moduli, e sotto i moduli ci sono funzioni.
- Le colonne **Totale** e **Auto (allocazioni)** mostrano le stesse informazioni della visualizzazione **Allocazione.**

Le **visualizzazioni Allocazioni**, **Struttura ad**albero delle chiamate e **Funzioni** contengono tutte le opzioni Mostra **codice**My , Mostra codice **nativo**e **Cerca:**

![Barra dei filtri](../profiling/media/filterbar.png "Barra dei filtri")

- **Mostra Just My Code** comprime sistemi, framework e altro codice non utente e in frame **[Codice esterno]** in modo che il codice utente possa essere focalizzato su. Per ulteriori informazioni, vedere [Eseguire il debug del codice utente con Just My Code](../debugger/just-my-code.md).
- **Mostra codice nativo** mostra il codice nativo all'interno della destinazione di analisi, incluso il codice non utente, se selezionato.
- La **casella Filtro** consente di filtrare la colonna **Nome** o Nome **funzione** in base al parametro fornito. È sufficiente digitare il campo e la tabella deve filtrare verso il basso per visualizzare solo i tipi che contengono la stringa fornita.
