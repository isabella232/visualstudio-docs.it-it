---
title: Introduzione ai linguaggi specifici del dominio
description: Informazioni sui concetti di base relativi alla definizione e all'uso di un linguaggio specifico di dominio (DSL) creato con Modeling SDK per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2ae488056986afbe35763be1eebb500ff0eab9a8
ms.sourcegitcommit: 674d3fafa7c9e0cb0d1338027ef419a49c028c36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2021
ms.locfileid: "112602264"
---
# <a name="get-started-with-domain-specific-languages"></a>Introduzione ai linguaggi specifici di dominio

Questo argomento illustra i concetti di base relativi alla definizione e all'uso di un linguaggio specifico di dominio (DSL) creato con Modeling SDK per Visual Studio.

> [!NOTE]
> Text Template Transformation SDK e Visual Studio Modeling SDK vengono installati automaticamente quando si installano funzionalità specifiche di Visual Studio. Per informazioni dettagliate, vedere [questo post di blog](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

Se non si ha una versione di DSL, è consigliabile usare il lab degli strumenti **DSL,** disponibile in questo sito: [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)

## <a name="what-can-you-do-with-a-domain-specific-language"></a>Cosa è possibile fare con un Domain-Specific lingua?

Un linguaggio specifico di dominio è una notazione, in genere grafica, progettata per essere usata per uno scopo specifico. Al contrario, i linguaggi come UML sono per utilizzo generico. In un DSL è possibile definire i tipi di elemento del modello e le relative relazioni e come vengono presentati sullo schermo.

Dopo aver progettato un DSL, è possibile distribuirlo come parte di un pacchetto Visual Studio Integration Extension (VSIX). Gli utenti lavorano con DSL in Visual Studio:

![Diagramma, casella degli strumenti e finestra di esplorazione dell'albero genealogico](../modeling/media/familyt_instance.png)

La notazione è solo parte di un DSL. Insieme alla notazione, il pacchetto VSIX include strumenti che gli utenti possono applicare per consentire loro di modificare e generare materiale dai modelli.

Una delle principali applicazioni delle DSL è la generazione di codice del programma, file di configurazione e altri elementi. Soprattutto nei progetti di grandi dimensioni e nelle linee di prodotti, in cui verranno create diverse varianti di un prodotto, la generazione di molti degli aspetti variabili dalle DSL può offrire un aumento significativo dell'affidabilità e una risposta molto rapida alle modifiche dei requisiti.

Il resto di questa panoramica è una procedura dettagliata che introduce le operazioni di base per la creazione e l'uso di un linguaggio specifico di dominio in Visual Studio.

## <a name="prerequisites"></a>Prerequisiti

Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:

| Componente | Collegamento |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [https://go.microsoft.com/fwlink/?linkid=2166172](../extensibility/visual-studio-sdk.md) |
| SDK di modellazione per Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="create-a-dsl-solution"></a>Creare una soluzione DSL

Per creare un nuovo linguaggio specifico di dominio, creare una nuova soluzione Visual Studio usando il modello di progetto Domain-Specific Language.

1. Scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.

2. In **Tipi di progetto** espandere il nodo Altri tipi **di** progetto e fare clic su **Estendibilità**.

3. Fare **clic Finestra di progettazione Domain-Specific Language**.

     ![Finestra di dialogo per la creazione di una soluzione DSL](../modeling/media/create_dsldialog.png)

4. Nella casella **Nome** digitare **FamilyTree**. Fare clic su **OK**.

     Verrà **Domain-Specific Language procedura guidata** e verrà visualizzato un elenco di soluzioni DSL modello.

     Fare clic su ogni modello per visualizzare una descrizione,

     I modelli sono punti di partenza utili. Ognuno di essi fornisce un DSL funzionante completo, che è possibile modificare in base alle proprie esigenze. In genere, è necessario scegliere il modello più vicino a quello che si vuole creare.

5. Per questa procedura dettagliata, scegliere il **modello Linguaggio** minimo.

6. Immettere un'estensione di file per il linguaggio DSL nella pagina appropriata della procedura guidata. Questa estensione verrà usata dai file contenenti le istanze del linguaggio DSL.

    - Scegliere un'estensione non associata ad alcuna applicazione nel computer o in qualsiasi computer in cui si vuole installare il DSL. Ad esempio, **docx** e **htm** sarebbero estensioni di file inaccettabili.

    - La procedura guidata avviserà se l'estensione immessa è in uso come DSL. Provare a usare un'estensione di file diversa. È anche possibile reimpostare l'istanza sperimentale di Visual Studio SDK per eliminare le precedenti finestre di progettazione sperimentali. Fare **clic su Start**, **scegliere** Tutti i programmi , Microsoft Visual Studio **SDK 2010**, **Strumenti** e quindi reimpostare l'istanza **sperimentale Microsoft Visual Studio 2010**.

7. Esaminare le altre pagine e quindi fare clic su **Fine**.

     Viene generata una soluzione che contiene due progetti. Sono denominati Dsl e DslPackage. Verrà aperto un file di diagramma denominato DslDefinition.dsl.

    > [!NOTE]
    > La maggior parte del codice che è possibile visualizzare nelle cartelle nei due progetti viene generata da DslDefinition.dsl. Per questo motivo, la maggior parte delle modifiche al DSL viene apportata in questo file.

L'interfaccia utente ora è simile a quella nell'immagine seguente.

![Progettazione DSL](../modeling/media/dsl_designer.png)

Questa soluzione definisce un linguaggio specifico di dominio. Per altre informazioni, vedere Panoramica di Domain-Specific [Language Tools Interfaccia utente](../modeling/overview-of-the-domain-specific-language-tools-user-interface.md).

## <a name="the-important-parts-of-the-dsl-solution"></a>Parti importanti della soluzione DSL

Si notino gli aspetti seguenti della nuova soluzione:

- **Dsl\DslDefinition.dsl** Questo è il file visualizzato quando si crea una soluzione DSL. Quasi tutto il codice nella soluzione viene generato da questo file e la maggior parte delle modifiche apportate a una definizione DSL viene apportata qui. Per altre informazioni, vedere Uso del diagramma di [definizione DSL](../modeling/working-with-the-dsl-definition-diagram.md).

- **Progetto Dsl** Questo progetto contiene codice che definisce il linguaggio specifico di dominio.

- **Progetto DslPackage** Questo progetto contiene codice che consente l'apertura e la modifica di istanze del DSL in Visual Studio.

## <a name="running-the-dsl"></a><a name="Debugging"></a> Esecuzione di DSL

È possibile eseguire la soluzione DSL non appena è stata creata. Successivamente, è possibile modificare gradualmente la definizione DSL, eseguendo di nuovo la soluzione dopo ogni modifica.

### <a name="to-experiment-with-the-dsl"></a>Per sperimentare con il DSL

1. Fare **clic su Trasforma tutti i** modelli nella barra **Esplora soluzioni** strumenti. In questo modo la maggior parte del codice sorgente viene rigenerata da DslDefinition.dsl.

    > [!NOTE]
    > Ogni volta che si *modifica DslDefinition.dsl,* è necessario fare clic **su Trasforma** tutti i modelli prima di ricompilare la soluzione. È possibile automatizzare questo passaggio. Per altre informazioni, vedere [Come automatizzare la trasformazione di tutti i modelli.](/previous-versions/visualstudio/visual-studio-2012/ff521399\(v\=vs.110\))

2. Premere **F5** o scegliere **Avvia debug** dal menu **Debug**.

     Il DSL viene compilato e installato nell'istanza sperimentale di Visual Studio.

     Viene avviata un'istanza sperimentale di Visual Studio. L'istanza sperimentale accetta le impostazioni da un sottoalbero separato del Registro di sistema, in cui Visual Studio le estensioni vengono registrate a scopo di debug. Le istanze normali Visual Studio non hanno accesso alle estensioni registrate.

3. Nell'istanza sperimentale di Visual Studio aprire il file di modello **denominato Test** da **Esplora soluzioni**.

     \- - oppure -

     Fare clic con il pulsante destro del mouse sul progetto Debug, scegliere **Aggiungi** e quindi fare clic su **Elemento**. Nella finestra **di dialogo Aggiungi** elemento selezionare il tipo di file DSL.

     Il file di modello viene aperto come diagramma vuoto.

     Verrà visualizzata la casella degli strumenti e verranno visualizzati gli strumenti appropriati per il tipo di diagramma.

4. Usare gli strumenti per creare forme e connettori nel diagramma.

    1. Per creare forme, trascinare dal riquadro Forma nel diagramma.

    2. Per connettere due forme, fare clic sul connettore di esempio, fare clic sulla prima forma e quindi fare clic sulla seconda forma.

5. Fare clic sulle etichette delle forme per modificarle.

L'Visual Studio sperimentale sarà simile all'esempio seguente:

![Albero di esempio del linguaggio specifico di dominio in Visual Studio](../modeling/media/dsl_min.png)

### <a name="the-content-of-a-model"></a>Contenuto di un modello

Il contenuto di un file che è un'istanza di un DSL è denominato *modello*. Il modello contiene *elementi del* <em>modello</em> e *collegamenti* tra gli elementi. La definizione DSL specifica quali tipi di elementi del modello e collegamenti possono esistere nel modello. Ad esempio, in un linguaggio DSL creato dal modello Minimal Language è presente un tipo di elemento del modello e un tipo di collegamento.

La definizione DSL può specificare la modalità di visualizzazione del modello in un diagramma. È possibile scegliere tra un'ampia gamma di stili di forme e connettori. È possibile specificare che alcune forme vengano visualizzate all'interno di altre forme.

È possibile visualizzare un modello come albero nella visualizzazione **Esplora** risorse durante la modifica di un modello. Quando si aggiungono forme al diagramma, anche gli elementi del modello vengono visualizzati nello explorer. Lo explorer può essere usato anche se non è presente alcun diagramma.

Se non è possibile visualizzare Esplora risorse nell'istanza di debug di Visual Studio, scegliere Altre **finestre** dal **menu** Visualizza e quindi fare clic su Esplora *\<Your Language>* **risorse**.

### <a name="the-api-of-your-dsl"></a>API del DSL

Il DSL genera un'API che consente di leggere e aggiornare i modelli che sono istanze del DSL. Un'applicazione dell'API è la generazione di file di testo da un modello. Per altre informazioni, vedere Generazione di codice in fase [di progettazione tramite modelli di testo T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

Nella soluzione Debug aprire i file modello con estensione ".tt". Questi esempi illustrano come generare testo dai modelli e consentono di testare l'API del DSL. Uno degli esempi è scritto in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] , l'altro in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] .

In ogni file modello è il file generato. Espandere il file modello in Esplora soluzioni e aprire il file generato.

Il file modello contiene un breve segmento di codice che elenca tutti gli elementi nel modello.

Il file generato contiene il risultato.

Quando si modifica un file di modello, dopo la rigenerazione dei file verranno apportate le modifiche corrispondenti nei file generati.

#### <a name="to-regenerate-text-files-after-you-change-the-model-file"></a>Per rigenerare i file di testo dopo aver modificato il file di modello

1. Nell'istanza sperimentale di Visual Studio salvare il file di modello.

2. Assicurarsi che il parametro del nome file in ogni file con estensione tt faccia riferimento al file di modello in uso per gli esperimenti. Salvare il file con estensione tt.

3. Fare **clic su Trasforma tutti i** modelli sulla barra degli strumenti **Esplora soluzioni**.

     \- - oppure -

     Fare clic con il pulsante destro del mouse sui modelli da rigenerare e quindi scegliere **Esegui strumento personalizzato**.

È possibile aggiungere un numero qualsiasi di file modello di testo a un progetto. Ogni modello genera un file di risultati.

> [!NOTE]
> Quando si modifica la definizione DSL, il codice del modello di testo di esempio non funzionerà, a meno che non venga aggiornato.

Per altre informazioni, vedere Generazione di codice da un linguaggio [Domain-Specific](../modeling/generating-code-from-a-domain-specific-language.md) e Scrittura di codice per personalizzare [un Domain-Specific linguaggio.](../modeling/writing-code-to-customise-a-domain-specific-language.md)

## <a name="customizing-the-dsl"></a>Personalizzazione del linguaggio DSL

Quando si vuole modificare la definizione DSL, chiudere l'istanza sperimentale e aggiornare la definizione nell'istanza Visual Studio principale.

> [!NOTE]
> Dopo aver modificato la definizione DSL, è possibile che si perdano le informazioni nei modelli di test creati con le versioni precedenti.  Ad esempio, la soluzione di debug contiene un file denominato Sample, che contiene alcune forme e connettori. Dopo aver avviato lo sviluppo della definizione DSL, non saranno visibili e andranno perse quando si salva il file.

È possibile creare un'ampia gamma di estensioni al linguaggio DSL. Gli esempi seguenti offrono un'idea delle possibilità.

Dopo ogni modifica, salvare la definizione DSL, fare clic su Trasforma tutti i modelli **in** Esplora soluzioni **e** quindi premere **F5** per sperimentare il DSL modificato.

### <a name="rename-the-types-and-tools"></a>Rinominare i tipi e gli strumenti

Rinominare le classi di dominio e le relazioni esistenti. Ad esempio, a partire da una definizione Dsl creata dal modello Linguaggio minimo, è possibile eseguire le operazioni di ridenominazione seguenti per fare in modo che il linguaggio DSL rappresenti alberi geneasi.

#### <a name="to-rename-domain-classes-relationships-and-tools"></a>Per rinominare classi di dominio, relazioni e strumenti

1. Nel diagramma DslDefinition rinominare **ExampleModel** in **FamilyTreeModel**, **ExampleElement** in **Person**, **Targets** to **Parents** e **Sources** to **Children**. È possibile fare clic su ogni etichetta per modificarla.

     ![Diagramma di definizione DSL &#45; albero genealogico](../modeling/media/familyt_person.png)

2. Rinominare gli strumenti dell'elemento e del connettore.

    1. Aprire la finestra Esplora DSL facendo clic sulla scheda in Esplora soluzioni. Se non è possibile visualizzarlo, scegliere Altre **finestre** **dal** menu Visualizza e quindi fare clic su Esplora **DSL.** Esplora DSL è visibile solo quando il diagramma di definizione DSL è la finestra attiva.

    2. Aprire il Finestra Proprietà e posizionarlo in modo che sia possibile visualizzare DSL Explorer e Proprietà contemporaneamente.

    3. In Esplora DSL espandere **Editor**, **Schede casella degli strumenti**, e quindi *\<your DSL>* **Strumenti**.

    4. Fare **clic su ExampleElement**. Si tratta dell'elemento della casella degli strumenti utilizzato per creare elementi.

    5. Nella finestra Finestra Proprietà modificare la **proprietà Name** in **Person**.

         Si noti che cambia anche la proprietà **Caption.**

    6. Allo stesso modo, modificare il nome dello strumento **ExampleConnector** in **ParentLink**. Modificare la **proprietà Caption** in modo che non sia una copia della proprietà Name. Ad esempio, immettere **Collegamento padre**.

3. Ricompilare il DSL.

    1. Salvare il file di definizione DSL.

    2. Fare **clic su Trasforma tutti i** modelli sulla barra degli strumenti Esplora soluzioni

    3. Premi F5. Attendere che venga visualizzata l'istanza sperimentale di Visual Studio.

4. Nella soluzione Debug nell'istanza sperimentale di Visual Studio aprire un file di modello di test. Trascinare gli elementi nella casella degli strumenti. Si noti che le didascalie degli strumenti e i nomi dei tipi in Esplora DSL sono stati modificati.

5. Salvare il file di modello.

6. Aprire un file con estensione tt e sostituire le occorrenze dei nomi di proprietà e tipo precedente con i nuovi nomi.

7. Assicurarsi che il nome file specificato nel file con estensione tt specifichi il modello di test.

8. Salvare il file con estensione tt. Aprire il file generato per visualizzare il risultato dell'esecuzione del codice nel file con estensione tt. Verificare che sia corretto.

### <a name="add-domain-properties-to-classes"></a>Aggiungere proprietà di dominio alle classi
 Aggiungere proprietà a una classe di dominio, ad esempio per rappresentare gli anni di nascita e di morte di una persona.

 Per rendere visibili le nuove proprietà nel diagramma, è necessario aggiungere *elementi Decorator* alla forma che visualizza l'elemento del modello. È anche necessario eseguire il mapping delle proprietà agli elementi Decorator.

##### <a name="to-add-properties-and-display-them"></a>Per aggiungere proprietà e visualizzarle

1. Aggiungere le proprietà.

   1. Nel diagramma di definizione DSL fare clic con il pulsante destro del mouse sulla classe di dominio **Person,** scegliere **Aggiungi** e quindi fare clic **su Proprietà dominio**.

   2. Digitare un elenco di nuovi nomi di proprietà, ad esempio **Nascita** **e Decesso.** Premere **INVIO** dopo ognuno di essi.

2. Aggiungere elementi Decorator che visualizzano le proprietà nella forma.

   1. Seguire la linea grigia che si estende dalla classe di dominio Person all'altro lato del diagramma. Si tratta di una mappa di elementi del diagramma. Collega la classe di dominio a una classe shape.

   2. Fare clic con il pulsante destro del mouse su questa classe di forma, scegliere **Aggiungi** e quindi fare clic **su Decorator di testo**.

   3. Aggiungere due elementi Decorator con nomi quali **BirthDecorator** e **DeathDecorator**.

   4. Selezionare ogni nuovo elemento Decorator e nella Finestra Proprietà impostare il **campo** Posizione. Questo determina dove verrà visualizzato il valore della proprietà di dominio nella forma. Ad esempio, impostare **InnerBottomLeft** e **InnerBottomRight**.

        ![Definizione della forma Raggruppamento](../modeling/media/familyt_compartment.png)

3. Eseguire il mapping degli elementi Decorator alle proprietà.

   1. Aprire la finestra Dettagli DSL. In genere si trova in una scheda accanto alla finestra Output. Se non è possibile visualizzarlo, scegliere Altre **finestre** dal **menu** Visualizza e quindi fare clic su Dettagli **DSL**.

   2. Nel diagramma di definizione DSL fare clic sulla linea che connette la classe di dominio **Person** alla classe shape.

   3. In **Dettagli DSL** nella scheda **Mappe decorator** fare clic sulla casella di controllo in un elemento Decorator non mappato. In **Proprietà di** visualizzazione selezionare la proprietà di dominio a cui si vuole eseguire il mapping. Ad esempio, eseguire il mapping **di BirthDecorator a** **Birth**.

4. Salvare il file DSL, fare clic su Trasforma tutti i modelli e premere F5.

5. In un diagramma del modello di esempio verificare che sia ora possibile fare clic sulla posizione scelta e digitarvi i valori. Inoltre, quando si seleziona una forma **Persona,** il Finestra Proprietà visualizza le nuove proprietà Birth and Death.

6. In un file con estensione tt è possibile aggiungere codice che ottiene le proprietà di ogni persona.

   ![Diagramma, casella degli strumenti e finestra di esplorazione dell'albero genealogico](../modeling/media/familyt_instance.png)

### <a name="define-new-classes"></a>Definire nuove classi
 È possibile aggiungere classi di dominio e relazioni a un modello. Ad esempio, è possibile creare una nuova classe per rappresentare la città e una nuova relazione per rappresentare una persona che ha una città.

 Per differenziare i diversi tipi in un diagramma del modello, è possibile eseguire il mapping delle classi di dominio a diversi tipi di forma o a forme con geometria e colori diversi.

##### <a name="to-add-and-display-a-new-domain-class"></a>Per aggiungere e visualizzare una nuova classe di dominio

1. Aggiungere una classe di dominio e renderla figlio della radice del modello.

    1. Nel diagramma di definizione DSL fare clic su relazione di incorporamento strumento, fare clic sulla classe radice **FamilyTreeModel** e quindi fare clic in una parte vuota del diagramma. 

         Viene visualizzata una nuova classe di dominio connessa a FamilyTreeModel con una relazione di incorporamento.

         Impostarne il nome, ad esempio **Città**.

        > [!NOTE]
        > Ogni classe di dominio, ad eccezione della radice del modello, deve essere la destinazione di almeno una relazione di incorporamento oppure deve ereditare da una classe che rappresenta la destinazione di un'incorporamento. Per questo motivo, spesso è utile creare una classe di dominio usando lo strumento Relazione di incorporamento.

    2. Aggiungere una proprietà di dominio alla nuova classe, ad esempio **Name**.

2. Aggiungere una relazione di riferimento tra Person e Town.

    1. Fare clic su **Relazione di** riferimento , quindi su Persona e infine su Città.

         ![Frammento della definizione DSL: radice dell'albero genealogico](../modeling/media/familyt_root.png)

        > [!NOTE]
        > Le relazioni di riferimento rappresentano riferimenti incrociati da una parte dell'albero del modello a un'altra.

3. Aggiungere una forma per rappresentare l'elemento nei diagrammi del modello.

    1. Trascinare **una forma Geometry dalla** casella degli strumenti al diagramma e rinominarla, ad esempio **TownShape**.

    2. Nella finestra Finestra Proprietà impostare i campi Aspetto della nuova forma, ad esempio Colore riempimento e Geometria.

    3. Aggiungere un elemento Decorator per visualizzare il nome della città e rinominarlo NameDecorator. Impostarne la proprietà Position.

4. Eseguire il mapping della classe di dominio Town a TownShape.

    1. Fare clic **su Diagram Element Map** , quindi sulla classe di dominio Town e infine sulla classe di forma TownShape.

    2. Nella scheda **Mappe decorator** della finestra **Dettagli DSL** con il connettore mappa selezionato selezionare NameDecorator e impostare **Proprietà di visualizzazione** su Nome.

5. Creare un connettore per visualizzare la relazione tra Person e Person.

    1. Trascinare un connettore dalla casella degli strumenti al diagramma. Rinominarlo e impostarne le proprietà di aspetto.

    2. Usare lo **strumento Mappa elementi** diagramma per collegare il nuovo connettore alla relazione tra Person e Town.

         ![Definizione dell'albero genealogico con mappa di forme aggiunte](../modeling/media/familyt_shapemap.png)

6. Creare uno strumento elemento per creare una nuova città.

    1. In **Esplora DSL espandere** **Editor** e quindi Schede casella **degli strumenti**.

    2. Fare clic con il pulsante *\<your DSL>* destro del mouse e quindi scegliere Aggiungi nuovo elemento **.**

    3. Impostare la **proprietà Name** del nuovo strumento e la relativa **proprietà Class** su Town.

    4. Impostare la proprietà **Icona casella degli** strumenti. Fare **clic su [...]** e nel campo Nome **file** selezionare un file di icona.

7. Creare uno strumento connettore per creare un collegamento tra persone e persone.

    1. Fare clic con il pulsante *\<your DSL>* destro del mouse su e quindi scegliere Aggiungi nuovo strumento **connettore**.

    2. Impostare la proprietà Name del nuovo strumento.

    3. Nella proprietà **ConnectionBuilder** selezionare il generatore che contiene il nome della relazione Person-Town connessione.

    4. Impostare **l'icona della casella degli strumenti**.

8. Salvare la definizione DSL, fare **clic su Trasforma tutti i** modelli e quindi premere **F5.**

9. Nell'istanza sperimentale di Visual Studio aprire un file di modello di test. Usare i nuovi strumenti per creare collegamenti e collegamenti tra persone e persone. Si noti che è possibile creare collegamenti solo tra i tipi corretti di elemento.

10. Creare il codice che elenca la città in cui risiede ogni persona. I modelli di testo sono una delle posizioni in cui è possibile eseguire tale codice. Ad esempio, è possibile modificare il file Sample.tt esistente nella soluzione debug in modo che contenga il codice seguente:

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

     Quando si salva il file *.tt, verrà creato un file affiliato che contiene l'elenco delle persone e delle rispettive persone. Per altre informazioni, vedere [Generating Code from a Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

## <a name="validation-and-commands"></a>Convalida e comandi
 È possibile sviluppare ulteriormente questo DSL aggiungendo vincoli di convalida. Questi vincoli sono metodi che è possibile definire, che assicurano che il modello sia in uno stato corretto. Ad esempio, è possibile definire un vincolo per assicurarsi che la data di nascita di un figlio sia successiva a quella dei suoi genitori. La funzionalità di convalida visualizza un avviso se l'utente DSL tenta di salvare un modello che interrompe uno dei vincoli. Per altre informazioni, vedere [Validation in a Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).

 È anche possibile definire comandi di menu che l'utente può richiamare. I comandi possono modificare il modello. Possono anche interagire con altri modelli in Visual Studio e con risorse esterne. Per altre informazioni, vedere [Procedura: Modificare un comando di menu standard.](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)

## <a name="deploying-the-dsl"></a>Distribuzione del DSL
 Per consentire ad altri utenti di usare il linguaggio specifico di dominio, si distribuisce un file vsix (Visual Studio Extension). Viene creato quando si compila la soluzione DSL.

 Individuare il file con estensione vsix nella cartella bin della soluzione. Copiarlo nel computer in cui si vuole installarlo. Nel computer fare doppio clic sul file VSIX. Il DSL può essere usato in tutte le istanze Visual Studio nel computer.

 È possibile usare la stessa procedura per installare il DSL nel proprio computer in modo che non sia necessario usare l'istanza sperimentale di Visual Studio.

 Per altre informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](msi-and-vsix-deployment-of-a-dsl.md).

## <a name="removing-old-experimental-dsls"></a><a name="Reset"></a> Rimozione di DSL sperimentali
 Se sono stati creati DSL sperimentali che non si desidera più, è possibile rimuoverli dal computer reimpostando l'istanza Visual Studio sperimentale.

 Questo rimuoverà dal computer tutti i DSL sperimentali e altre estensioni Visual Studio sperimentali. Si tratta di estensioni eseguite in modalità di debug.

 Questa procedura non rimuove le DSL o altre estensioni Visual Studio installate completamente eseguendo il file VSIX.

#### <a name="to-reset-the-visual-studio-experimental-instance"></a>Per reimpostare l'Visual Studio sperimentale

1. Fare clic  **sul pulsante Start**, scegliere Tutti i programmi Microsoft Visual Studio **SDK 2010** **,** Strumenti e quindi reimpostare **l'istanza sperimentale di Microsoft Visual Studio 2010**.

2. Ricompilare eventuali DSL sperimentali o altre estensioni Visual Studio sperimentali che si vuole ancora usare.

## <a name="see-also"></a>Vedere anche

- [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md)
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
