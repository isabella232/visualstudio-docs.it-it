---
title: Prestazioni XSLT
description: Informazioni sul profiler XSLT in Visual Studio che crea report dettagliati sulle prestazioni XSLT per ottimizzare le prestazioni del codice XSLT.
ms.custom: SEO-VS-2020
ms.date: 11/11/2020
ms.topic: conceptual
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 4e4c15f9185a967f2c200a00ad2312343600c73e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147492"
---
# <a name="the-xslt-profiler"></a>The XSLT Profiler

Il Profiler XSLT crea rapporti di prestazioni XSLT dettagliati utili per misurare, valutare e trattare problemi correlati alle prestazioni nel codice XSLT. Il Profiler XSLT include suggerimenti utili per le ottimizzazioni dei fogli di stile XSL e XSLT. Per applicazioni XSLT che richiedono massime prestazioni, questo strumento potrebbe essere essenziale.

Il profiler XSLT fa parte di Visual Studio ed è disponibile nel menu **XML.**

![XSLT Profiler](../xml-tools/media/profile-xslt-menu.png "Screenshot delle voci di menu XML in Visual Studio 2017")

> [!NOTE]
> Il profiler XSLT è disponibile solo nell'Enterprise di Visual Studio 2017.

## <a name="create-a-performance-report"></a>Creare un report sulle prestazioni

1. Aprire un documento XSLT in Visual Studio 2017.

2. Sulla barra dei menu scegliere **XML**  >  **Profile XSLT**.

3. Fornire un documento XML di input. Se non è già aperto un documento XML, verrà richiesto il file.

   L'analisi viene avviata e un indicatore di stato visualizza lo stato di avanzamento all'interno dell'editor. È visibile anche l'output XSLT.

4. Al termine della sessione di prestazioni, controllare il report sulle prestazioni per analizzare le prestazioni XSLT.

## <a name="get-all-available-views"></a>Ottenere tutte le visualizzazioni disponibili

1. Fare clic **sull'elenco a** discesa Visualizzazione corrente per ottenere tutte le visualizzazioni disponibili.

2. Selezionare **l'opzione Visualizzazione** riepilogo **nell'elenco a** discesa Visualizzazione corrente. Per impostazione predefinita, nella visualizzazione Riepilogo viene visualizzato un report **sulle prestazioni.** Questa visualizzazione costituisce un punto iniziale per determinare problemi di prestazioni con i documenti XSLT. Nella **visualizzazione Riepilogo sono** elencati i punti dati seguenti:

   - Funzioni più chiamate

   - Funzioni con più lavoro individuale

   - Funzioni la cui esecuzione richiede più tempo

   Per impostazione predefinita, esistono tre colonne per ogni punto dati: il nome della funzione, il numero di chiamate in valore assoluto e un valore percentuale della funzione denominata per sommare le chiamate di funzione. Da ogni punto dati nella visualizzazione **Riepilogo** è possibile passare a visualizzazioni più dettagliate facendo clic con il pulsante destro del mouse sui punti dati della funzione.

3. Selezionare **l'opzione Visualizzazione** funzione **nell'elenco a** discesa Visualizzazione corrente. Nella **visualizzazione Funzione sono** elencate le funzioni chiamate durante la profilatura. Per ordinare i dati è possibile fare clic sul nome di una colonna. Le colonne visualizzate per impostazione predefinita sono:

    - **Nome della funzione**

    - **Tempo inclusivo trascorso**

    - **Tempo esclusivo trascorso**

    - **Tempo inclusivo applicazione**

    - **Tempo esclusivo applicazione**

    - **Numero di chiamate**

   Tutte le colonne dell'ora vengono visualizzate sia in valori assoluti che in percentuali. Il termine **Esclusivo si** riferisce al tempo totale impiegato da una funzione per l'esecuzione del tempo esclusivo impiegato da altre funzioni chiamate durante l'esecuzione di questa funzione.

   Il termine **inclusivo** si riferisce al tempo totale impiegato per l'esecuzione di una funzione, incluso il tempo di esecuzione di tutte le funzioni chiamate e se una di queste funzioni chiamate ha chiamato altre funzioni.

## <a name="select-callercallee-view"></a>Selezionare la visualizzazione Chiamante/chiamato

Selezionare **la visualizzazione Chiamante/chiamato** nell'elenco **a** discesa Visualizzazione corrente. La **visualizzazione Chiamante/chiamato** include le tre parti distinte seguenti:

- **Funzioni che hanno chiamato**: tutte le funzioni che hanno chiamato una determinata funzione sono elencate nella parte superiore della visualizzazione.

- **Funzione corrente:** la funzione particolare chiamata è elencata nella parte centrale della visualizzazione.

- **Funzioni chiamate da**: tutte le funzioni chiamate dalla funzione specifica sono elencate nella parte inferiore della visualizzazione.

Se una funzione denominata `SyncToNavigator` viene riportata nella parte centrale della visualizzazione, tutte le funzioni che hanno chiamato la funzione `SyncToNavigator` vengono visualizzate nella parte superiore della visualizzazione e tutte le funzioni che sono state chiamate da `SyncToNavigator` vengono elencate nella parte inferiore della visualizzazione.

- È possibile modificare la funzione nella parte centrale della visualizzazione facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione. La visualizzazione verrà quindi automaticamente aggiornata in base alle modifiche.

- Per ordinare i dati, è anche possibile fare clic sui nomi delle colonne.

## <a name="select-call-tree-view"></a>Selezionare la visualizzazione Albero delle chiamate

- Selezionare **Visualizzazione Albero delle chiamate** **nell'elenco a** discesa Visualizzazione corrente. Questa visualizzazione è un albero dell'esecuzione del programma.

   La **visualizzazione Albero delle chiamate** mostra la radice dell'albero come nome del processo. Le funzioni sono i nodi dell'albero. Questa visualizzazione consente di esaminare determinate tracce di chiamata e di analizzare quali tracce hanno il maggiore impatto sulle prestazioni. La visualizzazione è simile alla visualizzazione **Stack di chiamate disponibile durante** il debug. Oltre alle colonne nella visualizzazione Funzione **,** nella **visualizzazione** Albero delle chiamate è presente una colonna aggiuntiva per visualizzare il nome **del modulo**.

- Selezionare **Contrassegni** **nell'elenco a** discesa Visualizzazione corrente.

   Con il profiler XSLT, nel flusso di raccolta dati vengono visualizzati contrassegni con un commento associato. I contrassegni sono parti del codice che dispongono di contatori. Indicando al Profiler XSLT di raccogliere contatori delle prestazioni XSLT, i contatori vengono raccolti ogni volta che viene eseguito uno di questi contrassegni. I dati vengono visualizzati in una tabella contenente **l'ID** contrassegno **,** il nome del contrassegno (**Start Program**, **End Program**) e **il timestamp**. I contrassegni non vengono aggregati e vengono visualizzati in ordine cronologico nella **visualizzazione Contrassegni** del report sulle prestazioni.

## <a name="select-modules-in-the-current-view"></a>Selezionare i moduli nella visualizzazione corrente

- Selezionare **Moduli** **nell'elenco a** discesa Visualizzazione corrente.

   La visualizzazione dei moduli è un elenco completo di tutte le funzioni aggregate a livello di modulo. Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo. Per ordinare i dati è possibile fare clic sul nome di una colonna. Per impostazione predefinita, sono presenti sia valori assoluti che numeri percentuali per Tempo inclusivo trascorso **,** Tempo esclusivo trascorso **,** Tempo inclusivo applicazione **,** Tempo esclusivo applicazione e Numero **di chiamate**.

- Selezionare **Processo** **nell'elenco a** discesa Visualizzazione corrente.

   Nella visualizzazione processo viene visualizzata una tabella che include **l'ID** processo, **il nome** del processo, **l'ora di** inizio e l'ora di **fine.** Per ordinare i dati, è possibile fare clic sui nomi delle colonne.

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Uso della gerarchia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)
