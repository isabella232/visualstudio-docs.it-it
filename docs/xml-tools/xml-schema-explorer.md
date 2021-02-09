---
title: XML Schema Explorer
description: Informazioni sulle funzionalità di XML Schema Explorer integrate con Visual Studio e l'editor XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4b16c1baa039a2f1e812d35e7a4994ffc0d5e5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874886"
---
# <a name="xml-schema-explorer"></a>XML Schema Explorer

**XML Schema Explorer** è integrato con Microsoft Visual Studio e l'editor XML per consentire l'utilizzo di schemi XSD (XML Schema Definition Language). Quando si apre un file di XML Schema, il nodo del **set di schemi** viene visualizzato in **XML Schema Explorer**. Tutti gli schemi inclusi, importati o ridefiniti per il file di destinazione, nonché tutti i file a cui viene fatto riferimento tramite `include` un' `import` istruzione o, vengono visualizzati anche in **XML Schema Explorer**.

**XML Schema Explorer** consente di eseguire le operazioni seguenti:

- Ottenere una rapida panoramica del set di schemi.

- Esplorare e spostarsi all'interno dell'albero.

- Eseguire ricerche per parola chiave e specifiche dello schema. Per ulteriori informazioni, vedere [la pagina relativa alla ricerca del set di schemi](../xml-tools/searching-the-schema-set.md).

- Aggiungere i risultati della ricerca alla visualizzazione grafico o al modello di contenuto

- Ordinare l'albero in base a nome, tipo o ordine dei documenti. Per ulteriori informazioni, vedere [ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).

- Aprire l'editor XML e passare a percorsi di codice nel file XSD. Per ulteriori informazioni, vedere [integrazione con l'editor XML](../xml-tools/integration-with-xml-editor.md).

- Generare codice XML di esempio per gli elementi globali.

**XML Schema Explorer** fornisce una visualizzazione gerarchica del set di schemi tramite una visualizzazione struttura ad albero. **XML Schema Explorer** fornisce inoltre funzionalità di ricerca, filtro, navigazione e ordinamento. Per accedere a **XML Schema Explorer**, eseguire una delle operazioni seguenti:

- Nella [visualizzazione iniziale](../xml-tools/start-view.md)fare clic sul collegamento **XML Schema Explorer** .

- Se si è nella [visualizzazione grafico](../xml-tools/graph-view.md) o nella [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) e sono presenti nodi nell'area di lavoro, utilizzare il menu di scelta rapida (clic con il pulsante destro del mouse) per selezionare **XML Schema Explorer**.

- È inoltre possibile selezionare **XML Schema Explorer** dal menu **Visualizza** .

- È possibile accedere a **XML Schema Explorer** da un file con *estensione VB* che dispone di un Visual Basic valore letterale XML associato a un file *xsd* . Per visualizzare il set di schemi in **XML Schema Explorer**, fare clic con il pulsante destro del mouse su un nodo XML in un valore letterale XML o su un'importazione di spazi dei nomi XML e selezionare il comando **Mostra in Esplora schema** . Per ulteriori informazioni, vedere [integrazione di valori letterali XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).

## <a name="tree-view"></a>Visualizzazione ad albero
In **XML Schema Explorer** vengono visualizzate le informazioni sul set di schemi precompilate in una struttura ad albero. La struttura ad albero è organizzata come segue:

- Al livello principale è presente il nodo del set di schemi.

- Il secondo livello contiene gli spazi dei nomi.

- Nel terzo livello sono presenti i file.

- Il quarto livello contiene i nodi globali e può includere elementi, gruppi, tipi complessi, tipi semplici, attributi, gruppi di attributi e istruzioni `include`, `import` e `redefine`.

Di seguito viene riportato un esempio di struttura ad albero:

![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif)

## <a name="selection-and-activation"></a>Selezione e attivazione
Per evidenziare e selezionare un nodo, fare clic una volta in Schema Explorer.

Per attivare un nodo, fare doppio clic su di esso oppure premere **invio** quando si seleziona il nodo.

- L'attivazione di un nodo consente di aprire il file in cui questo nodo è definito (se non è già aperto) e di selezionare il nodo nel file.

- L'attivazione di un nodo di file consente di aprire il file selezionato (se non è già aperto) e di evidenziare il nodo `<schema>`.

- L'attivazione di un nodo set di schemi o spazio dei nomi non esegue alcuna operazione.

## <a name="drag-and-drop-nodes"></a>Trascinare i nodi
È possibile trascinare nodi globali, nodi di file e nodi spazio dei nomi su una visualizzazione di Progettazione XSD. Se la visualizzazione corrente è la [visualizzazione iniziale](../xml-tools/start-view.md), il trascinamento di un nodo nella visualizzazione consente di aprire la [visualizzazione grafico](../xml-tools/graph-view.md). Se la visualizzazione corrente è la visualizzazione [modello di contenuto](../xml-tools/content-model-view.md) o la visualizzazione grafico, la visualizzazione non verrà modificata quando si rilascia un nodo.

Se si eliminano i file nella vista, tutti i nodi globali del file vengono aggiunti all' [area di lavoro di progettazione XSD](../xml-tools/xml-schema-designer-workspace.md). Il rilascio degli spazi dei nomi sulla visualizzazione aggiungerà tutti i nodi globali contenuti nello spazio dei nomi all'area di lavoro. L'area di lavoro è condivisa da tutte le visualizzazioni.

 Non è possibile trascinare e rilasciare nodi locali o importazioni.

## <a name="see-also"></a>Vedi anche

- [Procedura: aggiungere nodi all'area di lavoro da XML Schema Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
