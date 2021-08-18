---
title: Visualizzazione Albero delle chiamate | Microsoft Docs
description: Informazioni sulla visualizzazione Albero delle chiamate, che visualizza i percorsi di esecuzione delle funzioni attraversati nell'applicazione profilata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.calltree
helpviewer_keywords:
- Call Tree view
- profiling tools reports, Call Tree view
- performance reports, Call Tree view
- profiling tools, Call Tree view
ms.assetid: b2dbc033-bf95-4d10-8e51-f9462979133e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1bf12a7a4925493fc6bb978bc75da963c0436938
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131846"
---
# <a name="call-tree-view"></a>Visualizzazione albero delle chiamate
La visualizzazione Albero delle chiamate consente di visualizzare i percorsi di esecuzione della funzione usati nell'applicazione profilata. La radice dell'albero è il punto di ingresso nell'applicazione o nel componente. Per ogni nodo della funzione vengono elencate tutte le funzioni chiamate e i dati delle prestazioni delle chiamate di funzione.

 Nella visualizzazione Albero delle chiamate è anche possibile espandere ed evidenziare il percorso di esecuzione di una funzione che ha richiesto più tempo o che è stata campionata con maggiore frequenza. Per visualizzare il percorso più oneroso a livello di prestazioni, fare clic con il pulsante destro del mouse sulla funzione e scegliere **Espandi percorso critico**.

 Ogni processo nell'esecuzione della profilatura viene visualizzato come nodo radice. Per impostare il nodo iniziale della visualizzazione Albero delle chiamate, fare clic con il pulsante destro del mouse sul nodo che si vuole impostare come nodo iniziale e selezionare **Imposta radice**.

 Quando imposti il nodo radice, elimini dalla visualizzazione tutte le altre voci ad eccezione del sottoalbero del nodo selezionato. È possibile reimpostare il nodo radice sul nodo che si stava visualizzando. Nella finestra della visualizzazione Albero delle chiamate fare clic con il pulsante destro del mouse e selezionare **Reimposta radice**.

 La visualizzazione Albero delle chiamate può essere personalizzata per aggiungere o rimuovere colonne. Fare clic con il pulsante destro del mouse sulla **barra del titolo Nome colonna** e selezionare **Aggiungi/Rimuovi colonne**.

 La visualizzazione Albero delle chiamate può essere configurata per la riduzione del rumore limitando la quantità di dati presentati. Con la riduzione del rumore, i problemi di prestazioni nella visualizzazione sono più evidenti. Quando i problemi di prestazioni sono più facili da trovare anche l'analisi è più semplice. Per altre informazioni, vedere [Procedura: Configurare la riduzione del rumore nelle visualizzazioni report](../profiling/how-to-configure-noise-reduction-in-report-views.md).

> [!NOTE]
> Se la riduzione del rumore è configurata per visualizzare un avviso quando viene attivata, nel report viene visualizzata una barra informazioni.

 Per altre informazioni sulle definizioni delle colonne nella visualizzazione Albero delle chiamate, vedere gli argomenti seguenti:

- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-sampling-data.md)

- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-instrumentation-data.md)

- [Visualizzazione Albero delle chiamate: campionamento](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

- [Visualizzazione Albero delle chiamate](../profiling/call-tree-view-contention-data.md)

## <a name="see-also"></a>Vedi anche
- [Visualizzazioni dei report sulle prestazioni](../profiling/performance-report-views.md)
- [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)
- [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)
