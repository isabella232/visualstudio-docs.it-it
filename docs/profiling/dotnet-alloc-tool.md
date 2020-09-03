---
title: Analizzare l'utilizzo della memoria per gli oggetti .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: how-to
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 81c15753b083256b97c9f67219b64565a8db8736
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88247797"
---
# <a name="analyze-memory-usage-by-using-the-net-object-allocation-tool"></a>Analizzare l'utilizzo della memoria mediante lo strumento di allocazione oggetti .NET

È possibile visualizzare la quantità di memoria usata dall'app e i percorsi del codice che allocano la maggior parte della memoria mediante lo strumento di allocazione oggetti .NET.

Dopo aver eseguito lo strumento, è possibile visualizzare i percorsi di esecuzione della funzione in cui vengono allocati gli oggetti. È quindi possibile risalire alla radice dell'albero delle chiamate che sta occupando la maggior parte della memoria.

## <a name="setup"></a>Configurazione

1. Selezionare **ALT + F2** per aprire il profiler delle prestazioni in Visual Studio.

1. Selezionare la casella di controllo **rilevamento allocazione oggetti .NET** .

   ![Strumento di rilevamento dell'allocazione di oggetti DotNet selezionato](../profiling/media/dotnetalloctoolselected.png "Strumento di rilevamento dell'allocazione di oggetti DotNet selezionato")

1. Selezionare il pulsante **Avvia** per eseguire lo strumento.

1. Dopo l'avvio dell'esecuzione dello strumento, esaminare lo scenario che si vuole profilare nell'app. Quindi selezionare **Arresta raccolta** o Chiudi l'app per visualizzare i dati.

   ![Finestra che mostra la raccolta di arresti](../profiling/media/stopcollectionlighttheme.png "Finestra che mostra la raccolta di arresti")

1. Selezionare la scheda **allocazione** . Viene visualizzato il contenuto della finestra simile alla schermata seguente.

   ![Scheda allocazione](../profiling/media/allocationview.png "Scheda allocazione")

È ora possibile analizzare l'allocazione di memoria degli oggetti.

Durante la raccolta, lo strumento di rilevamento può rallentare l'applicazione profilata. Se le prestazioni dello strumento di rilevamento o dell'app sono lente e se non è necessario tenere traccia di ogni oggetto, è possibile regolare la frequenza di campionamento. A tale scopo, selezionare il simbolo dell'ingranaggio accanto allo strumento di rilevamento nella pagina di riepilogo del profiler.

![Impostazioni per lo strumento di allocazione DotNet](../profiling/media/dotnetallocsettings.png "Impostazioni per lo strumento di allocazione DotNet")

Modificare la frequenza di campionamento in base alla velocità desiderata. Questa modifica consente di velocizzare le prestazioni dell'applicazione durante la raccolta e l'analisi.

![Frequenza di campionamento regolata](../profiling/media/adjustedsamplingratedotnetalloctool.png "Frequenza di campionamento regolata")

Per ulteriori informazioni su come rendere più efficiente lo strumento, vedere [ottimizzazione delle impostazioni del profiler](../profiling/optimize-profiler-settings.md).

## <a name="understand-your-data"></a>Informazioni sui dati

![Grafico per lo strumento di allocazione DotNet](../profiling/media/graphdotnetalloc.png "Grafico per lo strumento di allocazione DotNet")

Nella visualizzazione grafica precedente il grafico superiore mostra il numero di oggetti attivi nell'app. Il grafico **Delta dell'oggetto** inferiore mostra la percentuale di modifica degli oggetti app. Le barre rosse indicano quando si è verificata Garbage Collection.

![Grafico filtrato del tempo di allocazione DotNet](../profiling/media/graphdotnetalloctimefiltered.png "Grafico filtrato del tempo di allocazione DotNet")

È possibile filtrare i dati tabulari per visualizzare l'attività solo per un intervallo di tempo specificato. È anche possibile ingrandire o ridurre il grafico.

### <a name="allocation"></a>Allocation (Allocazione)

![Visualizzazione allocazione espansa](../profiling/media/allocationexpandedlight.png "Visualizzazione allocazione espansa")

La visualizzazione **allocazione** Mostra la posizione degli oggetti che allocano memoria e la quantità di memoria allocata da tali oggetti.

- La colonna **tipo**   è un elenco di classi e strutture che utilizzano la memoria. Fare doppio clic su un tipo per visualizzarne il backtrace come albero delle chiamate invertito. Solo nella visualizzazione **allocazione** è possibile visualizzare gli elementi all'interno della categoria selezionata che interessano la memoria.

- Nella colonna **allocazioni**   viene visualizzato il numero di oggetti che utilizzano la memoria all'interno di una particolare funzione o tipo di allocazione. Questa colonna viene visualizzata solo nelle visualizzazioni **allocazione**, **albero delle chiamate**e **funzioni**   .

- Le colonne **bytes**   e **Average size (bytes)**   non vengono visualizzate per impostazione predefinita. Per visualizzarli, fare clic con il pulsante destro del mouse sulla colonna **tipo**   o **allocazioni**   , quindi selezionare le opzioni **byte**   e **dimensioni medie (byte)**   per aggiungerle al grafico. 

   Le due colonne sono simili a **totale (allocazioni)** e **self (allocazioni)**, ad eccezione del fatto che mostrano la quantità di memoria occupata anziché il numero di oggetti che occupano memoria. Queste colonne vengono visualizzate solo nella visualizzazione **allocazione** .

- Nella colonna **nome modulo**   viene visualizzato il modulo che contiene la funzione o il processo che sta chiamando.

Tutte le colonne sono ordinabili. Per le colonne del **tipo** e del **nome del modulo** , è possibile ordinare alfabeticamente gli elementi in ordine crescente o decrescente. Per le **allocazioni**, i **byte**   e le **dimensioni medie (byte)**, è possibile ordinare gli elementi aumentando o diminuendo il valore numerico.

#### <a name="symbols"></a>Simboli

I simboli seguenti vengono visualizzati nelle schede **allocazione**, **albero delle chiamate**e **funzioni** :

- ![Il tipo di valore symbol](../profiling/media/valuetypeicon.png "Simbolo del tipo di valore") , un tipo di valore come Integer

- ![Simbolo della raccolta di tipi di valore](../profiling/media/valuetypecollectionicon.png "Simbolo di raccolta di tipo valore") , ovvero una raccolta di tipi di valore, ad esempio una matrice di numeri interi

- ![Il simbolo del tipo di riferimento](../profiling/media/referencetypeicon.png "Simbolo del tipo di riferimento") , un tipo di riferimento come stringa

- ![Il simbolo della raccolta dei tipi di riferimento](../profiling/media/referencetypecollectionicon.png "Simbolo di raccolta dei tipi di riferimento") , ovvero una raccolta di tipi di riferimento, ad esempio una matrice di stringhe

### <a name="call-tree"></a>Albero delle chiamate

![Visualizzazione albero delle chiamate](../profiling/media/calltreelight.png "Visualizzazione albero delle chiamate")

La visualizzazione **albero delle chiamate**Mostra   i percorsi di esecuzione della funzione che contengono oggetti che allocano molta memoria.

- Nella colonna **nome funzione**   viene visualizzato il processo o il nome della funzione contenente oggetti che allocano memoria. La visualizzazione è basata sul livello del nodo che si sta controllando.
- Le colonne **totale (allocazioni)** e **dimensioni totali (byte)**   mostrano il numero di oggetti allocati e la quantità di memoria utilizzata da una funzione e da tutte le altre funzioni da essa chiamate.
- Le colonne **self (Allocations)** e **self-size (byte)** mostrano il numero di oggetti allocati e la quantità di memoria utilizzata da una singola funzione o tipo di allocazione selezionato.
- Nella colonna **dimensioni medie (byte)** vengono visualizzate le stesse informazioni presenti nella visualizzazione **allocazioni** .
- Nella colonna **nome modulo**   viene visualizzato il modulo che contiene la funzione o il processo che sta chiamando.

   ![Un percorso critico espanso](../profiling/media/hotpathlight.png "Un percorso critico espanso")

- Il pulsante **Espandi percorso critico** evidenzia un percorso di esecuzione della funzione che contiene molti oggetti che allocano memoria. L'algoritmo inizia in corrispondenza di un nodo selezionato ed evidenzia il percorso della maggior parte delle allocazioni, guidando l'utente nell'analisi.
- Il pulsante **Mostra percorso critico** Mostra o nasconde i simboli della fiamma che indicano i nodi che fanno parte del percorso critico.

### <a name="functions"></a>Funzioni

![Visualizzazione funzioni](../profiling/media/functionslight.png "Visualizzazione funzioni")

La visualizzazione **funzioni** Mostra i processi, i moduli e le funzioni che allocano memoria.

- Nella colonna **nome** vengono visualizzati i processi come nodi di livello più alto. I processi sotto sono moduli e sotto i moduli sono funzioni.
- In queste colonne vengono visualizzate le stesse informazioni eseguite nelle visualizzazioni albero di **allocazione** e **chiamate** :

  - **Totale (allocazioni)**
  - **Self (allocazioni)**
  - **Dimensione totale (byte)**
  - **Dimensione automatica (byte)**
  - **Dimensioni medie (byte)**

### <a name="collection"></a>Raccolta

![Visualizzazione raccolta](../profiling/media/collectionlight.png "Visualizzazione raccolta")

La visualizzazione **raccolta** Mostra il numero di oggetti raccolti o conservati durante Garbage Collection. Questa vista mostra anche i grafici a torta per visualizzare gli oggetti raccolti e superstiti per tipo.

- La colonna **raccolta** indica il numero di oggetti raccolti dal Garbage Collector.
- La colonna **superstite** Mostra il numero di oggetti rimasti dopo l'esecuzione del Garbage Collector.

### <a name="filtering-tools"></a>Strumenti di filtro

Le visualizzazioni **allocazioni**, **albero delle chiamate**e **funzioni** contengono tutte le opzioni **Mostra Just My Code** e **Mostra codice nativo** e una casella filtro.

- **Mostra Just My Code** comprime sistemi, Framework e altro codice non utente in frame **[codice esterno]** , in modo da potersi concentrare solo sul codice. Per altre informazioni, vedere [eseguire il debug del codice utente con Just My Code](../debugger/just-my-code.md).
- **Mostra codice nativo** Mostra il codice nativo all'interno della destinazione di analisi e può includere codice non utente.
- Con la casella filtro è possibile filtrare la colonna nome **o** **nome funzione** in base al valore fornito. Immettere un valore stringa nella casella. La tabella mostra quindi solo i tipi che contengono tale stringa.
