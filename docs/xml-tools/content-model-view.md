---
title: Visualizzazione del modello di contenuto di Progettazione XML Schema
description: Informazioni sulla visualizzazione modello di contenuto in Progettazione schema XAML che fornisce una rappresentazione grafica dei nodi dello schema locali e globali e dei relativi componenti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: e8db7c7d-31cf-479e-9dcc-299759891795
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: d2f9f642ef030778f94fd621b3eb122624e6586b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122091955"
---
# <a name="content-model-view"></a>Visualizzazione modello di contenuto

La visualizzazione modello di contenuto fornisce una rappresentazione grafica di nodi dello schema locali e globali e dei relativi componenti, inclusi tipi semplici e complessi, elementi, gruppi di modelli, attributi e gruppi di attributi. Non è possibile visualizzare commenti XML e istruzioni di elaborazione nella visualizzazione modello di contenuto. La visualizzazione modello di contenuto  contiene due pannelli: un pannello Area di lavoro che contiene un elenco dei nodi nell'area di lavoro Progettazione [XML Schema](../xml-tools/xml-schema-designer-workspace.md)e l'area di progettazione in cui è possibile visualizzare il modello di contenuto dei nodi dello schema selezionati nel pannello Area di **lavoro.** La visualizzazione modello di contenuto include anche la barra degli strumenti di Progettazione XML Schema e la barra di navigazione.

Nell'immagine seguente il pannello Area **di** lavoro contiene sei nodi dello schema. Il `purchaseOrder` nodo viene selezionato nel pannello Area **di** lavoro e visualizzato nell'area di progettazione.

![Visualizzazione del modello di contenuto di Progettazione XML Schema](../xml-tools/media/xsddesigner_contentmodelview.gif)

## <a name="workspace-panel"></a>Pannello Area di lavoro

Dopo aver aggiunto nodi all'area di lavoro, l'elenco dei nodi verrà visualizzato nel pannello **Area di** lavoro della visualizzazione modello di contenuto. Quando si selezionano i nodi nel pannello **Area di** lavoro, questi vengono visualizzati nell'area di progettazione della visualizzazione modello di contenuto. Per eliminare nodi dall'area di lavoro,  usare la barra degli strumenti di Progettazione XSD, il menu di scelta rapida del pannello Area di lavoro o **il tasto CANC.**

Per informazioni sull'aggiunta di nodi, vedere la sezione "Aggiunta di nodi all'area di lavoro" nell'area di lavoro [progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md).

## <a name="design-surface"></a>Area di progettazione

Quando un nodo viene selezionato nel **pannello** Area di lavoro, viene aggiunto all'area di progettazione Visualizzazione modello di contenuto in cui è possibile visualizzare i dettagli del nodo.

Il modello di contenuto di un nodo viene rappresentato tramite un albero grafico espandibile con elementi e attributi visualizzati come nodi dell'albero. Per impostazione predefinita, viene espanso solo un livello. Le altre informazioni, ad esempio compositor, nomi di tipo, gruppi e altri contenitori, vengono posizionate in una barra verticale (in caso di espansione) lungo gli elementi e gli attributi che includono. Facendo doppio clic su una barra verticale, questa diventa orizzontale e l'albero viene compresso. Facendo doppio clic su una barra orizzontale, questa diventa verticale e l'albero viene espanso. Selezionando la barra verticale vengono selezionati tutti i nodi nel contenitore. Gli espansori vengono visualizzati a destra di un nodo se un elemento può essere espanso o compresso.

Se l'area di progettazione è vuota, vengono visualizzati l'editor XML, **XML Schema Explorer** e la filigrana. La *filigrana* è un elenco di collegamenti a tutte le visualizzazioni di Progettazione XSD. Se il set di schemi contiene errori, alla fine dell'elenco viene visualizzato il testo: "Usare l'elenco degli errori per visualizzare e correggere gli errori nel set di schemi".

## <a name="breadcrumb-bar"></a>Barra di navigazione

Tramite la barra di navigazione nella parte inferiore della visualizzazione modello di contenuto viene mostrato dove si trova il nodo selezionato nel set di schemi.

## <a name="context-menus"></a>Menu di scelta rapida

Quando si fa clic con il pulsante destro del mouse su un elemento nell'area di progettazione o nel pannello **Area di** lavoro, viene visualizzato un menu di scelta rapida. Nella tabella seguente vengono descritte le opzioni disponibili per l'area di progettazione della visualizzazione modello di contenuto.

|Opzione|Descrizione|
|-|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|
|**Esportare il diagramma come immagine**|Salva l'area di progettazione in un file XPS.|
|**Visualizza codice**|Apre il file che contiene il nodo selezionato nell'editor XML. Anche l'elemento selezionato in **XML Schema Explorer** viene selezionato nell'editor XML.|
|**Finestra Proprietà**|Apre la **finestra** Proprietà (se non è già aperta). In questa finestra verranno visualizzate le informazioni sul nodo.|

La tabella seguente descrive le opzioni disponibili per il pannello Area **di** lavoro.

|Opzione|Descrizione|
|-|-----------------|
|**Mostra in XML Schema Explorer**|Inserisce lo stato attivo su Schema Explorer ed evidenzia il nodo del set di schemi.|
|**Mostra in visualizzazione grafico**|Passa alla visualizzazione grafico.|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovi dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Genera XML di esempio**|Disponibile solo per elementi globali. Consente di generare un file XML di esempio per l'elemento globale.|
|**Seleziona tutto**|Seleziona tutti i nodi nel pannello Area **di** lavoro.|
|**Visualizza codice**|Apre il file che contiene il nodo selezionato nell'editor XML. Anche l'elemento selezionato in **XML Schema Explorer** viene selezionato nell'editor XML.|
|**Finestra Proprietà**|Apre la **finestra** Proprietà (se non è già aperta). In questa finestra verranno visualizzate le informazioni sul nodo.|

## <a name="properties-window"></a>Finestra Proprietà

Usare il menu di scelta rapida per aprire inizialmente la **finestra** Proprietà. Per impostazione predefinita, **la finestra** Proprietà viene visualizzata nell'angolo inferiore destro del Visual Studio. Quando si fa clic su un nodo di cui viene eseguito il rendering nella visualizzazione modello di contenuto, le proprietà del nodo vengono visualizzate nella **finestra** Proprietà.

## <a name="xsd-designer-toolbar"></a>Barra degli strumenti della finestra di progettazione XSD

I seguenti pulsanti della barra degli strumenti di Progettazione XSD sono abilitati quando la visualizzazione modello di contenuto è attiva.

![Barra degli strumenti di Progettazione XML Schema](../xml-tools/media/xsdcontentmodelviewtoolbar.gif)

|Opzione|Descrizione|
|-|-----------------|
|**Mostra visualizzazione iniziale**|Passa alla [visualizzazione iniziale.](../xml-tools/start-view.md) È possibile accedere a questa visualizzazione usando i tasti di scelta **rapida** CTRL + **1.**|
|**Mostra visualizzazione modello di contenuto**|Passa alla visualizzazione [modello di contenuto](../xml-tools/content-model-view.md). È possibile accedere a questa visualizzazione usando i tasti di scelta **rapida** CTRL + **2.**|
|**Mostra visualizzazione grafico**|Passa alla visualizzazione [Graph.](../xml-tools/graph-view.md) È possibile accedere a questa visualizzazione usando i tasti di scelta **rapida** CTRL + **3.**|
|**Cancella area di lavoro**|Cancella l'area di lavoro e l'area di progettazione.|
|**Rimuovi dall'area di lavoro**|Rimuove i nodi selezionati dall'area di lavoro e dall'area di progettazione.|
|**Rimuovi tutto tranne gli elementi selezionati dall'area di lavoro**|Rimuove i nodi non selezionati dall'area di lavoro e dall'area di progettazione.|
|**Mostra documentazione**|Mostra o nasconde il contenuto del nodo annotazione/documentazione.|

## <a name="panscroll"></a>Panoramica/scorrimento

È possibile eseguire una panoramica dell'area di progettazione usando le barre di scorrimento o tenendo premuto **CTRL** mentre si fa clic e si trascina il mouse. Quando si esegue una panoramica dell'area di progettazione tramite clic e trascinamento, il cursore assume quattro frecce incrociate che puntano in quattro direzioni.

## <a name="undoredo"></a>Annullamento/ripristino

La funzionalità di annullamento/ripristino è abilitata nella visualizzazione modello di contenuto per le seguenti azioni:

- Aggiunta di un singolo nodo con trascinamento della selezione.

- Aggiunta di più nodi dalla finestra dei risultati della ricerca in Schema Explorer.

- Aggiunta di nodi dalla visualizzazione iniziale.

- Eliminazione di uno o più nodi.

## <a name="zoom"></a>Zoom

Lo zoom è disponibile nell'angolo inferiore destro della visualizzazione modello di contenuto.

È possibile controllare lo zoom nei seguenti modi:

- Tenendo premuto CTRL **e** ruotando la rotellina del mouse quando si passa il mouse sull'area di visualizzazione del modello di contenuto.

- Tramite il dispositivo di scorrimento. Il dispositivo di scorrimento mostra il livello di zoom corrente.

Il dispositivo di scorrimento Zoom è opaco quando lo si seleziona, si passa il mouse su di esso o si usa **CTRL** con la rotellina del mouse per eseguire lo zoom; in tutti gli altri casi, è trasparente.

## <a name="xml-editor-integration"></a>Integrazione dell'editor XML

È possibile spostarsi tra Progettazione **XSD** e l'editor XML usando il menu di scelta rapida.

Se si apportano modifiche al set di schemi nell'editor XML, le modifiche vengono sincronizzate nella visualizzazione modello di contenuto. Per altre informazioni, vedere Integrazione [con l'editor XML.](../xml-tools/integration-with-xml-editor.md)

## <a name="see-also"></a>Vedi anche

- [Area di lavoro di Progettazione XML Schema](../xml-tools/xml-schema-designer-workspace.md)
