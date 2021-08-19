---
title: Cercare e ridisporre le mappe codice
description: Informazioni su come ridisporre gli elementi nelle mappe codice per semplificarne la lettura e il miglioramento delle prestazioni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: fb620b4bae6c0baed22331ef3058c48397e07bcb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055666"
---
# <a name="browse-and-rearrange-code-maps"></a>Cercare e ridisporre le mappe codice

È possibile riorganizzare gli elementi nelle mappe codice per facilitarne la lettura e migliorarne le prestazioni.

Le mappe codice possono essere personalizzate senza influire sul codice sottostante di una soluzione. Questa operazione risulta utile quando si vuole concentrarsi sugli elementi di codice principali o comunicare informazioni sul codice. Ad esempio, per evidenziare aree interessanti, è possibile selezionare elementi di codice sulla mappa e filtrarli, modificarne lo stile e i collegamenti, nascondere o eliminare elementi di codice e organizzarli tramite proprietà, categorie o gruppi.

 **Requisiti**

- Per creare mappe codice, è necessario usare Visual Studio Enterprise.

- È possibile visualizzare le mappe codice e apportarvi modifiche limitate in Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a> Introduzione all'uso delle mappe codice

Creare una mappa del codice (per altri dettagli, [vedere Eseguire il mapping delle](../modeling/map-dependencies-across-your-solutions.md) dipendenze tra le soluzioni). Se non si vuole attendere il completamento della generazione  della mappa, fare clic sul collegamento Annulla in qualsiasi momento per arrestare il processo di generazione. In questo caso, non sarà però possibile vedere i dettagli di tutte le dipendenze e tutti i collegamenti.

Dopo aver generato la mappa, iniziare la revisione del codice attenendosi ai suggerimenti seguenti:

- Osservare i cluster di dipendenze naturali all'interno del codice. Sulla barra degli strumenti della mappa scegliere **il pulsante Layout**, Cluster **rapidi** Cluster rapidi sulla barra degli strumenti ![ del ](../modeling/media/quickclustersicon.gif) grafico. Vedere [Modificare il layout della mappa.](#Selecting)

     ![Grafico delle dipendenze &#45; di cluster rapidi](../modeling/media/dependencygraph_quickclusters.png)

- Organizzare la mappa in aree più piccole mediante il raggruppamento dei nodi correlati. Comprimere i gruppi per visualizzare solo le dipendenze intergruppi, che appaiono automaticamente. Vedere [Nodi del gruppo](#OrganizeGroups).

- Usare i filtri per semplificare la mappa e per concentrarsi sui tipi di nodi o di collegamenti a cui si è interessati. Vedere [Filtrare nodi e collegamenti.](#FilterNodes)

- Ottimizzare le prestazioni delle mappe di grandi dimensioni. Per [altre informazioni, vedere Eseguire](../modeling/map-dependencies-across-your-solutions.md) il mapping delle dipendenze tra le soluzioni. Ad esempio, attivare **Ignora** compilazione sulla barra degli strumenti della mappa in modo che Visual Studio ricompila la soluzione quando si aggiornano gli elementi sulla mappa.

## <a name="change-the-map-layout"></a><a name="Selecting"></a> Modificare il layout della mappa

|**To**|**Eseguire questi passaggi**|
|-|-|
|Disporre il flusso delle dipendenze per l'intera mappa in una direzione specifica. In questo modo si potranno vedere i livelli di architettura nel codice.|Sulla barra degli strumenti della mappa scegliere **Layout** e quindi:<br /><br /> -   **Dall'alto verso il basso** ![ Pulsante Grafico dall'alto verso il basso](../modeling/media/topbottomgraphbutton.gif)<br />-   **Dal basso verso l'alto** ![ Pulsante Grafico dal basso verso l'alto](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Da sinistra a destra** ![ Pulsante layout da sinistra a destra](../modeling/media/leftrightgraphbutton.gif)<br />-   **Da destra a sinistra** ![ Pulsante grafico da destra a sinistra](../modeling/media/rightleftgraphbutton.gif)|
|Visualizzare cluster di dipendenze naturali all'interno del codice con i nodi che presentano un maggior numero di dipendenze al centro dei cluster e quelli con meno dipendenze all'esterno.|Sulla barra degli strumenti della mappa scegliere **Layout** e quindi il pulsante Cluster **rapidi** cluster rapidi sulla barra degli strumenti ![ del ](../modeling/media/quickclustersicon.gif) grafico.|
|Selezionare uno o più nodi sulla mappa.|Fare clic su un nodo per selezionarlo. Per selezionare o deselezionare più nodi, tenere **premuto CTRL** mentre si fa clic.<br /><br /> Tastiera: premere **TAB** o usare i tasti di direzione per spostare il rettangolo di attivazione punteggiato in un nodo e premere **SPAZIO** per selezionarlo. Premere   +  **CTRL+BARRA SPAZIATRICE** per selezionare o deselezionare più nodi.|
|Spostare nodi specifici sulla mappa.|Trascinare i nodi per spostarli. Per spostare altri nodi e collegamenti mentre si trascinano i nodi, tenere premuto **MAIUSC.**<br /><br /> Tastiera: tenere **premuto CTRL** e premere i tasti di direzione.|
|Modificare il layout all'interno di un gruppo indipendentemente dagli altri nodi e gruppi sulla mappa.|Selezionare un nodo e aprire il menu di scelta rapida. Scegliere **Layout** e selezionare uno stile di layout.<br /><br /> - oppure -<br /><br /> Selezionare un nodo ed espanderlo per visualizzare i nodi figlio. Fare clic sul titolo del nodo per visualizzare la barra degli strumenti popup del gruppo e aprire l'elenco Modifica lo stile di **layout** del grafico delle dipendenze del gruppo &#45; della barra degli strumenti &#45; ![ ](../modeling/media/dependencygraph_grouptoolbar.gif) layout. Selezionare uno dei layout dell'albero, **Cluster rapidi** o **Visualizzazione** elenco, che dispone il contenuto del gruppo in un elenco.<br /><br /> Per [altri dettagli, vedere](#OrganizeGroups) Nodi del gruppo.|
|Annullare un'azione nella mappa.|Premere **CTRL**  +  **Z o** usare il comando Visual Studio **Annulla.**|

## <a name="browse-the-map"></a><a name="Explore"></a> Esplorare la mappa

|**To**|**Eseguire questi passaggi**|
|-|-|
|Analizzare la mappa.|Trascinare la mappa in qualsiasi direzione usando il mouse.<br /><br /> - oppure -<br /><br /> Tenere **premuto MAIUSC** e ruotare la rotellina del mouse per scorrere orizzontalmente. Tenere **premuto MAIUSC**  +  **CTRL** e ruotare la rotellina del mouse per scorrere orizzontalmente.|
|Ingrandire o ridurre la mappa.|Ruotare la rotellina del mouse.<br /><br /> - oppure -<br /><br /> Usare **l'elenco a** discesa Zoom sulla barra degli strumenti della mappa codice.<br /><br /> - oppure -<br /><br /> Usare i tasti di scelta rapida. Per eseguire lo zoom avanti, premere **CTRL+MAIUSC+.** (punto). Per eseguire lo zoom indietro, premere **CTRL+MAIUSC+,** (virgola).|
|Ingrandire un'area specifica usando il mouse.|Tenere premuto il pulsante destro del mouse mentre si disegna un rettangolo intorno all'area di interesse.|
|Ridimensionare e adattare la mappa alla relativa finestra.|Scegliere **Zoom per adattare dall'elenco** Zoom **sulla** barra degli strumenti della mappa codice.<br /><br /> - oppure -<br /><br /> Fare clic **sull'icona Zoom per adattare** l'icona Zoom sulla barra degli strumenti della mappa del ![ ](../modeling/media/almcodemapzoomicon.png) codice. Tastiera: premere **CTRL+0** (zero).|
|Trovare un nodo sulla mappa in base al nome. **Suggerimento:**  Questa operazione funziona solo per gli elementi sulla mappa. Per trovare gli elementi nella soluzione, ma non sulla mappa, individuarli **in** Esplora soluzioni e quindi trascinarli sulla mappa. Trascinare la selezione oppure sulla barra **degli strumenti Esplora soluzioni** fare clic su Mostra nella mappa **codice**.|1. Scegliere  l'icona Trova icona Trova sulla barra degli strumenti della mappa del codice ![ ](../modeling/media/almcodemapfindicon.png) (Tastiera: premere **CTRL + F**) per visualizzare la casella di ricerca nell'angolo superiore destro della mappa.<br />2. Digitare il nome dell'elemento e premere **Invio** o fare clic sull'icona "lente di ingrandimento". Il primo elemento che corrisponde alla ricerca appare selezionato nella mappa.<br />3. Per personalizzare la ricerca, aprire l'elenco a discesa e scegliere un'opzione di ricerca. Le opzioni sono **Trova successivo,** **Trova precedente** e **Seleziona tutto.** Fare quindi clic sul pulsante corrispondente accanto alla casella di testo di ricerca.<br />     ![Le opzioni di ricerca&#45;'elenco a discesa](../modeling/media/almcodemapssearchdropdown.png)<br />     In alternativa, usare la tastiera: premere **F3** per selezionare il nodo corrispondente successivo o **MAIUSC +F3** per selezionare il nodo corrispondente precedente.<br />4. Selezionare una delle opzioni che specificano la modalità di gestione dei termini di ricerca facendo clic sulle icone sotto la casella di testo di ricerca.<br />     ![Opzioni di corrispondenza della ricerca](../modeling/media/almcodemapssearchmatchicons.png)<br />     Da sinistra a destra, le opzioni sono, corrispondenza con distinzione tra maiuscole e minuscole, corrispondenza solo con parole intere, uso della sintassi per le espressioni regolari .NET, espansione automatica dei gruppi per mostrare le corrispondenze per gli elementi inclusi. **Importante:**  È possibile usare la casella di ricerca per trovare corrispondenze nei gruppi compressi solo se tali gruppi sono stati espansi in precedenza. Per trovare queste corrispondenze ed espandere automaticamente i relativi gruppi padre, scegliere questa opzione sotto la casella di ricerca.|
|Selezionare tutti i nodi non selezionati.|Aprire il menu di scelta rapida per i nodi selezionati. Scegliere **Seleziona**, **Inverti selezione**.|
|Selezionare altri nodi che si collegano a quelli selezionati.|Aprire il menu di scelta rapida per i nodi selezionati. Scegliere **Seleziona** e una delle opzioni seguenti:<br /><br /> - Per selezionare nodi aggiuntivi che si collegano direttamente al nodo selezionato, scegliere **Dipendenze in ingresso**.<br />- Per selezionare nodi aggiuntivi che si collegano direttamente dal nodo selezionato, scegliere **Dipendenze in uscita**.<br />- Per selezionare nodi aggiuntivi che si collegano direttamente a e dal nodo selezionato, scegliere **Entrambi.**<br />- Per selezionare tutti i nodi che si collegano a e dal nodo selezionato, scegliere **Sottogramma connesso**.<br />- Per selezionare tutti gli elementi figlio del nodo selezionato, scegliere **Figli**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a> Filtrare nodi e collegamenti

|**To**|**Eseguire questi passaggi**|
|-|-|
|Visualizzare o nascondere il riquadro Filtri.|Scegliere il **pulsante Filtri sulla** barra degli strumenti della mappa codice. Il **riquadro** Filtri viene visualizzato come pagina a schede in **Esplora soluzioni**, per impostazione predefinita.|
|Filtrare i tipi di nodi visualizzati sulla mappa.|Impostare o deselezionare le caselle di controllo **nell'elenco Elementi di** codice nel riquadro Filtri.|
|Filtrare i tipi di collegamenti visualizzati sulla mappa.|Impostare o deselezionare le caselle di controllo **nell'elenco Relazioni** nel riquadro Filtri.|
|Mostrare o nascondere i nodi del progetto di test sulla mappa.|Impostare o deselezionare la casella  di controllo Asset **di** test nell'elenco Varie nel riquadro Filtri.|

Le icone visualizzate nel riquadro Legenda della mappa riflettono le impostazioni definite nell'elenco. Per visualizzare o nascondere il pannello Legenda, fare clic sul **pulsante Legenda** sulla barra degli strumenti della mappa codice.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a> Esaminare nodi e collegamenti

Le mappe codice mostrano i tipi di collegamenti seguenti:

- Un singolo collegamento rappresenta una singola relazione tra due nodi.

- Un collegamento tra gruppi rappresenta un relazione tra due nodi in gruppi diversi.

- Un collegamento di aggregazione rappresenta tutte le relazioni che puntano nella stessa direzione tra due gruppi.

> [!TIP]
> Per impostazione predefinita, la mappa mostra i collegamenti tra gruppi solo per i nodi selezionati. Per modificare questo comportamento per visualizzare o nascondere i collegamenti aggregati tra gruppi, fare clic su **Layout** sulla barra degli strumenti della mappa codice e scegliere **Avanzate**, quindi **Mostra** tutti i collegamenti tra gruppi o Nascondi tutti i collegamenti tra **gruppi**. Per [altri dettagli, vedere Nascondere o visualizzare nodi](#HidingShowing) e collegamenti.

|**To**|**Eseguire questi passaggi**|
|-|-|
|Visualizzare altre informazioni su un nodo o un collegamento.|Spostare il puntatore del mouse sopra un nodo o un collegamento finché non viene visualizzata una descrizione comando.<br /><br /> La descrizione comando per un collegamento di aggregazione elenca le singole dipendenze che rappresenta.<br /><br /> - oppure -<br /><br /> Aprire il menu di scelta rapida per il nodo o il collegamento. Scegliere **Modifica**, **Proprietà**.|
|Mostrare o nascondere il contenuto di un gruppo.|- Per espandere un gruppo, aprire il menu di scelta rapida per il nodo e scegliere **Raggruppa**, **Espandi**.<br />     - oppure -<br />     Spostare il puntatore del mouse sopra il nodo finché non viene visualizzato il pulsante con la freccia di espansione (freccia giù). Fare clic su questo pulsante per espandere il gruppo. Tastiera: per espandere o comprimere il gruppo selezionato, premere il **tasto PIÙ** ( ) o il **+** tasto **MENO** ( **-** ).<br />- Per comprimere un gruppo, aprire il menu di scelta rapida per il nodo e scegliere **Raggruppa**, **Comprimi**.<br />     - oppure -<br />     Spostare il puntatore del mouse sopra un gruppo finché non viene visualizzato il pulsante con la freccia di espansione (freccia su). Fare clic su questo pulsante per comprimere il gruppo.<br />- Per espandere tutti i gruppi, premere **CTRL**  +  **A** per selezionare tutti i nodi. Aprire il menu di scelta rapida per la mappa e scegliere **Raggruppa**, **Espandi**. **Nota:**      Questo comando non è disponibile se l'espansione di tutti i gruppi genera problemi di mappa o memoria inutilizzabili. È consigliabile espandere la mappa solo fino al livello di dettaglio che interessa.<br />- Per comprimere tutti i gruppi, aprire il menu di scelta rapida per un nodo o per la mappa. Scegliere **Gruppo**, **Comprimi tutto**.|
|Visualizzare la definizione di codice per uno spazio dei nomi, un tipo o un membro.|Aprire il menu di scelta rapida per il nodo e scegliere **Vai a definizione**.<br /><br /> -oppure-<br /><br /> Fare doppio clic sul nodo. Per espandere i gruppi, fare doppio clic sull'intestazione del gruppo.<br /><br /> -oppure-<br /><br /> Selezionare il nodo e premere **F12.**<br /><br /> Esempio:<br /><br /> - Per uno spazio dei nomi contenente una classe, viene aperto il file di codice per la classe per visualizzare la definizione di tale classe. In altri casi, nella **finestra Risultati ricerca simbolo** viene visualizzato un elenco di file di codice. **Nota:**      Quando si esegue questa attività in uno spazio Visual Basic, il file di codice dietro lo spazio dei nomi non viene aperto. Questo problema si verifica anche quando si esegue questa attività in un gruppo di nodi selezionati che includono un Visual Basic spazio dei nomi. Per risolvere il problema, individuare manualmente il file di codice associato allo spazio dei nomi oppure omettere dalla selezione il nodo per lo spazio dei nomi.<br />- Per una classe o una classe parziale, viene aperto il file di codice per tale classe per visualizzare la definizione della classe.<br />- Per un metodo, viene aperto il file di codice per la classe padre per visualizzare la definizione del metodo.|
|Esaminare le dipendenze e gli elementi che fanno parte di un collegamento di aggregazione.|Selezionare i collegamenti a cui si è interessati e aprire il menu di scelta rapida per la selezione. Scegliere **Mostra collegamenti ai contributi** o Mostra collegamenti ai contributi nella nuova mappa **codice.**<br /><br /> In Visual Studio i gruppi vengono espansi a entrambe le estremità del collegamento e vengono mostrati solo gli elementi e le dipendenze che partecipano al collegamento. **Nota:**  Quando si esaminano le dipendenze tra elementi in gruppi parziali, è possibile che venga visualizzato questo comportamento: <ul><li>I collegamenti agli elementi che non partecipano all'esame scompaiono dalla mappa, anche se tali collegamenti esistono ancora.</li><li>Si supponga di esaminare un collegamento a un elemento in un gruppo parziale e successivamente di esaminare un collegamento diverso allo stesso elemento. Durante la seconda analisi, il gruppo parziale di destinazione mostra solo gli elementi della prima analisi. I collegamenti e gli elementi di destinazione che non hanno partecipato al primo esame ma che hanno partecipato al secondo esame non vengono visualizzati.</li></ul> Per visualizzare gli elementi mancanti da un gruppo, scegliere **Refetch Children Refetch Children** Icon (Icona Refetch Children Refetch Children), che indica che non tutti i membri di un gruppo ![ vengono visualizzati sulla ](../modeling/media/dependencygraph_deletednodesicon.png) mappa. È anche possibile provare ad annullare le azioni (tastiera: premere **CTRL+Z)** ed esaminare le dipendenze in una nuova mappa.|
|Esaminare le dipendenze tra più nodi in gruppi diversi.|Espandere i gruppi per visualizzare tutti i relativi elementi figlio. Selezionare tutti i nodi che interessano, inclusi i relativi elementi figlio. La mappa mostra i collegamenti tra gruppi tra i nodi selezionati.<br /><br /> Per selezionare tutti i nodi in un gruppo, tenere premuto **MAIUSC** e il pulsante sinistro del mouse mentre si disegna un rettangolo intorno a tale gruppo. Per selezionare tutti i nodi su una mappa, premere **CTRL** + **A.** **Suggerimento:**  Per visualizzare sempre i collegamenti tra gruppi, scegliere **Layout** sulla barra degli strumenti della mappa, **Avanzate,** **Mostra tutti i collegamenti tra gruppi.**|
|Visualizzare gli elementi a cui fa riferimento un nodo o un collegamento.|Aprire il menu di scelta rapida per il nodo e scegliere **Trova tutti i riferimenti**. **Nota:**  Si applica solo quando `Reference` l'attributo è impostato per il nodo o il collegamento nel file con estensione dgml della mappa. Per aggiungere riferimenti a elementi da nodi o collegamenti, vedere Personalizzare le mappe [codice modificando i file DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a> Nascondere o visualizzare nodi e collegamenti

Se vengono nascosti, i nodi non possono partecipare ad algoritmi di layout. Per impostazione predefinita, i collegamenti tra gruppi sono nascosti. I collegamenti tra gruppi sono collegamenti singoli che connettono nodi tra gruppi. Quando i gruppi vengono compressi, tutti i collegamenti tra gruppi presenti nella mappa vengono aggregati in singoli collegamenti tra gruppi. Quando si espande un gruppo e si selezionano nodi nel gruppo, i collegamenti tra gruppi vengono visualizzati mostrando le dipendenze nel gruppo.

> [!CAUTION]
> Prima di condividere una mappa creata in Visual Studio Enterprise con utenti che usano Visual Studio Professional, assicurarsi di scoprire tutti i nodi o i collegamenti tra gruppi che si desidera rendere visibili ad altri utenti. In caso contrario, gli utenti non saranno in grado di vedere tali elementi.

### <a name="to-hide-or-show-nodes"></a>Per nascondere o mostrare nodi

|**To**|**Eseguire questi passaggi**|
|-|-|
|Nascondere nodi selezionati.|1. Selezionare i nodi da nascondere.<br />2. Aprire il menu di scelta rapida per i nodi selezionati o per la mappa. Scegliere **Seleziona**, **Nascondi selezionato**.|
|Nascondere i nodi non selezionati.|1. Selezionare i nodi da mantenere visibili.<br />2. Aprire il menu di scelta rapida per i nodi selezionati o per la mappa. Scegliere **Seleziona**, **Nascondi non selezionato**.|
|Mostrare i nodi nascosti.|- Per visualizzare tutti i nodi nascosti all'interno di un gruppo, assicurarsi prima di tutto che il gruppo sia espanso. Aprire il menu di scelta rapida e **scegliere Seleziona**, Mostra **elementi figlio**.<br />     - oppure -<br />     Fare clic **sull'icona** Scopri elementi figlio Scopri elementi figlio nell'angolo superiore sinistro del gruppo ( questa opzione è visibile solo quando sono presenti ![ nodi figlio ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) nascosti).<br />- Per visualizzare tutti i nodi nascosti, aprire il menu di scelta rapida per la mappa o un nodo e scegliere **Seleziona**, **Mostra tutto**.|

### <a name="to-hide-or-show-links"></a>Per nascondere o mostrare collegamenti

|**To**|**Sulla barra degli strumenti della mappa scegliere Layout, Avanzate e quindi scegliere**|
|-|-|
|Mostrare sempre tutti i collegamenti tra gruppi.|**Mostra tutti i collegamenti tra gruppi**. In questo modo i collegamenti aggregati tra gruppi vengono nascosti.|
|Nascondere sempre i collegamenti tra gruppi.|**Nascondi tutti i collegamenti tra gruppi**|
|Mostrare solo i collegamenti tra gruppi per i nodi selezionati.|**Mostra collegamenti tra gruppi nei nodi selezionati**|
|Nascondere tutti i collegamenti.|**Nascondi tutti i collegamenti**. Per visualizzare di nuovo i collegamenti, scegliere una delle opzioni elencate sopra.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a> Nodi del gruppo

|**To**|**Eseguire questi passaggi**|
|-|-|
|Mostrare nodi contenitore come nodi gruppo o nodi foglia.|Per visualizzare i nodi del contenitore come nodi foglia: selezionare i nodi, aprire il menu di scelta rapida per la selezione e scegliere **Raggruppa**, **Converti in foglia**.<br /><br /> Per visualizzare i nodi del contenitore come nodi di gruppo: selezionare i nodi, aprire il menu di scelta rapida per la selezione e scegliere **Raggruppa**, **Converti in gruppo**.|
|Modificare il layout all'interno di un gruppo.|Selezionare il gruppo, aprire il menu di scelta rapida, **scegliere Layout** e selezionare lo stile di layout desiderato.<br /><br /> - oppure -<br /><br /> 1. Selezionare il gruppo e assicurarsi che sia espanso.<br />2. Fare di nuovo clic sull'intestazione del gruppo e verrà visualizzata la barra degli strumenti del gruppo.<br />     ![Grafico delle dipendenze &#45; barra degli strumenti del gruppo](../modeling/media/dependencygraph_group.png)<br />3. Aprire modifica lo stile **di layout** dell'elenco di gruppi Grafico dipendenze &#45; barra degli strumenti del gruppo &#45; layout e scegliere lo stile di ![ layout ](../modeling/media/dependencygraph_grouptoolbar.gif) desiderato.<br /><br /> **Visualizzazione elenco** consente di ridisporre i membri del gruppo in un elenco. **Graph predefinito** reimposta il layout del gruppo sul layout predefinito della mappa. Per altre opzioni, vedere [Modificare il layout della mappa.](#Selecting)|
|Aggiungere un nodo a un gruppo.|Trascinare il nodo nel gruppo.<br /><br /> Mentre si trascina il nodo, Visual Studio visualizza un indicatore per mostrare che si sta spostando il nodo.<br /><br /> È inoltre possibile trascinare i nodi da un gruppo.|
|Aggiungere un nodo a un nodo non di gruppo.|Trascinare il nodo nel nodo di destinazione. È possibile convertire qualsiasi nodo di destinazione in un gruppo aggiungendovi nodi.|
|Raggruppare nodi selezionati.|1. Selezionare i nodi da raggruppare. Sopra l'ultimo nodo selezionato viene visualizzata una barra degli strumenti popup.<br />     ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)<br />2. Sulla barra degli strumenti scegliere la quarta icona Raggruppa i nodi selezionati **(se** il nodo è espanso avrà cinque anziché quattro icone). Digitare il nome per il nuovo gruppo e premere **INVIO.**<br />     - oppure -<br />     Selezionare i nodi da raggruppare e aprire il menu di scelta rapida per la selezione. Scegliere **Gruppo,** **Aggiungi gruppo padre,** digitare il nome per il nuovo gruppo e premere **INVIO.**<br /><br /> Il gruppo può essere rinominato. Aprire il menu di scelta rapida per il gruppo e scegliere **Modifica**, **Proprietà** per aprire il Visual Studio Finestra Proprietà. Nella proprietà **Etichetta** rinominare il gruppo in base alle esigenze.|
|Rimuovere i gruppi.|Selezionare il gruppo o i gruppi da rimuovere. Aprire il menu di scelta rapida per la selezione e **scegliere Gruppo**, **Rimuovi gruppo**.|
|Rimuovere i nodi dal relativo gruppo padre.|Selezionare i nodi da spostare. Aprire il menu di scelta rapida per la selezione e **scegliere Raggruppa**, Rimuovi **da padre**. I nodi vengono rimossi fino al relativo gruppo padre del padre oppure all'esterno di un gruppo se non hanno un gruppo padre del padre.<br /><br /> - oppure -<br /><br /> Selezionare i nodi e trascinarli all'esterno del gruppo.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a> Aggiungere, rimuovere o rinominare nodi, collegamenti e commenti

Per eseguire il drill-down o semplificare la mappa, è possibile visualizzare più o meno elementi sulla mappa. È anche possibile rinominare gli elementi e aggiungervi commenti.

> [!CAUTION]
> Prima di condividere una mappa creata in Visual Studio Enterprise con utenti che usano Visual Studio Professional, assicurarsi che tutti i gli elementi di codice che si desidera rendere visibili ad altri utenti siano visibili sulla mappa. In caso contrario, gli utenti non saranno in grado di recuperare gli elementi di codice eliminati.

### <a name="add-a-node-for-a-code-element"></a>Aggiungere un nodo per un elemento di codice

|**To**|**Eseguire questi passaggi**|
|-|-|
|Aggiungere un nuovo nodo generico nella posizione corrente del puntatore del mouse.|1. Spostare il puntatore del mouse nel punto della mappa in cui si vuole inserire il nuovo elemento di codice e premere **Inserisci.**<br />     - oppure -<br />     Aprire il menu di scelta rapida per la mappa e scegliere **Modifica**, **Aggiungi**, **Nodo generico**.<br />2. Digitare il nome per il nuovo nodo e premere **Invio.**|
|Aggiungere un tipo specifico di nodo elemento di codice nella posizione corrente del puntatore del mouse.|1. Spostare il puntatore del mouse nel punto della mappa in cui si vuole inserire il nuovo elemento di codice e aprire il menu di scelta rapida per la mappa.<br />2. Scegliere **Modifica**, **Aggiungi** e selezionare il tipo di nodo desiderato.<br />3. Digitare il nome per il nuovo nodo e premere **Invio.**|
|Aggiungere un tipo specifico o generico di nodo elemento di codice a un gruppo.|1. Selezionare il nodo del gruppo e aprire il menu di scelta rapida.<br />2. Scegliere **Modifica**, **Aggiungi** e selezionare il tipo di nodo desiderato.<br />3. Digitare il nome per il nuovo nodo e premere **Invio.**|
|Aggiungere un nuovo nodo dello stesso tipo e collegato da un nodo esistente.|1. Selezionare l'elemento di codice. Sopra di esso verrà visualizzata una barra degli strumenti popup.<br />     ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)<br />2. Sulla barra degli strumenti scegliere la seconda icona Creare un nodo con la stessa categoria di questo nodo e aggiungerne **un nuovo collegamento.**<br />3. Scegliere una posizione sulla mappa per inserire il nuovo elemento di codice e fare clic con il pulsante sinistro del mouse.<br />4. Digitare il nome per il nuovo nodo e premere **INVIO.**|
|Aggiungere un nuovo nodo generico collegato da un elemento di codice esistente con lo stato attivo.|1. Usando la tastiera, premere **TAB** fino a quando l'elemento di codice da cui collegarsi ha lo stato attivo (rettangolo punteggiato).<br />2. Premere + **ALT+INS.**<br />3. Digitare il nome per il nuovo nodo e premere **INVIO.**|
|Aggiungere un nuovo nodo generico che si collega a un elemento di codice esistente con lo stato attivo.|1. Usando la tastiera, premere **TAB** fino a quando l'elemento di codice a cui collegarsi ha lo stato attivo (rettangolo punteggiato).<br />2. Premere **ALT** +  + **MAIUSC+INS.**<br />3. Digitare il nome per il nuovo nodo e premere **INVIO.**|

|**Per aggiungere elementi di codice per**|**Eseguire questi passaggi**|
|-|-|
|Elementi di codice nella soluzione.|1. Trovare l'elemento di codice in **Esplora soluzioni**. Usare la **Esplora soluzioni** di ricerca o esplorare la soluzione. **Suggerimento:**      Per trovare elementi di codice con dipendenze da un tipo o un membro, aprire il menu di scelta rapida per il tipo o il membro in **Esplora soluzioni**. Scegliere la relazione che interessa. **Esplora soluzioni** mostra solo gli elementi di codice con le dipendenze specificate.<br />2. Trascinare gli elementi di codice di interesse sulla superficie della mappa. È anche possibile trascinare elementi di codice da Visualizzazione classi o da Visualizzatore oggetti.<br />     - oppure -<br />     In **Esplora soluzioni** selezionare gli elementi di codice di cui si vuole eseguire il mapping. Sulla barra degli strumenti **Esplora soluzioni** fare clic su **Mostra sulla mappa codice.**<br /><br /> Per impostazione predefinita, sulla mappa viene visualizzata la gerarchia del contenitore padre per i nuovi elementi di codice. Usare il **pulsante Includi elementi** padre sulla barra degli strumenti della mappa codice per modificare questo comportamento. Quando è disattivato, solo lo stesso elemento di codice viene aggiunto alla mappa. Per invertire questo comportamento per una sola azione di trascinamento della selezione, tenere premuto **CTRL** mentre si trascinano gli elementi di codice sulla mappa.<br /><br /> Visual Studio aggiunge elementi di codice per gli elementi di codice di primo livello nella selezione. Per vedere se un elemento di codice contiene altri elementi di codice, spostare il puntatore del mouse sopra l'elemento di codice in modo da visualizzare la freccia di espansione (freccia giù). Fare clic sulla freccia di espansione per espandere l'elemento di codice. Per espandere tutti gli elementi di codice, premere **CTRL** A per selezionare tutti gli elementi, aprire il menu di scelta rapida per la mappa e scegliere +  **Raggruppa**, **Espandi**. Questo comando non è disponibile se l'espansione di tutti i gruppi genera una mappa inutilizzabile o problemi di memoria insufficiente.|
|Elementi di codice correlati a elementi di codice sulla mappa.|Fare clic **sul pulsante Mostra** elementi correlati sulla barra degli strumenti della mappa codice e scegliere il tipo di elementi correlati a cui si è interessati.<br /><br /> - oppure -<br /><br /> Aprire il menu di scelta rapida per l'elemento di codice. Scegliere una delle **voci Mostra ...** nel menu a seconda del tipo di relazione di interesse. Ad esempio, è possibile visualizzare gli elementi a cui fa riferimento l'elemento corrente, gli elementi che fanno riferimento all'elemento corrente, i tipi di base e derivati per classi, i chiamanti del metodo e le classi, gli spazi dei nomi e gli assembly che li contengono.<br /><br /> Per altri dettagli, vedere [questo argomento.](../modeling/map-dependencies-across-your-solutions.md)|
|Assembly .NET (con estensione dll o exe) o file binari compilati.|Trascinare gli assembly o i file binari dall'esterno di Visual Studio su una mappa.<br /><br /> È possibile trascinare da Esplora risorse o Esplora file solo se questo componente e Visual Studio vengono eseguiti allo stesso livello di autorizzazione del controllo di accesso utente. Se, ad esempio, il controllo di accesso utente è attivato e si esegue Visual Studio come amministratore, Esplora risorse o Esplora file blocca l'operazione di trascinamento.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Aggiungere un collegamento tra elementi di codice esistenti

1. Selezionare l'elemento di codice sorgente. Sopra l'elemento di codice viene visualizzata una barra degli strumenti.

    ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)

2. Sulla barra degli strumenti scegliere la prima icona Crea nuovo collegamento da questo nodo a cui fare clic **su Avanti.**

3. Selezionare l'elemento di codice di destinazione. Verrà visualizzato un collegamento tra i due elementi di codice.

**OR**

1. Selezionare l'elemento di codice sorgente nella mappa.

2. Se è installato un mouse, spostare il puntatore del mouse fuori dai limiti della mappa.

3. Aprire il menu di scelta rapida dell'elemento di codice e scegliere  >  **Modifica Aggiungi** collegamento  >  **generico.**

4. Premere TAB fino a selezionare l'elemento di codice di destinazione per il collegamento.

5. Premere **INVIO**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Aggiungere un commento a un nodo esistente sulla mappa

1. Selezionare l'elemento di codice. Sopra di esso verrà visualizzata una barra degli strumenti.

     ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)

2. Sulla barra degli strumenti scegliere la terza icona Crea **un nuovo nodo di commento con un nuovo collegamento al nodo selezionato.**

     \- - oppure -

     Aprire il menu di scelta rapida per l'elemento di codice e **scegliere Modifica**  >  **nuovo commento.**

3. Digitare i commenti. Per digitare in una nuova riga, premere **MAIUSC**  +  **INVIO.**

#### <a name="add-a-comment-to-the-map-itself"></a>Aggiungere un commento alla mappa

1. Aprire il menu di scelta rapida per la mappa e **scegliere Modifica**  >  **nuovo commento.**

2. Digitare i commenti. Per digitare in una nuova riga, premere **MAIUSC**  +  **INVIO.**

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Rinominare un elemento di codice o un collegamento

1. Selezionare l'elemento di codice o il collegamento da rinominare.

2. Premere **F2** oppure aprire il menu di scelta rapida e scegliere **Modifica**  >  **Rinomina.**

3. Quando viene visualizzata la casella di modifica nella mappa, rinominare l'elemento di codice o il collegamento.

**OR**

1. Aprire il menu di scelta rapida e **scegliere**  >  **Modifica proprietà.**

2. Modificare la **proprietà Label** nel Visual Studio Finestra Proprietà.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Rimuovere un elemento di codice o un collegamento dalla mappa

1. Selezionare l'elemento di codice o il collegamento e premere **CANC.**

     \- - oppure -

     Aprire il menu di scelta rapida per l'elemento di codice o il collegamento e scegliere **Modifica**  >  **Rimuovi.**

2. Se l'elemento o il collegamento fa parte di un gruppo, il pulsante Refetch Children (Elementi figlio **refetch) Refetch Children** Icon (Icona ![ refetch elementi ](../modeling/media/dependencygraph_deletednodesicon.png) figlio) viene visualizzato all'interno del gruppo. Fare clic su questo pulsante per recuperare elementi e collegamenti mancanti.

- È possibile rimuovere gli elementi di codice e i collegamenti da una mappa senza influire sul codice sottostante. Se vengono eliminati, le relative definizioni vengono rimosse dal file DGML (con estensione dgml).

- Le mappe create modificando il file DGML, aggiungendo elementi di codice non definiti o usando versioni precedenti di Visual Studio non supportano questa funzionalità.

#### <a name="flag-a-code-element-for-follow-up"></a>Contrassegnare un elemento di codice per il completamento

1. Selezionare l'elemento di codice o il collegamento da contrassegnare per il completamento.

2. Aprire il menu di scelta rapida e **scegliere Modifica** flag  >  **per Completa.**

- Per impostazione predefinita, all'elemento di codice viene applicato uno sfondo rosso. Prendere [in considerazione l'aggiunta](#AddComments) di un commento con le informazioni di follow-up appropriate.

- Modificare il colore di sfondo dell'elemento o deselezionare il flag di follow-up scegliendo **Modifica altri**  >  **colori flag**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a> Modificare lo stile di un elemento di codice o di un collegamento

È possibile modificare le icone per gli elementi di codice e i colori per gli elementi di codice e i collegamenti usando le icone e i colori predefiniti. Ad esempio, è possibile scegliere un colore per evidenziare elementi di codice e collegamenti con una determinata categoria o proprietà. In questo modo si possono identificare aree specifiche della mappa e concentrarsi su di esse. È possibile specificare icone e colori personalizzati modificando il file con estensione dgml della mappa. Vedere [Personalizzare le mappe codice modificando i file DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Per applicare un colore o un'icona predefinita agli elementi di codice o ai collegamenti con una determinata categoria o proprietà

1. Sulla barra degli strumenti della mappa scegliere **Legenda.**

2. Nella casella **Legenda** verificare se la categoria o la proprietà dell'elemento di codice è già presente nell'elenco.

3. Se l'elenco non include la categoria o la proprietà, scegliere nella casella Legenda , quindi scegliere Proprietà nodo , Categoria nodo **+** , Proprietà **collegamentoo** Categoria **collegamento**.   Scegliere quindi la proprietà o la categoria. La categoria o la proprietà viene ora visualizzata nella **casella Legenda.**

    > [!NOTE]
    > Per creare e assegnare una categoria o una proprietà a un elemento di codice, è possibile modificare il file con estensione dgml della mappa. Vedere [Personalizzare le mappe codice modificando i file DGML.](../modeling/customize-code-maps-by-editing-the-dgml-files.md)

4. Nella casella **Legenda** fare clic sull'icona accanto alla categoria o alla proprietà aggiunta o da modificare.

5. Utilizzare la tabella seguente per selezionare lo stile che si desidera modificare:

    |**Per modificare l'oggetto**|**Scegliere**|
    |-|-|
    |Colore di sfondo|**Background**|
    |Outline color|**infarto**|
    |Colore del testo (viene visualizzata una lettera "f" per visualizzare il risultato)|**Foreground**|
    |Icona|**Icone**|

     Verrà **visualizzata la finestra di** dialogo Selezione set di colori o Selezione **set** di icone per selezionare un colore o un'icona.

6. Nella finestra **di dialogo Selezione set di colori** o Selezione set di **icone** eseguire una delle operazioni seguenti:

    |**Per applicare un**|**Eseguire questi passaggi**|
    |-|-|
    |Set di colori o di icone|Aprire **l'elenco Seleziona set** di colori **(o** **icona).** Selezionare un set di colori o di icone.|
    |Colore o icona specifica|Aprire l'elenco di valori della proprietà o della categoria. Selezionare un colore o un'icona.|

    > [!NOTE]
    > È possibile ridisporre, eliminare o disattivare temporaneamente gli stili nella **casella Legenda.** Vedere [Modificare la casella Legenda](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a> Modificare la casella Legenda

È possibile ridisporre, eliminare o disattivare temporaneamente gli stili nella **casella Legenda:**

1. Aprire il menu di scelta rapida per uno stile nella **casella Legenda.**

2. Effettuare una delle attività seguenti:

    |**To**|**Scegliere**|
    |-|-|
    |Disattivare l'elemento di codice|**Disabilita**|
    |Eliminare l'elemento di codice|**Elimina**|
    |Spostare lo stile in alto|**Sposta su**|
    |Spostare l'elemento di codice in basso|**Sposta giù**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a> Copiare gli stili da una mappa a un'altra

1. Assicurarsi che la **casella Legenda** sia visualizzata nel source map. Se non è visibile, sulla barra degli strumenti della mappa fare clic su **Legenda**.

2. Aprire il menu di scelta rapida per la **casella Legenda.** Scegliere **Copia legenda**.

3. Incollare la legenda nella mappa di destinazione.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a> Unire mappe codice

È possibile unire le mappe copiando e incollando gli elementi di codice tra le mappe. Se gli identificatori degli elementi di codice corrispondono, l'operazione per incollare gli elementi di codice funziona come un'operazione di unione. Per semplificare questa attività, inserire tutti gli assembly o i file binari da visualizzare nella stessa cartella, in modo che il percorso completo di ogni assembly o file binario sia lo stesso per ogni mappa da unire.

In alternativa, è possibile trascinare gli assembly o file binari da tale cartella nella stessa mappa.

## <a name="see-also"></a>Vedi anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Riferimento di Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
