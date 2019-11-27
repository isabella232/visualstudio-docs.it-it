---
title: 'Diagrammi di sequenza UML: linee guida | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c5906084fc7db96ddf304e8362bf7692dac62d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297139"
---
# <a name="uml-sequence-diagrams-guidelines"></a>Diagrammi di sequenza UML: linee guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio è possibile creare un *diagramma di sequenza* per mostrare un'interazione. Un'interazione è una sequenza di messaggi tra istanze tipiche di classi, componenti, sistemi secondari o attori.

 I diagrammi sequenza UML fanno parte di un modello UML ed esistono soltanto all'interno dei progetti di modellazione UML. Per creare un diagramma di sequenza UML, scegliere **nuovo diagramma livello o UML**dal menu **architettura** . Altre informazioni sugli [elementi del diagramma di sequenza UML](../modeling/uml-sequence-diagrams-reference.md) o sui [diagrammi di modellazione UML](../modeling/edit-uml-models-and-diagrams.md) in generale. Per una dimostrazione video, vedere [Sketching Interactions by using Sequence Diagrams (2010)](https://channel9.msdn.com/Blogs/clinted/UML-with-VS-2010-Part-7-Sketching-Interactions-with-Sequence-Diagrams).

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>In questo argomento
 [Uso di diagrammi di sequenza UML](#Using)

 [Passaggi di base per la creazione di diagrammi di sequenza](#BasicSteps)

 [Creazione e utilizzo di diagrammi di sequenza semplici](#Simple)

 [Classi e linee di vita](#ClassesAndLifelines)

 [Creazione di sequenze di interazione riutilizzabili](#Multiple)

 [Compressione di gruppi di linee di vita](#Collapse)

 [Descrizione delle strutture di controllo con frammenti](#Fragments)

## <a name="Using"></a>Uso di diagrammi di sequenza UML
 È possibile usare i diagrammi di sequenza per diversi scopi in diversi livelli di dettaglio del programma. Le occasioni tipiche che richiedono il disegno di un diagramma di sequenza sono:

- Se si ha un diagramma caso di utilizzo che riepiloga gli utenti del sistema e i loro obiettivi, è possibile disegnare diagrammi di sequenza per descrivere in che modo interagiscono i componenti principali del sistema per raggiungere l'obiettivo di ogni caso di utilizzo. Per altre informazioni, vedere [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).

- Se all'interfaccia di un componente arrivano messaggi identificati, è possibile disegnare diagrammi di sequenza per descrivere in che modo interagiscono le parti del componente per raggiungere il risultato richiesto per ogni messaggio in ingresso. Per altre informazioni, vedere [diagrammi dei componenti UML: linee guida](../modeling/uml-component-diagrams-guidelines.md).

  Il disegno dei diagrammi di sequenza offre diversi vantaggi:

- È possibile visualizzare facilmente in che modo le attività vengono distribuite tra i componenti.

- È possibile identificare i motivi di interazione che rendono complesso l'aggiornamento del software.

## <a name="relationship-to-other-diagrams"></a>Relazione con altri diagrammi
 È possibile usare i diagrammi di sequenza UML insieme ad altri diagrammi in molti modi.

#### <a name="lifelines-and-types"></a>Linee di vita e tipi
 Le linee di vita disegnate in un diagramma di sequenza possono rappresentare delle istanze tipiche di componenti o classi nel sistema. È possibile creare linee di vita da tipi e tipi da linee di vita e visualizzare i tipi nei diagrammi classi UML e nei diagrammi dei componenti UML. Per altre informazioni, vedere [classi e linee di](#ClassesAndLifelines)vita.

#### <a name="parameter-types"></a>Tipi di parametro
 È anche possibile descrivere in un diagramma classi UML i tipi di parametri e i valori restituiti usati nei messaggi inviati tra le linee di vita.

#### <a name="use-case-details"></a>Dettagli relativi al caso di utilizzo
 Un caso di utilizzo rappresenta l'obiettivo di un utente e la sequenza di passaggi necessaria per raggiungerlo. La sequenza di passaggi può essere descritta in molti modi. Un'opzione consiste nel disegnare un diagramma di sequenza che mostra le interazioni tra gli utenti e i componenti principali del sistema. Per altre informazioni, vedere [diagrammi caso di utilizzo UML: linee guida](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Passaggi di base per la creazione di diagrammi di sequenza
 Per un elenco completo di elementi nei diagrammi di sequenza, vedere [diagrammi di sequenza UML:](../modeling/uml-sequence-diagrams-reference.md)informazioni di riferimento.

> [!NOTE]
> I passaggi dettagliati per la creazione di uno dei diagrammi di modellazione sono descritti in [modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-sequence-diagram"></a>Per creare un diagramma di sequenza

1. Scegliere **nuovo diagramma livello o UML**dal menu **architettura** .

2. In **modelli**fare clic su **diagramma di sequenza UML**.

3. Assegnare un nome al diagramma.

4. In **Aggiungi a progetto di modello**selezionare un progetto di modello esistente nella soluzione oppure **creare un nuovo progetto di modello**e quindi fare clic su **OK**.

    Viene visualizzato un nuovo diagramma di sequenza con la casella degli strumenti **diagramma sequenza** . La casella degli strumenti contiene gli elementi e i connettori richiesti.

   ![Parti di un diagramma di sequenza](../modeling/media/uml-sequence.png "UML_Sequence")

#### <a name="to-draw-a-sequence-diagram"></a>Per disegnare un diagramma di sequenza

1. Trascinare le **linee** di vita (1) dalla **casella degli strumenti** nel diagramma per rappresentare le istanze di classi, componenti, attori o dispositivi.

    > [!NOTE]
    > È anche possibile creare una linea di vita trascinando una classe, un'interfaccia, un attore o un componente esistente da **Esplora modelli UML** nel diagramma. Viene creata una linea di vita che rappresenta un'istanza del tipo selezionato.

2. Disegnare i messaggi per visualizzare in che modo le linee di vita collaborano per raggiungere uno specifico obiettivo.

     Per creare un messaggio (3, 4, 6, 7), fare clic su uno strumento dei messaggi. Fare clic sulla linea di vita di invio nel punto in cui deve iniziare il messaggio, quindi fare clic sulla linea di vita di ricezione.

     Viene visualizzata un'occorrenza esecuzione (5) nella linea di vita di ricezione. L'occorrenza esecuzione rappresenta un periodo di tempo durante il quale l'istanza esegue un metodo. È possibile creare altri messaggi che iniziano da un'occorrenza esecuzione.

3. Per visualizzare un messaggio proveniente da un'origine evento sconosciuta (9) o trasmesso a destinatari sconosciuti (10), disegnare un messaggio asincrono da o verso uno spazio vuoto nel diagramma. Questi messaggi vengono chiamati *messaggi trovati* (9) e *messaggi persi* (10).

    > [!NOTE]
    > Per spostare un gruppo di linee di vita con messaggi smarriti o trovati, attenersi alla procedura seguente per selezionare le linee di vita prima di spostarle: creare un rettangolo intorno alle linee di vita oppure tenere premuto **CTRL** mentre si fa clic su ciascuna linea di vita. Se si usa **Select All** o **CTRL**+a per selezionare tutte le linee di vita e quindi spostarle, tutti i messaggi smarriti o trovati collegati a tali **linee di vita** non vengono spostati. Se si verifica questo scenario, è possibile spostare questi messaggi separatamente.

4. Disegnare diagrammi di sequenza per ogni messaggio principale nello stesso componente o sistema.

#### <a name="to-change-the-order-of-messages"></a>Per modificare l'ordine dei messaggi

- Trascinare un messaggio verso l'alto o verso il basso sulla linea di vita. È possibile trascinarlo su altri messaggi o dentro o fuori un blocco di esecuzione.

     \- oppure -

- Fare clic sul messaggio e utilizzare i tasti **freccia su** e **freccia giù** per modificare le posizioni dei messaggi. Usare **MAIUSC + freccia su** e **MAIUSC + freccia giù** per modificare l'ordine dei messaggi.

#### <a name="to-move-or-copy-message-sequences-on-the-sequence-diagram"></a>Per spostare o copiare le sequenze di messaggi nel diagramma di sequenza

1. Fare clic con il pulsante destro del mouse su un messaggio (3, 4), quindi scegliere **copia**.

2. Fare clic con il pulsante destro del mouse sull'occorrenza esecuzione (5) o su una linea di vita (1) da cui si desidera inviare il nuovo messaggio, quindi fare clic su **Incolla**. Se si vuole, il nuovo mittente può trovarsi in un diagramma diverso.

     Una copia del messaggio e tutti i messaggi secondari vengono aggiunti alla fine dell'occorrenza esecuzione oppure alla fine della linea di vita.

    > [!NOTE]
    > Il messaggio incollato viene visualizzato sempre alla fine dell'occorrenza esecuzione o della linea di vita. Dopo averlo incollato, è possibile trascinarlo in una posizione precedente.

#### <a name="to-display-and-edit-the-signature-text-for-a-message"></a>Per visualizzare e modificare il testo della firma per un messaggio

- La linea di vita di destinazione deve essere associata o mappata ai tipi per poter visualizzare il testo della firma. Per completare questa attività, eseguire uno dei seguenti passaggi:

  - Fare clic con il pulsante destro del mouse sulla linea di vita, quindi scegliere **Crea classe**.

     -oppure-

  - Selezionare la linea di vita, premere **F4**, quindi nella finestra **Proprietà** impostare la proprietà **Type** su un tipo esistente o specificare il nome per un nuovo tipo. Fare clic con il pulsante destro del mouse sull'etichetta del messaggio, quindi scegliere **Crea operazione**.

    Il testo della firma viene visualizzato sotto l'etichetta del messaggio. Ora è possibile modificare il testo della firma. Per altre informazioni, vedere [classi e linee di](#ClassesAndLifelines)vita.

#### <a name="to-improve-the-layout-of-a-sequence-diagram"></a>Per migliorare il layout di un diagramma di sequenza

- Fare clic con il pulsante destro del mouse su una parte vuota del diagramma, quindi scegliere **Ridisponi layout**.

- Per annullare l'operazione, fare clic su **modifica**e quindi su **Annulla**.

#### <a name="to-change-the-package-that-owns-the-interaction"></a>Per modificare il pacchetto a cui appartiene l'interazione

1. In **Esplora modelli UML**individuare l'interazione visualizzata dal diagramma di sequenza.

    > [!NOTE]
    > L'interazione non verrà visualizzata in **Esplora modelli UML** fino a quando non si aggiunge la prima linea di vita al diagramma di sequenza.

2. Trascinare l'interazione nel pacchetto.

     \- oppure -

     Fare clic con il pulsante destro del mouse sull'interazione, quindi scegliere **taglia**. Fare clic con il pulsante destro del mouse sul pacchetto, quindi scegliere **Incolla**.

## <a name="Simple"></a>Creazione e utilizzo di diagrammi di sequenza semplici
 La forma più semplice e diffusa di diagramma di sequenza contiene solo linee di vita e messaggi. Un diagramma di questo tipo consente di visualizzare chiaramente una sequenza di interazioni tipica tra gli oggetti nella progettazione o tra il sistema e gli utenti. In genere, questo diagramma consente di discutere e comunicare in modo appropriato le informazioni sulla progettazione.

 Di seguito sono riportate alcuni aspetti da prendere in considerazione quando si disegna un diagramma di sequenza semplice.

### <a name="types-of-message"></a>Tipi di messaggio
 Sono disponibili tre strumenti per la creazione dei messaggi.

- Utilizzare lo strumento **sincrono** per descrivere un'interazione in cui il mittente attende che il ricevitore restituisca una risposta (3).

     Alla fine dell'occorrenza di esecuzione viene visualizzato un **<\<restituire > freccia >** . Indica la restituzione del controllo al mittente.

- Utilizzare lo strumento **asincrono** per descrivere un'interazione in cui il mittente può continuare immediatamente senza attendere il ricevitore (4).

- Utilizzare lo strumento **Crea** per descrivere un'interazione in cui il mittente crea il ricevitore (8).

     Un messaggio di creazione dovrebbe essere il primo messaggio ricevuto dal destinatario.

### <a name="annotating-the-interactions"></a>Annotazione delle interazioni
 Per descrivere in modo più dettagliato la sequenza, è possibile inserire un **Commento** in qualsiasi punto del diagramma.

 Con i **collegamenti ai commenti**è possibile collegare un commento a linee di vita, esecuzioni, utilizzi interazione e frammenti.

> [!CAUTION]
> Quando si collega un commento a un punto particolare della sequenza, collegarlo a un'occorrenza esecuzione, un utilizzo interazione o un frammento. Non collegarlo a una linea di vita perché, in questo caso, non resta collegato nel punto corretto della sequenza.

 Usare un commento per:

- Annotare gli obiettivi raggiunti nei punti chiave della sequenza. Ciò consente ai lettori di visualizzare gli obiettivi delle interazioni.

- Descrivere l'obiettivo generale dell'intera sequenza. Collegare il commento all'occorrenza esecuzione iniziale oppure lasciarlo scollegato. Ad esempio, "Il cliente ha scelto i prodotti dal menu e gli è stato fornito un prezzo".

- Descrivere le responsabilità di ogni linea di vita. Collegare il commento alla linea di vita. Ad esempio, "Il manager degli ordini raccoglie le scelte del menu del cliente".

- Annotare le eccezioni o le alternative che potrebbero essere eseguite al posto della sequenza tipica visualizzata. Ad esempio, "Il cliente può ignorare il resto della sequenza".

  - Valutare l'uso dei frammenti come alternativa più formale rispetto a questo tipo di nota. Vedere [Descrizione delle strutture di controllo con frammenti](#Fragments)

## <a name="deciding-the-scope-of-the-diagram"></a>Scelta dell'ambito del diagramma
 È importante chiarire cosa si vuole visualizzare nel diagramma.

#### <a name="initiating-event"></a>Evento di origine
 Ogni diagramma deve visualizzare la sequenza di interazioni risultante da un evento di origine. Ad esempio:

- Un utente che avvia un caso di utilizzo, ad esempio l'apertura della pagina Web per l'acquisto di un pasto.

- Un messaggio da un componente del sistema a un altro, ad esempio una query sulla disponibilità dei prodotti che l'utente vuole acquistare.

- Un evento attivato da una modifica dello stato, ad esempio la quantità delle scorte di un prodotto che scende al di sotto di una determinata soglia.

#### <a name="level-of-detail"></a>Livello di dettaglio
 I diagrammi di sequenza possono mostrare livelli di dettaglio diversi. È possibile decidere il livello di dettaglio in due dimensioni separate, in modo quasi indipendente:

 Le linee di vita possono rappresentare uno di questi livelli di dettaglio:

- Gli oggetti nel codice del programma, che esistono o sono in fase di sviluppo.

- I componenti o i componenti secondari, solitamente senza aspetti, proxy o altri meccanismi di connessione.

- Il sistema e gli attori esterni

  I messaggi possono rappresentare uno di questi livelli di dettaglio:

- I messaggi software nel codice del programma, in un'API o in un'interfaccia Web.

- Le transazioni o le transazioni secondarie, ad esempio tra gli utenti e il sistema oppure tra il codice e il database.

- Casi di utilizzo: interazioni principali tra gli utenti e il sistema.

  Se si esplora il codice esistente o si descrive una nuova progettazione, spesso è utile disegnare e discutere le visualizzazioni meno dettagliate.

## <a name="describing-variations"></a>Descrizione delle variazioni
 Il diagramma mostra un'unica sequenza di eventi tipica. Per visualizzare delle alternative possibili, ad esempio gli scenari di errore, è possibile usare una di queste opzioni:

- Disegnare diagrammi di sequenza separati per descrivere questi scenari

- Utilizzare [la descrizione delle strutture di controllo con frammenti](#Fragments) per visualizzare cicli, alternative e così via.

## <a name="assessing-the-design"></a>Valutazione della progettazione
 È possibile usare il diagramma per valutare la distribuzione delle attività tra gli oggetti o i componenti. Valutare il refactoring se vengono visualizzati questi motivi:

- Una linea di vita sembra eseguire tutte le operazioni mediante chiamate ad altri elementi, mentre le altre linee di vita rispondono solo passivamente.

- Molti messaggi attraversano le linee di vita. Ogni linea di vita deve inviare messaggi solo ad alcuni elementi adiacenti e non deve comunicare con gli elementi adiacenti dei relativi elementi adiacenti. In genere è possibile disporre le linee di vita in modo tale che siano presenti solo pochi punti in cui i messaggi attraversano le linee di vita e laddove si verificano tali intersezioni, la linea di vita di destinazione non dovrebbe scambiare anche i messaggi che contengono le linee di vita intersecate.

- Alcune linee di vita sembrano gestire più tipi di attività. È consigliabile trovare una frase breve che descriva le responsabilità di ogni linea di vita, riepilogando il lavoro svolto in risposta a ogni messaggio ricevuto.

## <a name="ClassesAndLifelines"></a>Classi e linee di vita
 Le linee di vita nei diagrammi di sequenza mostra le istanze di classi o di interfacce di componenti. È possibile assegnare un nome a una linea di vita in due modi:

|**A questo scopo**|**Usa questo formato**|
|--------------------------|-------------------------|
|Istanza anonima di un tipo.<br /><br /> Usare questo metodo se si ha una sola linea di vita di ogni tipo.|*typeName*|
|Istanza denominata di un tipo.<br /><br /> Usare questo metodo per visualizzare una sequenza costituita da più istanze dello stesso tipo.|*ObjectName*:*typeName*|

### <a name="creating-lifelines-from-types"></a>Creazione di linee di vita dai tipi
 È possibile creare nuove linee di vita dalle classi già definite, ad esempio in un diagramma classi.

> [!NOTE]
> Verificare che sia presente un diagramma di sequenza prima di eseguire questa attività.

##### <a name="to-create-a-lifeline-from-an-existing-type"></a>Per creare una linea di vita da un tipo esistente

- Trascinare una classe, un componente o un'interfaccia da Esplora modelli UML in un diagramma di sequenza.

   \- oppure -

  1. Fare clic con il pulsante destro del mouse sulla classe, sul componente o sull'interfaccia nel rispettivo diagramma, quindi scegliere **Crea linea**di vita.

  2. Nella finestra di dialogo **Crea linea** di vita selezionare un diagramma sequenza, quindi fare clic su **OK**.

     Viene visualizzata una nuova linea di vita con istanza denominata il cui tipo corrisponde a quello trascinato.

  > [!NOTE]
  > È possibile ripetere l'azione tutte le volte che si desidera. In questo modo vengono create linee di vita con nomi di istanza diversi.

##### <a name="to-change-the-type-of-a-lifeline"></a>Per modificare il tipo di una linea di vita

1. Fare clic con il pulsante destro del mouse su una linea di vita, quindi scegliere **Proprietà**.

2. Nella finestra **Proprietà** impostare la proprietà **tipo** . È possibile selezionare un tipo dal menu a discesa oppure digitare un nuovo nome.

### <a name="creating-classes-from-lifelines"></a>Creazione di classi dalle linee di vita
 Dopo aver creato uno o più diagrammi di sequenza, è possibile riepilogare le linee di vita creando classi o interfacce da tali diagrammi.

##### <a name="to-create-a-class-or-interface-from-a-lifeline"></a>Per creare una classe o un'interfaccia da una linea di vita

1. Fare clic con il pulsante destro del mouse sulla linea di vita, quindi scegliere **Crea classe** o **Crea interfaccia**.

     In Esplora modelli UML viene visualizzata una nuova classe o interfaccia.

2. Creare operazioni nella classe o interfaccia per ogni messaggio ricevuto dalla linea di vita:

    1. Selezionare tutti i messaggi da includere.

    2. Fare clic con il pulsante destro del mouse su uno dei messaggi, quindi scegliere **Crea metodo**.

         La nuova classe o interfaccia include operazioni per ogni messaggio selezionato.

         Il nome dell'operazione viene visualizzato sotto ogni freccia del messaggio e nella proprietà **Operation** del messaggio.

         Se il messaggio include parametri in formato "(parameter : type)", questi verranno visualizzati nell'elenco dei parametri della nuova operazione.

        > [!NOTE]
        > È necessario ripetere questo passaggio per aggiungere nuovi messaggi al diagramma di sequenza.

3. Per visualizzare la nuova classe o interfaccia in dettaglio, aggiungerla a un diagramma classi o dei componenti.

    1. Aprire o creare un diagramma classi o dei componenti.

    2. Trascinare la nuova classe o interfaccia da **Esplora modelli UML** a un diagramma classi.

         La classe o interfaccia viene visualizzata nel diagramma classi.

         \- oppure -

    3. Trascinare la nuova interfaccia da **Esplora modelli UML** su un componente o una porta in un diagramma dei componenti.

         L'interfaccia viene visualizzata nel componente come simbolo.

### <a name="creating-classes-for-parameters"></a>Creazione di classi per i parametri
 È possibile includere i parametri nei messaggi di un diagramma di sequenza. È possibile usare un diagramma classi UML per descrivere i tipi di parametri.

## <a name="Multiple"></a>Creazione di sequenze di interazione riutilizzabili
 È possibile usare diagramma separato per descrivere una sequenza contenente i dettagli da escludere oppure comuni a più diagrammi.

 È possibile creare un rettangolo di utilizzo interazione (12) in un diagramma che punta ai dettagli in un altro diagramma.

 Fare doppio clic su un utilizzo interazione per aprire il diagramma di sequenza collegato.

#### <a name="to-create-a-reusable-interaction-sequence-from-existing-lifelines"></a>Per creare un'interazione sequenza riutilizzabile da linee di vita esistenti

1. Nella **casella degli strumenti**fare clic su **utilizzo interazione**.

2. Nel diagramma di sequenza, tenere premuto il pulsante del mouse mentre si trascinano le linee di vita da includere nella sequenza riutilizzabile. Iniziare nella posizione verticale in cui inserire l'utilizzo interazione.

     Un utilizzo interazione viene visualizzato tra le linee di vita selezionate nel diagramma di sequenza.

3. Fare doppio clic sul nome dell'utilizzo interazione e rinominarlo per descrivere l'effetto della sequenza riutilizzabile nel diagramma.

     \- oppure -

     Scrivere il nome come chiamata di funzione con parametri.

4. Collegare l'utilizzo interazione a un altro diagramma di sequenza. Fare clic con il pulsante destro del mouse sull'utilizzo interazione, quindi:

     Fare clic su **Crea nuova sequenza** per creare un nuovo diagramma di sequenza

     \- oppure -

     Fare clic su **collega a sequenza** per eseguire il collegamento a un diagramma esistente.

     Visual Studio crea un collegamento tra l'utilizzo interazione e la nuova interazione sequenza.

     Nella soluzione viene visualizzato un nuovo diagramma di sequenza. Contiene le linee di vita usate per creare l'utilizzo interazione.

    > [!NOTE]
    > Verranno incluse solo le linee di vita usate per creare l'utilizzo interazione. Il nuovo diagramma non includerà le linee di vita create dopo l'utilizzo interazione, anche se ora sono incluse nell'utilizzo interazione.

#### <a name="to-create-a-reusable-sequence-from-existing-messages"></a>Per creare una sequenza riutilizzabile dai messaggi esistenti

- Fare clic con il pulsante destro del mouse sul messaggio che si desidera spostare e quindi scegliere **Sposta in diagramma**.

  Visual Studio:

  - Sostituisce con un utilizzo interazione il messaggio selezionato e tutti i messaggi sussidiari.

  - Sposta i messaggi sostituiti in un nuovo diagramma di sequenza.

  - Crea un collegamento tra l'utilizzo interazione e il nuovo diagramma di sequenza.

#### <a name="to-navigate-to-the-sequence-referenced-by-an-interaction-use"></a>Per spostarsi sulla sequenza a cui fa riferimento un utilizzo interazione

- Fare doppio clic sull'utilizzo interazione.

     \- oppure -

     Fare clic con il pulsante destro del mouse sull'utilizzo interazione, quindi scegliere **Vai a sequenza**.

### <a name="creating-a-placeholder-with-an-interaction-use"></a>Creazione di un segnaposto con un utilizzo interazione
 È possibile creare un utilizzo interazione senza collegarlo a un altro diagramma. È possibile usarlo come segnaposto per una parte della sequenza i cui dettagli devono ancora essere elaborati. Utilizzare il nome dell'interazione utilizzata per indicare il risultato desiderato.

## <a name="Collapse"></a>Compressione di gruppi di linee di vita
 È possibile comprimere un set di linee di vita, in modo che il gruppo venga visualizzato come una sola linea di vita, consentendo di visualizzare un gruppo di oggetti come un singolo componente. I messaggi e gli utilizzi interazione tra le linee di vita in un gruppo compresso sono nascosti. Vengono invece visualizzati i messaggi e le sequenze di interazioni che includono altre linee di vita.

#### <a name="to-collapse-a-group-of-lifelines-together"></a>Per comprimere un gruppo di linee di vita

1. Selezionare due o più linee di vita.

2. Fare clic con il pulsante destro del mouse su uno di essi, quindi scegliere **Comprimi**.

     Le linee di vita separate vengono sostituite da una singola linea di vita.

     I messaggi e gli utilizzi interazione che riguardano solo i membri del gruppo sono nascosti.

3. Per rinominare il gruppo, fare clic sul nome.

    > [!NOTE]
    > Il nome del gruppo andrà perso quando si espande il gruppo.

#### <a name="to-expand-a-collapsed-group"></a>Per espandere un gruppo compresso

- Fare clic con il pulsante destro del mouse sulla linea di vita compressa, quindi scegliere **Espandi**.

    > [!NOTE]
    > Il nome del gruppo verrà perso, insieme a tutti i collegamenti dal gruppo ai commenti o agli elementi di lavoro.

## <a name="Fragments"></a>Descrizione delle strutture di controllo con frammenti
 È possibile usare i frammenti combinati (13) per definire i cicli, i rami e l'elaborazione simultanea in un diagramma di sequenza. In alternativa, provare a usare un diagramma di attività. Il diagramma di attività non è utile per visualizzare i messaggi tra gli attori, ma in alcuni casi è più indicato perché visualizza meglio cicli, rami e concorrenza.

 Per un elenco completo dei tipi di frammento, vedere [descrivere il flusso di controllo con frammenti nei diagrammi di sequenza UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).

#### <a name="to-create-a-combined-fragment"></a>Per creare un frammento combinato

1. Selezionare un messaggio o una sequenza di messaggi tutti a partire dalla stessa occorrenza esecuzione o linea di vita.

    > [!NOTE]
    > Selezionare le frecce dei messaggi, non le occorrenze esecuzione alle quali puntano i messaggi.

2. Fare clic con il pulsante destro del mouse su uno dei messaggi, scegliere **Racchiudi**tra e quindi fare clic sul tipo di frammento necessario.

     Viene visualizzato un nuovo frammento che contiene i messaggi selezionati.

     Se il tipo di frammento combinato consente più frammenti, viene visualizzato anche un frammento vuoto.

3. Per impostare la protezione di un frammento, fare clic con il pulsante destro del mouse sul bordo del frammento, quindi scegliere **Proprietà**. Impostare la proprietà **Guard** .

     La proprietà Guard viene usata per definire la condizione per un ramo o un ciclo.

4. Per aggiungere un nuovo frammento a un tipo che consenta più frammenti, fare clic con il pulsante destro del mouse sul limite di un frammento e scegliere **Aggiungi**. Fare clic su **operando interazione prima** o **operando interazione dopo**.

5. Per aggiungere nuovi messaggi a un frammento, usare gli strumenti del messaggio o le funzioni di copia e incolla.

## <a name="see-also"></a>Vedere anche
 [Diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md) [modificare modelli UML e](../modeling/edit-uml-models-and-diagrams.md) diagrammi [caso d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md) diagrammi [classi UML: riferimento](../modeling/uml-class-diagrams-reference.md) [diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md) [diagrammi dei componenti UML: riferimento](../modeling/uml-component-diagrams-reference.md) [video: sketch di interazioni usando diagrammi di sequenza](https://go.microsoft.com/fwlink/?LinkId=201113)
