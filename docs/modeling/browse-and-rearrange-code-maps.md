---
title: Cercare e ridisporre le mappe codice
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 443d272216eaf88bcbd4dcb75c034779403f1ef7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666607"
---
# <a name="browse-and-rearrange-code-maps"></a>Cercare e ridisporre le mappe codice

È possibile riorganizzare gli elementi nelle mappe codice per facilitarne la lettura e migliorarne le prestazioni.

Le mappe codice possono essere personalizzate senza influire sul codice sottostante di una soluzione. Questa operazione risulta utile quando si vuole concentrarsi sugli elementi di codice principali o comunicare informazioni sul codice. Ad esempio, per evidenziare aree interessanti, è possibile selezionare elementi di codice sulla mappa e filtrarli, modificarne lo stile e i collegamenti, nascondere o eliminare elementi di codice e organizzarli tramite proprietà, categorie o gruppi.

 **Requirements**

- Per creare mappe codice, è necessario usare Visual Studio Enterprise.

- È possibile visualizzare le mappe codice e apportarvi modifiche limitate in Visual Studio Professional.

## <a name="ManageLargeGraphs"></a>Introduzione all'uso delle mappe codice

Creare una mappa del codice. per altri dettagli, vedere [eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) . Se non si desidera attendere il completamento della generazione della mappa, fare clic sul collegamento **Annulla** in qualsiasi momento per arrestare il processo di generazione. In questo caso, non sarà però possibile vedere i dettagli di tutte le dipendenze e tutti i collegamenti.

Dopo aver generato la mappa, iniziare la revisione del codice attenendosi ai suggerimenti seguenti:

- Osservare i cluster di dipendenze naturali all'interno del codice. Sulla barra degli strumenti della mappa scegliere **layout**, **cluster rapidi** ![Quick pulsante cluster sulla barra degli strumenti del grafico ](../modeling/media/quickclustersicon.gif). Vedere [modificare il layout della mappa](#Selecting).

     ![Layout del &#45; cluster rapido del grafico dipendenze](../modeling/media/dependencygraph_quickclusters.png)

- Organizzare la mappa in aree più piccole mediante il raggruppamento dei nodi correlati. Comprimere i gruppi per visualizzare solo le dipendenze intergruppi, che appaiono automaticamente. Vedere [nodi gruppo](#OrganizeGroups).

- Usare i filtri per semplificare la mappa e per concentrarsi sui tipi di nodi o di collegamenti a cui si è interessati. Vedere [filtrare nodi e collegamenti](#FilterNodes).

- Ottimizzare le prestazioni delle mappe di grandi dimensioni. Per altre informazioni, vedere [eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) . Ad esempio, attivare **Ignora compilazione** sulla barra degli strumenti della mappa in modo che Visual Studio non ricostruisca la soluzione quando si aggiornano gli elementi sulla mappa.

## <a name="Selecting"></a>Modificare il layout della mappa

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Disporre il flusso delle dipendenze per l'intera mappa in una direzione specifica. In questo modo si potranno vedere i livelli di architettura nel codice.|Sulla barra degli strumenti della mappa scegliere **layout**, quindi:<br /><br /> -    pulsante**dall'alto verso il basso** ![Top al grafico inferiore ](../modeling/media/topbottomgraphbutton.gif)<br />-    pulsante**dal basso verso l'alto** ![Bottom al grafico superiore ](../modeling/media/bottomtopgraphbutton.gif)<br />-    da**sinistra a destra** ![Left pulsante di layout a destra ](../modeling/media/leftrightgraphbutton.gif)<br />-    pulsante da**destra a sinistra** ![Right a sinistra del grafico ](../modeling/media/rightleftgraphbutton.gif)|
|Visualizzare cluster di dipendenze naturali all'interno del codice con i nodi che presentano un maggior numero di dipendenze al centro dei cluster e quelli con meno dipendenze all'esterno.|Sulla barra degli strumenti della mappa scegliere **layout**e quindi **cluster veloce** ![Quick pulsante cluster sulla barra degli strumenti del grafico ](../modeling/media/quickclustersicon.gif).|
|Selezionare uno o più nodi sulla mappa.|Fare clic su un nodo per selezionarlo. Per selezionare o deselezionare più di un nodo, tenere premuto **CTRL** mentre si fa clic su.<br /><br /> Tastiera: premere **Tab** o usare i tasti di direzione per spostare il rettangolo di attivazione punteggiata in un nodo e premere **lo spazio** per selezionarlo. Premere **CTRL**  + **spazio** per selezionare o deselezionare i nodi.|
|Spostare nodi specifici sulla mappa.|Trascinare i nodi per spostarli. Per spostare altri nodi e collegamenti fuori dalla modalità di trascinamento dei nodi, tenere premuto il tasto **MAIUSC** .<br /><br /> Tastiera: tenere premuto **CTRL** e premere i tasti di direzione.|
|Modificare il layout all'interno di un gruppo indipendentemente dagli altri nodi e gruppi sulla mappa.|Selezionare un nodo e aprire il menu di scelta rapida. Scegliere **layout** e selezionare uno stile di layout.<br /><br /> -oppure-<br /><br /> Selezionare un nodo ed espanderlo per visualizzare i nodi figlio. Fare clic sul titolo del nodo per visualizzare la barra degli strumenti popup del gruppo e aprire l'elenco **modificare lo stile di layout del gruppo** ![Dependency grafico &#45; ](../modeling/media/dependencygraph_grouptoolbar.gif) layout della barra degli strumenti &#45; . Selezionare uno dei layout di struttura ad albero, i **cluster rapidi**o la **visualizzazione elenco** (che consente di disporre il contenuto del gruppo in un elenco).<br /><br /> Per altri dettagli, vedere [nodi gruppo](#OrganizeGroups) .|
|Annullare un'azione nella mappa.|Premere **CTRL**  + **Z** o usare il comando **Annulla** di Visual Studio.|

## <a name="Explore"></a>Esplorare la mappa

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Analizzare la mappa.|Trascinare la mappa in qualsiasi direzione usando il mouse.<br /><br /> -oppure-<br /><br /> Tenere premuto **MAIUSC** e ruotare la rotellina del mouse per scorrere orizzontalmente. Tenere premuto **maiusc**  + **CTRL** e ruotare la rotellina del mouse per scorrere orizzontalmente.|
|Ingrandire o ridurre la mappa.|Ruotare la rotellina del mouse.<br /><br /> -oppure-<br /><br /> Usare l'elenco a discesa **Zoom** sulla barra degli strumenti della mappa codice.<br /><br /> -oppure-<br /><br /> Usare i tasti di scelta rapida. Per eseguire lo zoom avanti, premere **CTRL + MAIUSC +.** (punto). Per eseguire lo zoom indietro, premere **CTRL + MAIUSC +,** (virgola).|
|Ingrandire un'area specifica usando il mouse.|Tenere premuto il pulsante destro del mouse mentre si disegna un rettangolo intorno all'area di interesse.|
|Ridimensionare e adattare la mappa alla relativa finestra.|Scegliere **zoom per adattarlo** dall'elenco **Zoom** sulla barra degli strumenti della mappa codice.<br /><br /> -oppure-<br /><br /> Fare clic sull'icona ![Zoom icona **adatta allo zoom** sulla barra degli strumenti della mappa ](../modeling/media/almcodemapzoomicon.png) sulla barra degli strumenti della mappa codice. Tastiera: premere **CTRL + 0** (zero).|
|Trovare un nodo sulla mappa in base al nome. **Suggerimento:**  Funziona solo per gli elementi della mappa. Per trovare gli elementi nella soluzione, ma non nella mappa, individuarli in **Esplora soluzioni**, quindi trascinarli nella mappa. Trascinare la selezione oppure fare clic su **Mostra in mappa codice**sulla barra degli strumenti **Esplora soluzioni** .|1. scegliere l'icona **trova** ![Find icona nella barra degli strumenti della mappa ](../modeling/media/almcodemapfindicon.png) sulla barra degli strumenti della mappa codice (tastiera: premere **CTRL + F**) per visualizzare la casella di ricerca nell'angolo superiore destro della mappa.<br />2. digitare il nome dell'elemento e premere **invio** oppure fare clic sull'icona "Magnifier". Il primo elemento che corrisponde alla ricerca viene visualizzato nella mappa.<br />3. per personalizzare la ricerca, aprire l'elenco a discesa e scegliere un'opzione di ricerca. Le opzioni disponibili sono **Trova successivo**, **Trova precedente**e **Seleziona tutto**. Fare quindi clic sul pulsante corrispondente accanto alla casella di testo di ricerca.<br />     elenco a discesa&#45;opzioni ![Search ](../modeling/media/almcodemapssearchdropdown.png)<br />     In alternativa, usare la tastiera: premere **F3** per selezionare il nodo corrispondente successivo o **MAIUSC + F3** per selezionare il nodo corrispondente precedente.<br />4. Selezionare una delle opzioni che specificano la modalità di gestione dei termini di ricerca facendo clic sulle icone sotto la casella di testo di ricerca.<br />     opzioni di ![Search corrispondenza ](../modeling/media/almcodemapssearchmatchicons.png)<br />     Da sinistra a destra, le opzioni sono, corrispondenza con distinzione tra maiuscole e minuscole, corrispondenza solo con parole intere, uso della sintassi per le espressioni regolari .NET, espansione automatica dei gruppi per mostrare le corrispondenze per gli elementi inclusi. **Importante:**  È possibile usare la casella di ricerca per trovare le corrispondenze nei gruppi compressi solo se tali gruppi sono stati espansi in precedenza. Per trovare queste corrispondenze ed espandere automaticamente i relativi gruppi padre, scegliere questa opzione sotto la casella di ricerca.|
|Selezionare tutti i nodi non selezionati.|Aprire il menu di scelta rapida per i nodi selezionati. Scegliere **Seleziona**, **Inverti selezione**.|
|Selezionare altri nodi che si collegano a quelli selezionati.|Aprire il menu di scelta rapida per i nodi selezionati. Scegliere **Seleziona** e uno dei seguenti:<br /><br /> -Per selezionare nodi aggiuntivi collegati direttamente al nodo selezionato, scegliere **dipendenze in ingresso**.<br />-Per selezionare nodi aggiuntivi che si collegano direttamente dal nodo selezionato, scegliere **dipendenze in uscita**.<br />-Per selezionare nodi aggiuntivi che si collegano direttamente al e dal nodo selezionato, scegliere **entrambi**.<br />-Per selezionare tutti i nodi che si collegano al e dal nodo selezionato, scegliere **Sottografico connesso**.<br />-Per selezionare tutti gli elementi figlio del nodo selezionato, scegliere **figli**.|

## <a name="FilterNodes"></a>Filtrare nodi e collegamenti

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Visualizzare o nascondere il riquadro Filtri.|Scegliere il pulsante **filtri** sulla barra degli strumenti della mappa codice. Per impostazione predefinita, il riquadro **filtri** viene visualizzato come pagina a schede in **Esplora soluzioni**.|
|Filtrare i tipi di nodi visualizzati sulla mappa.|Impostare o deselezionare le caselle di controllo nell'elenco **elementi di codice** nel riquadro filtri.|
|Filtrare i tipi di collegamenti visualizzati sulla mappa.|Impostare o deselezionare le caselle di controllo nell'elenco **relazioni** nel riquadro filtri.|
|Mostrare o nascondere i nodi del progetto di test sulla mappa.|Impostare o deselezionare la casella di **controllo asset test** nell'elenco **varie** nel riquadro filtri.|

Le icone visualizzate nel riquadro Legenda della mappa riflettono le impostazioni definite nell'elenco. Per visualizzare o nascondere il pannello legenda, fare clic sul pulsante **Legenda** sulla barra degli strumenti della mappa codice.

## <a name="Inspect"></a>Esaminare nodi e collegamenti

Le mappe codice mostrano i tipi di collegamenti seguenti:

- Un singolo collegamento rappresenta una singola relazione tra due nodi.

- Un collegamento tra gruppi rappresenta un relazione tra due nodi in gruppi diversi.

- Un collegamento di aggregazione rappresenta tutte le relazioni che puntano nella stessa direzione tra due gruppi.

> [!TIP]
> Per impostazione predefinita, la mappa mostra i collegamenti tra gruppi solo per i nodi selezionati. Per modificare questo comportamento per mostrare o nascondere i collegamenti aggregati tra gruppi, fare clic su **layout** sulla barra degli strumenti della mappa codice e scegliere **Avanzate**, quindi **Mostra tutti i** collegamenti tra gruppi o **Nascondi tutti i collegamenti**tra gruppi. Per altri dettagli, vedere [nascondere o visualizzare nodi e collegamenti](#HidingShowing) .

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Visualizzare altre informazioni su un nodo o un collegamento.|Spostare il puntatore del mouse sopra un nodo o un collegamento finché non viene visualizzata una descrizione comando.<br /><br /> La descrizione comando per un collegamento di aggregazione elenca le singole dipendenze che rappresenta.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per il nodo o il collegamento. Scegliere **modifica**, **Proprietà**.|
|Mostrare o nascondere il contenuto di un gruppo.|-Per espandere un gruppo, aprire il menu di scelta rapida per il nodo e scegliere **gruppo**, **Espandi**.<br />     -oppure-<br />     Spostare il puntatore del mouse sopra il nodo finché non viene visualizzato il pulsante con la freccia di espansione (freccia giù). Fare clic su questo pulsante per espandere il gruppo. Tastiera: per espandere o comprimere il gruppo selezionato, premere il tasto **più** ( **+** ) o il tasto **meno** ( **-** ).<br />-Per comprimere un gruppo, aprire il menu di scelta rapida per il nodo e scegliere **gruppo**, **Comprimi**.<br />     -oppure-<br />     Spostare il puntatore del mouse sopra un gruppo finché non viene visualizzato il pulsante con la freccia di espansione (freccia su). Fare clic su questo pulsante per comprimere il gruppo.<br />-Per espandere tutti i gruppi, premere **CTRL**  + **a** per selezionare tutti i nodi. Aprire il menu di scelta rapida per la mappa e scegliere **gruppo**, **Espandi**. **Nota:**      Questo comando non è disponibile se l'espansione di tutti i gruppi genera una mappa inutilizzabile o problemi di memoria. È consigliabile espandere la mappa solo fino al livello di dettaglio che interessa.<br />-Per comprimere tutti i gruppi, aprire il menu di scelta rapida per un nodo o per la mappa. Scegliere **gruppo**, **Comprimi tutto**.|
|Visualizzare la definizione di codice per uno spazio dei nomi, un tipo o un membro.|Aprire il menu di scelta rapida per il nodo e scegliere **Vai a definizione**.<br /><br /> oppure<br /><br /> Fare doppio clic sul nodo. Per espandere i gruppi, fare doppio clic sull'intestazione del gruppo.<br /><br /> oppure<br /><br /> Selezionare il nodo e premere **F12**.<br /><br /> Esempio:<br /><br /> -Per uno spazio dei nomi contenente una classe, viene aperto il file di codice per la classe per visualizzare la definizione di tale classe. In altri casi, la finestra **Risultati ricerca simbolo** Visualizza un elenco di file di codice. **Nota:**      Quando si esegue questa attività in uno spazio dei nomi Visual Basic, il file di codice dietro lo spazio dei nomi non viene aperto. Questo problema si verifica anche quando si esegue questa attività su un gruppo di nodi selezionati che includono uno spazio dei nomi Visual Basic. Per risolvere il problema, individuare manualmente il file di codice associato allo spazio dei nomi oppure omettere dalla selezione il nodo per lo spazio dei nomi.<br />-Per una classe o una classe parziale, viene aperto il file di codice per tale classe per visualizzare la definizione della classe.<br />-Per un metodo, viene aperto il file di codice per la classe padre per visualizzare la definizione del metodo.|
|Esaminare le dipendenze e gli elementi che fanno parte di un collegamento di aggregazione.|Selezionare i collegamenti a cui si è interessati e aprire il menu di scelta rapida per la selezione. Scegliere **Mostra collegamenti partecipanti** o **Mostra collegamenti che contribuiscono alla nuova mappa del codice**.<br /><br /> In Visual Studio i gruppi vengono espansi a entrambe le estremità del collegamento e vengono mostrati solo gli elementi e le dipendenze che partecipano al collegamento. **Nota:**  Quando si esaminano le dipendenze tra elementi in gruppi parziali, è possibile che venga visualizzato questo comportamento: <ul><li>I collegamenti a elementi che non partecipano all'esame scompaiono dalla mappa, anche se tali collegamenti esistono ancora.</li><li>Si supponga di esaminare un collegamento a un elemento in un gruppo parziale e successivamente di esaminare un collegamento diverso allo stesso elemento. Durante la seconda analisi, il gruppo parziale di destinazione mostra solo gli elementi della prima analisi. I collegamenti e gli elementi di destinazione che non hanno partecipato al primo esame ma che partecipano al secondo esame non vengono visualizzati.</li></ul> Per visualizzare gli elementi mancanti da un gruppo, scegliere **rifetch children** ![Refetch children icon ](../modeling/media/dependencygraph_deletednodesicon.png), che indica che non tutti i membri di un gruppo vengono visualizzati nella mappa. È anche possibile provare a eseguire le azioni (tastiera: premere **CTRL + Z**) ed esaminare le dipendenze su una nuova mappa.|
|Esaminare le dipendenze tra più nodi in gruppi diversi.|Espandere i gruppi per visualizzare tutti i relativi elementi figlio. Selezionare tutti i nodi che interessano, inclusi i relativi elementi figlio. La mappa mostra i collegamenti tra gruppi tra i nodi selezionati.<br /><br /> Per selezionare tutti i nodi in un gruppo, tenere premuto **MAIUSC** e il pulsante sinistro del mouse mentre si estrae un rettangolo attorno a tale gruppo. Per selezionare tutti i nodi in una mappa, premere **CTRL** +**a**. **Suggerimento:**  Per visualizzare sempre i collegamenti tra gruppi, scegliere **layout** sulla barra degli strumenti della mappa, **Avanzate**, **Mostra tutti i collegamenti tra gruppi**.|
|Visualizzare gli elementi a cui fa riferimento un nodo o un collegamento.|Aprire il menu di scelta rapida per il nodo e scegliere **Trova tutti i riferimenti**. **Nota:**  Si applica solo quando l'attributo `Reference` è impostato per il nodo o il collegamento nel file con estensione dgml della mappa. Per aggiungere riferimenti a elementi da nodi o collegamenti, vedere [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="HidingShowing"></a>Nascondere o visualizzare nodi e collegamenti

Se vengono nascosti, i nodi non possono partecipare ad algoritmi di layout. Per impostazione predefinita, i collegamenti tra gruppi sono nascosti. I collegamenti tra gruppi sono collegamenti singoli che connettono nodi tra gruppi. Quando i gruppi vengono compressi, tutti i collegamenti tra gruppi presenti nella mappa vengono aggregati in singoli collegamenti tra gruppi. Quando si espande un gruppo e si selezionano nodi nel gruppo, i collegamenti tra gruppi vengono visualizzati mostrando le dipendenze nel gruppo.

> [!CAUTION]
> Prima di condividere una mappa creata in Visual Studio Enterprise con utenti che usano Visual Studio Professional, assicurarsi di scoprire tutti i nodi o i collegamenti tra gruppi che si desidera rendere visibili ad altri utenti. In caso contrario, gli utenti non saranno in grado di vedere tali elementi.

### <a name="to-hide-or-show-nodes"></a>Per nascondere o mostrare nodi

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Nascondere nodi selezionati.|1. Selezionare i nodi che si desidera nascondere.<br />2. Aprire il menu di scelta rapida per i nodi selezionati o per la mappa. Scegliere **Seleziona**, **Nascondi selezionato**.|
|Nascondere i nodi non selezionati.|1. Selezionare i nodi che si desidera mantenere visibili.<br />2. Aprire il menu di scelta rapida per i nodi selezionati o per la mappa. Scegliere **Seleziona**, **Nascondi non selezionato**.|
|Mostrare i nodi nascosti.|-Per visualizzare tutti i nodi nascosti all'interno di un gruppo, verificare innanzitutto che il gruppo sia espanso. Aprire il menu di scelta rapida e scegliere **Seleziona**, **Scopri elementi figlio**.<br />     -oppure-<br />     Fare clic sull'icona **Unhide children** ![Unhide Children ](../modeling/media/dependencygraph_filtericon_hiddennodes.gif) icona nell'angolo superiore sinistro del gruppo. questa operazione è visibile solo quando sono presenti nodi figlio nascosti.<br />-Per visualizzare tutti i nodi nascosti, aprire il menu di scelta rapida per la mappa o un nodo e scegliere **Seleziona**, **Scopri tutto**.|

### <a name="to-hide-or-show-links"></a>Per nascondere o mostrare collegamenti

|**Per**|**Sulla barra degli strumenti della mappa scegliere layout, avanzate, quindi scegliere**|
|-|-|
|Mostrare sempre tutti i collegamenti tra gruppi.|**Mostra tutti i collegamenti tra gruppi**. In questo modo i collegamenti aggregati tra gruppi vengono nascosti.|
|Nascondere sempre i collegamenti tra gruppi.|**Nascondi tutti i collegamenti tra gruppi**|
|Mostrare solo i collegamenti tra gruppi per i nodi selezionati.|**Mostra collegamenti tra gruppi nei nodi selezionati**|
|Nascondere tutti i collegamenti.|**Nascondi tutti i collegamenti**. Per visualizzare di nuovo i collegamenti, scegliere una delle opzioni elencate sopra.|

## <a name="OrganizeGroups"></a>Nodi gruppo

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Mostrare nodi contenitore come nodi gruppo o nodi foglia.|Per visualizzare i nodi del contenitore come nodi foglia: selezionare i nodi, aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **Converti in foglia**.<br /><br /> Per visualizzare i nodi del contenitore come nodi Gruppo: selezionare i nodi, aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **Converti in gruppo**.|
|Modificare il layout all'interno di un gruppo.|Selezionare il gruppo, aprire il menu di scelta rapida, scegliere **layout**e selezionare lo stile di layout desiderato.<br /><br /> -oppure-<br /><br /> 1. Selezionare il gruppo e verificare che sia espanso.<br />2. fare di nuovo clic sull'intestazione di gruppo per visualizzare la barra degli strumenti del gruppo.<br />     barra degli &#45; strumenti del gruppo ![Dependency Graph ](../modeling/media/dependencygraph_group.png)<br />3. Aprire la **modifica dello stile di layout dell'elenco di gruppi** ![Dependency &#45; layout della &#45; barra degli strumenti del gruppo di grafici ](../modeling/media/dependencygraph_grouptoolbar.gif) e scegliere lo stile di layout desiderato.<br /><br /> **Visualizzazione elenco** riorganizza i membri del gruppo nell'elenco. **Grafico predefinito** Reimposta il layout del gruppo sul layout predefinito della mappa. Per altre opzioni, vedere [modificare il layout della mappa](#Selecting).|
|Aggiungere un nodo a un gruppo.|Trascinare il nodo nel gruppo.<br /><br /> Mentre si trascina il nodo, Visual Studio visualizza un indicatore per mostrare che si sta spostando il nodo.<br /><br /> È inoltre possibile trascinare i nodi da un gruppo.|
|Aggiungere un nodo a un nodo non di gruppo.|Trascinare il nodo nel nodo di destinazione. È possibile convertire qualsiasi nodo di destinazione in un gruppo aggiungendovi nodi.|
|Raggruppare nodi selezionati.|1. Selezionare i nodi che si desidera raggruppare. Sopra l'ultimo nodo selezionato viene visualizzata una barra degli strumenti popup.<br />     barra degli strumenti grafico ![Dependency ](../modeling/media/depedencygraph_toolbar.png)<br />2. sulla barra degli strumenti scegliere la quarta icona **raggruppa i nodi selezionati** . se il nodo è espanso, avrà cinque anziché quattro icone. Digitare il nome del nuovo gruppo e premere **invio**.<br />     -oppure-<br />     Selezionare i nodi da raggruppare e aprire il menu di scelta rapida per la selezione. Scegliere **gruppo**, **Aggiungi gruppo padre**, digitare il nome del nuovo gruppo e premere **invio**.<br /><br /> Il gruppo può essere rinominato. Aprire il menu di scelta rapida per il gruppo e scegliere **modifica**, **Proprietà** per aprire Visual Studio finestra Proprietà. Nella proprietà **Label** rinominare il gruppo in modo che sia necessario.|
|Rimuovere i gruppi.|Selezionare il gruppo o i gruppi da rimuovere. Aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **Rimuovi gruppo**.|
|Rimuovere i nodi dal relativo gruppo padre.|Selezionare i nodi da spostare. Aprire il menu di scelta rapida per la selezione e scegliere **gruppo**, **Rimuovi da elemento padre**. I nodi vengono rimossi fino al relativo gruppo padre del padre oppure all'esterno di un gruppo se non hanno un gruppo padre del padre.<br /><br /> -oppure-<br /><br /> Selezionare i nodi e trascinarli all'esterno del gruppo.|

## <a name="AddRemoveNodesLinks"></a>Aggiunta, rimozione o ridenominazione di nodi, collegamenti e commenti

Per eseguire il drill-down o semplificare la mappa, è possibile visualizzare più o meno elementi sulla mappa. È anche possibile rinominare gli elementi e aggiungervi commenti.

> [!CAUTION]
> Prima di condividere una mappa creata in Visual Studio Enterprise con utenti che usano Visual Studio Professional, assicurarsi che tutti i gli elementi di codice che si desidera rendere visibili ad altri utenti siano visibili sulla mappa. In caso contrario, gli utenti non saranno in grado di recuperare gli elementi di codice eliminati.

### <a name="add-a-node-for-a-code-element"></a>Aggiungere un nodo per un elemento di codice

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Aggiungere un nuovo nodo generico nella posizione corrente del puntatore del mouse.|1. spostare il puntatore del mouse nella posizione sulla mappa in cui si vuole inserire il nuovo elemento di codice e premere **ins**.<br />     -oppure-<br />     Aprire il menu di scelta rapida per la mappa e scegliere **modifica**, **Aggiungi**, **nodo generico**.<br />2. digitare il nome del nuovo nodo e premere **invio**.|
|Aggiungere un tipo specifico di nodo elemento di codice nella posizione corrente del puntatore del mouse.|1. spostare il puntatore del mouse nella posizione sulla mappa in cui si vuole inserire il nuovo elemento di codice e aprire il menu di scelta rapida per la mappa.<br />2. scegliere **modifica**, **Aggiungi**e selezionare il tipo di nodo desiderato.<br />3. digitare il nome del nuovo nodo e premere **invio**.|
|Aggiungere un tipo specifico o generico di nodo elemento di codice a un gruppo.|1. Selezionare il nodo gruppo e aprire il menu di scelta rapida.<br />2. scegliere **modifica**, **Aggiungi**e selezionare il tipo di nodo desiderato.<br />3. digitare il nome del nuovo nodo e premere **invio**.|
|Aggiungere un nuovo nodo dello stesso tipo e collegato da un nodo esistente.|1. Selezionare l'elemento di codice. Sopra di esso verrà visualizzata una barra degli strumenti popup.<br />     barra degli strumenti grafico ![Dependency ](../modeling/media/depedencygraph_toolbar.png)<br />2. sulla barra degli strumenti scegliere la seconda icona **Crea un nodo con la stessa categoria di questo nodo e Aggiungi un nuovo collegamento**.<br />3. scegliere una posizione sulla mappa in cui inserire il nuovo elemento di codice e fare clic sul pulsante sinistro del mouse.<br />4. digitare il nome del nuovo nodo e premere **invio**.|
|Aggiungere un nuovo nodo generico collegato da un elemento di codice esistente con lo stato attivo.|1. utilizzando la tastiera, premere **Tab** fino a quando l'elemento di codice per il collegamento non ha lo stato attivo (rettangolo tratteggiato).<br />2. Premere **Alt** +**Inserisci**.<br />3. digitare il nome del nuovo nodo e premere **invio**.|
|Aggiungere un nuovo nodo generico che si collega a un elemento di codice esistente con lo stato attivo.|1. utilizzando la tastiera, premere **Tab** fino a quando l'elemento di codice a cui collegarsi ha lo stato attivo (rettangolo tratteggiato).<br />2. Premere **Alt** +**MAIUSC** +**Inserisci**.<br />3. digitare il nome del nuovo nodo e premere **invio**.|

|**Per aggiungere elementi di codice per**|**Eseguire questi passaggi**|
|-|-|
|Elementi di codice nella soluzione.|1. trovare l'elemento di codice in **Esplora soluzioni**. Utilizzare la casella di ricerca **Esplora soluzioni** o esplorare la soluzione. **Suggerimento:**      Per trovare gli elementi di codice con dipendenze da un tipo o un membro, aprire il menu di scelta rapida per il tipo o il membro in **Esplora soluzioni**. Scegliere la relazione che interessa. **Esplora soluzioni** Mostra solo gli elementi di codice con le dipendenze specificate.<br />2. trascinare gli elementi di codice che interessano la superficie della mappa. È anche possibile trascinare elementi di codice da Visualizzazione classi o da Visualizzatore oggetti.<br />     -oppure-<br />     In **Esplora soluzioni**selezionare gli elementi di codice di cui si desidera eseguire il mapping. Quindi, sulla barra degli strumenti **Esplora soluzioni** fare clic su **Mostra in mappa codici**.<br /><br /> Per impostazione predefinita, sulla mappa viene visualizzata la gerarchia del contenitore padre per i nuovi elementi di codice. Utilizzare il pulsante **Includi padri** nella barra degli strumenti della mappa codice per modificare questo comportamento. Quando è disattivato, solo lo stesso elemento di codice viene aggiunto alla mappa. Per invertire questo comportamento per una sola azione di trascinamento, tenere premuto il tasto **CTRL** mentre si trascinano gli elementi di codice nella mappa.<br /><br /> Visual Studio aggiunge elementi di codice per gli elementi di codice di primo livello nella selezione. Per vedere se un elemento di codice contiene altri elementi di codice, spostare il puntatore del mouse sopra l'elemento di codice in modo da visualizzare la freccia di espansione (freccia giù). Fare clic sulla freccia di espansione per espandere l'elemento di codice. Per espandere tutti gli elementi di codice, premere **CTRL** +**a** per selezionare tutti gli elementi, aprire il menu di scelta rapida per la mappa e scegliere **gruppo**, **Espandi**. Questo comando non è disponibile se l'espansione di tutti i gruppi genera una mappa inutilizzabile o problemi di memoria insufficiente.|
|Elementi di codice correlati a elementi di codice sulla mappa.|Fare clic sul pulsante **Mostra Related** sulla barra degli strumenti della mappa codice e scegliere il tipo di elementi correlati a cui si è interessati.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per l'elemento di codice. Scegliere uno degli elementi **Mostra...** nel menu a seconda del tipo di relazione che interessa. Ad esempio, è possibile visualizzare gli elementi a cui fa riferimento l'elemento corrente, gli elementi che fanno riferimento all'elemento corrente, i tipi di base e derivati per classi, i chiamanti del metodo e le classi, gli spazi dei nomi e gli assembly che li contengono.<br /><br /> Per altri dettagli, vedere [questo argomento](../modeling/map-dependencies-across-your-solutions.md).|
|Assembly .NET (con estensione dll o exe) o file binari compilati.|Trascinare gli assembly o i file binari dall'esterno di Visual Studio su una mappa.<br /><br /> È possibile trascinare da Esplora risorse o Esplora file solo se questo componente e Visual Studio vengono eseguiti allo stesso livello di autorizzazione del controllo di accesso utente. Se, ad esempio, il controllo di accesso utente è attivato e si esegue Visual Studio come amministratore, Esplora risorse o Esplora file blocca l'operazione di trascinamento.|

### <a name="AddNodes"></a>

#### <a name="add-a-link-between-existing-code-elements"></a>Aggiungere un collegamento tra elementi di codice esistenti

1. Selezionare l'elemento di codice sorgente. Sopra l'elemento di codice viene visualizzata una barra degli strumenti.

    ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)

2. Sulla barra degli strumenti scegliere la prima icona, **creare un nuovo collegamento da questo nodo al nodo che si fa clic su Avanti**.

3. Selezionare l'elemento di codice di destinazione. Verrà visualizzato un collegamento tra i due elementi di codice.

**OPPURE**

1. Selezionare l'elemento di codice sorgente nella mappa.

2. Se è installato un mouse, spostare il puntatore del mouse fuori dai limiti della mappa.

3. Aprire il menu di scelta rapida dell'elemento di codice e scegliere **modifica**  > **Aggiungi**  > **collegamento generico**.

4. Premere TAB fino a selezionare l'elemento di codice di destinazione per il collegamento.

5. Premere **INVIO**.

### <a name="AddComments"></a>

#### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Aggiungere un commento a un nodo esistente sulla mappa

1. Selezionare l'elemento di codice. Sopra di esso verrà visualizzata una barra degli strumenti.

     ![Barra degli strumenti del grafico delle dipendenze](../modeling/media/depedencygraph_toolbar.png)

2. Sulla barra degli strumenti scegliere la terza icona, **creare un nuovo nodo di commento con un nuovo collegamento al nodo selezionato**.

     \- oppure -

     Aprire il menu di scelta rapida per l'elemento di codice e scegliere **modifica**  > **nuovo commento**.

3. Digitare i commenti. Per digitare una nuova riga, premere **maiusc**  + **invio**.

#### <a name="add-a-comment-to-the-map-itself"></a>Aggiungere un commento alla mappa

1. Aprire il menu di scelta rapida per la mappa e scegliere **modifica**  > **nuovo commento**.

2. Digitare i commenti. Per digitare una nuova riga, premere **maiusc**  + **invio**.

### <a name="RenameNodes"></a>

#### <a name="rename-a-code-element-or-link"></a>Rinominare un elemento di codice o un collegamento

1. Selezionare l'elemento di codice o il collegamento da rinominare.

2. Premere **F2**oppure aprire il menu di scelta rapida e scegliere **modifica**  > **rinominare**.

3. Quando viene visualizzata la casella di modifica nella mappa, rinominare l'elemento di codice o il collegamento.

**OPPURE**

1. Aprire il menu di scelta rapida e scegliere **modifica** **Proprietà** > .

2. Modificare la proprietà **Label** nel finestra proprietà di Visual Studio.

#### <a name="remove-a-code-element-or-link-from-the-map"></a>Rimuovere un elemento di codice o un collegamento dalla mappa

1. Selezionare l'elemento di codice o il collegamento e premere il tasto **Canc** .

     \- oppure -

     Aprire il menu di scelta rapida per l'elemento di codice o il collegamento e scegliere **modifica**  > **Rimuovi**.

2. Se l'elemento o il collegamento fa parte di un gruppo, il pulsante **Recupera bambini** ![Refetch icona elementi figlio ](../modeling/media/dependencygraph_deletednodesicon.png) viene visualizzato all'interno del gruppo. Fare clic su questo pulsante per recuperare elementi e collegamenti mancanti.

- È possibile rimuovere gli elementi di codice e i collegamenti da una mappa senza influire sul codice sottostante. Se vengono eliminati, le relative definizioni vengono rimosse dal file DGML (con estensione dgml).

- Le mappe create modificando il file DGML, aggiungendo elementi di codice non definiti o usando versioni precedenti di Visual Studio non supportano questa funzionalità.

#### <a name="flag-a-code-element-for-follow-up"></a>Contrassegnare un elemento di codice per il completamento

1. Selezionare l'elemento di codice o il collegamento da contrassegnare per il completamento.

2. Aprire il menu di scelta rapida e scegliere **modifica**  > **flag per completamento**.

- Per impostazione predefinita, all'elemento di codice viene applicato uno sfondo rosso. Prendere in considerazione l' [aggiunta di un commento](#AddComments) con le informazioni di completamento appropriate.

- Modificare il colore di sfondo dell'elemento o cancellare il flag di completamento scegliendo **modifica**  > **altri colori del flag**.

## <a name="ChangeStyleCodeOrLink"></a>Modificare lo stile di un elemento di codice o un collegamento

È possibile modificare le icone per gli elementi di codice e i colori per gli elementi di codice e i collegamenti usando le icone e i colori predefiniti. Ad esempio, è possibile scegliere un colore per evidenziare elementi di codice e collegamenti con una determinata categoria o proprietà. In questo modo si possono identificare aree specifiche della mappa e concentrarsi su di esse. È possibile specificare icone e colori personalizzati modificando il file con estensione dgml della mappa; vedere [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Per applicare un colore o un'icona predefinita agli elementi di codice o ai collegamenti con una determinata categoria o proprietà

1. Sulla barra degli strumenti della mappa scegliere **Legenda**.

2. Nella casella **Legenda** verificare se la categoria o la proprietà dell'elemento di codice è già presente nell'elenco.

3. Se l'elenco non include la categoria o la proprietà, scegliere **+** nella casella **Legenda** , quindi scegliere **Proprietà nodo**, **Categoria nodo**, **Proprietà collegamento**o **categoria collegamento**. Scegliere quindi la proprietà o la categoria. La categoria o la proprietà ora viene visualizzata nella casella **Legenda** .

    > [!NOTE]
    > Per creare e assegnare una categoria o una proprietà a un elemento di codice, è possibile modificare il file con estensione dgml della mappa; vedere [personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. Nella casella **Legenda** fare clic sull'icona accanto alla categoria o alla proprietà aggiunta o che si desidera modificare.

5. Utilizzare la tabella seguente per selezionare lo stile che si desidera modificare:

    |**Per modificare il**|**Choose**|
    |-|-|
    |Colore di sfondo|**Sfondo**|
    |Colore del contorno|**Stroke**|
    |Colore del testo (viene visualizzata la lettera "f" per visualizzare il risultato)|**Foreground**|
    |Icona|**Icone**|

     Viene visualizzata la finestra di dialogo selezione **set colori** o **selezione set icone** per selezionare un colore o un'icona.

6. Nella finestra di dialogo **selezione set colori** o **selezione set icone** eseguire una delle operazioni seguenti:

    |**Per applicare un**|**Eseguire questi passaggi**|
    |-|-|
    |Set di colori o di icone|Aprire l'elenco seleziona **set** di **colori** (o **icona**). Selezionare un set di colori o di icone.|
    |Colore o icona specifica|Aprire l'elenco di valori della proprietà o della categoria. Selezionare un colore o un'icona.|

    > [!NOTE]
    > È possibile ridisporre, eliminare o disattivare temporaneamente gli stili nella casella **Legenda** . Vedere [modificare la casella Legenda](#ModifyLegend).

## <a name="ModifyLegend"></a>Modificare la casella Legenda

È possibile ridisporre, eliminare o disattivare temporaneamente gli stili nella casella **Legenda** :

1. Aprire il menu di scelta rapida per uno stile nella casella **Legenda** .

2. Effettuare una delle attività seguenti:

    |**Per**|**Choose**|
    |-|-|
    |Disattivare l'elemento di codice|**Disabilitato**|
    |Eliminare l'elemento di codice|**Eliminazione**|
    |Spostare lo stile in alto|**Sposta su**|
    |Spostare l'elemento di codice in basso|**Sposta giù**|

## <a name="CopyLegend"></a>Copia stili da una mappa a un'altra

1. Verificare che la casella **Legenda** sia visualizzata nella mappa di origine. Se non è visibile, fare clic su **Legenda**sulla barra degli strumenti della mappa.

2. Aprire il menu di scelta rapida per la casella **Legenda** . Scegliere **Copia legenda**.

3. Incollare la legenda nella mappa di destinazione.

## <a name="MergeMaps"></a>Eseguire il merge delle mappe codice

È possibile unire le mappe copiando e incollando gli elementi di codice tra le mappe. Se gli identificatori degli elementi di codice corrispondono, l'operazione per incollare gli elementi di codice funziona come un'operazione di unione. Per semplificare questa attività, inserire tutti gli assembly o i file binari da visualizzare nella stessa cartella, in modo che il percorso completo di ogni assembly o file binario sia lo stesso per ogni mappa da unire.

In alternativa, è possibile trascinare gli assembly o file binari da tale cartella nella stessa mappa.

## <a name="see-also"></a>Vedere anche

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- [Riferimento di Directed Graph Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)
