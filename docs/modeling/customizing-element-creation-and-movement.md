---
title: Personalizzazione della creazione e dello spostamento di elementi
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a94f1e3321d846578ea42c69e50d48713ff618fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547264"
---
# <a name="customizing-element-creation-and-movement"></a>Personalizzazione della creazione e dello spostamento di elementi

È possibile consentire il trascinamento di un elemento su un altro, dalla casella degli strumenti o in un'operazione di Incolla o spostamento. È possibile fare in modo che gli elementi spostati siano collegati agli elementi di destinazione usando le relazioni specificate.

Una direttiva di Unione elementi (EMD) specifica cosa accade quando un elemento del modello viene *Unito* a un altro elemento del modello. Ciò si verifica quando:

- L'utente trascina dalla casella degli strumenti sul diagramma o su una forma.

- L'utente crea un elemento utilizzando un menu Aggiungi nella forma di esplorazione o di raggruppamento.

- L'utente sposta un elemento da una corsia a un'altra.

- L'utente incolla un elemento.

- Il codice del programma chiama la direttiva di Unione degli elementi.

Sebbene le operazioni di creazione possano sembrare diverse dalle operazioni di copia, funzionano esattamente allo stesso modo. Quando viene aggiunto un elemento, ad esempio dalla casella degli strumenti, viene replicato un prototipo di tale elemento. Il prototipo viene unito al modello in modo analogo agli elementi copiati da un'altra parte del modello.

La responsabilità di un EMD consiste nel decidere come un oggetto o un gruppo di oggetti deve essere unito in una determinata posizione nel modello. In particolare, decide le relazioni di cui deve essere creata un'istanza per collegare il gruppo unito al modello. È anche possibile personalizzarlo per impostare le proprietà e creare oggetti aggiuntivi.

![DSL&#45;EMD&#95;merge](../modeling/media/dsl-emd_merge.png)

Un EMD viene generato automaticamente quando si definisce una relazione di incorporamento. Questo EMD predefinito crea un'istanza della relazione quando gli utenti aggiungono nuove istanze figlio all'elemento padre. È possibile modificare questi EMDs predefiniti, ad esempio aggiungendo codice personalizzato.

È anche possibile aggiungere EMDs personalizzati nella definizione DSL, per consentire agli utenti di trascinare o incollare diverse combinazioni di classi sottoposte a merge e ricezione.

## <a name="defining-an-element-merge-directive"></a>Definizione di una direttiva di Unione elementi

È possibile aggiungere direttive di Unione elementi a classi di dominio, relazioni di dominio, forme, connettori e diagrammi. È possibile aggiungerli o trovarli in DSL Explorer sotto la classe di dominio ricevente. La classe ricevente è la classe di dominio dell'elemento già presente nel modello e su cui verrà eseguito il merge dell'elemento nuovo o copiato.

![DSL&#45;EMD&#95;dettagli](../modeling/media/dsl-emd_details.png)

La **classe di indicizzazione** è la classe di dominio di elementi che possono essere Uniti in membri della classe ricevente. Anche le istanze delle sottoclassi della classe di indicizzazione verranno unite da questo EMD, a meno che non si imposti le **sottoclassi** su false.

Esistono due tipi di direttiva di Unione:

- Una direttiva di **Unione processi** specifica le relazioni in base alle quali il nuovo elemento deve essere collegato nell'albero.

- Una direttiva di **Unione** diretta reindirizza il nuovo elemento a un altro elemento ricevente, in genere un elemento padre.

È possibile aggiungere codice personalizzato alle direttive di Unione:

- Set **Usa l'istruzione Accept personalizzata** per aggiungere codice personalizzato per determinare se un'istanza specifica dell'elemento di indicizzazione deve essere unita nell'elemento di destinazione. Quando l'utente trascina dalla casella degli strumenti, il puntatore "non valido" indica se il codice non consente il merge.

   Ad esempio, è possibile consentire l'Unione solo quando l'elemento ricevente si trova in un determinato stato.

- Set **Usa l'Unione personalizzata** per aggiungere il codice fornito per definire le modifiche apportate al modello quando viene eseguita l'Unione.

   Ad esempio, è possibile impostare le proprietà nell'elemento Unito utilizzando i dati della nuova posizione nel modello.

> [!NOTE]
> Se si scrive codice di merge personalizzato, influiscono solo sulle unioni eseguite utilizzando questo EMD. Se sono presenti altri EMDs che uniscono lo stesso tipo di oggetto o se è presente altro codice personalizzato che crea questi oggetti senza usare EMD, non saranno interessati dal codice di merge personalizzato.
>
> Per assicurarsi che un nuovo elemento o una nuova relazione venga sempre elaborata dal codice personalizzato, valutare la possibilità di definire un oggetto `AddRule` nella relazione di incorporamento e un oggetto `DeleteRule` sulla classe di dominio dell'elemento. Per ulteriori informazioni, vedere la pagina relativa alla [propagazione delle modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="example-defining-an-emd-without-custom-code"></a>Esempio: definizione di un EMD senza codice personalizzato

L'esempio seguente consente agli utenti di creare contemporaneamente un elemento e un connettore trascinando dalla casella degli strumenti su una forma esistente. Nell'esempio viene aggiunto un EMD alla definizione DSL. Prima di questa modifica, gli utenti possono trascinare gli strumenti sul diagramma, ma non sulle forme esistenti.

Gli utenti possono anche incollare elementi su altri elementi.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Per consentire agli utenti di creare un elemento e un connettore nello stesso momento

1. Creare un nuovo linguaggio DSL usando il modello di soluzione per il **linguaggio minimo** .

    Quando si esegue questo linguaggio DSL, è possibile creare forme e connettori tra le forme. Non è possibile trascinare una nuova forma **ExampleElement** dalla casella degli strumenti su una forma esistente.

2. Per consentire agli utenti di unire elementi sulle `ExampleElement` forme, creare un nuovo EMD nella `ExampleElement` classe di dominio:

   1. In **DSL Explorer**espandere **classi di dominio**. Fare clic con il pulsante destro del mouse `ExampleElement` e scegliere **Aggiungi nuova direttiva di Unione elementi**.

   2. Assicurarsi che la finestra **Dettagli DSL** sia aperta, in modo che sia possibile visualizzare i dettagli del nuovo EMD. (Menu: **Visualizza**, **altre finestre**, **Dettagli DSL**).

3. Impostare la **classe di indicizzazione** nella finestra Dettagli DSL per definire la classe di elementi di cui è possibile eseguire il merge sugli `ExampleElement` oggetti.

    Per questo esempio, selezionare `ExampleElements` , in modo che l'utente possa trascinare nuovi elementi su elementi esistenti.

    Si noti che la classe di indicizzazione diventa il nome del EMD in DSL Explorer.

4. In **processo Unione mediante creazione di collegamenti**aggiungere due percorsi:

   - Un percorso collega il nuovo elemento al modello padre. L'espressione di percorso che è necessario immettere consente di spostarsi dall'elemento esistente, fino alla relazione di incorporamento con il modello padre. Infine, specifica il ruolo nel nuovo collegamento a cui verrà assegnato il nuovo elemento. Il percorso è il seguente:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - L'altro percorso collega il nuovo elemento all'elemento esistente. L'espressione di percorso specifica la relazione di riferimento e il ruolo a cui verrà assegnato il nuovo elemento. Questo percorso è il seguente:

      `ExampleElementReferencesTargets.Sources`

      È possibile utilizzare lo strumento di navigazione percorso per creare ogni percorso:

      1. In **processo Unione creando collegamenti nei percorsi**fare clic su **\<add path>** .

      2. Fare clic sulla freccia a discesa a destra della voce dell'elenco. Viene visualizzata una visualizzazione struttura ad albero.

      3. Espandere i nodi nella struttura ad albero per creare il percorso che si desidera specificare.

5. Testare il linguaggio DSL:

   1. Premere **F5** per ricompilare ed eseguire la soluzione.

        La ricompilazione importerà più tempo del solito perché il codice generato verrà aggiornato dai modelli di testo per conformarsi alla nuova definizione DSL.

   2. Quando l'istanza sperimentale di Visual Studio è stata avviata, aprire un file di modello del linguaggio DSL. Creare alcuni elementi di esempio.

   3. Trascinare dallo strumento **elemento di esempio** su una forma esistente.

        Viene visualizzata una nuova forma, che è collegata alla forma esistente con un connettore.

   4. Copiare una forma esistente. Selezionare un'altra forma e incollare.

        Viene creata una copia della prima forma.  Ha un nuovo nome e viene collegato alla seconda forma con un connettore.

Si notino i seguenti punti di questa procedura:

- Grazie alla creazione di direttive di Unione elementi, è possibile consentire a qualsiasi classe di elemento di accettare qualsiasi altra classe. EMD viene creato nella classe di dominio ricevente e la classe di dominio accettata viene specificata nel campo della **classe index** .

- Definendo i percorsi, è possibile specificare i collegamenti da utilizzare per connettere il nuovo elemento al modello esistente.

     I collegamenti specificati devono includere una relazione di incorporamento.

- EMD influiscono sia sulla creazione dalla casella degli strumenti, sia sulle operazioni Incolla.

     Se si scrive codice personalizzato per la creazione di nuovi elementi, è possibile richiamare in modo esplicito EMD usando il `ElementOperations.Merge` metodo. Ciò garantisce che il codice colleghi i nuovi elementi al modello in modo analogo alle altre operazioni. Per ulteriori informazioni, vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Esempio: aggiunta di codice Accept personalizzato a un EMD

Aggiungendo codice personalizzato a un EMD, è possibile definire un comportamento di merge più complesso. Questo semplice esempio impedisce all'utente di aggiungere al diagramma più di un numero fisso di elementi. Nell'esempio viene modificato il valore predefinito di EMD che accompagna una relazione di incorporamento.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Per scrivere codice Accept personalizzato per limitare le operazioni che l'utente può aggiungere

1. Creare un linguaggio DSL usando il modello di soluzione per la **lingua minima** . Aprire il diagramma di definizione DSL.

2. In DSL Explorer espandere **classi di dominio**, `ExampleModel` , **direttive di Unione elementi**. Selezionare la direttiva di Unione elementi denominata `ExampleElement` .

     Questo EMD controlla il modo in cui l'utente può creare nuovi `ExampleElement` oggetti nel modello, ad esempio trascinando dalla casella degli strumenti.

3. Nella finestra **Dettagli DSL** selezionare **USA Accept personalizzato**.

4. Ricompilare la soluzione. Questa operazione importerà più tempo del solito perché il codice generato verrà aggiornato dal modello.

     Verrà restituito un errore di compilazione simile a: "Company. ElementMergeSample. ExampleElement non contiene una definizione per CanMergeExampleElement..."

     È necessario implementare il metodo `CanMergeExampleElement` .

5. Creare un nuovo file di codice nel progetto **DSL** . Sostituire il contenuto con il codice seguente e impostare lo spazio dei nomi sullo spazio dei nomi del progetto.

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

    In questo semplice esempio viene limitato il numero di elementi che possono essere Uniti nel modello padre. Per condizioni più interessanti, il metodo può ispezionare qualsiasi proprietà e collegamento dell'oggetto ricevente. Può inoltre esaminare le proprietà degli elementi di Unione, che vengono trasportati in un oggetto <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> . Per ulteriori informazioni su `ElementGroupPrototypes` , vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md). Per ulteriori informazioni su come scrivere codice per la lettura di un modello, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

6. Testare il linguaggio DSL:

    1. Premere **F5** per ricompilare la soluzione. Quando si apre l'istanza sperimentale di Visual Studio, aprire un'istanza del linguaggio DSL.

    2. Creare nuovi elementi in diversi modi:

        - Trascinare dallo strumento **elemento di esempio** nel diagramma.

        - In **Esplora modelli di esempio**, fare clic con il pulsante destro del mouse sul nodo radice e quindi scegliere **Aggiungi nuovo elemento di esempio**.

        - Copiare e incollare un elemento nel diagramma.

    3. Verificare che non sia possibile utilizzare uno di questi modi per aggiungere più di quattro elementi al modello. Poiché tutti utilizzano la direttiva di Unione degli elementi.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Esempio: aggiunta di codice di merge personalizzato a un EMD

Nel codice di merge personalizzato è possibile definire cosa accade quando l'utente trascina uno strumento o incolla su un elemento. Esistono due modi per definire un'unione personalizzata:

1. Set **Usa l'Unione personalizzata** e fornisce il codice necessario. Il codice sostituisce il codice di merge generato. Utilizzare questa opzione se si desidera ridefinire completamente le operazioni di merge.

2. Eseguire l'override del `MergeRelate` metodo e, facoltativamente, il `MergeDisconnect` metodo. A tale scopo, è necessario impostare la proprietà **generata doppia derivata** della classe di dominio. Il codice può chiamare il codice di merge generato nella classe di base. Utilizzare questa opzione se si desidera eseguire operazioni aggiuntive dopo l'esecuzione del merge.

   Questi approcci influiscono solo sulle unioni eseguite utilizzando questo EMD. Se si desidera influire su tutti i modi in cui è possibile creare l'elemento Unito, un'alternativa consiste nel definire un oggetto `AddRule` nella relazione di incorporamento e un oggetto `DeleteRule` sulla classe di dominio unita. Per ulteriori informazioni, vedere la pagina relativa alla [propagazione delle modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Per eseguire l'override di MergeRelate

1. Nella definizione DSL verificare di aver definito il EMD a cui si desidera aggiungere il codice. Se lo si desidera, è possibile aggiungere percorsi e definire codice Accept personalizzato come descritto nelle sezioni precedenti.

2. Nel diagramma di DslDefinition selezionare la classe ricevente del merge. Si tratta in genere della classe all'estremità di origine di una relazione di incorporamento.

     Ad esempio, in un linguaggio DSL generato dalla soluzione di linguaggio minimo selezionare `ExampleModel` .

3. Nella finestra **Proprietà** impostare **genera Double come derivato** su **true**.

4. Ricompilare la soluzione.

5. Esaminare il contenuto di **Dsl\Generated Files\DomainClasses.cs**. Cercare i metodi denominati `MergeRelate` ed esaminarne il contenuto. Ciò consentirà di scrivere versioni personalizzate.

6. In un nuovo file di codice scrivere una classe parziale per la classe ricevente ed eseguire l'override del `MergeRelate` metodo. Ricordarsi di chiamare il metodo di base. Ad esempio:

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

### <a name="to-write-custom-merge-code"></a>Per scrivere codice di merge personalizzato

1. In **Dsl\Generated Code\DomainClasses.cs**controllare i metodi denominati `MergeRelate` . Questi metodi creano collegamenti tra un nuovo elemento e il modello esistente.

    Esaminare inoltre i metodi denominati `MergeDisconnect` . Questi metodi scollegano un elemento dal modello quando deve essere eliminato.

2. In **DSL Explorer**selezionare o creare la direttiva di Unione elementi che si desidera personalizzare. Nella finestra **Dettagli DSL** impostare **Usa unione personalizzata**.

    Quando si imposta questa opzione, le opzioni **elabora Unione** e Esegui **merge** vengono ignorate. Viene invece usato il codice.

3. Ricompilare la soluzione. Il tempo necessario per i file di codice generati verrà aggiornato dal modello.

    Verranno visualizzati i messaggi di errore. Fare doppio clic sui messaggi di errore per visualizzare le istruzioni nel codice generato. Queste istruzioni richiedono di specificare due metodi, `MergeRelate` *YourDomainClass* e `MergeDisconnect` *YourDomainClass*

4. Scrivere i metodi in una definizione di classe parziale in un file di codice separato. Gli esempi esaminati in precedenza dovrebbero suggerire gli elementi necessari.

   Il codice di merge personalizzato non avrà alcun effetto sul codice che crea direttamente oggetti e relazioni e non influirà sugli altri EMDs. Per assicurarsi che le modifiche aggiuntive vengano implementate indipendentemente dalla modalità di creazione dell'elemento, prendere in considerazione la possibilità di scrivere un oggetto `AddRule` e un oggetto `DeleteRule` . Per ulteriori informazioni, vedere la pagina relativa alla [propagazione delle modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Reindirizzamento di un'operazione di Unione

Una direttiva di Unione diretta reindirizza la destinazione di un'operazione di Unione. In genere, la nuova destinazione è l'elemento padre di incorporamento della destinazione iniziale.

Ad esempio, in un linguaggio DSL creato con il modello di diagramma dei componenti, le porte sono incorporate nei componenti. Le porte vengono visualizzate come forme piccole sul bordo di una forma componente. L'utente crea le porte trascinando lo strumento porta sulla forma di un componente. In alcuni casi, tuttavia, l'utente trascina erroneamente lo strumento porta su una porta esistente, anziché sul componente, e l'operazione ha esito negativo. Si tratta di un semplice errore quando sono presenti più porte esistenti. Per consentire all'utente di evitare questo problema, è possibile consentire il trascinamento delle porte su una porta esistente, ma fare in modo che l'azione venga reindirizzata al componente padre. L'operazione funziona come se l'elemento di destinazione fosse il componente.

È possibile creare una direttiva di Unione in diretta nella soluzione del modello di componenti. Se si compila ed esegue la soluzione originale, si noterà che gli utenti possono trascinare un numero qualsiasi di elementi della porta di **input** o di **output** dalla **casella degli strumenti** a un elemento **componente** . Tuttavia, non è possibile trascinare una porta in una porta esistente. Il puntatore non disponibile avvisa che lo spostamento non è abilitato. Tuttavia, è possibile creare una direttiva di Unione in avanti in modo che una porta non intenzionalmente eliminata su una **porta di input** esistente venga trasmessa all'elemento **Component** .

### <a name="to-create-a-forward-merge-directive"></a>Per creare una direttiva di Unione in diretta

1. Creare una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello di modello Component.

2. Visualizzare **DSL Explorer** aprendo DslDefinition. DSL.

3. In **DSL Explorer**espandere classi di **dominio**.

4. La classe di dominio astratta **ComponentPort** è la classe base sia di **InPort** che di **OutPort**. Fare clic con il pulsante destro del mouse su **ComponentPort** e quindi scegliere **Aggiungi nuova direttiva di Unione elementi**.

    Un nuovo nodo **della direttiva di Unione elementi** viene visualizzato sotto il nodo **direttive di Unione elementi** .

5. Selezionare il nodo della **direttiva di Unione elementi** e aprire la finestra **Dettagli DSL** .

6. Nell'elenco classe di indicizzazione selezionare **ComponentPort**.

7. Selezionare Esegui **merge in un'altra classe di dominio**.

8. Nell'elenco di selezione del percorso espandere **ComponentPort**, espandere **ComponentHasPorts**e quindi selezionare **Component**.

    Il nuovo percorso sarà simile a quello riportato di seguito:

    **Componente ComponentHasPorts. Component/!**

9. Salvare la soluzione, quindi trasformare i modelli facendo clic sul pulsante all'estrema destra sulla barra degli strumenti **Esplora soluzioni** .

10. Compilare ed eseguire la soluzione. Viene visualizzata una nuova istanza di Visual Studio.

11. In **Esplora soluzioni**aprire Sample. mydsl. Verranno visualizzati il diagramma e la **casella degli strumenti ComponentLanguage** .

12. Trascinare una **porta di input** dalla **casella degli strumenti** in un'altra **porta di input.** Trascinare quindi un **OutputPort** in **InputPort** e quindi in un altro **OutputPort**.

     Non dovrebbe essere visualizzato il puntatore non disponibile e dovrebbe essere possibile eliminare la nuova porta di **input** su quella esistente. Selezionare la nuova **porta di input** e trascinarla in un altro punto del **componente**.

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Personalizzazione di strumenti e della casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md)
- [Esempio di diagrammi circuito DSL](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
