---
title: Analizzare l'utilizzo della memoria per gli oggetti .NET | Microsoft Docs
description: Visualizzare la quantità di memoria utilizzata dall'app e i percorsi di codice che allocano la maggior parte della memoria usando lo strumento di allocazione di oggetti .NET.
ms.custom: SEO-VS-2020
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 1e44cadb3edb0d91b760b1827df3d8aa8fb3dbbd18190edb0eb18f2d2cf16ff6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442840"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>Analizzare l'utilizzo della memoria usando lo strumento di allocazione di oggetti .NET

È possibile visualizzare la quantità di memoria utilizzata dall'app e i percorsi di codice che allocano la maggior parte della memoria usando lo strumento di allocazione di oggetti .NET.

Dopo aver eseguito lo strumento, è possibile visualizzare i percorsi di esecuzione delle funzioni in cui vengono allocati gli oggetti. È quindi possibile risalire alla radice dell'albero delle chiamate che occupa la maggior parte della memoria.

## <a name="setup"></a>Eseguire la configurazione

1. Selezionare **ALT+F2** per aprire il Profiler prestazioni in Visual Studio.

1. Selezionare la **casella di controllo Rilevamento allocazione oggetti .NET.**

   ![Strumento dotnet Object Allocation Tracking selezionato](../profiling/media/dotnetalloctoolselected.png "Strumento dotnet Object Allocation Tracking selezionato")

1. Selezionare il **pulsante Avvia** per eseguire lo strumento.

1. Dopo l'avvio dell'esecuzione dello strumento, eseguire lo scenario da profilare nell'app. Selezionare quindi **Arresta raccolta** o chiudere l'app per visualizzare i dati.

   ![Finestra che mostra la raccolta Arresta](../profiling/media/stopcollectionlighttheme.png "Finestra che mostra la raccolta Arresta")

1. Selezionare la **scheda Allocazione.** Viene visualizzato il contenuto della finestra simile allo screenshot seguente.

   ![Scheda Allocazione](../profiling/media/allocationview.png "Scheda Allocazione")

È ora possibile analizzare l'allocazione di memoria degli oggetti.

Durante la raccolta, lo strumento di rilevamento può rallentare l'app profilata. Se le prestazioni dello strumento di rilevamento o dell'app sono lente e non è necessario tenere traccia di ogni oggetto, è possibile modificare la frequenza di campionamento. A tale scopo, selezionare il simbolo a forma di ingranaggio accanto a strumento di rilevamento nella pagina di riepilogo del profiler.

![Impostazioni per lo strumento di allocazione Dotnet](../profiling/media/dotnetallocsettings.png "Impostazioni per lo strumento di allocazione Dotnet")

Modificare la frequenza di campionamento in base alla frequenza desiderata. Questa modifica consente di velocizzare le prestazioni dell'app durante la raccolta e l'analisi.

![Frequenza di campionamento modificata](../profiling/media/adjustedsamplingratedotnetalloctool.png "Frequenza di campionamento modificata")

Per altre informazioni su come rendere lo strumento più efficiente, vedere [Ottimizzazione delle impostazioni del profiler.](../profiling/optimize-profiler-settings.md)

## <a name="understand-your-data"></a>Informazioni sui dati

![Grafico per lo strumento di allocazione Dotnet](../profiling/media/graphdotnetalloc.png "Grafico per lo strumento di allocazione Dotnet")

Nella visualizzazione grafica precedente il grafico superiore mostra il numero di oggetti live nell'app. Il grafico **a delta dell'oggetto** inferiore mostra la variazione percentuale degli oggetti dell'app. Le barre rosse indicano quando si è verificata l'operazione di Garbage Collection.

![Grafico filtrato del tempo di allocazione Dotnet](../profiling/media/graphdotnetalloctimefiltered.png "Grafico filtrato del tempo di allocazione Dotnet")

È possibile filtrare i dati tabulari per visualizzare l'attività solo per un intervallo di tempo specificato. È anche possibile eseguire lo zoom avanti o indietro del grafico.

### <a name="allocation"></a>Allocation (Allocazione)

![Visualizzazione Allocazione espansa](../profiling/media/allocationexpandedlight.png "Visualizzazione Allocazione espansa")

La **visualizzazione Allocazione** mostra la posizione degli oggetti che allocano memoria e la quantità di memoria allocata da tali oggetti.

- La **colonna Type** è un elenco di classi e strutture che accettano memoria. Fare doppio clic su un tipo per visualizzare il backtrace come albero delle chiamate invertito. Solo nella **visualizzazione Allocazione** è possibile visualizzare gli elementi all'interno della categoria selezionata che accettano memoria.

- La **colonna Allocazioni** mostra il numero di oggetti che accettano memoria all'interno di un particolare tipo di allocazione o funzione. Questa colonna viene visualizzata solo nelle **visualizzazioni Allocazione**, **Albero delle** chiamate **e** Funzioni .

- Le **colonne Byte** e Dimensioni medie **(byte)** non vengono visualizzate per impostazione predefinita. Per mostrarle, fare  clic con il pulsante destro  del mouse sulla colonna Tipo o Allocazioni e quindi selezionare le opzioni Byte e Dimensioni medie **(byte)** per aggiungerle al grafico.  

   Le due colonne sono simili a **Totale (allocazioni)** e Self **(allocazioni),** con la differenza che mostrano la quantità di memoria utilizzata anziché il numero di oggetti che occupano memoria. Queste colonne vengono visualizzate solo nella **visualizzazione Allocazione.**

- La **colonna Nome** modulo mostra il modulo che contiene la funzione o il processo che sta chiamando.

Tutte queste colonne sono ordinabili. Per le **colonne Tipo** e **Nome modulo** è possibile ordinare gli elementi alfabeticamente in ordine crescente o decrescente. Per **Allocazioni**, **Byte** e **Dimensioni medie (byte)**, è possibile ordinare gli elementi aumentando o diminuendo il valore numerico.

#### <a name="symbols"></a>Simboli

I simboli seguenti vengono visualizzati nelle **schede Allocazione**, **Albero delle** chiamate **e** Funzioni :

- ![Simbolo del tipo di valore:](../profiling/media/valuetypeicon.png "Simbolo del tipo di valore") tipo di valore come integer

- ![Simbolo di raccolta di tipo valore:](../profiling/media/valuetypecollectionicon.png "Simbolo della raccolta di tipo valore") raccolta di tipo valore come matrice di numeri interi

- ![Simbolo del tipo di riferimento:](../profiling/media/referencetypeicon.png "Simbolo del tipo di riferimento") tipo di riferimento come stringa

- ![Simbolo di raccolta reference-type:](../profiling/media/referencetypecollectionicon.png "Simbolo della raccolta reference-type") raccolta di tipi riferimento come matrice di stringhe

### <a name="call-tree"></a>Albero delle chiamate

![Visualizzazione Albero delle chiamate](../profiling/media/calltreelight.png "Visualizzazione Albero delle chiamate")

La **visualizzazione Albero delle** chiamate mostra i percorsi di esecuzione delle funzioni che contengono oggetti che allocano molta memoria.

- La **colonna Nome funzione** mostra il processo o il nome della funzione contenente gli oggetti che allocano memoria. La visualizzazione è basata sul livello del nodo che si sta esaminando.
- Le **colonne Total (Allocations)** e **Total Size (Bytes)** mostrano il numero di oggetti allocati e la quantità di memoria usata da una funzione e da tutte le altre funzioni chiamate.
- Le **colonne Self (Allocazioni)** e **Self-Size (Byte)** mostrano il numero di oggetti allocati e la quantità di memoria usata da una singola funzione o tipo di allocazione selezionato.
- La **colonna Dimensioni medie (byte)** mostra le stesse informazioni della visualizzazione **Allocazioni.**
- La **colonna Nome** modulo mostra il modulo che contiene la funzione o il processo che sta chiamando.

   ![Un percorso critico espanso](../profiling/media/hotpathlight.png "Un percorso critico espanso")

- Il **pulsante Espandi percorso critico** evidenzia un percorso di esecuzione della funzione che contiene molti oggetti che allocano memoria. L'algoritmo inizia da un nodo selezionato ed evidenzia il percorso della maggior parte delle allocazioni, guidando l'utente nell'indagine.
- Il **pulsante Mostra percorso critico** mostra o nasconde i simboli di fiamma che indicano quali nodi fanno parte del percorso critico.

### <a name="functions"></a>Funzioni

![Visualizzazione Funzioni](../profiling/media/functionslight.png "Visualizzazione Funzioni")

La **visualizzazione** Funzioni mostra processi, moduli e funzioni che allocano memoria.

- La **colonna Nome** mostra i processi come nodi di livello più alto. Sotto i processi sono presenti moduli e i moduli sottostanti sono funzioni.
- Queste colonne mostrano le stesse informazioni delle visualizzazioni Albero **di allocazione** **e** chiamata:

  - **Totale (allocazioni)**
  - **Self (allocazioni)**
  - **Dimensione totale (byte)**
  - **Dimensioni self (byte)**
  - **Dimensioni medie (byte)**

### <a name="collection"></a>Raccolta

![Visualizzazione Raccolta](../profiling/media/collectionlight.png "Visualizzazione Raccolta")

La **visualizzazione Raccolta** mostra il numero di oggetti raccolti o conservati durante l'operazione di Garbage Collection. Questa visualizzazione mostra anche i grafici a torta per visualizzare gli oggetti raccolti e non ancora raccolti in base al tipo.

- La **colonna Raccolta** mostra il numero di oggetti raccolti dal Garbage Collector.
- La **colonna Survived** mostra il numero di oggetti che sono stati creati dopo l'esecuzione del Garbage Collector.

### <a name="filtering-tools"></a>Strumenti di filtro

Le **visualizzazioni** Allocazioni  , Albero delle chiamate e Funzioni contengono tutte le opzioni **Mostra** Just My Code e **Mostra** codice nativo e una casella di filtro. 

- **Mostra Just My Code** comprime sistemi, framework e altro codice non utente in **frame [codice esterno]** in modo che sia possibile concentrarsi solo sul codice. Per altre informazioni, vedere [Eseguire il debug del codice utente con Just My Code](../debugger/just-my-code.md).
- **Mostra codice nativo mostra** il codice nativo all'interno della destinazione di analisi e può includere codice non utente.
- Con la casella di filtro è possibile filtrare la colonna **Nome** o Nome **funzione** in base al valore specificato. Immettere un valore stringa nella casella . La tabella mostra quindi solo i tipi che contengono tale stringa.
