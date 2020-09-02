---
title: Introduzione ai linguaggi specifici del dominio
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a4761703610a87818cd1512f96530a0f865faf0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238543"
---
# <a name="get-started-with-domain-specific-languages"></a>Introduzione ai linguaggi specifici di dominio

In questo argomento vengono illustrati i concetti di base per la definizione e l'utilizzo di un linguaggio specifico di dominio (DSL) creato con l'SDK di modellazione per Visual Studio.

> [!NOTE]
> L'SDK per la trasformazione del modello di testo e l'SDK di modellazione di Visual Studio vengono installati automaticamente quando si installano funzionalità specifiche di Visual Studio. Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Se non si ha familiarità con DSLs, è consigliabile usare il **Lab strumenti DSL**, disponibile in questo sito: [SDK di visualizzazione e modellazione](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Che cosa è possibile fare con un Domain-Specific Language?

Un linguaggio specifico di dominio è una notazione, in genere grafica, progettata per essere usata per uno scopo specifico. Al contrario, i linguaggi come UML sono di uso generale. In un linguaggio DSL è possibile definire i tipi di elemento del modello e le relative relazioni e il modo in cui vengono presentati sullo schermo.

Una volta progettato un linguaggio DSL, è possibile distribuirlo come parte di un pacchetto VSIX (Visual Studio Integration Extension). Gli utenti utilizzano il linguaggio DSL in Visual Studio:

![Diagramma, casella degli strumenti e finestra di esplorazione dell'albero genealogico](../modeling/media/familyt_instance.png)

La notazione è solo parte di un linguaggio DSL. Insieme alla notazione, il pacchetto VSIX include gli strumenti che gli utenti possono applicare per facilitare la modifica e la generazione del materiale dai propri modelli.

Una delle principali applicazioni di DSLs è la generazione di codice programma, file di configurazione e altri elementi. Soprattutto in progetti e linee di prodotti di grandi dimensioni, in cui verranno create diverse varianti di un prodotto, la generazione di molti degli aspetti variabili da DSLs può offrire un notevole aumento dell'affidabilità e una risposta molto rapida alle modifiche dei requisiti.

Il resto di questa panoramica è una procedura dettagliata in cui vengono introdotte le operazioni di base per la creazione e l'utilizzo di un linguaggio specifico di dominio in Visual Studio.

## <a name="prerequisites"></a>Prerequisiti

Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:

| Componente | Collegamento |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| SDK di modellazione per Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Creare una soluzione DSL

Per creare un nuovo linguaggio specifico di dominio, creare una nuova soluzione di Visual Studio usando il modello di progetto Domain-Specific Language.

1. Scegliere **Nuovo** dal menu **File**e quindi fare clic su **Progetto**.

2. In **Tipi progetto**espandere il nodo **altri tipi di progetto** e fare clic su **estensibilità**.

3. Fare clic su **finestra di progettazione Domain-Specific Language**.

     ![Finestra di dialogo per la creazione di una soluzione DSL](../modeling/media/create_dsldialog.png)

4. Nella casella **nome** digitare **FamilyTree**. Fare clic su **OK**.

     Viene aperta la **procedura guidata Domain-Specific Language** e viene visualizzato un elenco di soluzioni DSL del modello.

     Fare clic su ogni modello per visualizzare una descrizione,

     I modelli sono punti di partenza utili. Ognuno di essi fornisce un linguaggio DSL funzionante completo, che è possibile modificare in base alle proprie esigenze. In genere, è possibile scegliere il modello più vicino a quello che si vuole creare.

5. Per questa procedura dettagliata, scegliere il modello di **lingua minima** .

6. Immettere un'estensione di file per il linguaggio DSL nella pagina appropriata della procedura guidata. Questa estensione verrà usata dai file contenenti le istanze del linguaggio DSL.

    - Scegliere un'estensione non associata ad alcuna applicazione nel computer o in qualsiasi computer in cui si desidera installare il linguaggio DSL. Ad esempio, **docx** e **htm** sarebbero estensioni di file non accettabili.

    - La procedura guidata avviserà se l'estensione immessa è in uso come DSL. Provare a usare un'estensione di file diversa. È anche possibile reimpostare l'istanza sperimentale di Visual Studio SDK per eliminare le precedenti finestre di progettazione sperimentali. Fare clic sul pulsante **Start**, scegliere **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare l'istanza sperimentale Microsoft Visual Studio 2010**.

7. Esaminare le altre pagine e quindi fare clic su **fine**.

     Viene generata una soluzione che contiene due progetti. Sono denominate DSL e DslPackage. Viene aperto un file di diagramma denominato DslDefinition. DSL.

    > [!NOTE]
    > La maggior parte del codice che è possibile visualizzare nelle cartelle dei due progetti viene generata da DslDefinition. DSL. Per questo motivo, in questo file viene apportata la maggior parte delle modifiche al linguaggio DSL.

L'interfaccia utente ora è simile a quella nell'immagine seguente.

![Progettazione DSL](../modeling/media/dsl_designer.png)

Questa soluzione definisce un linguaggio specifico di dominio. Per ulteriori informazioni, vedere [Panoramica dell'interfaccia utente di strumenti Domain-Specific Language](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Parti importanti della soluzione DSL

Si notino gli aspetti seguenti della nuova soluzione:

- **Dsl\DslDefinition.DSL** Questo è il file visualizzato quando si crea una soluzione DSL. Quasi tutto il codice nella soluzione viene generato da questo file e la maggior parte delle modifiche apportate a una definizione DSL viene eseguita qui. Per ulteriori informazioni, vedere Utilizzo del [diagramma di definizione DSL](../modeling/working-with-the-dsl-definition-diagram.md).

- **Progetto DSL** Questo progetto contiene codice che definisce il linguaggio specifico di dominio.

- **Progetto DslPackage** Questo progetto contiene codice che consente di aprire e modificare le istanze del linguaggio DSL in Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Esecuzione del linguaggio DSL

È possibile eseguire la soluzione DSL appena creata. Successivamente, è possibile modificare la definizione DSL gradualmente, eseguendo di nuovo la soluzione dopo ogni modifica.

### <a name="to-experiment-with-the-dsl"></a>Per sperimentare il linguaggio DSL

1. Fare clic su **trasforma tutti i modelli** nella barra degli strumenti **Esplora soluzioni** . Questa operazione Rigenera la maggior parte del codice sorgente da DslDefinition. DSL.

    > [!NOTE]
    > Quando si modifica *DslDefinition. DSL*, è necessario fare clic su **trasforma tutti i modelli** prima di ricompilare la soluzione. È possibile automatizzare questo passaggio. Per ulteriori informazioni, vedere [come automatizzare Transform All Templates](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\)).

2. Premere **F5**o scegliere **Avvia debug** dal menu **Debug**.

     Il linguaggio DSL viene compilato ed è installato nell'istanza sperimentale di Visual Studio.

     Viene avviata un'istanza sperimentale di Visual Studio. L'istanza sperimentale prende le impostazioni da un sottoalbero separato del registro di sistema, in cui le estensioni di Visual Studio vengono registrate a scopo di debug. Le istanze normali di Visual Studio non hanno accesso alle estensioni registrate.

3. Nell'istanza sperimentale di Visual Studio aprire il file di modello denominato **test** da **Esplora soluzioni**.

     \- - oppure -

     Fare clic con il pulsante destro del mouse sul progetto di debug, scegliere **Aggiungi**, quindi fare clic su **elemento**. Nella finestra di dialogo **Aggiungi elemento** selezionare il tipo di file del linguaggio DSL.

     Il file del modello viene aperto come diagramma vuoto.

     Verrà aperta la casella degli strumenti e verranno visualizzati gli strumenti appropriati per il tipo di diagramma.

4. Usare gli strumenti per creare forme e connettori nel diagramma.

    1. Per creare forme, trascinare dall'esempio Forma nel diagramma.

    2. Per connettere due forme, fare clic sullo strumento connettore di esempio, fare clic sulla prima forma, quindi fare clic sulla seconda forma.

5. Fare clic sulle etichette delle forme per modificarle.

Il Visual Studio sperimentale sarà simile all'esempio seguente:

![Albero di esempio del linguaggio specifico di dominio in Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Contenuto di un modello

Il contenuto di un file che è un'istanza di un linguaggio DSL viene definito *modello*. Il modello contiene *model* <em>elementi</em> del modello e *collegamenti* tra gli elementi. La definizione DSL specifica i tipi di elementi del modello e i collegamenti che possono esistere nel modello. Ad esempio, in un linguaggio DSL creato dal modello di linguaggio minimo, esiste un tipo di elemento del modello e un tipo di collegamento.

La definizione DSL può specificare il modo in cui il modello viene visualizzato in un diagramma. È possibile scegliere tra diversi stili di forme e connettori. È possibile specificare che alcune forme vengano visualizzate all'interno di altre forme.

È possibile visualizzare un modello come albero nella visualizzazione di **esplorazione** durante la modifica di un modello. Quando si aggiungono forme al diagramma, gli elementi del modello vengono visualizzati anche nella finestra di esplorazione. La finestra di esplorazione può essere utilizzata anche se non è presente alcun diagramma.

Se la finestra di esplorazione non è visibile nell'istanza di debug di Visual Studio, scegliere **altre finestre**dal menu **Visualizza** , quindi fare clic su *\<Your Language>* **Esplora**.

### <a name="the-api-of-your-dsl"></a>API del linguaggio DSL

Il linguaggio DSL genera un'API che consente di leggere e aggiornare i modelli che sono istanze del linguaggio DSL. Un'applicazione dell'API consiste nel generare file di testo da un modello. Per altre informazioni, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

Nella soluzione di debug aprire i file del modello con estensione ". tt". Questi esempi dimostrano come è possibile generare testo da modelli e consentono di testare l'API del linguaggio DSL. Uno degli esempi è scritto in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , l'altro in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

In ogni file di modello è il file generato. Espandere il file modello in Esplora soluzioni e aprire il file generato.

Il file modello contiene un breve segmento di codice in cui sono elencati tutti gli elementi nel modello.

Il file generato contiene il risultato.

Quando si modifica un file di modello, dopo la rigenerazione dei file vengono visualizzate le modifiche corrispondenti nei file generati.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Per rigenerare i file di testo dopo aver modificato il file di modello

1. Nell'istanza sperimentale di Visual Studio salvare il file del modello.

2. Verificare che il parametro del nome file in ogni file con estensione tt faccia riferimento al file di modello usato per gli esperimenti. Salvare il file con estensione tt.

3. Fare clic su **trasforma tutti i modelli** nella barra degli strumenti di **Esplora soluzioni**.

     \- - oppure -

     Fare clic con il pulsante destro del mouse sui modelli che si desidera rigenerare, quindi scegliere **Esegui strumento personalizzato**.

È possibile aggiungere qualsiasi numero di file di modello di testo a un progetto. Ogni modello genera un file di risultati.

> [!NOTE]
> Quando si modifica la definizione DSL, il codice del modello di testo di esempio non funzionerà, a meno che non venga aggiornato.

Per ulteriori informazioni, vedere [generazione di codice da un Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md) e [scrittura di codice per personalizzare una Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

## <a name="customizing-the-dsl"></a>Personalizzazione del linguaggio DSL

Quando si desidera modificare la definizione DSL, chiudere l'istanza sperimentale e aggiornare la definizione nell'istanza principale di Visual Studio.

> [!NOTE]
> Dopo aver modificato la definizione DSL, è possibile che si perdano le informazioni nei modelli di test creati usando versioni precedenti.  La soluzione di debug, ad esempio, contiene un file denominato Sample, che contiene alcune forme e connettori. Dopo aver iniziato a sviluppare la definizione DSL, non saranno visibili e andranno perse quando si salva il file.

È possibile creare un'ampia gamma di estensioni per il linguaggio DSL. Gli esempi seguenti offrono un'idea delle possibilità.

Dopo ogni modifica, salvare la definizione DSL, fare clic su **trasforma tutti i modelli** in **Esplora soluzioni**, quindi premere **F5** per provare il DSL modificato.

### <a name="rename-the-types-and-tools"></a>Rinominare i tipi e gli strumenti

Rinominare le classi e le relazioni di dominio esistenti. Ad esempio, a partire da una definizione DSL creata dal modello di linguaggio minimo, è possibile eseguire le operazioni di ridenominazione seguenti per fare in modo che il linguaggio DSL rappresenti gli alberi genealogici.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Per rinominare le classi, le relazioni e gli strumenti di dominio

1. Nel diagramma di DslDefinition rinominare **ExampleModel** in **FamilyTreeModel**, **ExampleElement** to **Person**, **targets** to **parents**e **Sources** to **Children**. È possibile fare clic su ogni etichetta per modificarla.

     ![Diagramma di definizione DSL &#45; modello di albero genealogico](../modeling/media/familyt_person.png)

2. Rinominare gli strumenti elemento e connettore.

    1. Aprire la finestra Esplora DSL facendo clic sulla scheda sotto Esplora soluzioni. Se non è possibile visualizzarlo, scegliere **altre finestre** dal menu **Visualizza** , quindi fare clic su **Esplora DSL**. DSL Explorer è visibile solo quando il diagramma di definizione DSL è la finestra attiva.

    2. Aprire il Finestra Proprietà e posizionarlo in modo che sia possibile visualizzare le proprietà e la finestra di esplorazione DSL nello stesso momento.

    3. In DSL Explorer espandere **Editor**, **schede della casella degli strumenti**, *\<your DSL>* , quindi **strumenti**.

    4. Fare clic su **ExampleElement**. Si tratta dell'elemento della casella degli strumenti utilizzato per creare gli elementi.

    5. Nella Finestra Proprietà impostare la proprietà **nome** su **Person**.

         Si noti che la proprietà **Caption** cambia anche.

    6. Allo stesso modo, modificare il nome dello strumento **ExampleConnector** in **ParentLink**. Modificare la proprietà **Caption** in modo che non sia una copia della proprietà Name. Immettere, ad esempio, **collegamento padre**.

3. Ricompilare il linguaggio DSL.

    1. Salvare il file di definizione DSL.

    2. Fare clic su **trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni

    3. Premere F5. Attendere fino a quando non viene visualizzata l'istanza sperimentale di Visual Studio.

4. Nella soluzione di debug nell'istanza sperimentale di Visual Studio aprire un file del modello di test. Trascinare gli elementi nella casella degli strumenti. Si noti che le didascalie degli strumenti e i nomi dei tipi in DSL Explorer sono stati modificati.

5. Salvare il file del modello.

6. Aprire un file con estensione tt e sostituire le occorrenze dei nomi di tipo e proprietà obsoleti con i nuovi nomi.

7. Verificare che il nome file specificato nel file con estensione TT specifichi il modello di test.

8. Salvare il file con estensione tt. Aprire il file generato per visualizzare il risultato dell'esecuzione del codice nel file con estensione tt. Verificare che sia corretto.

### <a name="add-domain-properties-to-classes"></a>Aggiungere le proprietà del dominio alle classi
 Aggiungere proprietà a una classe di dominio, ad esempio per rappresentare gli anni di nascita e morte di una persona.

 Per rendere visibili le nuove proprietà nel diagramma, è necessario aggiungere elementi *Decorator* alla forma che Visualizza l'elemento del modello. È inoltre necessario eseguire il mapping delle proprietà agli elementi Decorator.

##### <a name="to-add-properties-and-display-them"></a>Per aggiungere proprietà e visualizzarle

1. Aggiungere le proprietà.

   1. Nel diagramma di definizione DSL, fare clic con il pulsante destro del mouse sulla classe di dominio **Person** , scegliere **Aggiungi**, quindi fare clic su **Proprietà dominio**.

   2. Digitare un elenco di nuovi nomi di proprietà, ad esempio **nascita** e **morte**. Premere **invio** dopo ogni.

2. Aggiungere elementi Decorator che visualizzeranno le proprietà nella forma.

   1. Seguire la linea grigia che si estende dalla classe di dominio person all'altro lato del diagramma. Si tratta di una mappa di elementi del diagramma. Collega la classe di dominio a una classe Shape.

   2. Fare clic con il pulsante destro del mouse su questa classe Shape, scegliere **Aggiungi**, quindi fare clic su **elemento Decorator testo**.

   3. Aggiungere due elementi Decorator con nomi quali **BirthDecorator** e **DeathDecorator**.

   4. Selezionare ogni nuovo elemento Decorator, quindi nella Finestra Proprietà impostare il campo **position** . Determina la posizione in cui verrà visualizzato il valore della proprietà del dominio nella forma. Ad esempio, impostare **InnerBottomLeft** e **InnerBottomRight**.

        ![Definizione della forma Raggruppamento](../modeling/media/familyt_compartment.png)

3. Eseguire il mapping degli elementi Decorator alle proprietà.

   1. Aprire la finestra Dettagli DSL. Si trova in genere in una scheda accanto alla finestra output. Se non è possibile visualizzarlo, scegliere **altre finestre**dal menu **Visualizza** , quindi fare clic su **Dettagli DSL**.

   2. Nel diagramma di definizione DSL fare clic sulla riga che connette la classe di dominio **Person** alla classe Shape.

   3. In **Dettagli DSL**, nella scheda **Mapping elementi Decorator** , fare clic sulla casella di controllo in un elemento Decorator non mappato. In **proprietà di visualizzazione**selezionare la proprietà del dominio a cui si desidera eseguire il mapping. Ad esempio, eseguire il mapping di **BirthDecorator** a **Birth**.

4. Salvare il linguaggio DSL, fare clic su trasforma tutti i modelli e premere F5.

5. In un diagramma modello di esempio, verificare che sia ora possibile fare clic sulle posizioni selezionate e digitare i relativi valori. Inoltre, quando si seleziona una forma **persona** , il finestra Proprietà Visualizza le nuove proprietà di nascita e morte.

6. In un file con estensione TT è possibile aggiungere il codice che ottiene le proprietà di ogni persona.

   ![Diagramma, casella degli strumenti e finestra di esplorazione dell'albero genealogico](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definire nuove classi
 È possibile aggiungere relazioni e classi di dominio a un modello. Ad esempio, è possibile creare una nuova classe per rappresentare le città e una nuova relazione per rappresentare la persona vissuta in una città.

 Per rendere i diversi tipi distinti in un diagramma del modello, è possibile eseguire il mapping delle classi di dominio a tipi diversi di forma o a forme con geometria e colori diversi.

##### <a name="to-add-and-display-a-new-domain-class"></a>Per aggiungere e visualizzare una nuova classe di dominio

1. Aggiungere una classe di dominio e impostarla come figlio della radice del modello.

    1. Nel diagramma di definizione DSL fare clic sullo strumento **relazione di incorporamento** , fare clic sulla classe radice **FamilyTreeModel**, quindi fare clic su una parte vuota del diagramma.

         Viene visualizzata una nuova classe di dominio, connessa a FamilyTreeModel con una relazione di incorporamento.

         Impostarne il nome, ad esempio **Town**.

        > [!NOTE]
        > Ogni classe di dominio ad eccezione della radice del modello deve essere la destinazione di almeno una relazione di incorporamento o deve ereditare da una classe che è la destinazione di un incorporamento. Per questo motivo, è spesso utile creare una classe di dominio usando lo strumento relazione di incorporamento.

    2. Aggiungere una proprietà di dominio alla nuova classe, ad esempio **Name**.

2. Aggiungere una relazione di riferimento tra Person e Town.

    1. Fare clic sullo strumento **relazione di riferimento** , scegliere persona, quindi fare clic su città.

         ![Frammento della definizione DSL: radice dell'albero genealogico](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Le relazioni di riferimento rappresentano riferimenti incrociati da una parte dell'albero del modello a un'altra.

3. Aggiungere una forma per rappresentare le città nei diagrammi del modello.

    1. Trascinare una **forma geometria** dalla casella degli strumenti al diagramma e rinominarla, ad esempio **TownShape**.

    2. Nella Finestra Proprietà impostare i campi aspetto della nuova forma, ad esempio colore riempimento e geometria.

    3. Aggiungere un elemento Decorator per visualizzare il nome della città e rinominarlo NameDecorator. Impostare la relativa proprietà Position.

4. Eseguire il mapping della classe di dominio Town a TownShape.

    1. Fare clic sullo strumento **Mappa elementi diagramma** , quindi sulla classe di dominio della città e infine sulla classe di forma TownShape.

    2. Nella scheda **Mapping elementi Decorator** della finestra **Dettagli DSL** con il connettore mappa selezionato selezionare NameDecorator e impostare proprietà di **visualizzazione** su nome.

5. Creare un connettore per visualizzare la relazione tra persona e città.

    1. Trascinare un connettore dalla casella degli strumenti al diagramma. Rinominare e impostare le proprietà relative all'aspetto.

    2. Utilizzare lo strumento **Mappa elementi diagramma** per collegare il nuovo connettore alla relazione tra persona e città.

         ![Definizione dell'albero genealogico con mappa di forme aggiunte](../modeling/media/familyt_shapemap.png)

6. Creazione di uno strumento elemento per la creazione di una nuova città.

    1. In **DSL Explorer**espandere **Editor** e quindi **schede della casella degli strumenti**.

    2. Fare clic con il pulsante destro del mouse *\<your DSL>* e scegliere **Aggiungi nuovo elemento strumento**.

    3. Impostare la proprietà **Name** del nuovo strumento e impostare la relativa proprietà **Class** su Town.

    4. Imposta la proprietà dell' **icona della casella degli strumenti** . Fare clic su **[...]** e nel campo **nome file** Selezionare un file di icona.

7. Creazione di uno strumento di connessione per la creazione di un collegamento tra città e persone.

    1. Fare clic con il pulsante destro del mouse *\<your DSL>* e quindi scegliere **Aggiungi nuovo strumento connettore**.

    2. Impostare la proprietà Name del nuovo strumento.

    3. Nella proprietà **ConnectionBuilder** selezionare il generatore che contiene il nome della relazione person-Town.

    4. Impostare l' **icona della casella degli strumenti**.

8. Salvare la definizione DSL, fare clic su **trasforma tutti i modelli**, quindi premere **F5**.

9. Nell'istanza sperimentale di Visual Studio aprire un file del modello di test. Usare i nuovi strumenti per creare città e collegamenti tra città e persone. Si noti che è possibile creare collegamenti solo tra i tipi di elemento corretti.

10. Creare codice che elenca la città in cui risiede ogni persona. I modelli di testo sono uno dei punti in cui è possibile eseguire tale codice. Ad esempio, è possibile modificare il file Sample.tt esistente nella soluzione di debug in modo che contenga il codice seguente:

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

     Quando si salva il file con estensione TT, viene creato un file sussidiario che contiene l'elenco di persone e le relative residenze. Per ulteriori informazioni, vedere [generazione di codice da un Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Convalida e comandi
 È possibile sviluppare ulteriormente questo DSL aggiungendo vincoli di convalida. Questi vincoli sono metodi che è possibile definire, che assicurano che lo stato del modello sia corretto. Ad esempio, è possibile definire un vincolo per assicurarsi che la data di nascita di un elemento figlio sia successiva a quella degli elementi padre. La funzionalità di convalida Visualizza un avviso se l'utente DSL tenta di salvare un modello che interrompe i vincoli. Per ulteriori informazioni, vedere [convalida in un Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

 È anche possibile definire i comandi di menu che l'utente può richiamare. I comandi possono modificare il modello. Possono anche interagire con altri modelli in Visual Studio e con risorse esterne. Per altre informazioni, vedere [procedura: modificare un comando di menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).

## <a name="deploying-the-dsl"></a>Distribuzione del linguaggio DSL
 Per consentire ad altri utenti di usare il linguaggio specifico di dominio, si distribuisce un file di estensione di Visual Studio (VSIX). Questa operazione viene creata quando si compila la soluzione DSL.

 Individuare il file con estensione VSIX nella cartella bin della soluzione. Copiarlo nel computer in cui si vuole installarlo. Nel computer fare doppio clic sul file VSIX. Il linguaggio DSL può essere usato in tutte le istanze di Visual Studio nel computer.

 È possibile usare la stessa procedura per installare il linguaggio DSL nel computer in uso, in modo da non dover usare l'istanza sperimentale di Visual Studio.

 Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Rimozione di DSLs sperimentali obsoleti
 Se sono stati creati DSLs sperimentali che non si desidera più, è possibile rimuoverli dal computer reimpostando l'istanza sperimentale di Visual Studio.

 Questo eliminerà dal computer tutte le DSLs sperimentali e altre estensioni sperimentali di Visual Studio. Si tratta di estensioni che sono state eseguite in modalità di debug.

 Questa procedura non rimuove DSLs o altre estensioni di Visual Studio installate completamente eseguendo il file VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Per reimpostare l'istanza sperimentale di Visual Studio

1. Fare clic sul pulsante **Start**, scegliere **tutti i programmi**, **Microsoft Visual Studio 2010 SDK**, **strumenti**e quindi **reimpostare l'istanza sperimentale Microsoft Visual Studio 2010**.

2. Ricompilare eventuali DSLs sperimentali o altre estensioni sperimentali di Visual Studio che si vuole ancora usare.

## <a name="see-also"></a>Vedere anche

- [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
