---
title: Cercare e ridisporre le mappe del codice
ms.date: 11/04/2016
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: cd9c431bdac6eb258084944bcff80c86e81796f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55042699"
---
# <a name="browse-and-rearrange-code-maps"></a>Cercare e ridisporre le mappe del codice

È possibile riorganizzare gli elementi nelle mappe codice per facilitarne la lettura e migliorarne le prestazioni.

Le mappe codice possono essere personalizzate senza influire sul codice sottostante di una soluzione. Questa operazione risulta utile quando si vuole concentrarsi sugli elementi di codice principali o comunicare informazioni sul codice. Ad esempio, per evidenziare aree interessanti, è possibile selezionare elementi di codice sulla mappa e filtrarli, modificarne lo stile e i collegamenti, nascondere o eliminare elementi di codice e organizzarli tramite proprietà, categorie o gruppi.

 **Requisiti**

-   Per creare mappe codice, è necessario usare Visual Studio Enterprise.

-   È possibile visualizzare le mappe codice e apportarvi modifiche limitate in Visual Studio Professional.

##  <a name="ManageLargeGraphs"></a> Iniziare a lavorare con le mappe codice

Creare una mappa codice (vedere [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) per altri dettagli). Se non si vuole attendere la mappa venga completato, fare clic sui **annullare** collegamento in qualsiasi momento per arrestare il processo di generazione. In questo caso, non sarà però possibile vedere i dettagli di tutte le dipendenze e tutti i collegamenti.

Dopo aver generato la mappa, iniziare la revisione del codice attenendosi ai suggerimenti seguenti:

-   Osservare i cluster di dipendenze naturali all'interno del codice. Sulla barra degli strumenti della mappa, scegliere **Layout**, **raggruppamenti veloci**![pulsante raggruppamenti veloci sulla barra degli strumenti grafico](../modeling/media/quickclustersicon.gif). Visualizzare [modificare il layout della mappa](#Selecting).

     ![Grafico delle dipendenze &#45; layout raggruppamenti veloci](../modeling/media/dependencygraph_quickclusters.png)

-   Organizzare la mappa in aree più piccole mediante il raggruppamento dei nodi correlati. Comprimere i gruppi per visualizzare solo le dipendenze intergruppi, che appaiono automaticamente. Visualizzare [raggruppare nodi](#OrganizeGroups).

-   Usare i filtri per semplificare la mappa e per concentrarsi sui tipi di nodi o di collegamenti a cui si è interessati. Visualizzare [filtrare nodi e collegamenti](#FilterNodes).

-   Ottimizzare le prestazioni delle mappe di grandi dimensioni. Visualizzare [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) per altre informazioni. Ad esempio, attivare **Skip Build** sulla barra degli strumenti della mappa in modo che Visual Studio non ricompilerà la soluzione quando si aggiornano elementi sulla mappa.

##  <a name="Selecting"></a> Modificare il layout della mappa

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Disporre il flusso delle dipendenze per l'intera mappa in una direzione specifica. In questo modo si potranno vedere i livelli di architettura nel codice.|Sulla barra degli strumenti della mappa, scegliere **Layout**e quindi:<br /><br /> -   **Dall'alto verso il basso** ![dall'alto verso il pulsante grafico in basso](../modeling/media/topbottomgraphbutton.gif)<br />-   **Dal basso in alto** ![inferiore al pulsante grafico in alto](../modeling/media/bottomtopgraphbutton.gif)<br />-   **Da sinistra a destra** ![da sinistra a pulsante layout corretto](../modeling/media/leftrightgraphbutton.gif)<br />-   **Zprava Doleva** ![zprava pulsante grafico a sinistra](../modeling/media/rightleftgraphbutton.gif)|
|Visualizzare cluster di dipendenze naturali all'interno del codice con i nodi che presentano un maggior numero di dipendenze al centro dei cluster e quelli con meno dipendenze all'esterno.|Sulla barra degli strumenti della mappa, scegliere **Layout**e quindi **raggruppamenti veloci**![pulsante raggruppamenti veloci sulla barra degli strumenti grafico](../modeling/media/quickclustersicon.gif).|
|Selezionare uno o più nodi sulla mappa.|Fare clic su un nodo per selezionarlo. Per selezionare o deselezionare più nodi, tenere premuto **CTRL** mentre si fa clic.<br /><br /> Tastiera: premere **della scheda** o usare i tasti di direzione per spostare il rettangolo di attivazione punteggiato su un nodo e premere **spazio** per selezionarlo. Premere **CTRL** + **spazio** a selezione multipla o deselezionare i nodi.|
|Spostare nodi specifici sulla mappa.|Trascinare i nodi per spostarli. Per spostare altri nodi e collegamenti dall'area di lavoro quando si trascinano i nodi, premere e tenere premuto il **MAIUSC** chiave.<br /><br /> Tastiera: tenere premuto **CTRL** e premere i tasti di direzione.|
|Modificare il layout all'interno di un gruppo indipendentemente dagli altri nodi e gruppi sulla mappa.|Selezionare un nodo e aprire il menu di scelta rapida. Scegli **Layout** e selezionare uno stile di layout.<br /><br /> -oppure-<br /><br /> Selezionare un nodo ed espanderlo per visualizzare i nodi figlio. Fare clic sul titolo del nodo per visualizzare una barra degli strumenti popup di gruppo e aprire il **modificare lo stile di layout del gruppo**![grafico delle dipendenze &#45; sulla barra degli strumenti gruppo &#45; layout](../modeling/media/dependencygraph_grouptoolbar.gif) elenco. Selezionare uno dei layout ad albero, **raggruppamenti veloci**, o **visualizzazione elenco** (che dispone i contenuti del gruppo in un elenco).<br /><br /> Visualizzare [raggruppare nodi](#OrganizeGroups) per altri dettagli.|
|Annullare un'azione nella mappa.|Premere **CTRL** + **Z** oppure usare Visual Studio **annullare** comando.|

##  <a name="Explore"></a> Sfogliare la mappa

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Analizzare la mappa.|Trascinare la mappa in qualsiasi direzione usando il mouse.<br /><br /> -oppure-<br /><br /> Tenere premuto **MAIUSC** e ruotare la rotellina del mouse per scorrere orizzontalmente. Tenere premuto **SHIFT** + **CTRL** e ruotare la rotellina del mouse per scorrere orizzontalmente.|
|Ingrandire o ridurre la mappa.|Ruotare la rotellina del mouse.<br /><br /> -oppure-<br /><br /> Usare la **Zoom** elenco a discesa sulla barra degli strumenti della mappa codice.<br /><br /> -oppure-<br /><br /> Usare i tasti di scelta rapida. Per ingrandire, premere **CTRL + MAIUSC +.** (punto). Per eseguire lo zoom indietro, premere **CTRL + MAIUSC +,** (virgola).|
|Ingrandire un'area specifica usando il mouse.|Tenere premuto il pulsante destro del mouse mentre si disegna un rettangolo intorno all'area di interesse.|
|Ridimensionare e adattare la mappa alla relativa finestra.|Scegli **adatta alla finestra** dal **Zoom** elenco sulla barra degli strumenti della mappa codice.<br /><br /> -oppure-<br /><br /> Scegliere il **adatta alla** icona ![icona Zoom sulla barra degli strumenti della mappa](../modeling/media/almcodemapzoomicon.png) sulla barra degli strumenti della mappa codice. Tastiera: premere **CTRL + 0** (zero).|
|Trovare un nodo sulla mappa in base al nome. **Suggerimento:**  Funziona solo per gli elementi sulla mappa. Per trovare gli elementi nella soluzione ma non sulla mappa, individuarli in **Esplora soluzioni**e quindi trascinare tali alla mappa. (Trascinare la selezione, o scegliere il **Esplora soluzioni** sulla barra degli strumenti, fare clic su **Mostra in mappa codice**).|1.  Scegliere il **trovare** icona ![icona trova sulla barra degli strumenti della mappa](../modeling/media/almcodemapfindicon.png) sulla barra degli strumenti della mappa codice (tastiera: premere **CTRL + F**) per visualizzare la casella di ricerca nell'angolo superiore destro della mappa.<br />2.  Digitare il nome dell'elemento e premere **restituire** o fare clic sull'icona "lente di ingrandimento". Il primo elemento che corrisponde alla ricerca appare selezionato nella mappa.<br />3.  Per personalizzare la ricerca, aprire l'elenco a discesa e scegliere un'opzione di ricerca. Le opzioni disponibili sono **Trova successivo**, **Trova precedente**, e **Seleziona tutto**. Fare quindi clic sul pulsante corrispondente accanto alla casella di testo di ricerca.<br />     ![Elenco di opzioni di ricerca&#45;elenco a discesa](../modeling/media/almcodemapssearchdropdown.png)<br />     In alternativa, usare la tastiera: premere **F3** per selezionare il nodo corrispondente successivo o **MAIUSC+F3** per selezionare il nodo corrispondente precedente.<br />4.  Selezionare una delle opzioni che specificano come gestire i termini di ricerca facendo clic sulle icone disponibili sotto la casella di testo di ricerca.<br />     ![Opzioni di corrispondenza ricerca](../modeling/media/almcodemapssearchmatchicons.png)<br />     Da sinistra a destra, le opzioni sono, corrispondenza con distinzione tra maiuscole e minuscole, corrispondenza solo con parole intere, uso della sintassi per le espressioni regolari .NET, espansione automatica dei gruppi per mostrare le corrispondenze per gli elementi inclusi. **Importante:**  È possibile usare la casella di ricerca per trovare corrispondenze nei gruppi compressi solo se questi sono stati espansi in precedenza. Per trovare queste corrispondenze ed espandere automaticamente i relativi gruppi padre, scegliere questa opzione sotto la casella di ricerca.|
|Selezionare tutti i nodi non selezionati.|Aprire il menu di scelta rapida per i nodi selezionati. Scegli **selezionate**, **Inverti selezione**.|
|Selezionare altri nodi che si collegano a quelli selezionati.|Aprire il menu di scelta rapida per i nodi selezionati. Scegli **seleziona** e uno dei seguenti:<br /><br /> -Per selezionare altri nodi collegati direttamente al nodo selezionato, scegliere **dipendenze in ingresso**.<br />-Per selezionare altri nodi collegati direttamente dal nodo selezionato, scegliere **dipendenze in uscita**.<br />-Per selezionare altri nodi collegati direttamente da e verso il nodo selezionato, scegliere **entrambi**.<br />-Per selezionare tutti i nodi che si collegano al e dal nodo selezionato, scegliere **sottografico connesso**.<br />-Per selezionare tutti gli elementi figlio del nodo selezionato, scegliere **figli**.|

##  <a name="FilterNodes"></a> Filtrare nodi e collegamenti

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Visualizzare o nascondere il riquadro Filtri.|Scegliere il **filtri** pulsante sulla barra degli strumenti della mappa codice. Il **filtri** come una pagina a schede in viene visualizzato il riquadro **Esplora soluzioni**, per impostazione predefinita.|
|Filtrare i tipi di nodi visualizzati sulla mappa.|Selezionare o deselezionare le caselle di controllo di **elementi di codice** elenco nel riquadro filtri.|
|Filtrare i tipi di collegamenti visualizzati sulla mappa.|Selezionare o deselezionare le caselle di controllo di **relazioni** elenco nel riquadro filtri.|
|Mostrare o nascondere i nodi del progetto di test sulla mappa.|Selezionare o deselezionare i **gli asset di Test** casella di controllo la **varie** elenco nel riquadro filtri.|

Le icone visualizzate nel riquadro Legenda della mappa riflettono le impostazioni definite nell'elenco. Per mostrare o nascondere il riquadro legenda, fare clic sui **legenda** pulsante sulla barra degli strumenti della mappa codice.

##  <a name="Inspect"></a> Esaminare nodi e collegamenti

Le mappe codice mostrano i tipi di collegamenti seguenti:

-   Un singolo collegamento rappresenta una singola relazione tra due nodi.

-   Un collegamento tra gruppi rappresenta un relazione tra due nodi in gruppi diversi.

-   Un collegamento di aggregazione rappresenta tutte le relazioni che puntano nella stessa direzione tra due gruppi.

> [!TIP]
> Per impostazione predefinita, la mappa mostra i collegamenti tra gruppi solo per i nodi selezionati. Per modificare questo comportamento per mostrare o nascondere collegamenti aggregati tra gruppi, fare clic su **Layout** sul codice di eseguire il mapping della barra degli strumenti e scegliere **Advanced**, quindi **Mostra tutti i collegamenti tra gruppi** o **Nascondi tutti i collegamenti tra gruppi**. Visualizzare [nascondere o mostrare nodi e collegamenti](#HidingShowing) per altri dettagli.

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Visualizzare altre informazioni su un nodo o un collegamento.|Spostare il puntatore del mouse sopra un nodo o un collegamento finché non viene visualizzata una descrizione comando.<br /><br /> La descrizione comando per un collegamento di aggregazione elenca le singole dipendenze che rappresenta.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per il nodo o il collegamento. Scegli **Edit**, **proprietà**.|
|Mostrare o nascondere il contenuto di un gruppo.|-Per espandere un gruppo, aprire il menu di scelta rapida per il nodo e scegliere **gruppo**, **Espandi**.<br />     -oppure-<br />     Spostare il puntatore del mouse sopra il nodo finché non viene visualizzato il pulsante con la freccia di espansione (freccia giù). Fare clic su questo pulsante per espandere il gruppo. Tastiera: per espandere o comprimere il gruppo selezionato, premere il **PLUS** chiave (**+**) o **meno** key (**-**).<br />-Per comprimere un gruppo, aprire il menu di scelta rapida per il nodo e scegliere **gruppo**, **comprimere**.<br />     -oppure-<br />     Spostare il puntatore del mouse sopra un gruppo finché non viene visualizzato il pulsante con la freccia di espansione (freccia su). Fare clic su questo pulsante per comprimere il gruppo.<br />-Per espandere tutti i gruppi, premere **CTRL** + **oggetto** per selezionare tutti i nodi. Aprire il menu di scelta rapida per la mappa e scegliere **gruppo**, **Espandi**. **Nota:**      Questo comando non è disponibile se l'espansione di tutti i gruppi genera una mappa inutilizzabile o problemi di memoria. È consigliabile espandere la mappa solo fino al livello di dettaglio che interessa.<br />-Per comprimere tutti i gruppi, aprire il menu di scelta rapida per un nodo o per la mappa. Scegli **gruppo**, **Comprimi tutto**.|
|Visualizzare la definizione di codice per uno spazio dei nomi, un tipo o un membro.|Aprire il menu di scelta rapida per il nodo e scegliere **Vai a definizione**.<br /><br /> -oppure-<br /><br /> Fare doppio clic sul nodo. Per espandere i gruppi, fare doppio clic sull'intestazione del gruppo.<br /><br /> -oppure-<br /><br /> Selezionare il nodo e premere **F12**.<br /><br /> Ad esempio:<br /><br /> -Per uno spazio dei nomi che contiene una classe, viene aperto il file di codice per la classe per visualizzarne la definizione di tale classe. In altri casi, il **risultati ricerca simbolo** finestra Mostra un elenco di file di codice. **Nota:**      Quando si esegue questa attività su uno spazio dei nomi Visual Basic, il file di codice dietro lo spazio dei nomi non viene aperto. Questo problema si verifica anche quando si esegue questa attività su un gruppo di nodi selezionati che includono uno spazio dei nomi Visual Basic. Per risolvere il problema, individuare manualmente il file di codice associato allo spazio dei nomi oppure omettere dalla selezione il nodo per lo spazio dei nomi.<br />-Per una classe o una classe parziale, si apre il file di codice per la classe per visualizzarne la definizione di classe.<br />-Per un metodo, il file di codice per la classe padre viene aperto per visualizzare la definizione del metodo.|
|Esaminare le dipendenze e gli elementi che fanno parte di un collegamento di aggregazione.|Selezionare i collegamenti si è interessati e aprire il menu di scelta rapida per la selezione. Scegli **Mostra collegamenti partecipanti** oppure **Mostra collegamenti partecipanti sulla nuova mappa codice**.<br /><br /> In Visual Studio i gruppi vengono espansi a entrambe le estremità del collegamento e vengono mostrati solo gli elementi e le dipendenze che partecipano al collegamento. **Nota:**  Quando si esaminano le dipendenze tra gli elementi di gruppi parziali, è possibile osservare il comportamento seguente: <ul><li>Collegamenti ad articoli che non fanno parte dell'analisi vengono nascosti nella mappa, anche se tali collegamenti esistono ancora.</li><li>Si supponga di esaminare un collegamento a un elemento in un gruppo parziale e successivamente di esaminare un collegamento diverso allo stesso elemento. Durante la seconda analisi, il gruppo parziale di destinazione mostra solo gli elementi della prima analisi. I collegamenti ed elementi di destinazione che non fanno parte della prima analisi, ma fanno parte della seconda, non vengono visualizzati.</li></ul> Per visualizzare gli elementi mancanti di un gruppo, scegliere **recupera di nuovo figli**![recupera di nuovo figli icona](../modeling/media/dependencygraph_deletednodesicon.png) (che indica che non tutti i membri di un gruppo vengono visualizzati sulla mappa). È anche possibile annullare le azioni (tastiera: premere **CTRL + Z**) ed esaminare le dipendenze in una nuova mappa.|
|Esaminare le dipendenze tra più nodi in gruppi diversi.|Espandere i gruppi per visualizzare tutti i relativi elementi figlio. Selezionare tutti i nodi che interessano, inclusi i relativi elementi figlio. La mappa mostra i collegamenti tra gruppi tra i nodi selezionati.<br /><br /> Per selezionare tutti i nodi in un gruppo, premere e tenere premuto **MAIUSC** e il pulsante sinistro del mouse mentre si disegna un rettangolo intorno a tale gruppo. Per selezionare tutti i nodi su una mappa, premere **CTRL**+**oggetto**. **Suggerimento:**  Per visualizzare i collegamenti tra gruppi in qualsiasi momento, scegliere **Layout** sulla barra degli strumenti della mappa **Advanced**, **Mostra tutti i collegamenti tra gruppi**.|
|Visualizzare gli elementi a cui fa riferimento un nodo o un collegamento.|Aprire il menu di scelta rapida per il nodo e scegliere **Trova tutti i riferimenti**. **Nota:**  Si applica solo quando è impostato l'attributo `Reference` per il nodo o il collegamento nel file della mappa con estensione dgml. Per aggiungere riferimenti a elementi di nodi o collegamenti, vedere [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

##  <a name="HidingShowing"></a> Nascondere o mostrare nodi e collegamenti

Se vengono nascosti, i nodi non possono partecipare ad algoritmi di layout. Per impostazione predefinita, i collegamenti tra gruppi sono nascosti. I collegamenti tra gruppi sono collegamenti singoli che connettono nodi tra gruppi. Quando i gruppi vengono compressi, tutti i collegamenti tra gruppi presenti nella mappa vengono aggregati in singoli collegamenti tra gruppi. Quando si espande un gruppo e si selezionano nodi nel gruppo, i collegamenti tra gruppi vengono visualizzati mostrando le dipendenze nel gruppo.

> [!CAUTION]
> Prima di condividere una mappa creata in Visual Studio Enterprise con utenti che usano Visual Studio Professional, assicurarsi di scoprire tutti i nodi o i collegamenti tra gruppi che si desidera rendere visibili ad altri utenti. In caso contrario, gli utenti non saranno in grado di vedere tali elementi.

### <a name="to-hide-or-show-nodes"></a>Per nascondere o mostrare nodi

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Nascondere nodi selezionati.|1.  Selezionare i nodi da nascondere.<br />2.  Aprire il menu di scelta rapida per i nodi selezionati o per la mappa. Scegli **selezionate**, **Nascondi selezionati**.|
|Nascondere i nodi non selezionati.|1.  Selezionare i nodi che dovranno rimanere visibili.<br />2.  Aprire il menu di scelta rapida per i nodi selezionati o per la mappa. Scegli **selezionate**, **Nascondi deselezionato**.|
|Mostrare i nodi nascosti.|-Per mostrare tutti i nodi nascosti all'interno di un gruppo, assicurarsi innanzitutto che il gruppo sia espanso. Aprire il menu di scelta rapida e scegliere **selezionate**, **Scopri figli**.<br />     -oppure-<br />     Scegliere il **Scopri figli**![Scopri figli icona](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) sull'icona nell'angolo superiore sinistro del gruppo (questo è visibile solo quando sono presenti nodi figlio nascosti).<br />-Per mostrare tutti i nodi nascosti, aprire il menu di scelta rapida per la mappa o un nodo e scegliere **selezionate**, **Mostra tutto**.|

### <a name="to-hide-or-show-links"></a>Per nascondere o mostrare collegamenti

|**Per**|**Sulla barra degli strumenti della mappa, scegliere il Layout, avanzato e quindi scegliere**|
|-|-|
|Mostrare sempre tutti i collegamenti tra gruppi.|**Mostra tutti i collegamenti tra gruppi**. In questo modo i collegamenti aggregati tra gruppi vengono nascosti.|
|Nascondere sempre i collegamenti tra gruppi.|**Nascondi tutti i collegamenti tra gruppi**|
|Mostrare solo i collegamenti tra gruppi per i nodi selezionati.|**Mostra i collegamenti tra gruppi nei nodi selezionati**|
|Nascondere tutti i collegamenti.|**Nascondi tutti i collegamenti**. Per visualizzare di nuovo i collegamenti, scegliere una delle opzioni elencate sopra.|

##  <a name="OrganizeGroups"></a> Nodi del gruppo

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Mostrare nodi contenitore come nodi gruppo o nodi foglia.|Per mostrare nodi contenitore come nodi foglia: consente di selezionare i nodi, aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **Converti in foglia**.<br /><br /> Per mostrare nodi contenitore come nodi gruppo: selezionare i nodi, aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **Converti in gruppo**.|
|Modificare il layout all'interno di un gruppo.|Selezionare il gruppo, aprire il menu di scelta rapida, scegliere **Layout**e selezionare lo stile di layout desiderato.<br /><br /> -oppure-<br /><br /> 1.  Selezionare il gruppo e verificare che sia espanso.<br />2.  Fare di nuovo clic sull'intestazione del gruppo. Verrà visualizzata la barra degli strumenti del gruppo.<br />     ![Grafico delle dipendenze &#45; barra degli strumenti di gruppo](../modeling/media/dependencygraph_group.png)<br />3.  Aprire il **modificare lo stile di layout del gruppo** elenco ![grafico delle dipendenze &#45; sulla barra degli strumenti gruppo &#45; layout](../modeling/media/dependencygraph_grouptoolbar.gif) e scegliere lo stile di layout desiderato.<br /><br /> **Visualizzazione elenco** Riorganizza i membri del gruppo nell'elenco. **Grafico predefinito** Reimposta il layout di gruppo per il layout predefinito della mappa. Per altre opzioni, vedere [modificare il layout della mappa](#Selecting).|
|Aggiungere un nodo a un gruppo.|Trascinare il nodo nel gruppo.<br /><br /> Mentre si trascina il nodo, Visual Studio visualizza un indicatore per mostrare che si sta spostando il nodo.<br /><br /> È inoltre possibile trascinare i nodi da un gruppo.|
|Aggiungere un nodo a un nodo non di gruppo.|Trascinare il nodo nel nodo di destinazione. È possibile convertire qualsiasi nodo di destinazione in un gruppo aggiungendovi nodi.|
|Raggruppare nodi selezionati.|1.  Selezionare i nodi da raggruppare. Sopra l'ultimo nodo selezionato viene visualizzata una barra degli strumenti popup.<br />     ![Barra degli strumenti grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)<br />2.  Sulla barra degli strumenti, scegliere l'icona del quarta **Raggruppa i nodi selezionati** (se il nodo è espanso, avrà cinque icone invece di quattro). Digitare il nome del nuovo gruppo e premere **restituire**.<br />     -oppure-<br />     Selezionare i nodi da raggruppare e aprire il menu di scelta rapida per la selezione. Scegli **gruppo**, **Aggiungi gruppo padre**, digitare il nome per il nuovo gruppo, quindi premere **restituire**.<br /><br /> Il gruppo può essere rinominato. Aprire il menu di scelta rapida per il gruppo e scegliere **Edit**, **proprietà** per aprire la finestra proprietà di Visual Studio. Nel **etichetta** proprietà, rinominare il gruppo in base alle esigenze.|
|Rimuovere i gruppi.|Selezionare il gruppo o i gruppi da rimuovere. Aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **rimuovere il gruppo**.|
|Rimuovere i nodi dal relativo gruppo padre.|Selezionare i nodi da spostare. Aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **Rimuovi da elemento padre**. I nodi vengono rimossi fino al relativo gruppo padre del padre oppure all'esterno di un gruppo se non hanno un gruppo padre del padre.<br /><br /> -oppure-<br /><br /> Selezionare i nodi e trascinarli all'esterno del gruppo.|

##  <a name="AddRemoveNodesLinks"></a> Aggiungere, rimuovere o rinominare i nodi, collegamenti e commenti

Per eseguire il drill-down o semplificare la mappa, è possibile visualizzare più o meno elementi sulla mappa. È anche possibile rinominare gli elementi e aggiungervi commenti.

> [!CAUTION]
> Prima di condividere una mappa creata in Visual Studio Enterprise con utenti che usano Visual Studio Professional, assicurarsi che tutti i gli elementi di codice che si desidera rendere visibili ad altri utenti siano visibili sulla mappa. In caso contrario, gli utenti non saranno in grado di recuperare gli elementi di codice eliminati.

### <a name="add-a-node-for-a-code-element"></a>Aggiungere un nodo per un elemento di codice

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Aggiungere un nuovo nodo generico nella posizione corrente del puntatore del mouse.|1.  Spostare il puntatore del mouse nella posizione sulla mappa in cui si desidera inserire il nuovo elemento di codice e premere **Inserisci**.<br />     -oppure-<br />     Aprire il menu di scelta rapida per la mappa e scegliere **Edit**, **Add**, **nodo generico**.<br />2.  Digitare il nome del nuovo nodo e premere **restituire**.|
|Aggiungere un tipo specifico di nodo elemento di codice nella posizione corrente del puntatore del mouse.|1.  Spostare il puntatore del mouse nella posizione sulla mappa in cui si vuole inserire il nuovo elemento di codice e aprire il menu di scelta rapida per la mappa.<br />2.  Scegli **Edit**, **Add**e selezionare il tipo di nodo desiderato.<br />3.  Digitare il nome del nuovo nodo e premere **restituire**.|
|Aggiungere un tipo specifico o generico di nodo elemento di codice a un gruppo.|1.  Selezionare un nodo gruppo e aprire il menu di scelta rapida.<br />2.  Scegli **Edit**, **Add**e selezionare il tipo di nodo desiderato.<br />3.  Digitare il nome del nuovo nodo e premere **restituire**.|
|Aggiungere un nuovo nodo dello stesso tipo e collegato da un nodo esistente.|1.  Selezionare l'elemento di codice. Sopra di esso verrà visualizzata una barra degli strumenti popup.<br />     ![Barra degli strumenti grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)<br />2.  Sulla barra degli strumenti scegliere la seconda icona **creare un nodo con la stessa categoria di questo nodo e aggiungervi un nuovo collegamento**.<br />3.  Scegliere una posizione sulla mappa in cui inserire il nuovo elemento di codice e fare clic con il pulsante sinistro del mouse.<br />4.  Digitare il nome del nuovo nodo e premere **restituire**.|
|Aggiungere un nuovo nodo generico collegato da un elemento di codice esistente con lo stato attivo.|1.  Uso della tastiera, premere **scheda** fino a quando l'elemento di codice un collegamento dall'ha lo stato attivo (rettangolo punteggiato).<br />2.  Premere **Alt**+**Inserisci**.<br />3.  Digitare il nome del nuovo nodo e premere **restituire**.|
|Aggiungere un nuovo nodo generico che si collega a un elemento di codice esistente con lo stato attivo.|1.  Uso della tastiera, premere **scheda** fino a quando l'elemento di codice a cui collegarsi ha lo stato attivo (rettangolo punteggiato).<br />2.  Premere **Alt**+**MAIUSC**+**Inserisci**.<br />3.  Digitare il nome del nuovo nodo e premere **restituire**.|

|**Per aggiungere elementi di codice per**|**Eseguire questi passaggi**|
|-|-|
|Elementi di codice nella soluzione.|1.  Trovare l'elemento di codice nel **Esplora soluzioni**. Usare la **Esplora soluzioni** casella di ricerca o cercare la soluzione. **Suggerimento:**      Per trovare gli elementi di codice che presentano dipendenze da un tipo o un membro, aprire il menu di scelta rapida per il tipo o il membro **Esplora soluzioni**. Scegliere la relazione che interessa. **Esplora soluzioni** Mostra solo gli elementi di codice con dipendenze specificate.<br />2.  Trascinare gli elementi di codice desiderati nell'area della mappa. È anche possibile trascinare elementi di codice da Visualizzazione classi o da Visualizzatore oggetti.<br />     -oppure-<br />     Nelle **Esplora soluzioni**, selezionare gli elementi di codice che si desidera eseguire il mapping. Quindi, nella **Esplora soluzioni** sulla barra degli strumenti, fare clic su **Mostra in mappa codice**.<br /><br /> Per impostazione predefinita, sulla mappa viene visualizzata la gerarchia del contenitore padre per i nuovi elementi di codice. Usare la **Includi padri** pulsante sulla barra degli strumenti della mappa codice per modificare questo comportamento. Quando è disattivato, solo lo stesso elemento di codice viene aggiunto alla mappa. Per annullare questo comportamento per una sola e drop action, premere e tenere premuto il **CTRL** mentre si trascinano gli elementi di codice alla mappa.<br /><br /> Visual Studio aggiunge elementi di codice per gli elementi di codice di primo livello nella selezione. Per vedere se un elemento di codice contiene altri elementi di codice, spostare il puntatore del mouse sopra l'elemento di codice in modo da visualizzare la freccia di espansione (freccia giù). Fare clic sulla freccia di espansione per espandere l'elemento di codice. Per espandere tutti gli elementi di codice, premere **CTRL**+**oggetto** per selezionare tutti gli elementi, aprire il menu di scelta rapida per la mappa e scegliere **gruppo**, **Espandi** . Questo comando non è disponibile se l'espansione di tutti i gruppi genera una mappa inutilizzabile o problemi di memoria insufficiente.|
|Elementi di codice correlati a elementi di codice sulla mappa.|Scegliere il **Mostra correlati** sulla barra degli strumenti della mappa codice e scegliere il tipo di elementi correlati si è interessati.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per l'elemento di codice. Scegliere una del **Mostra...**  le voci del menu a seconda del tipo di relazione che interessa. Ad esempio, è possibile visualizzare gli elementi a cui fa riferimento l'elemento corrente, gli elementi che fanno riferimento all'elemento corrente, i tipi di base e derivati per classi, i chiamanti del metodo e le classi, gli spazi dei nomi e gli assembly che li contengono.<br /><br /> Per altre informazioni, vedere [in questo argomento](../modeling/map-dependencies-across-your-solutions.md).|
|Assembly .NET (con estensione dll o exe) o file binari compilati.|Trascinare gli assembly o i file binari dall'esterno di Visual Studio su una mappa.<br /><br /> È possibile trascinare da Esplora risorse o Esplora file solo se questo componente e Visual Studio vengono eseguiti allo stesso livello di autorizzazione del controllo di accesso utente. Se, ad esempio, il controllo di accesso utente è attivato e si esegue Visual Studio come amministratore, Esplora risorse o Esplora file blocca l'operazione di trascinamento.|

###  <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Aggiungere un collegamento tra elementi di codice esistenti

1. Selezionare l'elemento di codice sorgente. Sopra l'elemento di codice viene visualizzata una barra degli strumenti.

    ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)

2. Sulla barra degli strumenti, scegliere la prima icona **crea un collegamento da questo nodo a nodo che farà clic successivamente**.

3. Selezionare l'elemento di codice di destinazione. Verrà visualizzato un collegamento tra i due elementi di codice.

**OPPURE**

1. Selezionare l'elemento di codice sorgente nella mappa.

2. Se è installato un mouse, spostare il puntatore del mouse fuori dai limiti della mappa.

3. Aprire il menu di scelta rapida dell'elemento di codice e scegliere **Edit** > **Add** > **collegamento generico**.

4. Premere TAB fino a selezionare l'elemento di codice di destinazione per il collegamento.

5. Premere **INVIO**.

###  <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Aggiungere un commento a un nodo esistente sulla mappa

1.  Selezionare l'elemento di codice. Sopra di esso verrà visualizzata una barra degli strumenti.

     ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)

2.  Sulla barra degli strumenti scegliere la terza icona **creare un nuovo nodo di commento con un nuovo collegamento al nodo selezionato**.

     \- oppure -

     Aprire il menu di scelta rapida per l'elemento di codice e scegliere **Edit** > **nuovo commento**.

3.  Digitare i commenti. Per inserire una nuova riga, premere **Shift** + **invio**.

#### <a name="add-a-comment-to-the-map-itself"></a>Aggiungere un commento alla mappa

1.  Aprire il menu di scelta rapida per la mappa e scegliere **Edit** > **nuovo commento**.

2.  Digitare i commenti. Per inserire una nuova riga, premere **Shift** + **invio**.

###  <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Rinominare un elemento di codice o un collegamento

1.  Selezionare l'elemento di codice o il collegamento da rinominare.

2.  Premere **F2**, o aprire il menu di scelta rapida e scegliere **Edit** > **rinominare**.

3.  Quando viene visualizzata la casella di modifica nella mappa, rinominare l'elemento di codice o il collegamento.

**OPPURE**

1.  Aprire il menu di scelta rapida e scegliere **Edit** > **proprietà**.

2.  Modificare il **etichetta** proprietà nella finestra delle proprietà di Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Rimuovere un elemento di codice o un collegamento dalla mappa

1.  Selezionare l'elemento di codice o link e premere il **eliminare** chiave.

     \- oppure -

     Aprire il menu di scelta rapida per l'elemento di codice o il collegamento e scegliere **Edit** > **rimuovere**.

2.  Se l'elemento o il collegamento fa parte di un gruppo, il **recupera di nuovo figli** pulsante ![recupera di nuovo figli icona](../modeling/media/dependencygraph_deletednodesicon.png) verrà visualizzato nel gruppo. Fare clic su questo pulsante per recuperare elementi e collegamenti mancanti.

-   È possibile rimuovere gli elementi di codice e i collegamenti da una mappa senza influire sul codice sottostante. Se vengono eliminati, le relative definizioni vengono rimosse dal file DGML (con estensione dgml).

-   Le mappe create modificando il file DGML, aggiungendo elementi di codice non definiti o usando versioni precedenti di Visual Studio non supportano questa funzionalità.

#### <a name="flag-a-code-element-for-follow-up"></a>Contrassegnare un elemento di codice per il completamento

1.  Selezionare l'elemento di codice o il collegamento da contrassegnare per il completamento.

2.  Aprire il menu di scelta rapida e scegliere **Edit** > **Flag per completamento**.

-   Per impostazione predefinita, all'elemento di codice viene applicato uno sfondo rosso. Prendere in considerazione [aggiungendo un commento](#AddComments) a esso con le informazioni di completamento appropriate.

-   Modificare il colore di sfondo dell'elemento o cancellare il contrassegno di completamento scegliendo **Edit** > **altri colori Flag**.

##  <a name="ChangeStyleCodeOrLink"></a> Modificare lo stile di un elemento di codice o un collegamento

È possibile modificare le icone per gli elementi di codice e i colori per gli elementi di codice e i collegamenti usando le icone e i colori predefiniti. Ad esempio, è possibile scegliere un colore per evidenziare elementi di codice e collegamenti con una determinata categoria o proprietà. In questo modo si possono identificare aree specifiche della mappa e concentrarsi su di esse. È possibile specificare i colori e icone personalizzate mediante la modifica di file con estensione dgml della mappa. visualizzare [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Per applicare un colore o un'icona predefinita agli elementi di codice o ai collegamenti con una determinata categoria o proprietà

1.  Sulla barra degli strumenti della mappa, scegliere **legenda**.

2.  Nel **legenda** casella, vedere se la categoria di elemento di codice o proprietà già presente nell'elenco.

3.  Se l'elenco non include la categoria o proprietà, scegliere **+** nel **legenda** casella e quindi scegliere **proprietà dei nodi**, **categoria nodo** , **Proprietà collegamento**, o **collegamento categoria**. Scegliere quindi la proprietà o la categoria. La categoria o proprietà sono ora inclusi i **legenda** casella.

    > [!NOTE]
    > Per creare e assegnare una categoria o una proprietà a un elemento di codice, è possibile modificare i file con estensione dgml della mappa. visualizzare [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4.  Nel **legenda** finestra, fai clic sull'icona accanto alla categoria o proprietà è stato aggiunto o si desidera modificare.

5.  Utilizzare la tabella seguente per selezionare lo stile che si desidera modificare:

    |**Per modificare il**|**Choose**|
    |-|-|
    |Colore di sfondo|**Sfondo**|
    |Colore del contorno|**Tratto**|
    |Colore del testo (una lettera "f" viene visualizzata per mostrare il risultato)|**Foreground**|
    |Icona|**Icone**|

     Il **selezione Set colori** oppure **selezione Set icone** verrà visualizzata la finestra di dialogo per selezionare un colore o icona.

6.  Nel **selezione Set colori** oppure **selezione Set icone** nella finestra di dialogo, effettuare una delle operazioni seguenti:

    |**Per applicare un**|**Eseguire questi passaggi**|
    |-|-|
    |Set di colori o di icone|Aprire il **Seleziona colore** (o **icona**) **impostare** elenco. Selezionare un set di colori o di icone.|
    |Colore o icona specifica|Aprire l'elenco di valori della proprietà o della categoria. Selezionare un colore o un'icona.|

    > [!NOTE]
    > È possibile ridisporre, eliminare o disattivare temporaneamente stili nella **legenda** casella. Visualizzare [modificare la casella legenda](#ModifyLegend).

##  <a name="ModifyLegend"></a> Modificare la casella legenda

È possibile ridisporre, eliminare o disattivare temporaneamente stili nella **legenda** casella:

1.  Aprire il menu di scelta rapida per uno stile nel **legenda** casella.

2.  Effettuare una delle attività seguenti:

    |**Per**|**Choose**|
    |-|-|
    |Disattivare l'elemento di codice|**Disabilitato**|
    |Eliminare l'elemento di codice|**Eliminazione**|
    |Spostare lo stile in alto|**Spostare verso l'alto**|
    |Spostare l'elemento di codice in basso|**Sposta giù**|

##  <a name="CopyLegend"></a> Copiare stili da una mappa a un altro

1.  Assicurarsi che il **legenda** verrà visualizzata la finestra nella mappa di origine. Se non è visibile, nella barra degli strumenti della mappa, fare clic su **legenda**.

2.  Aprire il menu di scelta rapida per il **legenda** casella. Scegli **Copia legenda**.

3.  Incollare la legenda nella mappa di destinazione.

##  <a name="MergeMaps"></a> Unire le mappe codice

È possibile unire le mappe copiando e incollando gli elementi di codice tra le mappe. Se gli identificatori degli elementi di codice corrispondono, l'operazione per incollare gli elementi di codice funziona come un'operazione di unione. Per semplificare questa attività, inserire tutti gli assembly o i file binari da visualizzare nella stessa cartella, in modo che il percorso completo di ogni assembly o file binario sia lo stesso per ogni mappa da unire.

In alternativa, è possibile trascinare gli assembly o file binari da tale cartella nella stessa mappa.

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Riferimento di Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
