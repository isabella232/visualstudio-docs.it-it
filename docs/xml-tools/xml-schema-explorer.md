---
title: XML Schema Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ac977be83440bfd3e0b1436635bbeb9c39c0ec
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915986"
---
# <a name="xml-schema-explorer"></a>XML Schema Explorer

Il **XML Schema Explorer** è integrato con Microsoft Visual Studio e l'Editor XML per consentire di lavorare con schemi XML Schema definition language (XSD). Quando si apre un file di XML Schema, il **del Set di schemi** verrà visualizzato nel nodo il **XML Schema Explorer**. Tutti gli schemi inclusi, importati o ridefiniti per il file di destinazione, nonché tutti i file che vengono fatto riferimento tramite un `include` oppure `import` istruzione, vengono visualizzati anche nella **XML Schema Explorer**.

 Il **XML Schema Explorer** consente di eseguire le operazioni seguenti:

-   Ottenere una rapida panoramica del set di schemi.

-   Esplorare e spostarsi all'interno dell'albero.

-   Eseguire ricerche per parola chiave e specifiche dello schema. Per altre informazioni, vedere [ricerche nel set di schemi](../xml-tools/searching-the-schema-set.md).

-   Aggiungere i risultati della ricerca alla visualizzazione grafico o visualizzazione modello di contenuto

-   Ordinare l'albero in base a nome, tipo o ordine dei documenti. Per altre informazioni, vedere [ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

-   Aprire l'editor XML e passare ai percorsi del codice nel file XSD. Per altre informazioni, vedere [integrazione con l'Editor XML](../xml-tools/integration-with-xml-editor.md).

-   Generare codice XML di esempio per gli elementi globali.

Il **XML Schema Explorer** fornisce una visualizzazione gerarchica del set di schemi tramite una visualizzazione albero. Il **XML Schema Explorer** fornisce inoltre ricerca, filtro, navigazione e l'ordinamento. Per l'accesso di **XML Schema Explorer**, effettuare una delle operazioni seguenti:

-   Se si usa la [visualizzazione iniziale](../xml-tools/start-view.md), fare clic sui **XML Schema Explorer** collegamento.

-   Se si usa il [visualizzazione grafico](../xml-tools/graph-view.md) o nella [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) e dispone di nodi nell'area di lavoro, usare il menu di scelta rapida per selezionare il **XML Schema Explorer**.

-   È anche possibile selezionare i **XML Schema Explorer** dalle **visualizzazione** menu.

-   È possibile accedere la **XML Schema Explorer** da un *vb* file con un valore letterale XML di Visual Basic associato un *XSD* file. Per visualizzare lo schema impostati nella **XML Schema Explorer**, fare doppio clic su un nodo XML in un valore letterale XML o un'importazione di spazi dei nomi XML e selezionare il **Mostra in Schema Explorer** comando. Per altre informazioni, vedere [valori letterali di integrazione di XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Visualizzazione albero
 Il **XML Schema Explorer** schema consente di visualizzare precompilati imposta le informazioni in una struttura ad albero. La struttura ad albero è organizzata come segue:

-   Al livello principale è presente il nodo del set di schemi.

-   Il secondo livello contiene gli spazi dei nomi.

-   Nel terzo livello sono presenti i file.

-   Il quarto livello contiene i nodi globali e può includere elementi, gruppi, tipi complessi, tipi semplici, attributi, gruppi di attributi e istruzioni `include`, `import` e `redefine`.

Di seguito viene riportato un esempio di struttura ad albero:

![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Selezione e attivazione
 Per evidenziare e selezionare un nodo, fare clic una volta in Schema Explorer.

 Per attivare un nodo, fare doppio clic oppure premere **invio** quando si seleziona il nodo.

-   L'attivazione di un nodo consente di aprire il file in cui questo nodo è definito (se non è già aperto) e di selezionare il nodo nel file.

-   L'attivazione di un nodo di file consente di aprire il file selezionato (se non è già aperto) e di evidenziare il nodo `<schema>`.

-   L'attivazione di un nodo set di schemi o spazio dei nomi non esegue alcuna operazione.

## <a name="drag-and-drop-nodes"></a>Trascinare e rilasciare nodi
 È possibile trascinare e rilasciare nodi globali, nodi di file e nodi spazio dei nomi su una visualizzazione di Progettazione XSD. Se la visualizzazione corrente è il [visualizzazione iniziale](../xml-tools/start-view.md), trascinare un nodo sulla visualizzazione verrà aperto il [visualizzazione grafico](../xml-tools/graph-view.md). Se la visualizzazione corrente è il [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) o visualizzazione grafico, la visualizzazione non cambierà quando si elimina un nodo su di esso.

 Eliminazione di file sulla visualizzazione aggiungerà tutti i nodi globali nel file per il [dell'area di lavoro di progettazione XSD](../xml-tools/xml-schema-designer-workspace.md). Il rilascio degli spazi dei nomi sulla visualizzazione aggiungerà tutti i nodi globali contenuti nello spazio dei nomi all'area di lavoro. L'area di lavoro è condivisa da tutte le visualizzazioni.

 Non è possibile trascinare e rilasciare nodi locali o importazioni.

## <a name="see-also"></a>Vedere anche

- [Procedura: Aggiungere nodi all'area di lavoro da XML Schema Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)