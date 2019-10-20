---
title: Visualizzazione modello di contenuto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 47f4703b90446dc615df350ee0641678996196c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657535"
---
# <a name="content-model-view"></a>Visualizzazione modello di contenuto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La visualizzazione modello di contenuto fornisce una rappresentazione grafica di nodi dello schema locali e globali e dei relativi componenti, inclusi tipi semplici e complessi, elementi, gruppi di modelli, attributi e gruppi di attributi. Non è possibile visualizzare commenti XML e istruzioni di elaborazione nella visualizzazione modello di contenuto. La visualizzazione modello di contenuto contiene due pannelli: un pannello dell' **area di lavoro** che contiene un elenco dei nodi nell'area di [lavoro di progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md)e l'area di progettazione in cui è possibile visualizzare il modello di contenuto dei nodi dello schema selezionati nell' **area di lavoro.** pannello. La visualizzazione modello di contenuto include anche la barra degli strumenti di Progettazione XML Schema e la barra di navigazione.

 Nell'immagine seguente, il pannello Area di lavoro contiene sei nodi dello schema. Il nodo `purchaseOrder` è selezionato nel pannello Area di lavoro e visualizzato nell'area di progettazione.

 ![Visualizzazione modello di contenuto Progettazione XML Schema](../xml-tools/media/xsddesigner-contentmodelview.gif "XSDDesigner_ContentModelView")

## <a name="workspace-panel"></a>Pannello Area di lavoro
 Dopo aver aggiunto i nodi all'area di lavoro, l'elenco di nodi verrà visualizzato nel pannello **area di lavoro** della visualizzazione modello di contenuto. Quando si selezionano i nodi nel pannello dell' **area di lavoro** , vengono visualizzati nell'area di progettazione della visualizzazione modello di contenuto. Per eliminare i nodi dal area, utilizzare la barra degli strumenti di progettazione XSD, il menu di scelta rapida del pannello dell' **area di lavoro** o il tasto CANC.

 Per informazioni sull'aggiunta di nodi, vedere la sezione relativa all'aggiunta di nodi all'area di lavoro nell' [area di lavoro di progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Area di progettazione
 Quando un nodo viene selezionato nel pannello Area di lavoro, viene aggiunto all'area di progettazione della visualizzazione modello di contenuto dove è possibile visualizzare i dettagli del nodo.

 Il modello di contenuto di un nodo viene rappresentato tramite un albero grafico espandibile con elementi e attributi visualizzati come nodi dell'albero. Per impostazione predefinita, viene espanso solo un livello. Le altre informazioni, ad esempio compositor, nomi di tipo, gruppi e altri contenitori, vengono posizionate in una barra verticale (in caso di espansione) lungo gli elementi e gli attributi che includono. Facendo doppio clic su una barra verticale, questa diventa orizzontale e l'albero viene compresso. Facendo doppio clic su una barra orizzontale, questa diventa verticale e l'albero viene espanso. Selezionando la barra verticale verranno selezionati tutti i nodi nel contenitore. Gli espansori saranno visualizzati sulla destra di un nodo quando un elemento può essere espanso o compresso.

 Se l'area di progettazione è vuota, vengono visualizzati l'editor XML, XML Schema Explorer e la filigrana. La *filigrana* è un elenco di collegamenti a tutte le visualizzazioni di progettazione XSD. Se il set di schemi contiene errori, alla fine dell'elenco viene visualizzato il testo: "Usare l'elenco degli errori per visualizzare e correggere gli errori nel set di schemi".

## <a name="breadcrumb-bar"></a>Barra di navigazione
 Tramite la barra di navigazione nella parte inferiore della visualizzazione modello di contenuto viene mostrato dove si trova il nodo selezionato nel set di schemi.

## <a name="context-menus"></a>Menu di scelta rapida
 Quando si fa clic con il pulsante destro del mouse su un elemento nell'area di progettazione o sul pannello Area di lavoro, viene visualizzato un menu di scelta rapida. Nella tabella seguente vengono descritte le opzioni disponibili per l'area di progettazione della visualizzazione modello di contenuto.

|Opzione|Descrizione|
|------------|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|
|**Esporta diagramma come immagine...**|Salva l'area di progettazione in un file XPS.|
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato in XML Schema Explorer sarà selezionato anche nell'editor XML.|
|**Finestra Proprietà**|Apre la finestra **Proprietà** , se non è già aperta. In questa finestra verranno visualizzate le informazioni sul nodo.|

 Nella tabella seguente vengono descritte le opzioni disponibili per il pannello Area di lavoro.

|Opzione|Descrizione|
|------------|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovi dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne la selezione dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Seleziona tutto**|Seleziona tutti i nodi nel pannello Area di lavoro.|
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML. L'elemento selezionato in XML Schema Explorer sarà selezionato anche nell'editor XML.|
|**Finestra Proprietà**|Apre la finestra **Proprietà** , se non è già aperta. In questa finestra verranno visualizzate le informazioni sul nodo.|

## <a name="properties-window"></a>Finestra Proprietà
 Utilizzare il menu di scelta rapida per aprire inizialmente la finestra **Proprietà** . Per impostazione predefinita, la finestra **Proprietà** viene visualizzata nell'angolo inferiore destro di Visual Studio. Quando si fa clic su un nodo di cui viene eseguito il rendering nella visualizzazione modello di contenuto, le proprietà di tale nodo verranno visualizzate nella finestra **Proprietà** .

## <a name="xsd-designer-toolbar"></a>Barra degli strumenti di Progettazione XSD
 I seguenti pulsanti della barra degli strumenti di Progettazione XSD sono abilitati quando la visualizzazione modello di contenuto è attiva.

 ![Barra degli strumenti di progettazione XML Schema](../xml-tools/media/xsdcontentmodelviewtoolbar.gif "XSDContentModelViewToolbar")

|Opzione|Descrizione|
|------------|-----------------|
|**Mostra visualizzazione iniziale**|Passa alla [visualizzazione iniziale](../xml-tools/start-view.md). È possibile accedere a questa visualizzazione tramite i tasti di scelta rapida: **CTRL + 1**.|
|**Mostra visualizzazione modello di contenuto**|Passa alla [visualizzazione modello di contenuto](../xml-tools/content-model-view.md). È possibile accedere a questa visualizzazione tramite i tasti di scelta rapida: **CTRL + 2**.|
|**Mostra visualizzazione grafico**|Passa alla [visualizzazione grafico](../xml-tools/graph-view.md). È possibile accedere a questa visualizzazione tramite i tasti di scelta rapida: **CTRL + 3**.|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovi dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne la selezione dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|

## <a name="panscroll"></a>Panoramica/scorrimento
 È possibile eseguire una panoramica dell'area di progettazione tramite le barre di scorrimento o tenendo premuto il tasto CTRL mentre si fa clic e si trascina il mouse. Quando si esegue una panoramica dell'area di progettazione tramite selezione e trascinamento, il cursore sarà modificato in quattro frecce incrociate che puntano in quattro direzioni.

## <a name="undoredo"></a>Annullamento/ripristino
 La funzionalità di annullamento/ripristino è abilitata nella visualizzazione modello di contenuto per le seguenti azioni:

- Aggiunta di un singolo nodo con trascinamento della selezione.

- Aggiunta di più nodi dalla finestra dei risultati della ricerca in Schema Explorer.

- Aggiunta di nodi dalla visualizzazione iniziale.

- Eliminazione di uno o più nodi.

## <a name="zoom"></a>Zoom
 Lo zoom è disponibile nell'angolo inferiore destro della visualizzazione modello di contenuto.

 È possibile controllare lo zoom nei seguenti modi:

- Tenendo premuto il tasto CTRL e ruotando la rotellina del mouse quando il mouse si trova sull'area di visualizzazione modello di contenuto.

- Tramite il dispositivo di scorrimento. Il dispositivo di scorrimento mostra il livello di zoom corrente.

  Il dispositivo di scorrimento dello zoom è opaco quando lo si seleziona, si posiziona il mouse su di esso o si usa il tasto CTRL insieme alla rotellina del mouse per ingrandire; altrimenti è trasparente.

## <a name="xml-editor-integration"></a>Integrazione dell'editor XML
 È possibile passare dalla Progettazione XSD all'editor XML tramite il menu di scelta rapida.

 Se si apportano modifiche al set di schemi nell'editor XML, le modifiche saranno sincronizzate nella visualizzazione modello di contenuto. Per ulteriori informazioni, vedere [integrazione con l'editor XML](../xml-tools/integration-with-xml-editor.md).

## <a name="see-also"></a>Vedere anche
 [Area di lavoro di Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md)
