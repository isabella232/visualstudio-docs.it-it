---
title: 'Diagrammi di sequenza UML: Linee guida | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.linktosequencediagram
- vs.teamarch.logicalclassdiagram.createlifeline
- vs.teamarch.componentdiagram.createlifeline
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- interactions, UML
- diagrams - modeling, UML sequence
- UML interactions
- UML, sequence diagrams
- UML sequence diagrams
- behaviors, UML
ms.assetid: 5990ef7c-ba60-4e20-a36d-e29c1fa6c8bb
caps.latest.revision: 55
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 388bb32aa871b220768e856e96cced2d5bced694
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518250"
---
# <a name="uml-sequence-diagrams-guidelines"></a>UML Sequence Diagrams: Guidelines
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [diagrammi di sequenza UML: linee guida](https://docs.microsoft.com/visualstudio/modeling/uml-sequence-diagrams-guidelines).  
  
In Visual Studio, è possibile creare un *diagramma di sequenza* per visualizzare un'interazione. Un'interazione è una sequenza di messaggi tra istanze tipiche di classi, componenti, sistemi secondari o attori.  
  
 I diagrammi sequenza UML fanno parte di un modello UML ed esistono soltanto all'interno dei progetti di modellazione UML. Per creare un diagramma di sequenza UML nel **Architecture** menu, fare clic su **nuovo diagramma livello o UML**. Altre informazioni sulle [elementi dei diagrammi sequenza UML](../modeling/uml-sequence-diagrams-reference.md) oppure [diagrammi di modellazione UML](../modeling/edit-uml-models-and-diagrams.md) in generale. Per una dimostrazione video, vedere [disegno delle interazioni con i diagrammi di sequenza (2010)](http://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="in-this-topic"></a>Contenuto dell'argomento  
 [Uso dei diagrammi di sequenza UML](#Using)  
  
 [Passaggi di base per la creazione di diagrammi di sequenza](#BasicSteps)  
  
 [Creazione e uso di diagrammi di sequenza semplice](#Simple)  
  
 [Le classi e linee di vita](#ClassesAndLifelines)  
  
 [Creazione di sequenze di interazione riutilizzabili](#Multiple)  
  
 [Compressione di gruppi di linee di vita](#Collapse)  
  
 [Descrizione delle strutture di controllo con frammenti](#Fragments)  
  
##  <a name="Using"></a> Uso dei diagrammi di sequenza UML  
 È possibile usare i diagrammi di sequenza per diversi scopi in diversi livelli di dettaglio del programma. Le occasioni tipiche che richiedono il disegno di un diagramma di sequenza sono:  
  
-   Se si ha un diagramma caso di utilizzo che riepiloga gli utenti del sistema e i loro obiettivi, è possibile disegnare diagrammi di sequenza per descrivere in che modo interagiscono i componenti principali del sistema per raggiungere l'obiettivo di ogni caso di utilizzo. Per altre informazioni, vedere [diagrammi caso d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).  
  
-   Se all'interfaccia di un componente arrivano messaggi identificati, è possibile disegnare diagrammi di sequenza per descrivere in che modo interagiscono le parti del componente per raggiungere il risultato richiesto per ogni messaggio in ingresso. Per altre informazioni, vedere [diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md).  
  
 Il disegno dei diagrammi di sequenza offre diversi vantaggi:  
  
-   È possibile visualizzare facilmente in che modo le attività vengono distribuite tra i componenti.  
  
-   È possibile identificare i motivi di interazione che rendono complesso l'aggiornamento del software.  
  
## <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi  
 È possibile usare i diagrammi di sequenza UML insieme ad altri diagrammi in molti modi.  
  
#### <a name="lifelines-and-types"></a>Linee di vita e tipi  
 Le linee di vita disegnate in un diagramma di sequenza possono rappresentare delle istanze tipiche di componenti o classi nel sistema. È possibile creare linee di vita da tipi e tipi da linee di vita e visualizzare i tipi nei diagrammi classi UML e nei diagrammi dei componenti UML. Per altre informazioni, vedere [classi e linee di vita](#ClassesAndLifelines).  
  
#### <a name="parameter-types"></a>Tipi di parametro.  
 È anche possibile descrivere in un diagramma classi UML i tipi di parametri e i valori restituiti usati nei messaggi inviati tra le linee di vita.  
  
#### <a name="use-case-details"></a>Dettagli relativi al caso di utilizzo  
 Un caso di utilizzo rappresenta l'obiettivo di un utente e la sequenza di passaggi necessaria per raggiungerlo. La sequenza di passaggi può essere descritta in molti modi. Un'opzione consiste nel disegnare un diagramma di sequenza che mostra le interazioni tra gli utenti e i componenti principali del sistema. Per altre informazioni, vedere [diagrammi caso d'uso UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).  
  
##  <a name="BasicSteps"></a> Passaggi di base per la creazione di diagrammi di sequenza  
 Per un elenco completo degli elementi nei diagrammi di sequenza, vedere [diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md).  
  
> [!NOTE]
>  Procedura dettagliata per creare i diagrammi di modellazione è descritte nel [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
#### <a name="to-create-a-sequence-diagram"></a>Per creare un diagramma di sequenza  
  
1.  Nel **Architecture** menu, fare clic su **nuovo diagramma livello o UML**.  
  
2.  Sotto **modelli**, fare clic su **diagramma di sequenza UML**.  
  
3.  Assegnare un nome al diagramma.  
  
4.  Nelle **aggiungere al progetto di modellazione**, selezionare un progetto di modellazione esistente nella soluzione, o **creare un nuovo progetto di modellazione**, quindi fare clic su **OK**.  
  
     Verrà visualizzato un nuovo diagramma di sequenza con il **diagramma di sequenza** della casella degli strumenti. La casella degli strumenti contiene gli elementi e i connettori richiesti.  
  
 ![Parti di un diagramma di sequenza](../modeling/media/uml-sequence.png "UML_Sequence")  
  
#### <a name="to-draw-a-sequence-diagram"></a>Per disegnare un diagramma di sequenza  
  
1.  Trascinare **linee di vita** (1) dalle **della casella degli strumenti** nel diagramma per rappresentare le istanze di classi, componenti, attori o dispositivi.  
  
    > [!NOTE]
    >  È anche possibile creare una linea di vita trascinando una classe esistente, interfaccia, attore o componente da **Esplora modelli UML** nel diagramma. Viene creata una linea di vita che rappresenta un'istanza del tipo selezionato.  
  
2.  Disegnare i messaggi per visualizzare in che modo le linee di vita collaborano per raggiungere uno specifico obiettivo.  
  
     Per creare un messaggio (3, 4, 6, 7), fare clic su uno strumento dei messaggi. Fare clic sulla linea di vita di invio nel punto in cui deve iniziare il messaggio, quindi fare clic sulla linea di vita di ricezione.  
  
     Viene visualizzata un'occorrenza esecuzione (5) nella linea di vita di ricezione. L'occorrenza esecuzione rappresenta un periodo di tempo durante il quale l'istanza esegue un metodo. È possibile creare altri messaggi che iniziano da un'occorrenza esecuzione.  
  
3.  Per visualizzare un messaggio proveniente da un'origine evento sconosciuta (9) o trasmesso a destinatari sconosciuti (10), disegnare un messaggio asincrono da o verso uno spazio vuoto nel diagramma. Questi messaggi sono denominati *messaggi trovati* (9) e *perdeva dei messaggi* (10).  
  
    > [!NOTE]
    >  Per spostare un gruppo di linee di vita contenenti messaggi trovati o persi, attenersi alla procedura seguente per selezionare le linee di vita prima di spostarle: disegnare un rettangolo attorno a tali linee di vita o premere e tenere premuto il **CTRL** mentre si fa clic su ogni linea di vita. Se si usa **Seleziona tutto** oppure **CTRL**+**oggetto** per selezionare tutte le linee di vita e spostarle, qualsiasi persi o trovati collegati a queste linee di vita dei messaggi non può essere spostata. Se si verifica questo scenario, è possibile spostare questi messaggi separatamente.  
  
4.  Disegnare diagrammi di sequenza per ogni messaggio principale nello stesso componente o sistema.  
  
#### <a name="to-change-the-order-of-messages"></a>Per modificare l'ordine dei messaggi  
  
-   Trascinare un messaggio verso l'alto o verso il basso sulla linea di vita. È possibile trascinarlo su altri messaggi o dentro o fuori un blocco di esecuzione.  
  
     \- oppure -  
  
-   Fare clic sul messaggio e usare la **freccia** e **freccia giù** le chiavi per regolare le posizioni del messaggio. Uso **MAIUSC + freccia** e **MAIUSC + freccia giù** per modificare l'ordine dei messaggi.  
  
#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Per spostare o copiare le sequenze di messaggi nel diagramma di sequenza  
  
1.  Fare doppio clic su un messaggio (3, 4) e quindi fare clic su **copia**.  
  
2.  Fare doppio clic occorrenza esecuzione (5) o una linea di vita (1) da cui si desidera che il nuovo messaggio da inviare, e quindi fare clic su **Incolla**. Se si vuole, il nuovo mittente può trovarsi in un diagramma diverso.  
  
     Una copia del messaggio e tutti i messaggi secondari vengono aggiunti alla fine dell'occorrenza esecuzione oppure alla fine della linea di vita.  
  
    > [!NOTE]
    >  Il messaggio incollato viene visualizzato sempre alla fine dell'occorrenza esecuzione o della linea di vita. Dopo averlo incollato, è possibile trascinarlo in una posizione precedente.  
  
#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Per visualizzare e modificare il testo della firma per un messaggio  
  
-   La linea di vita di destinazione deve essere associata o mappata ai tipi per poter visualizzare il testo della firma. Per completare questa attività, eseguire uno dei seguenti passaggi:  
  
    -   Fare doppio clic la linea di vita e quindi scegliere **Crea classe**.  
  
         oppure  
  
    -   Selezionare la linea di vita, premere **F4**e quindi nel **proprietà** impostare nella finestra di **tipo** proprietà a un oggetto esistente digitare oppure specificare il nome di un nuovo tipo. Fare doppio clic sull'etichetta di messaggio e quindi scegliere **operazione Create**.  
  
     Il testo della firma viene visualizzato sotto l'etichetta del messaggio. Ora è possibile modificare il testo della firma. Per altre informazioni, vedere [classi e linee di vita](#ClassesAndLifelines).  
  
#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Per migliorare il layout di un diagramma di sequenza  
  
-   Fare doppio clic su una parte vuota del diagramma e quindi fare clic su **Ridisponi Layout**.  
  
-   Per annullare l'operazione, fare clic su **Edit**, quindi fare clic su **Annulla**.  
  
#### <a name="to-change-the-package-that-owns-the-interaction"></a>Per modificare il pacchetto a cui appartiene l'interazione  
  
1.  Nelle **Esplora modelli UML**, trovare l'interazione visualizzata dal diagramma di sequenza.  
  
    > [!NOTE]
    >  L'interazione non compariranno nella **Esplora modelli UML** finché non si aggiunge la prima linea di vita al diagramma di sequenza.  
  
2.  Trascinare l'interazione nel pacchetto.  
  
     \- oppure -  
  
     Fare doppio clic sull'interazione e quindi fare clic su **Taglia**. Fare doppio clic su pacchetto e quindi fare clic su **Incolla**.  
  
##  <a name="Simple"></a> Creazione e uso di diagrammi di sequenza semplice  
 La forma più semplice e diffusa di diagramma di sequenza contiene solo linee di vita e messaggi. Un diagramma di questo tipo consente di visualizzare chiaramente una sequenza di interazioni tipica tra gli oggetti nella progettazione o tra il sistema e gli utenti. In genere, questo diagramma consente di discutere e comunicare in modo appropriato le informazioni sulla progettazione.  
  
 Di seguito sono riportate alcuni aspetti da prendere in considerazione quando si disegna un diagramma di sequenza semplice.  
  
### <a name="types-of-message"></a>Tipi di messaggio  
 Sono disponibili tre strumenti per la creazione dei messaggi.  
  
-   Usare la **sincrono** dello strumento per descrivere un'interazione in cui il mittente attende che il destinatario invii una risposta (3).  
  
     Oggetto  **< \<restituire >>** verrà visualizzata sulla freccia alla fine dell'occorrenza esecuzione. Indica la restituzione del controllo al mittente.  
  
-   Usare la **asincrono** dello strumento per descrivere un'interazione in cui il mittente può continuare immediatamente senza attendere che il destinatario (4).  
  
-   Usare la **Create** dello strumento per descrivere un'interazione in cui il mittente crea il ricevitore (8).  
  
     Un messaggio di creazione dovrebbe essere il primo messaggio ricevuto dal destinatario.  
  
### <a name="annotating-the-interactions"></a>Annotazione delle interazioni  
 Per descrivere più dettagliatamente sulla sequenza, è possibile inserire un **commento** in qualsiasi punto nel diagramma.  
  
 Usando **collegamenti al commento**, è possibile collegare un commento a linee di vita, esecuzioni, utilizzi interazione e frammenti.  
  
> [!CAUTION]
>  Quando si collega un commento a un punto particolare della sequenza, collegarlo a un'occorrenza esecuzione, un utilizzo interazione o un frammento. Non collegarlo a una linea di vita perché, in questo caso, non resta collegato nel punto corretto della sequenza.  
  
 Usare un commento per:  
  
-   Annotare gli obiettivi raggiunti nei punti chiave della sequenza. Ciò consente ai lettori di visualizzare gli obiettivi delle interazioni.  
  
-   Descrivere l'obiettivo generale dell'intera sequenza. Collegare il commento all'occorrenza esecuzione iniziale oppure lasciarlo scollegato. Ad esempio, "Il cliente ha scelto i prodotti dal menu e gli è stato fornito un prezzo".  
  
-   Descrivere le responsabilità di ogni linea di vita. Collegare il commento alla linea di vita. Ad esempio, "Il manager degli ordini raccoglie le scelte del menu del cliente".  
  
-   Annotare le eccezioni o le alternative che potrebbero essere eseguite al posto della sequenza tipica visualizzata. Ad esempio, "Il cliente può ignorare il resto della sequenza".  
  
    -   Valutare l'uso dei frammenti come alternativa più formale rispetto a questo tipo di nota. Vedere [che descrive le strutture di controllo con frammenti](#Fragments)  
  
## <a name="deciding-the-scope-of-the-diagram"></a>Scelta dell'ambito del diagramma  
 È importante chiarire cosa si vuole visualizzare nel diagramma.  
  
#### <a name="initiating-event"></a>Evento di origine  
 Ogni diagramma deve visualizzare la sequenza di interazioni risultante da un evento di origine. Ad esempio:  
  
-   Un utente che avvia un caso di utilizzo, ad esempio l'apertura della pagina Web per l'acquisto di un pasto.  
  
-   Un messaggio da un componente del sistema a un altro, ad esempio una query sulla disponibilità dei prodotti che l'utente vuole acquistare.  
  
-   Un evento attivato da una modifica dello stato, ad esempio la quantità delle scorte di un prodotto che scende al di sotto di una determinata soglia.  
  
#### <a name="level-of-detail"></a>Livello di dettaglio  
 I diagrammi di sequenza possono mostrare livelli di dettaglio diversi. È possibile decidere il livello di dettaglio in due dimensioni separate, in modo quasi indipendente:  
  
 Le linee di vita possono rappresentare uno di questi livelli di dettaglio:  
  
-   Gli oggetti nel codice del programma, che esistono o sono in fase di sviluppo.  
  
-   I componenti o i componenti secondari, solitamente senza aspetti, proxy o altri meccanismi di connessione.  
  
-   Il sistema e gli attori esterni  
  
 I messaggi possono rappresentare uno di questi livelli di dettaglio:  
  
-   I messaggi software nel codice del programma, in un'API o in un'interfaccia Web.  
  
-   Le transazioni o le transazioni secondarie, ad esempio tra gli utenti e il sistema oppure tra il codice e il database.  
  
-   Casi di utilizzo: interazioni principali tra gli utenti e il sistema.  
  
 Se si esplora il codice esistente o si descrive una nuova progettazione, spesso è utile disegnare e discutere le visualizzazioni meno dettagliate.  
  
## <a name="describing-variations"></a>Descrizione delle variazioni  
 Il diagramma mostra un'unica sequenza di eventi tipica. Per visualizzare delle alternative possibili, ad esempio gli scenari di errore, è possibile usare una di queste opzioni:  
  
-   Disegnare diagrammi di sequenza separati per descrivere questi scenari  
  
-   Uso [che descrive le strutture di controllo con frammenti](#Fragments) per mostrare cicli, alternative e così via.  
  
## <a name="assessing-the-design"></a>Valutazione della progettazione  
 È possibile usare il diagramma per valutare la distribuzione delle attività tra gli oggetti o i componenti. Valutare il refactoring se vengono visualizzati questi motivi:  
  
-   Una linea di vita sembra eseguire tutte le operazioni mediante chiamate ad altri elementi, mentre le altre linee di vita rispondono solo passivamente.  
  
-   Molti messaggi attraversano le linee di vita. Ogni linea di vita deve inviare messaggi solo ad alcuni elementi adiacenti e non deve comunicare con gli elementi adiacenti dei relativi elementi adiacenti. In genere è possibile disporre le linee di vita in modo tale che siano presenti solo pochi punti in cui i messaggi attraversano le linee di vita e laddove si verificano tali intersezioni, la linea di vita di destinazione non dovrebbe scambiare anche i messaggi che contengono le linee di vita intersecate.  
  
-   Alcune linee di vita sembrano gestire più tipi di attività. È consigliabile trovare una frase breve che descriva le responsabilità di ogni linea di vita, riepilogando il lavoro svolto in risposta a ogni messaggio ricevuto.  
  
##  <a name="ClassesAndLifelines"></a> Le classi e linee di vita  
 Le linee di vita nei diagrammi di sequenza mostra le istanze di classi o di interfacce di componenti. È possibile assegnare un nome a una linea di vita in due modi:  
  
|**A tale scopo**|**Usare questo formato**|  
|--------------------------|-------------------------|  
|Istanza anonima di un tipo.<br /><br /> Usare questo metodo se si ha una sola linea di vita di ogni tipo.|*typeName*|  
|Istanza denominata di un tipo.<br /><br /> Usare questo metodo per visualizzare una sequenza costituita da più istanze dello stesso tipo.|*objectName*:*typeName*|  
  
### <a name="creating-lifelines-from-types"></a>Creazione di linee di vita dai tipi  
 È possibile creare nuove linee di vita dalle classi già definite, ad esempio in un diagramma classi.  
  
> [!NOTE]
>  Verificare che sia presente un diagramma di sequenza prima di eseguire questa attività.  
  
##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Per creare una linea di vita da un tipo esistente  
  
-   Trascinare una classe, un componente o un'interfaccia da Esplora modelli UML in un diagramma di sequenza.  
  
     \- oppure -  
  
    1.  Fare doppio clic la classe, componente o interfaccia nel diagramma corrispondente e quindi fare clic su **Crea linea di vita**.  
  
    2.  Nel **Crea linea di vita** finestra di dialogo, selezionare un diagramma di sequenza e quindi fare clic su **OK**.  
  
     Viene visualizzata una nuova linea di vita con istanza denominata il cui tipo corrisponde a quello trascinato.  
  
    > [!NOTE]
    >  È possibile ripetere l'azione tutte le volte che si desidera. In questo modo vengono create linee di vita con nomi di istanza diversi.  
  
##### <a name="to-change-the-type-of-a-lifeline"></a>Per modificare il tipo di una linea di vita  
  
1.  Fare doppio clic su una linea di vita e quindi fare clic su **proprietà**.  
  
2.  Nel **delle proprietà** impostare nella finestra di **tipo** proprietà. È possibile selezionare un tipo dal menu a discesa oppure digitare un nuovo nome.  
  
### <a name="creating-classes-from-lifelines"></a>Creazione di classi dalle linee di vita  
 Dopo aver creato uno o più diagrammi di sequenza, è possibile riepilogare le linee di vita creando classi o interfacce da tali diagrammi.  
  
##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Per creare una classe o un'interfaccia da una linea di vita  
  
1.  Fare doppio clic la linea di vita e quindi fare clic su **Crea classe** oppure **Crea interfaccia**.  
  
     In Esplora modelli UML viene visualizzata una nuova classe o interfaccia.  
  
2.  Creare operazioni nella classe o interfaccia per ogni messaggio ricevuto dalla linea di vita:  
  
    1.  Selezionare tutti i messaggi da includere.  
  
    2.  Fare doppio clic su uno dei messaggi e quindi fare clic su **Crea metodo**.  
  
         La nuova classe o interfaccia include operazioni per ogni messaggio selezionato.  
  
         Il nome dell'operazione viene visualizzata sotto ogni freccia del messaggio e nel **operazione** proprietà del messaggio.  
  
         Se il messaggio include parametri in formato "(parameter : type)", questi verranno visualizzati nell'elenco dei parametri della nuova operazione.  
  
        > [!NOTE]
        >  È necessario ripetere questo passaggio per aggiungere nuovi messaggi al diagramma di sequenza.  
  
3.  Per visualizzare la nuova classe o interfaccia in dettaglio, aggiungerla a un diagramma classi o dei componenti.  
  
    1.  Aprire o creare un diagramma classi o dei componenti.  
  
    2.  Trascinare la nuova classe o interfaccia da **Esplora modelli UML** a un diagramma classi.  
  
         La classe o interfaccia viene visualizzata nel diagramma classi.  
  
         \- oppure -  
  
    3.  Trascinare la nuova interfaccia dal **Esplora modelli UML** a un componente o una porta in un diagramma dei componenti.  
  
         L'interfaccia viene visualizzata nel componente come simbolo.  
  
### <a name="creating-classes-for-parameters"></a>Creazione di classi per i parametri  
 È possibile includere i parametri nei messaggi di un diagramma di sequenza. È possibile usare un diagramma classi UML per descrivere i tipi di parametri.  
  
##  <a name="Multiple"></a> Creazione di sequenze di interazione riutilizzabili  
 È possibile usare diagramma separato per descrivere una sequenza contenente i dettagli da escludere oppure comuni a più diagrammi.  
  
 È possibile creare un rettangolo di utilizzo interazione (12) in un diagramma che punta ai dettagli in un altro diagramma.  
  
 Fare doppio clic su un utilizzo interazione per aprire il diagramma di sequenza collegato.  
  
#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Per creare un'interazione sequenza riutilizzabile da linee di vita esistenti  
  
1.  Nel **casella degli strumenti**, fare clic su **utilizzo interazione**.  
  
2.  Nel diagramma di sequenza, tenere premuto il pulsante del mouse mentre si trascinano le linee di vita da includere nella sequenza riutilizzabile. Iniziare nella posizione verticale in cui inserire l'utilizzo interazione.  
  
     Un utilizzo interazione viene visualizzato tra le linee di vita selezionate nel diagramma di sequenza.  
  
3.  Fare doppio clic sul nome dell'utilizzo interazione e rinominarlo per descrivere l'effetto della sequenza riutilizzabile nel diagramma.  
  
     \- oppure -  
  
     Scrivere il nome come chiamata di funzione con parametri.  
  
4.  Collegare l'utilizzo interazione a un altro diagramma di sequenza. Fare clic con il pulsante destro del mouse sull'utilizzo interazione, quindi:  
  
     Fare clic su **Crea nuova sequenza** per creare un nuovo diagramma di sequenza  
  
     \- oppure -  
  
     Fare clic su **Collega a sequenza** da collegare a un diagramma esistente.  
  
     Visual Studio crea un collegamento tra l'utilizzo interazione e la nuova interazione sequenza.  
  
     Nella soluzione viene visualizzato un nuovo diagramma di sequenza. Contiene le linee di vita usate per creare l'utilizzo interazione.  
  
    > [!NOTE]
    >  Verranno incluse solo le linee di vita usate per creare l'utilizzo interazione. Il nuovo diagramma non includerà le linee di vita create dopo l'utilizzo interazione, anche se ora sono incluse nell'utilizzo interazione.  
  
#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Per creare una sequenza riutilizzabile dai messaggi esistenti  
  
-   Fare clic sul messaggio che si desidera spostare e quindi fare clic su **passa a diagramma**.  
  
     Visual Studio:  
  
    -   Sostituisce con un utilizzo interazione il messaggio selezionato e tutti i messaggi sussidiari.  
  
    -   Sposta i messaggi sostituiti in un nuovo diagramma di sequenza.  
  
    -   Crea un collegamento tra l'utilizzo interazione e il nuovo diagramma di sequenza.  
  
#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Per spostarsi sulla sequenza a cui fa riferimento un utilizzo interazione  
  
-   Fare doppio clic sull'utilizzo interazione.  
  
     \- oppure -  
  
     Fare doppio clic su utilizzo interazione e quindi fare clic su **Vai a sequenza**.  
  
### <a name="creating-a-placeholder-with-an-interaction-use"></a>Creazione di un segnaposto con un utilizzo interazione  
 È possibile creare un utilizzo interazione senza collegarlo a un altro diagramma. È possibile usarlo come segnaposto per una parte della sequenza i cui dettagli devono ancora essere elaborati. Usare il nome dell'utilizzo interazione per indicare il risultato desiderato.  
  
##  <a name="Collapse"></a> Compressione di gruppi di linee di vita  
 È possibile comprimere un set di linee di vita, in modo che il gruppo venga visualizzato come una sola linea di vita, consentendo di visualizzare un gruppo di oggetti come un singolo componente. I messaggi e gli utilizzi interazione tra le linee di vita in un gruppo compresso sono nascosti. Vengono invece visualizzati i messaggi e le sequenze di interazioni che includono altre linee di vita.  
  
#### <a name="to-collapse-a-group-of-lifelines-together"></a>Per comprimere un gruppo di linee di vita  
  
1.  Selezionare due o più linee di vita.  
  
2.  Fare doppio clic su uno di essi e quindi fare clic su **Comprimi**.  
  
     Le linee di vita separate vengono sostituite da una singola linea di vita.  
  
     I messaggi e gli utilizzi interazione che riguardano solo i membri del gruppo sono nascosti.  
  
3.  Per rinominare il gruppo, fare clic sul nome.  
  
    > [!NOTE]
    >  Il nome del gruppo andrà perso quando si espande il gruppo.  
  
#### <a name="to-expand-a-collapsed-group"></a>Per espandere un gruppo compresso  
  
-   Fare doppio clic la linea di vita compressa e quindi fare clic su **Espandi**.  
  
    > [!NOTE]
    >  Il nome del gruppo verrà perso, insieme a tutti i collegamenti dal gruppo ai commenti o agli elementi di lavoro.  
  
##  <a name="Fragments"></a> Descrizione delle strutture di controllo con frammenti  
 È possibile usare i frammenti combinati (13) per definire i cicli, i rami e l'elaborazione simultanea in un diagramma di sequenza. In alternativa, provare a usare un diagramma di attività. Il diagramma di attività non è utile per visualizzare i messaggi tra gli attori, ma in alcuni casi è più indicato perché visualizza meglio cicli, rami e concorrenza.  
  
 Per un elenco completo dei tipi di frammento, vedere [flusso di controllo sono descritti con frammenti nei diagrammi di sequenza UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).  
  
#### <a name="to-create-a-combined-fragment"></a>Per creare un frammento combinato  
  
1.  Selezionare un messaggio o una sequenza di messaggi tutti a partire dalla stessa occorrenza esecuzione o linea di vita.  
  
    > [!NOTE]
    >  Selezionare le frecce dei messaggi, non le occorrenze esecuzione alle quali puntano i messaggi.  
  
2.  Fare doppio clic su uno dei messaggi, scegliere **Racchiudi**e quindi scegliere il tipo di frammento richiesto.  
  
     Viene visualizzato un nuovo frammento che contiene i messaggi selezionati.  
  
     Se il tipo di frammento combinato consente più frammenti, viene visualizzato anche un frammento vuoto.  
  
3.  Per impostare la protezione di un frammento, fare clic sul bordo del frammento e quindi fare clic su **proprietà**. Impostare il **Guard** proprietà.  
  
     La proprietà Guard viene usata per definire la condizione per un ramo o un ciclo.  
  
4.  Per aggiungere un nuovo frammento a un tipo che consente più frammenti, fare doppio clic il limite di un frammento e scegliere **Add**. Fare clic su **operando interazione prima** oppure **operando interazione dopo**.  
  
5.  Per aggiungere nuovi messaggi a un frammento, usare gli strumenti del messaggio o le funzioni di copia e incolla.  
  
## <a name="see-also"></a>Vedere anche  
 [Diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md)   
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammi caso di utilizzo UML: riferimento](../modeling/uml-use-case-diagrams-reference.md)   
 [Diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md)   
 [Diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md)   
 [Diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md)   
 [Video: Disegno delle interazioni con i diagrammi di sequenza](http://go.microsoft.com/fwlink/?LinkId=201113)



