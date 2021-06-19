---
title: Personalizzazione della creazione e dello spostamento di elementi
description: Informazioni su come è possibile trascinare un elemento in un altro elemento, dalla casella degli strumenti o in un'operazione Incolla o Sposta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.elementmergedirective
helpviewer_keywords:
- Domain-Specific Language, element merge directives
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42339c532db3442d5fb5c5da3b51d94801a0907d
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389397"
---
# <a name="customizing-element-creation-and-movement"></a>Personalizzazione della creazione e dello spostamento di elementi

È possibile consentire il trascinamento di un elemento in un altro, dalla casella degli strumenti o in un'operazione Incolla o Sposta. È possibile collegare gli elementi spostati agli elementi di destinazione usando le relazioni specificate.

Una direttiva di unione degli elementi (EMD) specifica cosa accade quando un elemento del modello *viene unito* in un altro elemento del modello. Ciò si verifica quando:

- L'utente trascina dalla casella degli strumenti al diagramma o a una forma.

- L'utente crea un elemento usando un menu Aggiungi nello strumento di esplorazione o una forma raggruppamento.

- L'utente sposta un elemento da una corsia a un'altra.

- L'utente incolla un elemento .

- Il codice del programma chiama la direttiva di unione degli elementi.

Anche se le operazioni di creazione possono sembrare diverse dalle operazioni di copia, funzionano nello stesso modo. Quando un elemento viene aggiunto, ad esempio dalla casella degli strumenti, viene replicato un prototipo di esso. Il prototipo viene unito nel modello nello stesso modo degli elementi copiati da un'altra parte del modello.

La responsabilità di un emd è decidere in che modo un oggetto o un gruppo di oggetti deve essere unito in una posizione specifica nel modello. In particolare, decide di quali relazioni creare un'istanza per collegare il gruppo unito nel modello. È anche possibile personalizzarlo per impostare le proprietà e creare oggetti aggiuntivi.

![Diagramma che mostra un prima e dopo esaminare un albero di elementi e le relative relazioni di riferimento quando an E M D determina come viene aggiunto un nuovo elemento.](../modeling/media/dsl-emd_merge.png)

Un emd viene generato automaticamente quando si definisce una relazione di incorporamento. Questo EMD predefinito crea un'istanza della relazione quando gli utenti aggiungono nuove istanze figlio all'elemento padre. È possibile modificare questi emD predefiniti, ad esempio aggiungendo codice personalizzato.

È anche possibile aggiungere emd personalizzati nella definizione DSL per consentire agli utenti di trascinare o incollare diverse combinazioni di classi unite e riceventi.

## <a name="defining-an-element-merge-directive"></a>Definizione di una direttiva di unione di elementi

È possibile aggiungere direttive di unione degli elementi a classi di dominio, relazioni di dominio, forme, connettori e diagrammi. È possibile aggiungerli o trovarli in Esplora DSL nella classe di dominio ricevente. La classe ricevente è la classe di dominio dell'elemento già presente nel modello e in cui verrà unito l'elemento nuovo o copiato.

![Screenshot di DSL Explorer che mostra l'aggiunta di un E MD con ExampleElement selezionato come classe Indexing e l'opzione Si applica alle sottoclassi selezionata.](../modeling/media/dsl-emd_details.png)

Indexing **Class è** la classe di dominio di elementi che possono essere uniti nei membri della classe ricevente. Anche le istanze delle sottoclassi della classe di indicizzazione verranno unite da questo EMD, a meno che non si imposta Si applica alle **sottoclassi** su False.

Esistono due tipi di direttiva merge:

- Una **direttiva Process Merge** specifica le relazioni in base alle quali il nuovo elemento deve essere collegato all'albero.

- Una **direttiva Forward Merge** reindirizza il nuovo elemento a un altro elemento ricevente, in genere un elemento padre.

È possibile aggiungere codice personalizzato per unire le direttive:

- Imposta **Usa l'accettazione** personalizzata per aggiungere codice personalizzato per determinare se una particolare istanza dell'elemento di indicizzazione deve essere unita nell'elemento di destinazione. Quando l'utente trascina dalla casella degli strumenti, il puntatore "non valido" indica se il codice non consente l'unione.

   Ad esempio, è possibile consentire l'unione solo quando l'elemento ricevente si trova in uno stato specifico.

- Imposta **Usa merge personalizzato** per aggiungere codice personalizzato per definire le modifiche apportate al modello quando viene eseguita l'unione.

   Ad esempio, è possibile impostare le proprietà nell'elemento unito usando i dati della nuova posizione nel modello.

> [!NOTE]
> Se si scrive codice di unione personalizzato, questa operazione influisce solo sulle unioni eseguite tramite questo EMD. Se sono presenti altri emD che uniscono lo stesso tipo di oggetto o se è presente altro codice personalizzato che crea questi oggetti senza usare EMD, non saranno interessati dal codice di unione personalizzato.
>
> Per assicurarsi che un nuovo elemento o una nuova relazione vengano sempre elaborati dal codice personalizzato, è consigliabile definire un elemento nella relazione di incorporamento e un elemento nella classe di dominio `AddRule` `DeleteRule` dell'elemento. Per altre informazioni, vedere [Regole di propagazione delle modifiche all'interno del modello.](../modeling/rules-propagate-changes-within-the-model.md)

## <a name="example-defining-an-emd-without-custom-code"></a>Esempio: Definizione di un file EMD senza codice personalizzato

L'esempio seguente consente agli utenti di creare contemporaneamente un elemento e un connettore trascinando dalla casella degli strumenti a una forma esistente. Nell'esempio viene aggiunto un emd alla definizione DSL. Prima di questa modifica, gli utenti possono trascinare gli strumenti nel diagramma, ma non nelle forme esistenti.

Gli utenti possono anche incollare elementi in altri elementi.

### <a name="to-let-users-create-an-element-and-a-connector-at-the-same-time"></a>Per consentire agli utenti di creare contemporaneamente un elemento e un connettore

1. Creare un nuovo linguaggio DSL usando il modello **di soluzione Linguaggio** minimo.

    Quando si esegue questo DSL, è possibile creare forme e connettori tra le forme. Non è possibile trascinare una **nuova forma ExampleElement** dalla casella degli strumenti in una forma esistente.

2. Per consentire agli utenti di unire elementi `ExampleElement` nelle forme, creare un nuovo EMD nella `ExampleElement` classe di dominio:

   1. In **Esplora DSL espandere** Classi di **dominio**. Fare clic con il pulsante `ExampleElement` destro del mouse su e quindi scegliere Aggiungi nuova direttiva di unione **elemento**.

   2. Assicurarsi che la **finestra Dettagli DSL** sia aperta, in modo da poter visualizzare i dettagli del nuovo EMD. (Menu: **Visualizza**, **Altre finestre**, Dettagli **DSL).**

3. Impostare la **classe Indexing** nella finestra Dettagli DSL per definire la classe di elementi che è possibile unire agli `ExampleElement` oggetti.

    Per questo esempio, selezionare `ExampleElements` , in modo che l'utente possa trascinare nuovi elementi in elementi esistenti.

    Si noti che la classe Indexing diventa il nome dell'EMD in DSL Explorer.

4. In **Unione processi mediante la creazione di collegamenti** aggiungere due percorsi:

   - Un percorso collega il nuovo elemento al modello padre. L'espressione di percorso che è necessario immettere consente di spostarsi dall'elemento esistente, fino alla relazione di incorporamento al modello padre. Infine, specifica il ruolo nel nuovo collegamento a cui verrà assegnato il nuovo elemento. Il percorso è il seguente:

      `ExampleModelHasElements.ExampleModel/!ExampleModel/.Elements`

   - L'altro percorso collega il nuovo elemento all'elemento esistente. L'espressione di percorso specifica la relazione di riferimento e il ruolo a cui verrà assegnato il nuovo elemento. Questo percorso è il seguente:

      `ExampleElementReferencesTargets.Sources`

      È possibile usare lo strumento di navigazione percorso per creare ogni percorso:

      1. In **Unione processi mediante la creazione di collegamenti nei percorsi** fare clic su **\<add path>** .

      2. Fare clic sulla freccia a discesa a destra dell'elemento dell'elenco. Verrà visualizzata una visualizzazione albero.

      3. Espandere i nodi nell'albero per formare il percorso che si desidera specificare.

5. Testare il DSL:

   1. Premere **F5 per** ricompilare ed eseguire la soluzione.

        La ricompilazione richiederà più tempo del solito perché il codice generato verrà aggiornato dai modelli di testo per essere conforme alla nuova definizione DSL.

   2. Quando l'istanza sperimentale di Visual Studio avviata, aprire un file di modello del DSL. Creare alcuni elementi di esempio.

   3. Trascinare dallo **strumento Elemento di** esempio in una forma esistente.

        Viene visualizzata una nuova forma collegata alla forma esistente con un connettore.

   4. Copiare una forma esistente. Selezionare un'altra forma e incollare.

        Viene creata una copia della prima forma.  Ha un nuovo nome ed è collegato alla seconda forma con un connettore.

Si notino i punti seguenti di questa procedura:

- Creando direttive di unione degli elementi, è possibile consentire a qualsiasi classe di elemento di accettare qualsiasi altra classe di elementi. L'EMD viene creato nella classe di dominio ricevente e la classe di dominio accettata viene specificata nel **campo Classe index.**

- Definendo i percorsi, è possibile specificare quali collegamenti usare per connettere il nuovo elemento al modello esistente.

     I collegamenti specificati devono includere una relazione di incorporamento.

- L'EMD influisce sia sulla creazione dalla casella degli strumenti che sulle operazioni Incolla.

     Se si scrive codice personalizzato che crea nuovi elementi, è possibile richiamare in modo esplicito l'EMD usando il `ElementOperations.Merge` metodo . In questo modo si garantisce che il codice collega nuovi elementi nel modello nello stesso modo delle altre operazioni. Per altre informazioni, vedere [Personalizzazione del comportamento di copia.](../modeling/customizing-copy-behavior.md)

## <a name="example-adding-custom-accept-code-to-an-emd"></a>Esempio: Aggiunta di codice Accept personalizzato a un emd

Aggiungendo codice personalizzato a un emd, è possibile definire un comportamento di unione più complesso. Questo semplice esempio impedisce all'utente di aggiungere più di un numero fisso di elementi al diagramma. L'esempio modifica l'EMD predefinito che accompagna una relazione di incorporamento.

### <a name="to-write-custom-accept-code-to-restrict-what-the-user-can-add"></a>Per scrivere codice Accept personalizzato per limitare gli elementi che l'utente può aggiungere

1. Creare un linguaggio DSL usando il modello **di soluzione Linguaggio** minimo. Aprire il diagramma di definizione DSL.

2. In Esplora DSL espandere **Classi di dominio**, Direttive di unione degli `ExampleModel` **elementi**. Selezionare la direttiva di unione degli elementi denominata `ExampleElement` .

     Questo EMD controlla come l'utente può creare nuovi oggetti nel modello, ad esempio trascinando dalla `ExampleElement` casella degli strumenti.

3. Nella finestra **Dettagli DSL** selezionare Usa **accettazione personalizzata.**

4. Ricompilare la soluzione. Questa operazione richiederà più tempo del solito perché il codice generato verrà aggiornato dal modello.

     Verrà segnalato un errore di compilazione simile al seguente: "Company.ElementMergeSample.ExampleElement non contiene una definizione per CanMergeExampleElement..."

     È necessario implementare il metodo `CanMergeExampleElement` .

5. Creare un nuovo file di codice nel **progetto Dsl.** Sostituire il contenuto con il codice seguente e modificare lo spazio dei nomi nello spazio dei nomi del progetto.

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

    Questo semplice esempio limita il numero di elementi che possono essere uniti nel modello padre. Per condizioni più interessanti, il metodo può esaminare le proprietà e i collegamenti dell'oggetto ricevente. Può anche esaminare le proprietà degli elementi di unione, che vengono trasportati in un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> oggetto . Per altre informazioni su `ElementGroupPrototypes` , vedere [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md). Per altre informazioni su come scrivere codice che legge un modello, vedere Esplorazione e aggiornamento di [un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

6. Testare il DSL:

    1. Premere **F5** per ricompilare la soluzione. Quando si apre l'istanza sperimentale Visual Studio, aprire un'istanza del DSL.

    2. Creare nuovi elementi in diversi modi:

        - Trascinare dallo **strumento Elemento di** esempio nel diagramma.

        - In **Esplora modelli di esempio** fare clic con il pulsante destro del mouse sul nodo radice e quindi scegliere **Aggiungi nuovo elemento di esempio**.

        - Copiare e incollare un elemento nel diagramma.

    3. Verificare che non sia possibile usare uno di questi modi per aggiungere più di quattro elementi al modello. Ciò è dovuto al fatto che tutti usano la direttiva di unione degli elementi.

## <a name="example-adding-custom-merge-code-to-an-emd"></a>Esempio: aggiunta di codice di unione personalizzato a un emd

Nel codice di unione personalizzato è possibile definire cosa accade quando l'utente trascina uno strumento o incolla su un elemento. Esistono due modi per definire un'unione personalizzata:

1. Impostare **Usa unione personalizzata** e specificare il codice necessario. Il codice sostituisce il codice di unione generato. Usare questa opzione se si vuole ridefinire completamente le operazioni di unione.

2. Eseguire `MergeRelate` l'override del metodo e, facoltativamente, del `MergeDisconnect` metodo . A tale scopo, è necessario impostare la **proprietà Generates Double Derived** della classe di dominio. Il codice può chiamare il codice di unione generato nella classe di base. Utilizzare questa opzione se si desidera eseguire operazioni aggiuntive dopo l'esecuzione dell'unione.

   Questi approcci influiscono solo sulle unioni eseguite usando questo EMD. Se si vuole influire su tutti i modi in cui è possibile creare l'elemento unito, un'alternativa consiste nel definire un nella relazione di incorporamento e un nella classe di `AddRule` `DeleteRule` dominio unita. Per altre informazioni, vedere [Regole propagare le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="to-override-mergerelate"></a>Per eseguire l'override di MergeRelate

1. Nella definizione DSL assicurarsi di aver definito l'EMD a cui si vuole aggiungere il codice. Se si desidera, è possibile aggiungere percorsi e definire codice di accettazione personalizzato come descritto nelle sezioni precedenti.

2. Nel diagramma DslDefinition selezionare la classe ricevente dell'unione. In genere si tratta della classe all'estremità di origine di una relazione di incorporamento.

     Ad esempio, in un linguaggio DSL generato dalla soluzione Minimal Language selezionare `ExampleModel` .

3. Nella finestra **Proprietà** impostare **Generates Double Derived** su **true.**

4. Ricompilare la soluzione.

5. Esaminare il contenuto di **Dsl\Generated Files\DomainClasses.cs**. Cercare i metodi denominati `MergeRelate` ed esaminarne il contenuto. In questo modo sarà possibile scrivere le proprie versioni.

6. In un nuovo file di codice scrivere una classe parziale per la classe ricevente ed eseguire l'override del `MergeRelate` metodo . Ricordarsi di chiamare il metodo di base. Ad esempio:

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

### <a name="to-write-custom-merge-code"></a>Per scrivere codice di unione personalizzato

1. In **Dsl\Generated Code\DomainClasses.cs** esaminare i metodi denominati `MergeRelate` . Questi metodi creano collegamenti tra un nuovo elemento e il modello esistente.

    Esaminare anche i metodi denominati `MergeDisconnect` . Questi metodi scollegano un elemento dal modello quando deve essere eliminato.

2. In **Esplora DSL** selezionare o creare la direttiva di unione degli elementi da personalizzare. Nella finestra **Dettagli DSL** impostare **Usa unione personalizzata**.

    Quando si imposta questa opzione, le **opzioni Process Merge e** Forward **Merge** vengono ignorate. Viene invece usato il codice.

3. Ricompilare la soluzione. L'aggiornamento dei file di codice generati dal modello richiederà più tempo del solito.

    Verranno visualizzati messaggi di errore. Fare doppio clic sui messaggi di errore per visualizzare le istruzioni nel codice generato. Queste istruzioni chiedono di fornire due metodi, `MergeRelate` *YourDomainClass* e `MergeDisconnect` *YourDomainClass*

4. Scrivere i metodi in una definizione di classe parziale in un file di codice separato. Gli esempi esaminati in precedenza dovrebbero suggerire le informazioni necessarie.

   Il codice di unione personalizzato non influisce sul codice che crea direttamente oggetti e relazioni e non influisce su altri EMD. Per assicurarsi che le modifiche aggiuntive siano implementate indipendentemente dalla modalità di creazione dell'elemento, prendere in considerazione la scrittura di `AddRule` e `DeleteRule` . Per altre informazioni, vedere [Regole propagare le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

## <a name="redirecting-a-merge-operation"></a>Reindirizzamento di un'operazione di merge

Una direttiva forward merge reindirizza la destinazione di un'operazione di merge. In genere, la nuova destinazione è l'elemento padre di incorporamento della destinazione iniziale.

Ad esempio, in un DSL creato con il modello di diagramma dei componenti, le porte sono incorporate in Componenti. Le porte vengono visualizzate come forme piccole sul bordo di una forma del componente. L'utente crea le porte trascinando lo strumento Porta in una forma Componente. A volte, tuttavia, l'utente trascina erroneamente lo strumento Porta su una porta esistente, anziché sul componente, e l'operazione non riesce. Si tratta di un errore facile quando sono presenti diverse porte esistenti. Per aiutare l'utente a evitare questo problema, è possibile consentire il trascinamento delle porte su una porta esistente, ma l'azione viene reindirizzata al componente padre. L'operazione funziona come se l'elemento di destinazione fosse il componente.

È possibile creare una direttiva di unione in avanti nella soluzione Modello di componente. Se si compila ed esegue la soluzione originale, si dovrebbe vedere che gli  utenti possono trascinare un numero qualsiasi di elementi Porta di **input** o **Porta** di output dalla Casella degli strumenti a un **elemento Componente.** Non possono tuttavia trascinare una porta in una porta esistente. Il puntatore Non disponibile avvisa che lo spostamento non è abilitato. Tuttavia, è possibile creare una direttiva di inoltro merge in modo che una porta eliminata involontariamente su una porta **di input** esistente sia inoltrata all'elemento **Component.**

### <a name="to-create-a-forward-merge-directive"></a>Per creare una direttiva di merge in avanti

1. Creare una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione usando il modello Modello di componente.

2. Visualizzare **Esplora DSL** aprendo DslDefinition.dsl.

3. In **Esplora DSL espandere** **Classi di dominio**.

4. La classe di dominio astratta **ComponentPort** è la classe di base sia **di InPort** che **di OutPort.** Fare clic con il pulsante destro del mouse su **ComponentPort** e quindi **scegliere Aggiungi nuova direttiva di unione elementi**.

    Nel nodo **Direttive di unione elementi** viene visualizzato un nuovo nodo Direttiva di **unione** elementi.

5. Selezionare il **nodo Direttiva di unione elementi** e aprire la finestra Dettagli **DSL.**

6. Nell'elenco Classe di indicizzazione selezionare **ComponentPort**.

7. Selezionare **Inoltra merge a una classe di dominio diversa.**

8. Nell'elenco di selezione del percorso espandere **ComponentPort**, **ComponentHasPorts** e quindi **selezionare Componente**.

    Il nuovo percorso dovrebbe essere simile al seguente:

    **ComponentHasPorts.Component/!Component**

9. Salvare la soluzione e quindi trasformare i modelli facendo clic sul pulsante più a destra Esplora soluzioni barra **degli strumenti.**

10. Compilare ed eseguire la soluzione. Verrà visualizzata una nuova Visual Studio di .

11. In **Esplora soluzioni** aprire Sample.mydsl. Vengono visualizzati il diagramma e **la casella degli strumenti ComponentLanguage.**

12. Trascinare una **porta di input** dalla casella degli strumenti **a** un'altra porta **di input.** Trascinare quindi un **oggetto OutputPort** in un **inputPort** e quindi in un altro **OutputPort.**

     Il puntatore Non disponibile non dovrebbe essere visualizzato e dovrebbe essere possibile eliminare la nuova porta **di input** su quella esistente. Selezionare la nuova **porta di input** e trascinarla in un altro punto in **Componente**.

## <a name="see-also"></a>Vedi anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Personalizzazione di strumenti e della casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md)
- [Diagramma di circuito DSL di esempio](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)
