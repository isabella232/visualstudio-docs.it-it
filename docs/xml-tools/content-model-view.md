---
title: Visualizzazione del modello di contenuto di Progettazione XML Schema
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b858d0b5fb8aab1dabb90ae47d234869412adf2e
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525791"
---
# <a name="content-model-view"></a>Visualizzazione modello di contenuto

La visualizzazione modello di contenuto fornisce una rappresentazione grafica di nodi dello schema locali e globali e dei relativi componenti, inclusi tipi semplici e complessi, elementi, gruppi di modelli, attributi e gruppi di attributi. Non è possibile visualizzare commenti XML e istruzioni di elaborazione nella visualizzazione modello di contenuto. Dalla visualizzazione modello di contenuto contiene due pannelli: un **dell'area di lavoro** pannello che contiene un elenco dei nodi la [dell'area di lavoro XML schema della finestra di progettazione](../xml-tools/xml-schema-designer-workspace.md)e l'area di progettazione in cui è possibile visualizzare il modello di contenuto dello schema i nodi selezionati nel **dell'area di lavoro** pannello. La visualizzazione modello di contenuto include anche la barra degli strumenti di Progettazione XML Schema e la barra di navigazione.

Nell'immagine seguente, il **dell'area di lavoro** pannello contiene sei nodi dello schema. Il `purchaseOrder` nodo selezionato nel **dell'area di lavoro** pannello e viene visualizzato nella finestra di progettazione.

![Visualizzazione del modello di contenuto di Progettazione XML Schema](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Pannello area di lavoro

Dopo avere aggiunto nodi all'area di lavoro, verrà visualizzato l'elenco di nodi nel **dell'area di lavoro** pannello della visualizzazione modello di contenuto. Quando si seleziona i nodi le **dell'area di lavoro** pannello vengono visualizzati nell'area di progettazione della visualizzazione modello di contenuto. Per eliminare i nodi dall'area di lavoro, usare la barra degli strumenti progettazione XSD, il **dell'area di lavoro** menu di scelta rapida del pannello, o il **eliminare** chiave.

Per informazioni sull'aggiunta di nodi, vedere la sezione "Aggiunta di nodi all'area di lavoro" in [area di lavoro della finestra di progettazione dello schema XML](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Nell'area di progettazione

Quando si seleziona un nodo nel **dell'area di lavoro** pannello, aggiungerlo all'area di progettazione visualizzazione modello di contenuto in cui è possibile visualizzare i dettagli del nodo.

Il modello di contenuto di un nodo viene rappresentato tramite un albero grafico espandibile con elementi e attributi visualizzati come nodi dell'albero. Per impostazione predefinita, viene espanso solo un livello. Le altre informazioni, ad esempio compositor, nomi di tipo, gruppi e altri contenitori, vengono posizionate in una barra verticale (in caso di espansione) lungo gli elementi e gli attributi che includono. Facendo doppio clic su una barra verticale, questa diventa orizzontale e l'albero viene compresso. Facendo doppio clic su una barra orizzontale, questa diventa verticale e l'albero viene espanso. Selezionando la barra verticale, verranno selezionati tutti i nodi nel contenitore. Gli espansori vengono visualizzati a destra di un nodo, se un elemento può essere espansi o compressi.

Se l'area di progettazione è vuota, l'editor XML, il **XML Schema Explorer**, e vengono visualizzate la filigrana. Il *filigrana* è riportato un elenco di collegamenti a tutte le visualizzazioni di progettazione XSD. Se il set di schemi contiene errori, alla fine dell'elenco viene visualizzato il testo seguente: : Usare l'elenco errori per visualizzare e correggere gli errori nel set di".

## <a name="breadcrumb-bar"></a>Barra di navigazione

Tramite la barra di navigazione nella parte inferiore della visualizzazione modello di contenuto viene mostrato dove si trova il nodo selezionato nel set di schemi.

## <a name="context-menus"></a>Menu di scelta rapida

Quando si fare doppio clic su un elemento nell'area di progettazione oppure **dell'area di lavoro** pannello viene visualizzato un menu di scelta rapida. Nella tabella seguente vengono descritte le opzioni disponibili per l'area di progettazione della visualizzazione modello di contenuto.

|Opzione|Descrizione|
|-|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|
|**Esporta diagramma come immagine**|Salva l'area di progettazione in un file XPS.|
|**Visualizza codice**|Apre il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato nel **XML Schema Explorer** viene selezionato anche nell'editor XML.|
|**Finestra Proprietà**|Apre la **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|

Nella tabella seguente vengono descritte le opzioni disponibili per il **dell'area di lavoro** pannello.

|Opzione|Descrizione|
|-|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Cancella l'area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovere dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Seleziona tutto**|Seleziona tutti i nodi le **dell'area di lavoro** pannello.|
|**Visualizza codice**|Apre il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato nel **XML Schema Explorer** viene selezionato anche nell'editor XML.|
|**Finestra Proprietà**|Apre la **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|

## <a name="properties-window"></a>Finestra Proprietà

Usare il menu di scelta rapida (contesto) per aprire inizialmente la **proprietà** finestra. Per impostazione predefinita, il **proprietà** finestra viene visualizzata nell'angolo inferiore destro di Visual Studio. Quando si fa clic su un nodo che viene eseguito il rendering nella visualizzazione modello di contenuto, le proprietà di tale nodo vengono visualizzate nei **proprietà** finestra.

## <a name="xsd-designer-toolbar"></a>Barra degli strumenti progettazione XSD

I seguenti pulsanti della barra degli strumenti di Progettazione XSD sono abilitati quando la visualizzazione modello di contenuto è attiva.

![Barra degli strumenti di Progettazione XML Schema](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opzione|Descrizione|
|-|-----------------|
|**Mostra visualizzazione iniziale**|Consente di attivare i [avvio della vista](../xml-tools/start-view.md). In questa vista sono accessibili tramite il tasto di scelta rapida: **Ctrl**+**1**.|
|**Mostra visualizzazione modello di contenuto**|Consente di attivare i [visualizzazione modello di contenuto](../xml-tools/content-model-view.md). In questa vista sono accessibili tramite il tasto di scelta rapida: **Ctrl**+**2**.|
|**Mostra visualizzazione grafico**|Consente di attivare i [visualizzazione grafico](../xml-tools/graph-view.md). In questa vista sono accessibili tramite il tasto di scelta rapida: **Ctrl**+**3**.|
|**Cancella l'area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovere dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|

## <a name="panscroll"></a>Panoramica/scorrimento

È possibile eseguire una panoramica di area di progettazione tramite le barre di scorrimento o tenendo il **Ctrl** mentre si fa clic e trascinare il mouse. Quando si pan in area di progettazione tramite selezione e trascinamento, il cursore cambia in quattro frecce incrociate che puntano in quattro direzioni.

## <a name="undoredo"></a>Annullamento/ripristino

La funzionalità di annullamento/ripristino è abilitata nella visualizzazione modello di contenuto per le seguenti azioni:

-   Aggiunta di un singolo nodo tramite trascinamento.

-   Aggiunta di più nodi dalla finestra dei risultati della ricerca in Schema Explorer.

-   Aggiunta di nodi dalla visualizzazione iniziale.

-   Eliminazione di uno o più nodi.

## <a name="zoom"></a>Zoom

Lo zoom è disponibile nell'angolo inferiore destro della visualizzazione modello di contenuto.

È possibile controllare lo zoom nei seguenti modi:

-   Tenendo il **Ctrl** chiave e il puntatore del mouse in rotazione rotellina quando il mouse è posizionato sull'area di visualizzazione modello di contenuto.

-   Tramite il dispositivo di scorrimento. Il dispositivo di scorrimento mostra il livello di zoom corrente.

Il dispositivo di scorrimento dello Zoom è opaco quando lo selezionarlo, passare il mouse su di essa o usare **Ctrl** con la rotellina del mouse per ingrandire; tutte le altre volte, è trasparente.

## <a name="xml-editor-integration"></a>Integrazione dell'editor XML

È possibile spostarsi avanti e indietro tra i **progettazione XSD** all'editor XML tramite il menu di scelta rapida (contesto).

Se si apportano modifiche allo schema nell'editor XML le modifiche vengono sincronizzate nella visualizzazione modello di contenuto. Per altre informazioni, vedere [integrazione con l'editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vedere anche

- [Area di lavoro di Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md)