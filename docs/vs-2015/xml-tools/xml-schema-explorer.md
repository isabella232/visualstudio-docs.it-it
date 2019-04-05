---
title: XML Schema Explorer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 59f2c4ba05b0e802f1daa303db0646a94f36fd31
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970119"
---
# <a name="xml-schema-explorer"></a>XML Schema Explorer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
XML Schema Explorer è integrato con Microsoft Visual Studio e con l'editor XML per consentire di usare gli schemi XML Schema Definition Language (XSD). Quando si apre un file di XML Schema, il **del Set di schemi** nodo viene visualizzato nel XML Schema Explorer. In XML Schema Explorer vengono visualizzati anche tutti gli schemi inclusi, importati o ridefiniti per il file di destinazione e qualsiasi file a cui viene fatto riferimento tramite un'istruzione `include` o `import`.  
  
 XML Schema Explorer consente di eseguire le operazioni seguenti:  
  
- Ottenere una rapida panoramica del set di schemi.  
  
- Esplorare e spostarsi all'interno dell'albero.  
  
- Eseguire ricerche per parola chiave e specifiche dello schema. Per altre informazioni, vedere [la ricerca del Set di schemi](../xml-tools/searching-the-schema-set.md).  
  
- Aggiungere i risultati della ricerca alla visualizzazione grafico o alla visualizzazione modello di contenuto  
  
- Ordinare l'albero in base a nome, tipo o ordine dei documenti. Per altre informazioni, vedere [ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
- Aprire l'editor XML e passare ai percorsi del codice nel file XSD. Per altre informazioni, vedere [integrazione con l'Editor XML](../xml-tools/integration-with-xml-editor.md).  
  
- Generare codice XML di esempio per gli elementi globali.  
  
  XML Schema Explorer fornisce una visualizzazione gerarchica del set di schemi tramite una visualizzazione ad albero. XML Schema Explorer offre inoltre funzionalità di ricerca, filtro, navigazione e ordinamento. Per accedere a XML Schema Explorer, eseguire una delle operazioni seguenti:  
  
- Se si usa la [visualizzazione iniziale](../xml-tools/start-view.md), fare clic sui **XML Schema Explorer** collegamento.  
  
- Se si usa la [visualizzazione grafico](../xml-tools/graph-view.md) o nella [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) e dispone di nodi nell'area di lavoro, usare il menu di scelta rapida per selezionare XML Schema Explorer.  
  
- È anche possibile selezionare il Explorerfrom dello Schema XML di **vista** menu.  
  
- È possibile accedere il XML Schema Explorerfrom un file con estensione vb che dispone di un XML di Visual Basic letterale associata a un file con estensione XSD. Per visualizzare lo schema impostato in XML Schema Explorer, fare clic con il pulsante destro su un nodo XML in un valore letterale XML o un'importazione di spazi dei nomi XML e selezionare il **Mostra in Schema Explorer** comando. Per altre informazioni, vedere [integrazione di valori letterali XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## <a name="tree-view"></a>Visualizzazione albero  
 In XML Schema Explorer le informazioni sul set di schemi precompilati vengono visualizzate in una struttura ad albero. La struttura ad albero è organizzata come segue:  
  
- Al livello principale è presente il nodo del set di schemi.  
  
- Il secondo livello contiene gli spazi dei nomi.  
  
- Nel terzo livello sono presenti i file.  
  
- Il quarto livello contiene i nodi globali e può includere elementi, gruppi, tipi complessi, tipi semplici, attributi, gruppi di attributi e istruzioni `include`, `import` e `redefine`.  
  
  Di seguito viene riportato un esempio di struttura ad albero:  
  
  ![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## <a name="selection-and-activation"></a>Selezione e attivazione  
 Per evidenziare e selezionare un nodo, fare clic una volta in Schema Explorer.  
  
 Per attivare un nodo, fare doppio clic oppure premere **invio** quando si seleziona il nodo.  
  
-   L'attivazione di un nodo consente di aprire il file in cui questo nodo è definito (se non è già aperto) e di selezionare il nodo nel file.  
  
-   L'attivazione di un nodo di file consente di aprire il file selezionato (se non è già aperto) e di evidenziare il nodo `<schema>`.  
  
-   L'attivazione di un nodo set di schemi o spazio dei nomi non esegue alcuna operazione.  
  
## <a name="draging-and-dropping-nodes"></a>Trascinamento e rilascio di nodi  
 È possibile trascinare nodi globali, nodi di file e nodi spazio dei nomi su una visualizzazione di Progettazione XSD. Se la visualizzazione corrente è il [visualizzazione iniziale](../xml-tools/start-view.md), trascinare un nodo sulla visualizzazione verrà aperto il [visualizzazione grafico](../xml-tools/graph-view.md). Se la visualizzazione corrente è il [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) o visualizzazione grafico, la visualizzazione non cambierà quando si elimina un nodo su di esso.  
  
 Eliminazione di file sulla visualizzazione aggiungerà tutti i nodi globali nel file per il [area di lavoro di progettazione XSD](../xml-tools/xml-schema-designer-workspace.md). Il rilascio degli spazi dei nomi sulla visualizzazione aggiungerà tutti i nodi globali contenuti nello spazio dei nomi all'area di lavoro. L'area di lavoro è condivisa da tutte le visualizzazioni.  
  
 Non è possibile trascinare e rilasciare nodi locali o importazioni.  
  
## <a name="in-this-section"></a>In questa sezione  
  
-   [Ricerche nel set di schemi](../xml-tools/searching-the-schema-set.md)  
  
-   [Ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Integrazione di valori letterali XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Aggiungere nodi all'area di lavoro da XML Schema Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)
