---
title: 'Procedura dettagliata: Profiler XSLT | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7ee6665aea98edf7cb701f5fdfe07d293887bac
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669530"
---
# <a name="walkthrough-xslt-profiler"></a>Procedura dettagliata: XSLT Profiler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il Profiler XSLT crea rapporti di prestazioni XSLT dettagliati utili per misurare, valutare e trattare problemi correlati alle prestazioni nel codice XSLT. Il Profiler XSLT include suggerimenti utili per le ottimizzazioni dei fogli di stile XSL e XSLT. Per applicazioni XSLT che richiedono massime prestazioni, questo strumento potrebbe essere essenziale.

## <a name="prerequisites"></a>Prerequisiti
 Le operazioni descritte nella seguente procedura dettagliata richiedono Visual Studio 2010 e .NET Framework versione 4. Il Profiler XSLT è disponibile solo con Microsoft Visual Studio Team System con gli strumenti di analisi installati.

### <a name="create-the-performance-report"></a>Creare il rapporto di prestazioni

1. Aprire un documento XSLT in Visual Studio.

2. Fare clic sull'opzione **profile XSLT** disponibile nel menu XML.

3. Fornire un documento XML di input. Se non è già aperto un documento XML, verrà richiesto il file.

4. L'analisi viene avviata e un indicatore di stato visualizza lo stato di avanzamento all'interno dell'editor.

5. L'output XSLT è visibile nel riquadro di output.

6. Al termine di una sessione di prestazioni, controllare il rapporto di prestazioni. I dati salvati in un rapporto di prestazioni consentono di visualizzare e analizzare le prestazioni di XSLT.

### <a name="get-all-the-available-views"></a>Ottenere tutte le visualizzazioni disponibili

1. Fare clic sull'elenco a discesa **visualizzazione corrente** per ottenere tutte le visualizzazioni disponibili.

2. Selezionare l'opzione **visualizzazione Riepilogo** nell'elenco a discesa **visualizzazione corrente** . Per impostazione predefinita, un rapporto di prestazioni viene visualizzato nella **visualizzazione Riepilogo**. Questa visualizzazione costituisce un punto iniziale per determinare problemi di prestazioni con i documenti XSLT. La **visualizzazione Riepilogo** elenca i punti dati seguenti:

    - Funzioni più chiamate

    - Funzioni con più lavoro individuale

    - Funzioni la cui esecuzione richiede più tempo

3. Per impostazione predefinita, esistono tre colonne per ogni punto dati: il nome della funzione, il numero di chiamate in valore assoluto e un valore percentuale della funzione denominata per sommare le chiamate di funzione. Da ogni punto dati nella **visualizzazione di riepilogo**, è possibile passare a visualizzazioni più dettagliate facendo clic con il pulsante destro del mouse sui punti dati della funzione.

4. Selezionare l'opzione **visualizzazione funzione** nell'elenco a discesa **visualizzazione corrente** . La **visualizzazione** funzioni elenca le funzioni chiamate durante la profilatura. Per ordinare i dati è possibile fare clic sul nome di una colonna. Le colonne visualizzate per impostazione predefinita sono:

    - **Nome funzione**

    - **Tempo inclusivo trascorso**

    - **Tempo esclusivo trascorso**

    - **Tempo inclusivo applicazione**

    - **Tempo esclusivo applicazione**

    - **Numero di chiamate**

5. Tutte le colonne dell'ora vengono visualizzate sia in valori assoluti che in percentuali. Il termine **esclusivo** si riferisce al tempo totale impiegato da una funzione per l'esecuzione esclusiva del tempo impiegato da altre funzioni chiamate durante l'esecuzione di questa funzione.

6. Il termine **inclusivo** si riferisce al tempo totale impiegato per l'esecuzione di una funzione, incluso il tempo di esecuzione di tutte le funzioni chiamate e se una di queste funzioni denominate ha chiamato altre funzioni.

### <a name="select-callercallee-view"></a>Selezionare la visualizzazione Chiamante/chiamato

1. Selezionare la visualizzazione **chiamante/chiamato** nell'elenco a discesa **visualizzazione corrente** .

2. La visualizzazione **chiamante/chiamato** include le tre parti distinte seguenti:

    - **Funzioni che hanno chiamato**: tutte le funzioni che hanno chiamato una particolare funzione sono elencate nella parte superiore della vista.

    - **Funzione corrente**: la funzione specifica chiamata viene elencata nella parte centrale della visualizzazione.

    - **Funzioni che sono state chiamate da** : tutte le funzioni chiamate dalla funzione specifica sono elencate nella parte inferiore della visualizzazione.

3. Se una funzione denominata `SyncToNavigator` viene riportata nella parte centrale della visualizzazione, tutte le funzioni che hanno chiamato la funzione `SyncToNavigator` vengono visualizzate nella parte superiore della visualizzazione e tutte le funzioni che sono state chiamate da `SyncToNavigator` vengono elencate nella parte inferiore della visualizzazione.

4. È possibile modificare la funzione nella parte centrale della visualizzazione facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione. La visualizzazione verrà quindi automaticamente aggiornata in base alle modifiche.

5. Per ordinare i dati, è anche possibile fare clic sui nomi delle colonne.

### <a name="select-calltree-view"></a>Selezionare la visualizzazione albero delle chiamate

1. Selezionare **visualizzazione albero delle chiamate** nell'elenco a discesa **visualizzazione corrente** . Questa visualizzazione è un albero dell'esecuzione del programma.

2. La **visualizzazione albero delle chiamate** Mostra la radice della struttura ad albero come nome del processo. Le funzioni sono i nodi dell'albero. Questa visualizzazione consente di esaminare determinate tracce di chiamata e di analizzare quali tracce hanno il maggiore impatto sulle prestazioni. La visualizzazione è simile alla **visualizzazione dello stack di chiamate** disponibile durante il debug. Oltre alle colonne nella **visualizzazione funzione**, nella **visualizzazione albero delle chiamate**è presente una colonna aggiuntiva per visualizzare il **nome del modulo**.

3. Selezionare **Contrassegni** nell'elenco a discesa **visualizzazione corrente** .

4. Con il Profiler SLT, vengono visualizzati contrassegni nel flusso di raccolta dati con un commento associato. I contrassegni sono parti del codice che dispongono di contatori. Indicando al Profiler XSLT di raccogliere contatori delle prestazioni XSLT, i contatori vengono raccolti ogni volta che viene eseguito uno di questi contrassegni. I dati vengono visualizzati in una tabella contenente l' **ID contrassegno**, il **nome del contrassegno** (**programma Start**, il **programma finale**) e il **timestamp**. I contrassegni non vengono aggregati e vengono visualizzati in ordine cronologico nella **visualizzazione Contrassegni** del rapporto di prestazioni.

### <a name="select-modules-in-the-current-view"></a>Selezionare i moduli nella visualizzazione corrente

1. Selezionare **moduli** nell'elenco a discesa **visualizzazione corrente** .

2. La visualizzazione dei moduli è un elenco completo di tutte le funzioni aggregate a livello di modulo. Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo. Per ordinare i dati è possibile fare clic sul nome di una colonna. Per impostazione predefinita, sono presenti sia valori assoluti che numeri percentuali per il **tempo inclusivo trascorso**, il tempo **esclusivo trascorso**, il **tempo inclusivo applicazione**, il **tempo esclusivo applicazione**e il **numero di chiamate**.

3. Selezionare **processo** nell'elenco a discesa **visualizzazione corrente** .

4. Nella visualizzazione processo viene visualizzata una tabella che include l' **ID del processo**, il nome del **processo**, l'ora di **inizio**e l'ora di **fine**. Per ordinare i dati, è possibile fare clic sui nomi delle colonne.

## <a name="see-also"></a>Vedere anche
 [Procedura dettagliata: uso della gerarchia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
