---
title: Modificare modelli e diagrammi UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 157e605ae16167317e02e92070d859870b4709cf
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060151"
---
# <a name="edit-uml-models-and-diagrams"></a>Modificare modelli e diagrammi UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare e modificare un modello UML tramite le visualizzazioni fornite da diversi tipi di diagramma. Grazie alle diverse prospettive sul sistema, questi diagrammi semplificano la comprensione e l'esame di vari aspetti della progettazione e dei requisiti. Visual Studio offre modelli per cinque dei tipi di diagramma UML più usati.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Questo argomento descrive le tecniche per modificare il modello, comuni a diversi tipi di diagramma. Per altre informazioni specifiche di particolari tipi di diagrammi, vedere [creare modelli per l'app](../modeling/create-models-for-your-app.md).  
  
## <a name="in-this-topic"></a>In questo argomento  
  
- [Diagrammi UML sono viste di un modello UML](#Views)  
  
- [Creazione di diagrammi di modellazione UML](#Creating)  
  
- [Creazione di diagrammi di modellazione UML](#Drawing)  
  
- [Modifica di forme e connettori](#Editing)  
  
- [Annullamento delle modifiche al modello](#Undo)  
  
- [Condivisione di elementi tra diagrammi](#Sharing)  
  
- [Copia gli elementi e i gruppi di elementi correlati](#Copying)  
  
- [L'eliminazione di un elemento del modello o le relative visualizzazioni](#Deleting)  
  
- [Ricerca di testo in un diagramma](#Searching)  
  
- [Preparazione di un diagramma per la presentazione](#presentation)  
  
- [Estendere gli strumenti di progettazione UML](#extensions)  
  
## <a name="Views"></a> Diagrammi UML sono viste di un modello UML  
 È possibile creare e usare i diagrammi UML solo nei progetti di modellazione. Per altre informazioni su come creare diagrammi e progetti, vedere [diagrammi e progetti di modellazione UML creare](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
- Un progetto di modellazione contiene un solo modello UML. Ogni diagramma UML nel progetto è una visualizzazione del modello UML.  
  
- È possibile visualizzare il modello in **Esplora modelli UML**. Nel **architettura** dal menu **Windows**, quindi fare clic su **Esplora modelli UML**.  
  
- Ogni forma in un diagramma è una visualizzazione di un elemento del modello. Quando si inserisce una nuova forma in un diagramma, si crea un nuovo elemento nel modello.  
  
- Quando si salva un diagramma, Visual Studio salva l'intero modello, tutti i diagrammi di modellazione di progetto e file.  
  
## <a name="Creating"></a> Creazione di diagrammi di modellazione UML  
  
1. Nel **Architecture** dal menu in Visual Studio, fare clic su **nuovo diagramma livello o UML**.  
  
2. Selezionare e denominare il diagramma.  
  
3. Nelle **aggiunta al progetto di modellazione**, selezionare un progetto di modellazione esistente o selezionare **creare un nuovo progetto di modellazione**.  
  
   > [!NOTE]
   >  È necessario che il diagramma di modellazione sia presente all'interno di un progetto di modellazione.  
  
   È inoltre possibile aggiungere un diagramma a un progetto di modellazione esistente in Esplora soluzioni. Fare clic sul progetto di modellazione, scegliere **Add**, quindi fare clic su **nuovo elemento**.  
  
#### <a name="to-create-an-empty-uml-modeling-project"></a>Per creare un progetto di modellazione UML vuoto  
  
- Nel **File** dal menu **New**, fare clic su **progetto**e nel **nuovo progetto** della finestra di dialogo fare doppio clic su **di modellazione I progetti**.  
  
  Per altre informazioni su come gestire i progetti di modellazione, vedere [diagrammi e progetti di modellazione UML creare](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
## <a name="Drawing"></a> Creazione di diagrammi di modellazione UML  
 Un diagramma di modellazione visualizza una raccolta di elementi del modello collegati da relazioni. Ogni elemento viene visualizzato come forma e ogni relazione viene visualizzata come connettore tra due forme.  
  
 Esistono due tipi di strumenti, uno per gli elementi e uno per le relazioni. Ad esempio, nel diagramma classi UML casella degli strumenti **classe** è uno strumento elemento, e **Association** è uno strumento di relazione.  
  
> [!NOTE]
>  Se si vuole informazioni specifiche di particolari tipi di diagramma, vedere [creare modelli per l'app](../modeling/create-models-for-your-app.md).  
  
#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Per creare elementi e relazioni in un diagramma di modellazione UML  
  
1. Per creare un elemento del modello, fare clic su uno strumento per gli elementi nella casella degli strumenti e quindi fare clic sul diagramma nel punto in cui si vuole visualizzarlo. Dopo avere creato l'elemento, regolarne le dimensioni e la forma trascinando i quadratini di ridimensionamento.  
  
    In alcuni casi, è possibile inserire un nuovo elemento all'interno di un altro elemento. Ad esempio, in un diagramma classi UML, è possibile inserire una classe all'interno di un pacchetto.  
  
   > [!NOTE]
   >  Se non è possibile visualizzare la casella degli strumenti, fare clic su **casella degli strumenti** nel **visualizzazione** menu.  
  
2. Per creare una relazione, fare clic su uno strumento per le relazioni, fare clic sull'elemento da cui far iniziare la relazione e quindi fare clic sull'elemento con cui farla terminare.  
  
    Diversi tipi di relazioni possono iniziare o terminare in diversi tipi di elementi. Ad esempio, in un diagramma classi UML, una relazione di associazione non può iniziare o terminare in un elemento commento.  
  
   > [!NOTE]
   >  Per usare lo stesso strumento più volte, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** dello strumento.  
  
   In alcuni tipi di diagrammi, è anche possibile disegnare forme semplici. Queste forme non fanno parte del modello, ma è possibile usarle per attirare l'attenzione su parti del diagramma o per dividerlo in aree diverse.  
  
## <a name="Editing"></a> Modifica di forme e connettori  
 Quando si ridimensiona o si colora una forma oppure si reindirizza un connettore, questa operazione non influisce sul modello sottostante. Quando però si rinomina una forma nel diagramma o in Esplora modelli UML, l'elemento corrispondente viene rinominato in Esplora modelli UML e in qualsiasi altro diagramma che presenta tale elemento.  
  
> [!NOTE]
>  È possibile creare facilmente nuovi elementi della casella degli strumenti da cui creare gruppi di elementi o elementi con proprietà a scelta. Per altre informazioni, vedere [definire un oggetto personalizzato elemento della casella degli strumenti di modellazione](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
 La figura seguente mostra come modificare le dimensioni o il nome di una forma.  
  
 ![Modificare un elemento del modello](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")  
  
> [!TIP]
>  I comandi incorporati non includono un comando per allineare accuratamente le forme, Tuttavia, è possibile creare facilmente un comando di allineamento copiando il codice nell'esempio nella [visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md).  
  
 La figura seguente mostra come regolare la route e la posizione di un connettore o delle sue etichette.  
  
 ![Modifica di un connettore](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")  
  
#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Per spostare un'estremità di un connettore in un'altra forma  
  
1. Eseguire una delle operazioni seguenti:  
  
   - Premere **CTRL** e spostare l'estremità.  
  
     \- oppure -  
  
   - Il pulsante destro del connettore e quindi fare clic su **Riconnetti**.  
  
2. Fare clic sull'estremità del connettore che si vuole spostare.  
  
3. Fare clic sulla forma in cui si vuole spostare il connettore.  
  
#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Per modificare il colore o altre proprietà di un elemento, una relazione o un diagramma  
  
- Fare clic sull'elemento e impostare i campi nella **proprietà** finestra.  
  
     Se non è possibile visualizzare il **delle proprietà** finestra, fare doppio clic sull'elemento e quindi fare clic su **proprietà.**  
  
#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Per eseguire lo zoom avanti e indietro in un diagramma di modellazione  
  
- Premere e tenere premuto il **CTRL** mentre si ruota la rotellina del mouse.  
  
     \- oppure -  
  
- Premere e tenere premuto **CTRL + MAIUSC**, quindi fare clic sul pulsante sinistro o destro del mouse.  
  
     \- oppure -  
  
- Nel **Progettazione architettura** sulla barra degli strumenti, fare clic sul segno più (**+**) o meno (-) (**-**), oppure scegliere un livello di zoom.  
  
## <a name="Searching"></a> Ricerca in un diagramma  
 La funzione di ricerca veloce troverà gli elementi in un diagramma. È necessario impostare **Cerca in:** al **documento corrente**.  
  
#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Per cercare un testo in un diagramma di modellazione  
  
1. Premere **CTRL + F**.  
  
     \- oppure -  
  
     Nel **modifica** dal menu **Trova e sostituisci**, quindi fare clic su **ricerca veloce**.  
  
    > [!NOTE]
    >  Nel **Trova e sostituisci** finestra di dialogo, è necessario lasciare il **esaminare** campo impostato su **documento corrente**. Le altre opzioni non sono supportate.  
  
2. Digitare il testo che si desidera trovare e quindi fare clic su **Trova successivo**.  
  
    > [!NOTE]
    >  Se il testo che si vuole trovare è all'interno di una forma compressa, la forma verrà evidenziata. Espandere la forma e quindi fare clic su **Trova successivo** nuovamente.  
  
## <a name="Undo"></a> Annullamento delle modifiche al modello  
 È possibile annullare e ripristinare le modifiche apportate al modello e diagrammi usando il **annullare** e **rollforward** comandi il **modifica** menu.  
  
 **Ogni progetto di modellazione delle minacce ha un unico stack di modifiche.** In questo stack vengono mantenute tutte le modifiche apportate al modello e ai diagrammi. Lo stack include anche i passaggi dello stato attivo da un diagramma a un altro. Il comando Annulla inverte le modifiche in questo stack.  
  
 Ad esempio, si supponga di eseguire queste operazioni: Apportare una modifica al Diagram1; modificare lo stato attivo sul diagramma 2; modificare il diagramma 2. Quando si annullano le modifiche, il primo annullamento invertirà l'ultima modifica, l'annullamento successivo riporterà lo stato attivo sul diagramma 1 e il terzo annullamento invertirà la modifica al diagramma 1.  
  
 **Chiude un diagramma tronca lo stack di modifiche.** Se si chiude un diagramma, non è possibile annullare le modifiche eseguite nel diagramma né annullare le modifiche precedenti al modello o ai suoi diagrammi.  
  
 **È possibile annullare mentre si modifica una proprietà.** Mentre si modifica una proprietà nella finestra Proprietà, in un'etichetta o in un diagramma, è possibile annullare solo le modifiche apportate in tale proprietà. Completare la modifica nella proprietà premendo INVIO o annullarla premendo ESC. Sarà quindi possibile annullare le modifiche nel modello e nei diagrammi.  
  
 **Chiude un diagramma senza salvare le modifiche potrebbe non avere l'effetto desiderato.** Se si apportano modifiche e quindi si chiude un diagramma senza salvarlo, le modifiche verranno tuttavia conservate nel modello. Si consiglia di chiudere l'intero modello se si vuole chiudere senza salvare le modifiche.  
  
## <a name="Sharing"></a> Condivisione di elementi tra diagrammi  
 È possibile visualizzare più di una volta un'istanza specifica di un elemento del modello nei diagrammi. È possibile farlo con classi, interfacce, componenti, casi di utilizzo e attori.  
  
 È utile se si vogliono mostrare gruppi diversi di relazioni in diagrammi diversi. In un diagramma, ad esempio, si potrebbero mostrare le associazioni tra le classi Customer e Address. In un altro, si potrebbe mostrare ancora la classe Address, con l'associazione a Postal Area.  
  
 È possibile modificare le proprietà di un elemento del modello, ad esempio il nome, selezionando una qualsiasi delle visualizzazioni in qualsiasi diagramma o selezionandolo in Esplora modelli UML.  
  
 Ogni tipo di diagramma può mostrare solo alcuni tipi di elemento del modello. Ad esempio, non è possibile mostrare un caso di utilizzo in un diagramma dei componenti. Le seguenti procedure sono quindi valide solo per alcune combinazioni di elemento del modello e diagramma.  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Per aggiungere una nuova visualizzazione di un elemento del modello usando Esplora modelli UML  
  
1. Per aprire **Esplora modelli UML**via le **architettura** dal menu **Windows**, quindi fare clic su **Esplora modelli UML**.  
  
2. Trascinare l'elemento del modello dal **Esplora modelli UML** in un diagramma compatibile nello stesso progetto.  
  
     Viene visualizzata una forma che offre una visualizzazione dell'elemento del modello, oltre alle visualizzazioni in altri diagrammi oppure nello stesso diagramma.  
  
    > [!NOTE]
    >  L'effetto è diverso quando si trascina una classe o un componente in un diagramma di sequenza. In tal caso, viene creata una nuova linea di vita il cui tipo è quella classe o componente. Per altre informazioni, vedere [diagrammi di sequenza UML: Linee guida](../modeling/uml-sequence-diagrams-guidelines.md).  
  
#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Per aggiungere una nuova visualizzazione di un elemento del modello usando Incolla riferimento  
  
1. Fare doppio clic su un elemento esistente e quindi fare clic su **copia**.  
  
    - È possibile copiare diversi elementi contemporaneamente. Tenere premuto il tasto CTRL mentre fare clic su ogni elemento, fare doppio clic su uno di essi e quindi fare clic su **copia**.  
  
2. Fare doppio clic su una parte vuota di un diagramma compatibile e quindi fare clic su **Incolla riferimento**.  
  
     Appare un'altra visualizzazione dello stesso elemento.  
  
    > [!NOTE]
    >  Questo comportamento è diverso dal **Incolla** comando, che crea un nuovo elemento del modello. Per altre informazioni, vedere [copia di elementi e i gruppi di elementi correlati](#Copying).  
  
> [!NOTE]
>  Se si aggiungono a un diagramma visualizzazioni di due elementi del modello già connessi da una relazione, una visualizzazione della relazione apparirà anche nel diagramma. È possibile eliminare questa visualizzazione solo rimuovendo uno degli elementi dal diagramma o eliminando la relazione dal modello.  
  
## <a name="Copying"></a> Copia gli elementi e i gruppi di elementi correlati  
 È possibile copiare e incollare gli elementi del modello ed è possibile copiare e incollare gruppi di elementi e le relazioni tra di essi.  
  
> [!NOTE]
>  Il **Incolla** e **Incolla riferimento** comandi hanno effetti diversi. **Incolla** crea nuovi elementi le cui proprietà sono simili a quelli degli elementi copiati. **Incolla riferimento** crea nuove visualizzazioni degli stessi elementi.  
  
#### <a name="to-copy-elements-and-their-relationships"></a>Per copiare gli elementi e le loro relazioni  
  
1. Nel diagramma con gli elementi da copiare selezionare uno o più elementi.  
  
    > [!NOTE]
    >  Non è possibile copiare relazioni se non come parte di un gruppo di elementi.  
  
2. Nel **Edit** menu, fare clic su **copia**.  
  
3. Per copiare gli elementi in un altro diagramma, creare il nuovo diagramma o aprire il diagramma esistente.  
  
4. Nel **Edit** menu, fare clic su **Incolla**.  
  
    - Le copie degli elementi vengono visualizzate insieme alle copie delle relazioni che li collegano.  
  
    - Ogni nuovo elemento avrà un nuovo nome generato automaticamente.  
  
5. Modificare le posizioni, i nomi e le altre proprietà dei nuovi elementi e delle nuove relazioni.  
  
> [!NOTE]
>  Non è possibile copiare un elemento da un modello a un altro, ad esempio se sono presenti due modelli nella stessa soluzione, ma è possibile copiare gli elementi da un diagramma a un altro.  
  
#### <a name="to-copy-an-entire-diagram"></a>Per copiare un intero diagramma  
  
1. Creare un nuovo diagramma.  
  
2. Selezionare tutti gli elementi in un diagramma esistente, copiarli e incollarli in quello nuovo.  
  
   Non è possibile replicare un diagramma copiando e incollando in Esplora soluzioni.  
  
## <a name="Deleting"></a> L'eliminazione di un elemento del modello o le relative visualizzazioni  
 Alcuni tipi di elementi, in particolare i classificatori, possono essere rimossi da un diagramma senza eliminarli dal modello. I classificatori sono i principali elementi visualizzati nei diagrammi classi, nei diagrammi dei componenti e nei diagrammi caso di utilizzo. Possono apparire in più diagrammi. Per questi tipi di elementi, esistono due comandi separati: **Rimuovi da diagramma** e **Elimina da modello**.  
  
 Al contrario, quando si elimina una relazione da un diagramma, la si elimina sempre anche dal modello.  
  
> [!NOTE]
>  Alcuni tipi di elementi in un diagramma UML dispongono di etichette. Quando si selezionano questi elementi disegnandovi attorno un rettangolo, è possibile selezionare le etichette, ma non gli elementi proprietari delle etichette. L'eliminazione di un subset di elementi selezionati in questo modo non è supportata. Per selezionare un subset di questi elementi, premere e tenere premuto il **CTRL** mentre si fa clic su ogni elemento.  
  
#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Per rimuovere la visualizzazione di un classificatore da un diagramma  
  
- Fare doppio clic sull'elemento del diagramma e quindi fare clic su **Rimuovi da diagramma**.  
  
  \- oppure -  
  
- Fare clic sull'elemento nel diagramma e quindi premere il **eliminare** chiave.  
  
  - La visualizzazione dell'elemento scompare. Tuttavia, l'elemento rimane nel modello ed è comunque possibile trovarlo nel **Esplora modelli UML**. Rimangono anche le altre visualizzazioni dello stesso elemento.  
  
  - Ogni connettore che termina in questa forma viene rimosso dal diagramma, ma la relazione rappresentata rimane nel modello. È possibile visualizzare la relazione in **Esplora modelli UML** sotto **relazioni**, in ogni elemento che si connette.  
  
#### <a name="to-delete-an-element-from-the-model"></a>Per eliminare un elemento dal modello  
  
- Fare doppio clic sull'elemento sia nel **Esplora modelli UML** o in un diagramma e quindi fare clic su **Elimina da modello**.  
  
    - L'elemento viene eliminato da ogni diagramma in cui è visualizzato.  
  
    - Anche ogni relazione che termina in questo elemento viene eliminata anche dal modello.  
  
#### <a name="to-delete-a-relationship-from-the-model"></a>Per eliminare una relazione dal modello  
  
- Fare doppio clic la relazione in un diagramma o in **Esplora modelli UML**, quindi fare clic su **Elimina da modello**.  
  
    > [!CAUTION]
    >  Non è possibile rimuovere una relazione da un diagramma senza rimuoverla dal modello.  
  
     La relazione viene eliminata dal modello e da ogni diagramma in cui viene visualizzata.  
  
## <a name="presentation"></a> Preparazione di un diagramma per la presentazione  
 La seguenti funzionalità consentono di mettere in evidenza determinate parti del diagramma, aggiungere spiegazioni o dividere un diagramma in aree di interesse diverse.  
  
- È possibile copiare qualsiasi parte di un diagramma in Word, in PowerPoint o in un altro documento. Selezionare le forme e connettori desiderato, fare doppio clic su e quindi fare clic su **copia**.  
  
- È possibile cambiare il colore delle forma o dei connettori. Selezionare una o più forme e cambiare il **colore** proprietà. Se non è possibile visualizzare la finestra **Proprietà**, premere **F4**.  
  
- In alcuni tipi di diagramma, è possibile disegnare linee, rettangoli ed ellissi dal **forme semplici** sezione della casella degli strumenti. Queste forme non fanno parte del modello UML.  
  
- Per etichettare un'area, è possibile trascinare un commento nella casella degli strumenti e quindi impostare relativi **Transparent** proprietà **True**. Come le forme semplici, i commenti non fanno parte del modello UML e non vengono visualizzati in Esplora modelli UML.  
  
- Per aggiungere note e spiegazioni agli elementi del modello, è possibile creare commenti e quindi collegarli agli elementi.  
  
- Per allineare accuratamente le forme di una colonna o di una riga nel diagramma, è possibile installare il comando per allineare le forme, Questa funzionalità è disponibile come estensione UML di esempio:  [UML: Comando per allineare le forme](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)  
  
### <a name="to-export-a-diagram-as-an-image"></a>Per esportare un diagramma come immagine  
 Per altre informazioni, vedere [esportare diagrammi come immagini](../modeling/export-diagrams-as-images.md).  
  
## <a name="extensions"></a> Estendere gli strumenti di progettazione UML  
 È possibile aggiungere nuove funzionalità agli strumenti UML e adattare la notazione dei diagrammi alle proprie esigenze. Per altre informazioni, vedere [modelli e diagrammi UML estendere](../modeling/extend-uml-models-and-diagrams.md).  
  
 Sono disponibili numerose estensioni di esempio. È possibile limitarsi a installarle e usarle oppure usare il codice sorgente per creare le proprie estensioni. Gli esempi includono:  
  
|||  
|-|-|  
|[Allineare le forme](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Comando di menu che consente di ordinare un diagramma.|  
|[Collegamento alla documentazione](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Collega un elemento UML a intestazioni di Word, diapositive di PowerPoint, file di qualsiasi tipo, diagrammi UML o altri elementi UML. Per creare il collegamento, basta trascinare, quindi è possibile fare doppio clic sull'elemento per visualizzare l'elemento collegato. Ad esempio, si possono collegare i casi di utilizzo a specifiche di Word o diagrammi di attività dettagliati e le azioni a diapositive dello storyboard.|  
|[Immissione rapida](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Crea rapidamente un modello usando l'immissione di testo. È utile per raccogliere le idee durante le riunioni.|  
|[Colora in base allo stereotipo](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Colora le classi in base allo stereotipo. È possibile estendere facilmente il codice in modo che funzioni per i propri stereotipi.|  
|[Modellazione del dominio](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Pratiche impostazioni predefinite per i modelli aziendali. Per impostazione predefinita, le associazioni sono mostrate senza frecce e le operazioni non vengono visualizzate nelle classi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Creare diagrammi e progetti di modellazione UML](../modeling/create-uml-modeling-projects-and-diagrams.md)   
 [Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)   
 [Creare modelli per l'app](../modeling/create-models-for-your-app.md)
