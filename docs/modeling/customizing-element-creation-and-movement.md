---
title: Personalizzazione della creazione e dello spostamento di elementi
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b4b2f57485a942877861400aec9ec7d0f13f977
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55957611"
---
# <a name="customizing-element-creation-and-movement"></a>Personalizzazione della creazione e dello spostamento di elementi

È possibile consentire a un elemento è possibile trascinare un altro, dalla casella degli strumenti o in un incollare o spostare l'operazione. È possibile avere gli elementi spostati collegati agli elementi di destinazione, usando le relazioni che si specificano.

Una direttiva di unione elementi (EMD) specifica che cosa avviene quando un elemento del modello è *unito* in un altro elemento del modello. Ciò si verifica quando:

- L'utente trascina dalla casella degli strumenti in una forma o diagramma.

- L'utente crea un elemento con un menu Aggiungi nella finestra di esplorazione o di una forma raggruppamento.

- L'utente sposta un elemento da una corsia a un'altra.

- L'utente incolla un elemento.

- Il codice del programma chiama la direttiva di unione elementi.

Anche se le operazioni di creazione potrebbero sembrare può essere diverso dalle operazioni di copia, effettivamente funzionano nello stesso modo. Quando viene aggiunto un elemento, ad esempio dalla casella degli strumenti, un prototipo di esso verrà replicato. Il prototipo è unito al modello allo stesso modo come elementi che sono stati copiati da un'altra parte del modello.

La responsabilità di una EMD consiste nel decidere come un oggetto o gruppo di oggetti deve essere unita in una determinata posizione nel modello. In particolare, decide quali relazioni dovrebbero essere istanziati per collegare il gruppo unito nel modello. È anche possibile personalizzare per impostare le proprietà e per creare altri oggetti.

![DSL&#45;EMD&#95;Merge](../modeling/media/dsl-emd_merge.png)

Una EMD viene generata automaticamente quando si definisce una relazione di incorporamento. Questa impostazione predefinita EMD crea un'istanza della relazione quando gli utenti aggiungono nuove istanze figlio al padre. È possibile modificare questi EMDs predefinito, ad esempio aggiungendo codice personalizzato.

È anche possibile aggiungere il proprio EMDs nella definizione DSL, per consentire agli utenti di trascinare o incollare diverse combinazioni di classi unite e quello destinatario.

## <a name="defining-an-element-merge-directive"></a>La definizione di una direttiva di unione elementi

È possibile aggiungere direttive di merge per le classi di dominio, relazioni di dominio, forme, connettori e i diagrammi. È possibile aggiungere o individuarli in Esplora DSL sotto la classe di dominio ricevente. La classe ricevente è la classe di dominio dell'elemento che si trova già nel modello e a cui verrà unito l'elemento nuovo o copiato.

![DSL&#45;EMD&#95;Details](../modeling/media/dsl-emd_details.png)

Il **classe di indicizzazione** è la classe di dominio di elementi che possono essere uniti in membri della classe ricevente. Le istanze di sottoclassi della classe di indicizzazione verranno unite anche da questo EMD, a meno che non si imposta **si applica alle sottoclassi** su False.

Esistono due tipi di direttiva di unione:

- Oggetto **processo di Merge** direttiva specifica le relazioni mediante il quale il nuovo elemento deve essere collegato all'albero.

- Oggetto **inoltrare Merge** direttiva reindirizza il nuovo elemento a un altro elemento ricevente, in genere un elemento padre.

È possibile aggiungere codice personalizzato per le direttive di merge:

- Impostare **accettazione personalizzata Usa** per aggiungere codice personalizzato per determinare se una particolare istanza dell'elemento indicizzazione deve essere unita nell'elemento di destinazione. Quando l'utente trascina dalla casella degli strumenti, il puntatore "invalid" Mostra se il codice non consente l'unione.

   Ad esempio, è possibile consentire l'unione solo quando l'elemento ricevente è in uno stato specifico.

- Impostare **merge personalizzato utilizza** aggiungere fornire proprio codice per definire le modifiche apportate al modello quando viene eseguito il merge.

   Ad esempio, è possibile impostare le proprietà nell'elemento unito utilizzando i dati dalla nuova posizione nel modello.

> [!NOTE]
> Se si scrive codice personalizzato di tipo merge, soli operazioni di merge che vengono eseguite tramite questo EMD influisce su. Se sono presenti altri EMDs che lo stesso tipo di oggetto di tipo merge, o se è presente altro codice personalizzato che crea questi oggetti senza usare il EMD, quindi queste verranno non interessate dal codice personalizzato di tipo merge.
>
> Se si desidera assicurarsi che un nuovo elemento o una nuova relazione viene sempre elaborato dal codice personalizzato, si consiglia di definire un `AddRule` nella relazione di incorporamento e un `DeleteRule` nella classe di dominio dell'elemento. Per altre informazioni, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Esempio: La definizione di una EMD senza scrivere codice personalizzato

Nell'esempio seguente consente agli utenti di creare un elemento e un connettore nello stesso momento mediante il trascinamento dalla casella degli strumenti in una forma esistente. L'esempio aggiunge una EMD alla definizione DSL. Prima di questa modifica, gli utenti potranno trascinare gli strumenti nel diagramma, ma non in forme esistenti.

Gli utenti possono anche incollare gli elementi su altri elementi.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Per consentire agli utenti di creare un elemento e un connettore nello stesso momento

1. Creare un nuovo linguaggio specifico di dominio usando il **linguaggio minimo** modello di soluzione.

    Quando si esegue questo linguaggio DSL, è possibile creare forme e connettori tra le forme. Non è possibile trascinare una nuova **ExampleElement** forma dalla casella degli strumenti in una forma esistente.

2. Per consentire agli utenti di unire elementi nel `ExampleElement` forme, creare un nuovo EMD nel `ExampleElement` della classe di dominio:

   1.  Nelle **DSL Explorer**, espandere **classi di dominio**. Fare doppio clic su `ExampleElement` e quindi fare clic su **Aggiungi nuova direttiva di unione**.

   2.  Assicurarsi che il **dettagli DSL** finestra è aperta, in modo che è possibile visualizzare i dettagli di EMD di nuovo. (Menu: **Consente di visualizzare**, **altri Windows**, **dettagli DSL**.)

3. Impostare il **classe di indicizzazione** nella finestra Dettagli DSL per definire la classe di elementi può essere unita nel `ExampleElement` oggetti.

    In questo esempio selezionare `ExampleElements`, in modo che l'utente può trascinare elementi nuovi in elementi esistenti.

    Si noti che la classe di indicizzazione diventa il nome del EMD in DSL Explorer.

4. Sotto **elabora l'unione creando collegamenti**, aggiungere due percorsi:

   - Un percorso collega il nuovo elemento al modello padre. L'espressione di percorso che è necessario immettere consente di passare dall'elemento esistente, backup tramite la relazione di incorporamento per il modello padre. Infine, specifica il ruolo nel nuovo collegamento a cui verrà assegnato il nuovo elemento. Il percorso è come segue:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - L'altro percorso collega il nuovo elemento all'elemento esistente. L'espressione di percorso Specifica la relazione di riferimento e il ruolo a cui verrà assegnato il nuovo elemento. Questo percorso è il seguente:

      `ExampleElementReferencesTargets.Sources`

      È possibile utilizzare lo strumento di navigazione del percorso per creare ciascun percorso:

      1. Sotto **elabora l'unione creando collegamenti nei percorsi**, fare clic su  **\<aggiungere percorso >**.

      2. Fare clic sulla freccia giù a destra dell'elemento dell'elenco. Verrà visualizzata una visualizzazione albero.

      3. Espandere i nodi dell'albero per formare il percorso che si desidera specificare.

5. Testare il linguaggio DSL:

   1.  Premere **F5** per ricompilare ed eseguire la soluzione.

        La ricompilazione richiede più tempo superiore al normale perché il codice generato verrà aggiornato da modelli di testo per essere conforme alla nuova definizione DSL.

   2.  Quando ha avviato l'istanza sperimentale di Visual Studio, aprire un file di modello del linguaggio DSL. Creare alcuni elementi di esempio.

   3.  Trascinare il **elemento esempio** dello strumento in una forma esistente.

        Verrà visualizzata una nuova forma e collegarla alla forma esistente con un connettore.

   4.  Copiare una forma esistente. Selezionare un'altra forma e incollare.

        Viene creata una copia della prima forma.  Dispone di un nuovo nome ed è collegato alla seconda forma con un connettore.

Notare gli aspetti seguenti da questa procedura:

-   Tramite la creazione di direttive di unione, è possibile consentire qualsiasi classe di elemento per accettare qualsiasi altro. Il EMD viene creato nella classe del ricevente dominio e la classe di dominio accettato è specificata nel **classe Index** campo.

-   Definendo i percorsi, è possibile specificare quali collegamenti devono essere usato per connettersi al nuovo elemento al modello esistente.

     I collegamenti che specificano devono includere una relazione di incorporamento.

-   Il EMD influisce sia creazione dalla casella degli strumenti e anche le operazioni Incolla.

     Se si scrive codice personalizzato che crea nuovi elementi, è possibile richiamare in modo esplicito il EMD utilizzando il `ElementOperations.Merge` (metodo). Ciò assicura che il codice di collegamenti nuovi elementi nel modello in esattamente come altre operazioni. Per altre informazioni, vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Esempio: Aggiunta di codice di accettazione personalizzata a una EMD

Aggiungendo codice personalizzato a una EMD, è possibile definire il comportamento di unione più complessa. Questo semplice esempio impedisce all'utente di aggiungere più di un numero fisso di elementi nel diagramma. Nell'esempio viene modificato il valore predefinito EMD che accompagna una relazione di incorporamento.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Scrivere il codice di accettazione personalizzata per limitare gli elementi che è possibile aggiungere l'utente

1.  Creare un linguaggio DSL utilizzando il **linguaggio minimo** modello di soluzione. Aprire il diagramma di definizione DSL.

2.  In DSL Explorer, espandere **classi di dominio**, `ExampleModel`, **direttive di unione**. Selezionare la direttiva di unione elementi denominato `ExampleElement`.

     Questo EMD controlla la modalità con cui l'utente può creare nuovi `ExampleElement` gli oggetti del modello, ad esempio mediante il trascinamento dalla casella degli strumenti.

3.  Nel **dettagli DSL** finestra, seleziona **accettazione personalizzata Usa**.

4.  Ricompilare la soluzione. Questa operazione richiederà più tempo del solito poiché verrà aggiornato il codice generato dal modello.

     Un errore di compilazione verranno segnalate, simile a: "Company.ElementMergeSample.ExampleElement non contiene una definizione per CanMergeExampleElement..."

     È necessario implementare il metodo `CanMergeExampleElement`.

5.  Creare un nuovo file di codice nel **Dsl** progetto. Sostituirne il contenuto con il codice seguente e modificare lo spazio dei nomi per lo spazio dei nomi del progetto.

    ```csharp
    using Microsoft.VisualStudio.Modeling;

    namespace Company.ElementMergeSample // EDIT.
    {
      partial class ExampleModel
      {
        /// <summary>
        /// Called whenever an ExampleElement is to be merged into this ExampleModel.
        /// This happens when the user pastes an ExampleElement
        /// or drags from the toolbox.
        /// Determines whether the merge is allowed.
        /// </summary>
        /// <param name="rootElement">The root element in the merging EGP.</param>
        /// <param name="elementGroupPrototype">The EGP that the user wants to merge.</param>
        /// <returns>True if the merge is allowed</returns>
        private bool CanMergeExampleElement(ProtoElementBase rootElement, ElementGroupPrototype elementGroupPrototype)
        {
          // Allow no more than 4 elements to be added:
          return this.Elements.Count < 4;
        }
      }
    }
    ```

    Questo semplice esempio limita il numero di elementi che possono essere uniti nel modello padre. Per le condizioni più interessante, il metodo può esaminare le proprietà e i collegamenti dell'oggetto di destinazione. Anche possibile esaminare le proprietà degli elementi di unione, che vengono eseguiti in un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype>. Per altre informazioni sulle `ElementGroupPrototypes`, vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md). Per altre informazioni su come scrivere codice che legge un modello, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

6.  Testare il linguaggio DSL:

    1.  Premere **F5** per ricompilare la soluzione. Quando si apre l'istanza sperimentale di Visual Studio, aprire un'istanza del linguaggio DSL.

    2.  Creare nuovi elementi in diversi modi:

        - Trascinare dal **elemento esempio** strumento nel diagramma.

        - Nel **Esplora modelli di esempio**, fare clic sul nodo radice e quindi fare clic su **Aggiungi nuovo elemento di esempio**.

        - Copiare e incollare un elemento nel diagramma.

    3.  Verificare che non è possibile utilizzare uno dei modi seguenti per aggiungere più di quattro elementi nel modello. Questo avviene perché usano la direttiva di unione.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Esempio: Aggiunta di codice personalizzato di tipo Merge per una EMD

Nel codice personalizzato di tipo merge, è possibile definire cosa accade quando l'utente trascina uno strumento o Incolla su un elemento. Esistono due modi per definire un'unione nell'indice personalizzato:

1. Impostare **viene utilizzato Merge personalizzato** e fornire il codice richiesto. Il codice sostituisce il codice generato di tipo merge. Usare questa opzione se si desidera ridefinire completamente il funzionamento dell'unione.

2. Eseguire l'override di `MergeRelate` metodo e, facoltativamente, il `MergeDisconnect` (metodo). A tale scopo, è necessario impostare il **genera una derivata doppia** proprietà della classe di dominio. Il codice può chiamare il codice generato merge nella classe di base. Usare questa opzione se si desidera eseguire operazioni aggiuntive dopo aver eseguito il merge.

   Questi approcci influiscono solo sui processi di merge che vengono eseguite tramite questo EMD. Se si desidera influiscono su tutti i modi in cui è possibile creare l'elemento unito, un'alternativa consiste nel definire un `AddRule` nella relazione di incorporamento e un `DeleteRule` nella classe di dominio unito. Per altre informazioni, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Per eseguire l'override MergeRelate

1.  Nella definizione DSL, assicurarsi che sia stata definita la EMD a cui si desidera aggiungere il codice. Se si desidera, è possibile aggiungere i percorsi e definire accettazione di codice personalizzata come descritto nelle sezioni precedenti.

2.  Nel diagramma DslDefinition, selezionare la classe ricevente dell'unione. In genere si tratta della classe alla fine dell'origine di una relazione di incorporamento.

     Ad esempio, in un DSL generato dalla soluzione di linguaggio minimo, selezionare `ExampleModel`.

3.  Nel **delle proprietà** impostare nella finestra **genera una derivata doppia** al **true**.

4.  Ricompilare la soluzione.

5.  Esaminare il contenuto del **Dsl\Generated Files\DomainClasses.cs**. Ricerca di metodi denominati `MergeRelate` ed esaminare il relativo contenuto. Ciò consentirà di scrivere le versioni personalizzate.

6.  In un nuovo file di codice, scrivere una classe parziale per la classe ricevente ed eseguire l'override di `MergeRelate` (metodo). Ricordare di chiamare il metodo di base. Ad esempio:

    ```csharp
    partial class ExampleModel
    {
      /// <summary>
      /// Called when the user drags or pastes an ExampleElement onto the diagram.
      /// Sets the time of day as the name.
      /// </summary>
      /// <param name="sourceElement">Element to be added</param>
      /// <param name="elementGroup">Elements to be merged</param>
      protected override void MergeRelate(ModelElement sourceElement, ElementGroup elementGroup)
      {
        // Connect the element according to the EMD:
        base.MergeRelate(sourceElement, elementGroup);

        // Custom actions:
        ExampleElement mergingElement = sourceElement as ExampleElement;
        if (mergingElement != null)
        {
          mergingElement.Name = DateTime.Now.ToLongTimeString();
        }
      }
    }
    ```

### <a name="to-write-custom-merge-code"></a>Scrivere codice personalizzato di tipo Merge

1. Nelle **Dsl\Generated Code\DomainClasses.cs**, esaminare i metodi denominati `MergeRelate`. Questi metodi creano collegamenti tra un nuovo elemento e il modello esistente.

    Inoltre, esaminare i metodi denominati `MergeDisconnect`. Questi metodi scollega un elemento dal modello in questo caso da eliminare.

2. Nelle **DSL Explorer**selezionare o creare la direttiva di unione elementi che si desidera personalizzare. Nel **dettagli DSL** impostare nella finestra **utilizza personalizzato di tipo Merge**.

    Quando si imposta questa opzione, il **processo di Merge** e **inoltrare Merge** opzioni vengono ignorate. Viene usato il codice.

3. Ricompilare la soluzione. Richiederà più tempo del solito poiché verranno aggiornati i file di codice generati dal modello.

    Verranno visualizzati messaggi di errore. Fare doppio clic sui messaggi di errore per vedere le istruzioni nel codice generato. È possibile fornire due metodi, chiedere a queste istruzioni `MergeRelate` *YourDomainClass* e `MergeDisconnect` *YourDomainClass*

4. Scrivere i metodi in una definizione di classe parziale in un file di codice separato. Gli esempi che esaminato in precedenza dovrebbero suggerire ciò che è necessario.

   Codice personalizzato di tipo merge non influirà sul codice che crea oggetti e relazioni direttamente e non influirà su altre EMDs. Per assicurarsi che le modifiche aggiuntive vengono implementate indipendentemente dal modo in cui viene creato l'elemento, è consigliabile scrivere un `AddRule` e un `DeleteRule` invece. Per altre informazioni, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Reindirizzamento di un'operazione di unione

Una direttiva di unione in avanti reindirizza la destinazione di un'operazione di unione. In genere, la nuova destinazione è l'oggetto padre di incorporamento della destinazione iniziale.

In un linguaggio DSL creata con il modello di diagramma componente, ad esempio, le porte sono incorporate nei componenti. Le porte vengono visualizzate come piccole forme sul bordo di una forma di componente. L'utente crea porte trascinando sullo strumento della porta in una forma di componente. Ma in alcuni casi, l'utente trascina erroneamente sullo strumento della porta su una porta esistente, anziché il componente e l'operazione ha esito negativo. Si tratta di un errore comune quando sono presenti numerose porte esistenti. Per consentire all'utente per evitare questa difficoltà, è possibile consentire le porte essere trascinati da una porta esistente, ma l'azione reindirizzato al componente padre. L'operazione funziona come se l'elemento di destinazione fosse il componente.

È possibile creare una direttiva di unione in avanti nella soluzione di modello del componente. Se compilare ed eseguire la soluzione originale, si noterà che gli utenti potranno trascinare un numero qualsiasi di **porta di Input** o **porta di Output** elementi dal **della casella degli strumenti** a un **Componente** elemento. Tuttavia, questi non potranno trascinare una porta a una porta esistente. Il puntatore del mouse non disponibile avvisa loro che questo passaggio non è abilitato. Tuttavia, è possibile creare una direttiva di unione in avanti, in modo che una porta che viene accidentalmente eliminato in un oggetto esistente **porta di Input** viene inoltrato al **componente** elemento.

### <a name="to-create-a-forward-merge-directive"></a>Per creare una direttiva di unione in avanti

1. Creare un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello di modello del componente.

2. Visualizzare il **DSL Explorer** , aprire Dsldefinition.

3. Nel **DSL Explorer**, espandere **classi di dominio**.

4. Il **ComponentPort** della classe di dominio astratta è la classe di base di entrambe **InPort** e **OutPort**. Fare doppio clic su **ComponentPort** e quindi fare clic su **aggiungere nuova direttiva di unione**.

    Una nuova **direttiva di unione** nodo viene visualizzato sotto il **direttive di unione** nodo.

5. Selezionare il **direttiva di unione** nodo e aprire il **dettagli DSL** finestra.

6. Nell'elenco delle classi di indicizzazione, selezionare **ComponentPort**.

7. Selezionare **inoltra il merge a una classe di dominio diverso**.

8. Nell'elenco di selezione dei percorsi, espandere **ComponentPort**, espandere **ComponentHasPorts**, quindi selezionare **componente**.

    Il nuovo percorso dovrebbe essere simile a questo:

    **ComponentHasPorts.Component/!Component**

9. Salvare la soluzione e quindi trasformare i modelli facendo clic sul pulsante all'estrema destra sul **Esplora soluzioni** sulla barra degli strumenti.

10. Compilare ed eseguire la soluzione. Verrà visualizzata una nuova istanza di Visual Studio.

11. Nelle **Esplora soluzioni**, aprire Sample.mydsl. Il diagramma e il **casella degli strumenti ComponentLanguage** vengono visualizzati.

12. Trascinare un' **porta di Input** dalle **della casella degli strumenti** a un altro **porta di Input.** Procedere quindi trascinando un' **OutputPort** a un **InputPort** e quindi a un'altra **OutputPort**.

     Non dovrebbe essere visualizzato il puntatore del mouse non disponibile, e dovrebbe essere in grado di rilasciare il nuovo **porta di Input** su quella esistente. Selezionare nuovo **porta di Input** e trascinarlo su un altro punto **componente**.

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Personalizzazione di strumenti e della casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md)
- [Esempio di diagrammi circuito DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)