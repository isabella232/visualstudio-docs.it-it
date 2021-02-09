---
title: Prestazioni XSLT
description: Informazioni sul Profiler XSLT in Visual Studio che consente di creare report di prestazioni XSLT dettagliati che consentono di ottimizzare le prestazioni del codice XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/11/2020
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 9dc37ceddd87fa0b6c8029c0acb8ea195f9ce10b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900809"
---
# <a name="the-xslt-profiler"></a>Profiler XSLT

Il Profiler XSLT crea rapporti di prestazioni XSLT dettagliati utili per misurare, valutare e trattare problemi correlati alle prestazioni nel codice XSLT. Il Profiler XSLT include suggerimenti utili per le ottimizzazioni dei fogli di stile XSL e XSLT. Per applicazioni XSLT che richiedono massime prestazioni, questo strumento potrebbe essere essenziale.

Il Profiler XSLT è parte di Visual Studio ed è disponibile nel menu **XML** .

![Profiler XSLT](../xml-tools/media/profile-xslt-menu.png "Screenshot delle voci di menu XML in Visual Studio 2017")

> [!NOTE]
> Il Profiler XSLT è disponibile solo nell'edizione Enterprise di Visual Studio 2017.

## <a name="create-a-performance-report"></a>Creazione di un report di prestazioni

1. Aprire un documento XSLT in Visual Studio 2017.

2. Sulla barra dei menu scegliere profilo **XML**  >  **XSLT**.

3. Fornire un documento XML di input. Se non è già aperto un documento XML, verrà richiesto il file.

   L'analisi viene avviata e un indicatore di stato visualizza lo stato di avanzamento all'interno dell'editor. Anche l'output XSLT è visibile.

4. Al termine della sessione di prestazioni, controllare il rapporto di prestazioni per analizzare le prestazioni di XSLT.

## <a name="get-all-available-views"></a>Ottenere tutte le visualizzazioni disponibili

1. Fare clic sull'elenco a discesa **visualizzazione corrente** per ottenere tutte le visualizzazioni disponibili.

2. Selezionare l'opzione **visualizzazione Riepilogo** nell'elenco a discesa **visualizzazione corrente** . Per impostazione predefinita, un rapporto di prestazioni viene visualizzato nella **visualizzazione Riepilogo**. Questa visualizzazione costituisce un punto iniziale per determinare problemi di prestazioni con i documenti XSLT. La **visualizzazione Riepilogo** elenca i punti dati seguenti:

   - Funzioni più chiamate

   - Funzioni con più lavoro individuale

   - Funzioni la cui esecuzione richiede più tempo

   Per impostazione predefinita, esistono tre colonne per ogni punto dati: il nome della funzione, il numero di chiamate in valore assoluto e un valore percentuale della funzione denominata per sommare le chiamate di funzione. Da ogni punto dati nella **visualizzazione di riepilogo**, è possibile passare a visualizzazioni più dettagliate facendo clic con il pulsante destro del mouse sui punti dati della funzione.

3. Selezionare l'opzione **visualizzazione funzione** nell'elenco a discesa **visualizzazione corrente** . La **visualizzazione** funzioni elenca le funzioni chiamate durante la profilatura. Per ordinare i dati è possibile fare clic sul nome di una colonna. Le colonne visualizzate per impostazione predefinita sono:

    - **Nome funzione**

    - **Tempo inclusivo trascorso**

    - **Tempo esclusivo trascorso**

    - **Tempo inclusivo applicazione**

    - **Tempo esclusivo applicazione**

    - **Numero di chiamate**

   Tutte le colonne dell'ora vengono visualizzate sia in valori assoluti che in percentuali. Il termine **esclusivo** si riferisce al tempo totale impiegato da una funzione per l'esecuzione esclusiva del tempo impiegato da altre funzioni chiamate durante l'esecuzione di questa funzione.

   Il termine **inclusivo** si riferisce al tempo totale impiegato per l'esecuzione di una funzione, incluso il tempo di esecuzione di tutte le funzioni chiamate e se una di queste funzioni denominate ha chiamato altre funzioni.

## <a name="select-callercallee-view"></a>Selezionare la visualizzazione Chiamante/chiamato

Selezionare la visualizzazione **chiamante/chiamato** nell'elenco a discesa **visualizzazione corrente** . La visualizzazione **chiamante/chiamato** include le tre parti distinte seguenti:

- **Funzioni che hanno chiamato**: tutte le funzioni che hanno chiamato una particolare funzione sono elencate nella parte superiore della vista.

- **Funzione corrente**: la funzione specifica chiamata viene elencata nella parte centrale della visualizzazione.

- **Funzioni che sono state chiamate da**: tutte le funzioni chiamate dalla funzione specifica sono elencate nella parte inferiore della visualizzazione.

Se una funzione denominata `SyncToNavigator` viene riportata nella parte centrale della visualizzazione, tutte le funzioni che hanno chiamato la funzione `SyncToNavigator` vengono visualizzate nella parte superiore della visualizzazione e tutte le funzioni che sono state chiamate da `SyncToNavigator` vengono elencate nella parte inferiore della visualizzazione.

- È possibile modificare la funzione nella parte centrale della visualizzazione facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione. La visualizzazione verrà quindi automaticamente aggiornata in base alle modifiche.

- Per ordinare i dati, è anche possibile fare clic sui nomi delle colonne.

## <a name="select-call-tree-view"></a>Selezione visualizzazione albero delle chiamate

- Selezionare **visualizzazione albero delle chiamate** nell'elenco a discesa **visualizzazione corrente** . Questa visualizzazione è un albero dell'esecuzione del programma.

   La **visualizzazione albero delle chiamate** Mostra la radice della struttura ad albero come nome del processo. Le funzioni sono i nodi dell'albero. Questa visualizzazione consente di esaminare determinate tracce di chiamata e di analizzare quali tracce hanno il maggiore impatto sulle prestazioni. La visualizzazione è simile alla **visualizzazione dello stack di chiamate** disponibile durante il debug. Oltre alle colonne nella **visualizzazione funzione**, nella **visualizzazione albero delle chiamate** è presente una colonna aggiuntiva per visualizzare il **nome del modulo**.

- Selezionare **Contrassegni** nell'elenco a discesa **visualizzazione corrente** .

   Con il Profiler XSLT sono presenti contrassegni che vengono visualizzati nel flusso di raccolta dati con un commento associato. I contrassegni sono parti del codice che dispongono di contatori. Indicando al Profiler XSLT di raccogliere contatori delle prestazioni XSLT, i contatori vengono raccolti ogni volta che viene eseguito uno di questi contrassegni. I dati vengono visualizzati in una tabella contenente l' **ID contrassegno**, il **nome del contrassegno** (**programma Start**, il **programma finale**) e il **timestamp**. I contrassegni non vengono aggregati e vengono visualizzati in ordine cronologico nella **visualizzazione Contrassegni** del rapporto di prestazioni.

## <a name="select-modules-in-the-current-view"></a>Selezionare i moduli nella visualizzazione corrente

- Selezionare **moduli** nell'elenco a discesa **visualizzazione corrente** .

   La visualizzazione dei moduli è un elenco completo di tutte le funzioni aggregate a livello di modulo. Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo. Per ordinare i dati è possibile fare clic sul nome di una colonna. Per impostazione predefinita, sono presenti sia valori assoluti che numeri percentuali per il **tempo inclusivo trascorso**, il tempo **esclusivo trascorso**, il **tempo inclusivo applicazione**, il **tempo esclusivo applicazione** e il **numero di chiamate**.

- Selezionare **processo** nell'elenco a discesa **visualizzazione corrente** .

   Nella visualizzazione processo viene visualizzata una tabella che include l' **ID del processo**, il nome del **processo**, l'ora di **inizio** e l'ora di **fine**. Per ordinare i dati, è possibile fare clic sui nomi delle colonne.

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: utilizzo della gerarchia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
