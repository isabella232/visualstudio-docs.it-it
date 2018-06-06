---
title: Visualizzazione del modello di contenuto di Progettazione XML Schema
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0d7f04c482149cbc063a3788dd6be44c643bae6a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/04/2018
ms.locfileid: "34751793"
---
# <a name="content-model-view"></a>Visualizzazione modello di contenuto

La visualizzazione modello di contenuto fornisce una rappresentazione grafica di nodi dello schema locali e globali e dei relativi componenti, inclusi tipi semplici e complessi, elementi, gruppi di modelli, attributi e gruppi di attributi. Non è possibile visualizzare commenti XML e istruzioni di elaborazione nella visualizzazione modello di contenuto. La visualizzazione modello di contenuto contiene due pannelli: un **dell'area di lavoro** pannello che contiene un elenco dei nodi il [area di lavoro della finestra di progettazione di XML schema](../xml-tools/xml-schema-designer-workspace.md)e l'area di progettazione in cui è possibile visualizzare il modello di contenuto dello schema i nodi selezionati nel **dell'area di lavoro** pannello. La visualizzazione modello di contenuto include anche la barra degli strumenti di Progettazione XML Schema e la barra di navigazione.

 Nella figura seguente, il **dell'area di lavoro** pannello contiene sei nodi dello schema. Il `purchaseOrder` selezionato nel nodo il **dell'area di lavoro** pannello e viene visualizzato nell'area di progettazione.

 ![Visualizzazione del modello di contenuto di Progettazione XML Schema](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Pannello area di lavoro

 Dopo avere aggiunto nodi all'area di lavoro, l'elenco dei nodi verrà inclusi il **dell'area di lavoro** pannello della visualizzazione modello di contenuto. Quando si seleziona i nodi di **dell'area di lavoro** pannello, vengono visualizzati nell'area di progettazione della visualizzazione modello di contenuto. Per eliminare i nodi dall'area di lavoro, utilizzare la barra degli strumenti progettazione XSD, il **dell'area di lavoro** menu di scelta rapida pannello o il **eliminare** chiave.

 Per informazioni sull'aggiunta di nodi, vedere la sezione "Aggiunta di nodi all'area di lavoro" in [area di lavoro della finestra di progettazione di XML schema](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Area di progettazione

 Quando viene selezionato un nodo nel **dell'area di lavoro** pannello, aggiungerlo all'area di progettazione visualizzazione modello di contenuto in cui è possibile visualizzare i dettagli del nodo.

 Il modello di contenuto di un nodo viene rappresentato tramite un albero grafico espandibile con elementi e attributi visualizzati come nodi dell'albero. Per impostazione predefinita, viene espanso solo un livello. Le altre informazioni, ad esempio compositor, nomi di tipo, gruppi e altri contenitori, vengono posizionate in una barra verticale (in caso di espansione) lungo gli elementi e gli attributi che includono. Facendo doppio clic su una barra verticale, questa diventa orizzontale e l'albero viene compresso. Facendo doppio clic su una barra orizzontale, questa diventa verticale e l'albero viene espanso. Selezionando la barra verticale verranno selezionati tutti i nodi nel contenitore. Gli espansori vengono visualizzati nella parte destra di un nodo se un elemento può essere espansi o compressi.

 Se l'area di progettazione è vuota, l'Editor XML, il **XML Schema Explorer**, e vengono visualizzate la filigrana. Il *filigrana* è un elenco di collegamenti a tutte le visualizzazioni di progettazione XSD. Se il set di schemi contiene errori, alla fine dell'elenco viene visualizzato il testo: "Usare l'elenco degli errori per visualizzare e correggere gli errori nel set di schemi".

## <a name="breadcrumb-bar"></a>Barra di navigazione

 Tramite la barra di navigazione nella parte inferiore della visualizzazione modello di contenuto viene mostrato dove si trova il nodo selezionato nel set di schemi.

## <a name="context-menus"></a>Menu di scelta rapida

 Quando si fa clic su un elemento nell'area di progettazione o **dell'area di lavoro** pannello, viene visualizzato un menu di scelta rapida. Nella tabella seguente vengono descritte le opzioni disponibili per l'area di progettazione della visualizzazione modello di contenuto.

|Opzione|Descrizione|
|------------|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|
|**Esporta diagramma come immagine**|Salva l'area di progettazione in un file XPS.|
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato nel **XML Schema Explorer** sia selezionata nell'Editor XML.|
|**Finestra Proprietà**|Apre il **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|

 Nella tabella seguente vengono descritte le opzioni disponibili per il **dell'area di lavoro** pannello.

|Opzione|Descrizione|
|------------|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovere dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovere tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Seleziona tutto**|Seleziona tutti i nodi il **dell'area di lavoro** pannello.|
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato nel **XML Schema Explorer** sia selezionata nell'Editor XML.|
|**Finestra Proprietà**|Apre il **proprietà** finestra (se non è già aperto). In questa finestra verranno visualizzate le informazioni sul nodo.|

## <a name="properties-window"></a>Finestra Proprietà

 Utilizzare il menu di scelta rapida per aprire inizialmente la **proprietà** finestra. Per impostazione predefinita, il **proprietà** finestra viene visualizzata nell'angolo inferiore destro di Visual Studio. Quando si fa clic su un nodo che viene eseguito il rendering nella visualizzazione modello di contenuto, le proprietà di tale nodo vengono visualizzate nella **proprietà** finestra.

## <a name="xsd-designer-toolbar"></a>Barra degli strumenti progettazione XSD

 I seguenti pulsanti della barra degli strumenti di Progettazione XSD sono abilitati quando la visualizzazione modello di contenuto è attiva.

 ![Barra degli strumenti di Progettazione XML Schema](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opzione|Descrizione|
|------------|-----------------|
|**Mostra visualizzazione iniziale**|Consente di attivare il [vista](../xml-tools/start-view.md). Questa vista è accessibile tramite il tasto di scelta rapida: **Ctrl**+**1**.|
|**Mostra visualizzazione modello di contenuto**|Consente di attivare il [visualizzazione modello di contenuto](../xml-tools/content-model-view.md). Questa vista è accessibile tramite il tasto di scelta rapida: **Ctrl**+**2**.|
|**Mostra visualizzazione grafico**|Consente di attivare il [visualizzazione grafica](../xml-tools/graph-view.md). Questa vista è accessibile tramite il tasto di scelta rapida: **Ctrl**+**3**.|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovere dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovere tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|

## <a name="panscroll"></a>Panoramica/scorrimento

 È possibile eseguire una panoramica di area di progettazione tramite le barre di scorrimento o tenendo premuto il **Ctrl** mentre si fa clic e trascinare il mouse. Quando si esegue una panoramica di area di progettazione tramite selezione e trascinamento, il cursore assuma quattro frecce incrociate che puntano in quattro direzioni.

## <a name="undoredo"></a>Annullamento/ripristino

 La funzionalità di annullamento/ripristino è abilitata nella visualizzazione modello di contenuto per le seguenti azioni:

-   Aggiunta di un singolo nodo tramite trascinamento.

-   Aggiunta di più nodi dalla finestra dei risultati della ricerca in Schema Explorer.

-   Aggiunta di nodi dalla visualizzazione iniziale.

-   Eliminazione di uno o più nodi.

## <a name="zoom"></a>Zoom

 Lo zoom è disponibile nell'angolo inferiore destro della visualizzazione modello di contenuto.

 È possibile controllare lo zoom nei seguenti modi:

-   Tenendo il **Ctrl** chiave e ruotando il mouse wheel quando il mouse è posizionato sull'area di visualizzazione modello di contenuto.

-   Tramite il dispositivo di scorrimento. Il dispositivo di scorrimento mostra il livello di zoom corrente.

Il dispositivo di scorrimento dello Zoom è opaco quando lo selezionarlo, passare il mouse su di esso o utilizzare **Ctrl** con la rotellina del mouse per ingrandire; tutte le altre volte, altrimenti è trasparente.

## <a name="xml-editor-integration"></a>Integrazione dell'editor XML

 È possibile passare avanti e indietro tra i **progettazione XSD** all'editor XML tramite il menu di scelta rapida.

 Se si apportano modifiche allo schema nell'Editor XML le modifiche vengono sincronizzate nella visualizzazione modello di contenuto. Per altre informazioni, vedere [integrato con l'editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vedere anche

- [Area di lavoro di Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md)