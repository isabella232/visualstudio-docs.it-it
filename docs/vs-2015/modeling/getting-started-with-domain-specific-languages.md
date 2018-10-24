---
title: Introduzione ai linguaggi specifici dei domini | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 024392a2-2c04-404f-a27b-7273553c3b60
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 29699609ee095c7e95434492afc531869453da4a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49877770"
---
# <a name="getting-started-with-domain-specific-languages"></a>Introduzione ai linguaggi specifici del dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento illustra i concetti di base nella definizione e uso di un linguaggio specifico di dominio (DSL) creato con il SDK di modellazione per Visual Studio.  
  
 Se si ha familiarità con linguaggi specifici di dominio, è consigliabile usare la **Lab strumenti DSL**, che è possibile trovare in questo sito: [alcuna and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)  
  
## <a name="what-can-you-do-with-a-domain-specific-language"></a>Cosa può fare con un linguaggio specifico di dominio?  
 Un linguaggio specifico di dominio è una notazione, in genere con interfaccia grafica, che è progettata per essere usato per uno scopo specifico. Al contrario, linguaggi, ad esempio UML sono per uso generico. In un linguaggio DSL, è possibile definire i tipi di elemento del modello e le relative relazioni e modalità di presentazione sullo schermo.  
  
 Quando è stato progettato un linguaggio DSL, è possibile distribuirlo come parte di un pacchetto di Visual Studio Integration Extension (VSIX). Gli utenti di lavorare con il linguaggio DSL in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
 ![Diagramma dell'albero genealogico, casella degli strumenti e soluzioni](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
 La notazione rappresenta solo una parte di un linguaggio DSL. Unitamente alla notazione, il pacchetto VSIX include strumenti che gli utenti possono applicare per aiutarli a modificare e generare materiale dai relativi modelli.  
  
 Una delle applicazioni dei linguaggi specifici di dominio principale consiste nel generare codice programma, i file di configurazione e altri elementi. In particolare in progetti di grandi dimensioni e linee di prodotti, in cui verranno create diverse varianti di un prodotto, la generazione di molti aspetti variabili da linguaggi specifici di dominio può fornire un notevole aumento in Monitoraggio affidabilità e una risposta molto rapida alle modifiche dei requisiti.  
  
 Il resto di questa panoramica è una procedura dettagliata che illustra le operazioni di base di creazione e utilizzo di un linguaggio specifico di dominio in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:  
  
|||  
|-|-|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579)|  
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580)|  
|Modeling SDK per Visual Studio|[Scaricare MSDK](http://www.microsoft.com/download/details.aspx?id=40754)|  
  
## <a name="creating-a-dsl-solution"></a>Creazione di una soluzione DSL  
 Per creare un nuovo linguaggio specifico di dominio, si crea un nuovo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione usando il modello di progetto linguaggio specifico di dominio.  
  
#### <a name="to-create-a-dsl-solution"></a>Per creare una soluzione DSL  
  
1. Scegliere **Nuovo** dal menu **File**, quindi fare clic su **Progetto**.  
  
2. Sotto **tipi di progetto**, espandere il **altri tipi di progetto** nodo e fare clic su **estendibilità**.  
  
3. Fare clic su **finestra di progettazione Domain-Specific Language**.  
  
    ![Creare finestra di dialogo DSL](../modeling/media/create-dsldialog.png "Create_DSLDialog")  
  
4. Nel **Name** , digitare **albero genealogico FamilyTree**. Fare clic su **OK**.  
  
    Il **Domain-Specific Language guidata** apre e visualizza un elenco di soluzioni di modello DSL.  
  
    Fare clic su ogni modello per visualizzare una descrizione,  
  
    Sono utili i modelli di punti di partenza. Ognuno di essi fornisce un completo funzionante DSL, che è possibile modificare in base alle esigenze. In genere, è necessario scegliere il modello più vicino di ciò che si desidera creare.  
  
5. In questa procedura dettagliata scegliere la **linguaggio minimo** modello.  
  
6. Immettere un'estensione di file per il linguaggio DSL nella pagina appropriata della procedura guidata. Questa estensione verrà usata dai file contenenti le istanze del linguaggio DSL.  
  
   -   Scegliere un'estensione che non è associata a tutte le applicazioni in computer in uso o in qualsiasi computer in cui si desidera installare il linguaggio DSL. Ad esempio, **docx** e **htm** è le estensioni di nome file inaccettabili.  
  
   -   La procedura guidata avviserà se l'estensione immessa è in uso come DSL. Provare a usare un'estensione di file diversa. È anche possibile reimpostare l'istanza sperimentale di Visual Studio SDK per eliminare le precedenti finestre di progettazione sperimentali. Fare clic su **avviare**, fare clic su **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare Microsoft Istanza di Visual Studio 2010 sperimentale**.  
  
7. Esaminare le altre pagine e quindi fare clic su **fine**.  
  
    Viene generata una soluzione contenente due progetti. Essi sono denominati Dsl e DslPackage. Diagramma verrà aperto un file che è denominata Dsldefinition.  
  
   > [!NOTE]
   >  La maggior parte del codice che è possibile visualizzare nelle cartelle nei due progetti è generato dal Dsldefinition. Per questo motivo, la maggior parte delle modifiche per il linguaggio DSL vengono apportate in questo file.  
  
   L'interfaccia utente ora è simile a quella nell'immagine seguente.  
  
   ![finestra di progettazione DSL](../modeling/media/dsl-designer.png "dsl_designer")  
  
   Questa soluzione definisce un linguaggio specifico di dominio. Per altre informazioni, vedere [panoramica dell'interfaccia utente di Domain-Specific Language Tools](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).  
  
## <a name="the-important-parts-of-the-dsl-solution"></a>Le parti importanti della soluzione DSL  
 Si noti che i seguenti aspetti della nuova soluzione.  
  
-   **Dsl\DslDefinition.DSL** si tratta del file che venga visualizzato quando si crea una soluzione DSL. Quasi tutto il codice nella soluzione viene generato da questo file, e vengono apportata qui la maggior parte delle modifiche apportate a una definizione DSL. Per altre informazioni, vedere Working with con il [lavora sul diagramma di definizione DSL](../modeling/working-with-the-dsl-definition-diagram.md).  
  
-   **Progetto DSL** questo progetto contiene codice che definisce il linguaggio specifico di dominio.  
  
-   **Progetto DslPackage** questo progetto contiene codice che consente alle istanze del linguaggio DSL di essere aperti e modificati [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
##  <a name="Debugging"></a> Esegue il linguaggio DSL  
 È possibile eseguire la soluzione DSL, non appena è stato creato. In un secondo momento, è possibile modificare la definizione DSL gradualmente, eseguire la soluzione dopo ogni modifica.  
  
#### <a name="to-experiment-with-the-dsl"></a>Per provare a usare il linguaggio DSL  
  
1. Fare clic su **Trasforma tutti i modelli** sulla barra degli strumenti Esplora soluzioni. La maggior parte del codice sorgente da Dsldefinition verrà rigenerato.  
  
   > [!NOTE]
   >  Ogni volta che si modifica Dsldefinition, è necessario fare clic su **Trasforma tutti i modelli** prima della ricompilazione della soluzione. È possibile automatizzare questo passaggio. Per altre informazioni, vedere [come automatizzare Trasforma tutti i modelli](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a).  
  
2. Premere F5 o scegliere il **Debug** menu, fare clic su **Avvia debug**.  
  
    Il linguaggio DSL si basa e viene installato nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
    Viene avviata un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . L'istanza sperimentale accetta le impostazioni da un sottoalbero distinto del Registro di sistema, in cui [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] le estensioni vengono registrate a scopo di debug. Le normali istanze di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] non sono disponibili per le estensioni registrate non esiste.  
  
3. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aprire il file di modello denominato **Test** dalla **Esplora**.  
  
    \- oppure -  
  
    Fare clic sul progetto di debug, scegliere **Add**, quindi fare clic su **elemento**. Nel **Aggiungi elemento** finestra di dialogo, seleziona il tipo di file del linguaggio DSL.  
  
    Il file del modello viene aperto come un diagramma vuoto.  
  
    Casella degli strumenti si apre e visualizza gli strumenti appropriati per il tipo di diagramma.  
  
4. Usare gli strumenti per creare forme e connettori nel diagramma.  
  
   1.  Per creare forme, trascinare dallo strumento di esempio forma nel diagramma.  
  
   2.  Per connettere due forme, scegliere lo strumento di connessione di esempio, fare clic sulla prima e quindi fare clic sulla seconda forma.  
  
5. Selezionare le etichette delle forme modificarle.  
  
   Sperimentale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sarà simile all'esempio seguente:  
  
   ![](../modeling/media/dsl-min.png "DSL_min")  
  
### <a name="the-content-of-a-model"></a>Il contenuto di un modello  
 Il contenuto di un file che è un'istanza di un linguaggio DSL viene chiamato un *modello*. Il modello contiene *elementi del modello* e *collegamenti* tra gli elementi. La definizione DSL specifica i tipi di elementi del modello e i collegamenti possono esistere nel modello. Ad esempio, in un linguaggio DSL creato dal modello di linguaggio minimo, vi è un tipo di elemento del modello e un tipo di collegamento.  
  
 La definizione DSL può specificare come il modello viene visualizzato in un diagramma. È possibile scegliere tra una varietà di stili di forme e connettori. È possibile specificare che alcune forme visualizzate all'interno di altre forme.  
  
 È possibile visualizzare un modello come un albero nel **Explorer** visualizzare mentre si sta modificando un modello. Quando si aggiungono forme nel diagramma, gli elementi del modello vengono visualizzati anche nella finestra di esplorazione. Finestra di esplorazione è utilizzabile anche se è presente alcun diagramma.  
  
 Se non è possibile visualizzare l'Explorer nell'istanza di debug di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]via il **View** dal menu **Other Windows**e quindi fare clic su  *\<Your linguaggio >* **Explorer**.  
  
### <a name="the-api-of-your-dsl"></a>L'API del linguaggio DSL  
 Il linguaggio DSL genera un'API che consente di leggere e aggiornare i modelli che sono istanze del linguaggio DSL. Un'applicazione dell'API consiste nel generare file di testo da un modello. Per altre informazioni, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
 Nella soluzione di debug, aprire i file del modello con estensione "tt". Questi esempi illustrano come è possibile generare il testo dai modelli e consentono di testare l'API del linguaggio DSL. Uno degli esempi è scritta in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], l'altro in [!INCLUDE[csprcs](../includes/csprcs-md.md)].  
  
 In ogni modello di file è il file generato. Espandere il file di modello in Esplora soluzioni e aprire il file generato.  
  
 Il file modello contiene un breve segmento di codice in cui sono elencati tutti gli elementi del modello.  
  
 Il file generato contiene il risultato.  
  
 Quando si modifica un file di modello, si noterà le modifiche corrispondenti nel file generati dopo la rigenerazione di file.  
  
##### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Per rigenerare i file di testo dopo aver modificato il file del modello  
  
1. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], salvare il file del modello.  
  
2. Assicurarsi che il parametro del nome file in ogni file con estensione tt fa riferimento al file di modello che si usa per esperimenti. Salvare il file con estensione tt.  
  
3. Fare clic su **Trasforma tutti i modelli** nella barra degli strumenti **Esplora soluzioni**.  
  
    \- oppure -  
  
    Fare doppio clic sui modelli che si desidera rigenerare e quindi fare clic su **Esegui strumento personalizzato**.  
  
   È possibile aggiungere qualsiasi numero di file modello di testo a un progetto. Ogni modello genera un file dei risultati.  
  
> [!NOTE]
>  Quando si modifica la definizione DSL, il codice di modello testo di esempio non funzionerà, a meno che non venga aggiornata.  
  
 Per altre informazioni, vedere [generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md) e [scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).  
  
## <a name="customizing-the-dsl"></a>Personalizzazione del linguaggio DSL  
 Quando si desidera modificare la definizione DSL, chiudere l'istanza sperimentale e aggiornare la definizione principale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] istanza.  
  
> [!NOTE]
>  Dopo avere modificato la definizione DSL, si potrebbero perdere informazioni nei modelli di prova creato con le versioni precedenti.  Ad esempio, la soluzione di debug contiene un file denominato campione, che contiene alcune forme e connettori. Dopo avere iniziato a sviluppare la definizione DSL, non saranno visibili e andranno perse quando si salva il file.  
  
 È possibile rendere un'ampia gamma di estensioni per il linguaggio DSL. Nell'esempio seguente fornirà una visione delle possibilità.  
  
 Dopo ogni modifica, salvare la definizione DSL, fare clic su **Trasforma tutti i modelli** nelle **Esplora soluzioni**e quindi premere **F5** per sperimentare il DSL modificato.  
  
### <a name="rename-the-types-and-tools"></a>Rinominare i tipi e strumenti  
 Rinominare le classi di dominio esistenti e le relazioni. Ad esempio, a partire da una definizione Dsl creata dal modello di linguaggio minimo, è possibile eseguire le seguenti operazioni di ridenominazione, per rendere il linguaggio DSL rappresentano strutture ad albero della famiglia.  
  
##### <a name="to-rename-domain-classes-relationships-and-tools"></a>Per rinominare gli strumenti, le relazioni e le classi di dominio  
  
1.  Nel diagramma DslDefinition, rinominare **ExampleModel** al **FamilyTreeModel**, **ExampleElement** al **persona**,  **Destinazioni** al **padri**, e **origini** alla **figli**. È possibile fare clic su ogni etichetta per modificarla.  
  
     ![Diagramma di definizione DSL &#45; modello di albero genealogico](../modeling/media/familyt-person.png "FamilyT_Person")  
  
2.  Rinominare gli strumenti elemento e il connettore.  
  
    1.  Aprire la finestra di DSL Explorer facendo clic sulla scheda sotto Esplora soluzioni. Se non è visualizzato, scegliere il **View** dal menu **Other Windows** e quindi fare clic su **DSL Explorer**. Esplora DSL è visibile solo quando il diagramma di definizione DSL è la finestra attiva.  
  
    2.  Aprire la finestra proprietà e posizionarlo in modo che è possibile visualizzare Esplora DSL e proprietà nello stesso momento.  
  
    3.  In DSL Explorer, espandere **Editor**, **schede della casella degli strumenti**,  *\<il linguaggio DSL >* e quindi **strumenti**.  
  
    4.  Fare clic su **ExampleElement**. Si tratta dell'elemento della casella degli strumenti che è possibile creare elementi.  
  
    5.  Nella finestra Proprietà modificare il **Name** proprietà **persona**.  
  
         Si noti che il **didascalia** cambia anche proprietà.  
  
    6.  Allo stesso modo, modificare il nome del **ExampleConnector** dello strumento **ParentLink**. Modificare il **didascalia** proprietà in modo che non è una copia della proprietà Name. Ad esempio, immettere **collegamento padre**.  
  
3.  Ricompilare il linguaggio DSL.  
  
    1.  Salvare il file di definizione DSL.  
  
    2.  Fare clic su **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni  
  
    3.  Premere F5. Attendere finché l'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] viene visualizzata.  
  
4.  La soluzione di debug nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aprire un file di modello di test. Trascina gli elementi dalla casella degli strumenti. Si noti che sono state modificate le didascalie degli strumenti e i nomi dei tipi in DSL Explorer.  
  
5.  Salvare il file del modello.  
  
6.  Aprire un file con estensione tt e sostituire le occorrenze dei nomi di tipo e proprietà precedente con i nuovi nomi.  
  
7.  Assicurarsi che il nome del file specificato nel file con estensione tt consente di specificare il modello di test.  
  
8.  Salvare il file con estensione tt. Aprire il file generato per visualizzare il risultato dell'esecuzione del codice nel file con estensione tt. Verificare che sia corretto.  
  
### <a name="add-domain-properties-to-classes"></a>Aggiungere le proprietà di dominio a classi  
 Aggiungere proprietà a una classe di dominio, ad esempio rappresentare gli anni di nascita e morte di una persona.  
  
 Per rendere visibili le nuove proprietà del diagramma, è necessario aggiungere *gli elementi Decorator* alla forma che visualizza l'elemento del modello. È necessario anche mappare le proprietà per gli elementi Decorator.  
  
##### <a name="to-add-properties-and-display-them"></a>Per aggiungere proprietà e visualizzarli  
  
1. Aggiungere le proprietà.  
  
   1.  Nel diagramma di definizione DSL, fare doppio clic sul **persona** della classe di dominio, scegliere **Add**, quindi fare clic su **della proprietà di dominio**.  
  
   2.  Digitare un elenco di nuovi nomi di proprietà, ad esempio **nascita** e **morte**. Premere **invio** dopo ciascuna di esse.  
  
2. Aggiungere gli elementi Decorator che verranno visualizzate le proprietà della forma.  
  
   1.  Seguire la linea grigia che si estende dalla classe di dominio della persona a altro lato del diagramma. Si tratta di una mappa degli elementi del diagramma. La classe di dominio è collegato a una classe di forma.  
  
   2.  Fare doppio clic su questa classe di forma, scegliere **Add**, quindi fare clic su **Decorator testo**.  
  
   3.  Aggiungere due elementi Decorator con nomi quali **BirthDecorator** e **DeathDecorator**.  
  
   4.  Selezionare ogni nuovo decorator e nella finestra Proprietà impostare il **posizione** campo. Ciò determina dove verrà visualizzato il valore della proprietà di dominio della forma. Ad esempio, impostare **InnerBottomLeft** e **InnerBottomRight**.  
  
        ![Definizione della forma di raggruppamento](../modeling/media/familyt-compartment.png "FamilyT_Compartment")  
  
3. Mappare gli elementi Decorator per la proprietà.  
  
   1.  Aprire la finestra Dettagli DSL. È in genere in una scheda accanto alla finestra di Output. Se non è visualizzato, scegliere il **View** dal menu **Other Windows**, quindi fare clic su **dettagli DSL**.  
  
   2.  Diagramma di definizione DSL fare clic sulla riga che connette il **persona** della classe di dominio per la classe shape.  
  
   3.  Nelle **dettagli DSL**via le **mappe elementi Decorator** , selezionare la casella di controllo su un elemento decorator non mappata. Nelle **proprietà di visualizzazione**, selezionare la proprietà di dominio a cui si desidera venga eseguito il mapping. Ad esempio, eseguire il mapping **BirthDecorator** al **nascita**.  
  
4. Salvare il linguaggio DSL, fare clic su Trasforma tutti i modelli e premere F5.  
  
5. In un diagramma del modello di esempio, verificare che ora è possibile scegliere le posizioni in cui che si è scelto e digitare i valori al loro interno. Inoltre, quando si seleziona una **persona** forma, la finestra proprietà vengono visualizzate le nuove proprietà di nascita e morte.  
  
6. In un file con estensione TT, è possibile aggiungere il codice che ottiene le proprietà di ogni persona.  
  
   ![Diagramma dell'albero genealogico, casella degli strumenti e soluzioni](../modeling/media/familyt-instance.png "FamilyT_Instance")  
  
### <a name="define-new-classes"></a>Definire nuove classi  
 È possibile aggiungere classi di dominio e le relazioni a un modello. Ad esempio, è possibile creare una nuova classe per rappresentare città e una nuova relazione per rappresentare che una persona vissuto in una città.  
  
 Per rendere i diversi tipi distinti in un diagramma del modello, è possibile mappare le classi di dominio diversi tipi di forma o forme geometria diversa e i colori.  
  
##### <a name="to-add-and-display-a-new-domain-class"></a>Per aggiungere e visualizzare una nuova classe di dominio  
  
1.  Aggiungere una classe di dominio e impostarla come figlio della radice del modello.  
  
    1.  Nel diagramma di definizione DSL, scegliere il **relazione di incorporamento** dello strumento, fare clic sulla classe radice **FamilyTreeModel**e quindi fare clic su una parte vuota del diagramma.  
  
         Una nuova classe di dominio viene visualizzato, che è connessa la FamilyTreeModel con una relazione di incorporamento.  
  
         Impostare il relativo nome, ad esempio **Town (città)**.  
  
        > [!NOTE]
        >  Ogni classe di dominio, tranne la radice del modello deve essere la destinazione di almeno una relazione di incorporamento, o deve ereditare da una classe che rappresenta la destinazione dell'incorporamento. Per questo motivo, è spesso utile creare una classe di dominio usando lo strumento di relazione di incorporamento.  
  
    2.  Aggiungere una proprietà di dominio per la nuova classe, ad esempio **nome**.  
  
2.  Aggiungere una relazione di riferimento tra Person e Town (città).  
  
    1.  Scegliere il **relazione di riferimento** dello strumento, fare clic su Person e quindi fare clic su Town (città).  
  
         ![Frammento della definizione DSL: radice dell'albero genealogico](../modeling/media/familyt-root.png "FamilyT_Root")  
  
        > [!NOTE]
        >  Le relazioni di riferimento rappresentano riferimenti incrociati da una parte dell'albero del modello a un'altra.  
  
3.  Aggiungere una forma per rappresentare i diagrammi del modello di città.  
  
    1.  Trascinare un **forma geometrica** dalla casella degli strumenti nel diagramma e rinominarla, ad esempio **TownShape**.  
  
    2.  Nella finestra Proprietà, impostare i campi di aspetto della nuova forma, ad esempio colore di riempimento e Geometry.  
  
    3.  Aggiungere un elemento Decorator per visualizzare il nome della città e rinominarlo NameDecorator. Impostare la proprietà Position.  
  
4.  Eseguire il mapping della classe di dominio Town (città) per il TownShape.  
  
    1.  Scegliere il **mappa elementi diagramma** dello strumento, quindi scegliere la classe di dominio Town (città) e quindi la classe di forma TownShape.  
  
    2.  Nel **mappe elementi Decorator** scheda della finestra di **dettagli DSL** finestra con il connettore della mappa selezionata, verificare NameDecorator e impostare **proprietà di visualizzazione** al nome.  
  
5.  Creare un connettore per visualizzare la relazione tra due persone di città.  
  
    1.  Trascinare un connettore dalla casella degli strumenti nel diagramma. Rinominarlo e impostare l'aspetto delle proprietà.  
  
    2.  Usare la **mappa elementi diagramma** dello strumento per collegare il nuovo connettore alla relazione tra Person e Town (città).  
  
         ![Definizione dell'albero genealogico con mappa di forme aggiunte](../modeling/media/familyt-shapemap.png "FamilyT_ShapeMap")  
  
6.  Creare uno strumento elemento per l'esecuzione di una città di new.  
  
    1.  Nelle **DSL Explorer**, espandere **Editor** quindi **schede della casella degli strumenti**.  
  
    2.  Fare doppio clic su  *\<il linguaggio DSL >* e quindi fare clic su **Aggiungi nuovo strumento elemento**.  
  
    3.  Impostare il **Name** proprietà del nuovo strumento e set relativo **classe** proprietà Town (città).  
  
    4.  Impostare il **icona casella degli strumenti** proprietà. Fare clic su **[...]**  e il **nome File** field, selezionare un file di icona.  
  
7.  Creare uno strumento di connessione per effettuare un collegamento tra città e persone.  
  
    1.  Fare doppio clic su  *\<il linguaggio DSL >* e quindi fare clic su **Aggiungi nuovo strumento connettore**.  
  
    2.  Impostare la proprietà nome del nuovo strumento.  
  
    3.  Nel **ConnectionBuilder** proprietà, selezionare il generatore che contiene il nome della relazione persona-città.  
  
    4.  Impostare il **icona casella degli strumenti**.  
  
8.  Salvare la definizione DSL, fare clic su **Trasforma tutti i modelli**, quindi premere **F5**.  
  
9. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], aprire un file di modello di test. Usare i nuovi strumenti per creare di città e i collegamenti tra città e le persone. Si noti che è possibile creare solo i collegamenti tra i tipi corretti dell'elemento.  
  
10. Creare codice che elenca la città in cui si trova ogni persona. Modelli di testo sono uno dei posti in cui è possibile eseguire tale codice. Ad esempio, è possibile modificare il file Sample.tt esistente nella soluzione di debug in modo che contenga il codice seguente:  
  
    ```  
    <#@ template inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" debug="true" #>  
    <#@ output extension=".txt" #>  
    <#@ FamilyTree processor="FamilyTreeDirectiveProcessor" requires="fileName='Sample.ftree'" #>  
  
    <#  
      foreach (Person person in this.FamilyTreeModel.People)  
      {  
    #>  
        <#= person.Name #><#if (person.Town != null) {#> of <#= person.Town.Name #> <#}#>  
  
    <#  
          foreach (Person child in person.Children)  
      {  
    #>  
                <#= child.Name #>  
    <#  
      }  
      }  
    #>  
  
    ```  
  
     Quando si salva il file TT, creerà un file secondario che contiene l'elenco di persone e loro residenze. Per altre informazioni, vedere [generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
## <a name="validation-and-commands"></a>Convalida e comandi  
 È possibile sviluppare ulteriormente questo linguaggio DSL aggiungendo i vincoli di convalida. Questi vincoli sono metodi che è possibile definire, assicurarsi che il modello è in uno stato corretto. Ad esempio, è possibile definire un vincolo per assicurarsi che la data di nascita di un elemento figlio è successiva a quella dei relativi elementi padre. La funzionalità di convalida viene visualizzato un avviso se l'utente DSL tenta di salvare un modello che causa l'interruzione di uno qualsiasi dei vincoli. Per altre informazioni, vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
 È anche possibile definire comandi di menu che l'utente può richiamare. I comandi è possono modificare il modello. Possono anche interagire con altri modelli di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e con risorse esterne. Per altre informazioni, vedere [procedura: modificare un comando di Menu Standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
## <a name="deploying-the-dsl"></a>Distribuzione DSL  
 Per consentire ad altri utenti di usare il linguaggio specifico di dominio, si distribuisce un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] file Extension (VSIX). Viene creato quando si compila la soluzione DSL.  
  
 Individuare il file con estensione VSIX nella cartella bin della soluzione. Copiarlo nel computer in cui si desidera installarlo. Nello stesso computer, fare doppio clic sul file VSIX. Il linguaggio DSL può essere utilizzato in tutte le istanze di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in tale computer.  
  
 È possibile usare la stessa procedura per installare il linguaggio DSL nel computer in modo che non è necessario utilizzare l'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Per altre informazioni, vedere [distribuzione di soluzioni Domain-Specific Language](../modeling/deploying-domain-specific-language-solutions.md).  
  
##  <a name="Reset"></a> Rimozione di vecchi DSL sperimentale  
 Se è stato creato DSL sperimentale che non si desidera più, è possibile rimuoverli dal computer reimpostando il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] istanza sperimentale.  
  
 Verranno rimossi dal computer tutti i linguaggi DSL sperimentale e altri sperimentale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensioni. Si tratta di estensioni che sono state eseguite in modalità di debug.  
  
 Questa procedura non rimuove linguaggi specifici di dominio o un altro [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensioni che è stato completamente installate eseguendo il file VSIX.  
  
#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Per reimpostare l'istanza sperimentale di Visual Studio  
  
1.  Fare clic su **avviare**, fare clic su **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare Microsoft Istanza di Visual Studio 2010 sperimentale**.  
  
2.  Ricompilare qualsiasi DSL sperimentali o altri sperimentale [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensioni che si desidera utilizzare.  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)   
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)   
 [Alcuna and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)



