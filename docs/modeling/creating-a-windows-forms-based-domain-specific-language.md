---
title: Creare un linguaggio specifico di dominio basato su Windows Form
description: Vengono fornite informazioni su come usare Windows form per visualizzare lo stato di un modello linguistico specifico di dominio.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 3355a84d34e297bb7394ca0e0feb8c3e635f615b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061324"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Creare un Windows basato su Domain-Specific Form

È possibile usare Windows form per visualizzare lo stato di un modello DSL (Domain Specific Language), invece di usare un diagramma DSL. Questo argomento illustra come associare un form Windows a un DSL usando Visual Studio Visualization and Modeling SDK.

L'immagine seguente mostra un'interfaccia Windows form e Esplora modelli per un'istanza DSL:

![Istanza DSL in Visual Studio](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Creare un DSL Windows Forms

Il **modello DSL minimale** di Progettazione Windows Form crea un DSL minimo che è possibile modificare in base alle proprie esigenze.

1. Creare un DSL dal **modello minimale di Progettazione Windows** Form.

    In questa procedura dettagliata vengono utilizzati i nomi seguenti:

    - Soluzione e nome DSL: `FarmApp`
    - Spazio dei nomi: `Company.FarmApp`

2. Provare a eseguire l'esempio iniziale fornito dal modello:

   1. Trasforma tutti i modelli.

   2. Compilare ed eseguire l'esempio (**CTRL** + **F5**).

   3. Nell'istanza sperimentale Visual Studio aprire il `Sample` file nel progetto di debug.

        Si noti che viene visualizzato in un controllo Windows Form.

        È anche possibile visualizzare gli elementi del modello visualizzati in Esplora risorse.

        Aggiungere alcuni elementi nel form o in Explorer e notare che vengono visualizzati nell'altra visualizzazione.

   Nell'istanza principale di Visual Studio, si notino i punti seguenti sulla soluzione DSL:

- `DslDefinition.dsl` non contiene elementi del diagramma. Questo perché non si useranno diagrammi DSL per visualizzare i modelli di istanza di questo DSL. Si associa invece un form Windows al modello e gli elementi nel form visualizzano il modello.

- Oltre ai progetti e , la soluzione contiene un terzo progetto denominato Progetto dell'interfaccia utente che contiene la definizione di `Dsl` `DslPackage` un controllo Windows `UI.`  Form. `DslPackage` dipende da `UI` e `UI` dipende da `Dsl` .

- Nel progetto contiene il codice che visualizza il Windows Form definito `DslPackage` `UI\DocView.cs` nel `UI` progetto.

- Il `UI` progetto contiene un esempio funzionante di un controllo form associato al DSL. Tuttavia, non funzionerà dopo aver modificato la definizione DSL. Il `UI` progetto contiene:

  - Classe Windows Forms denominata `ModelViewControl` .

  - File denominato `DataBinding.cs` che contiene una definizione parziale aggiuntiva di `ModelViewControl` . Per visualizzarne il contenuto, in **Esplora soluzioni** aprire il menu di scelta rapida per il file e scegliere **Visualizza codice.**

### <a name="about-the-ui-project"></a>Informazioni sul progetto dell'interfaccia utente

Quando si aggiorna il file di definizione DSL per definire il proprio DSL, sarà necessario aggiornare il controllo nel progetto per visualizzare `UI` il DSL. A differenza `Dsl` dei progetti e , il progetto di esempio non viene generato da `DslPackage` `UI` `DslDefinitionl.dsl` . È possibile aggiungere file con estensione tt per generare il codice, se lo si desidera, anche se questo non è illustrato in questa procedura dettagliata.

## <a name="update-the-dsl-definition"></a>Aggiornare la definizione DSL

L'immagine seguente è la definizione DSL usata in questa procedura dettagliata.

![Definizione DSL](../modeling/media/dsl-wpf-1.png)

1. Aprire DslDefinition.dsl nella finestra di progettazione DSL.

2. Eliminare **ExampleElement**

3. Rinominare la **classe di dominio ExampleModel** in `Farm` .

     Assegnare ad esso proprietà di dominio `Size` aggiuntive denominate di tipo **Int32** e `IsOrganic` di tipo **Boolean.**

    > [!NOTE]
    > Se si elimina la classe di dominio radice e quindi si crea una nuova radice, sarà necessario reimpostare la proprietà Classe radice editor. In **Esplora DSL selezionare** **Editor.** Nella finestra di Finestra Proprietà quindi impostare **Root Class (Classe radice)** su `Farm` .

4. Usare lo **strumento Classe di dominio** denominato per creare le classi di dominio seguenti:

    - `Field` - Assegnare a questa proprietà di dominio aggiuntiva denominata `Size` .

    - `Animal`- Nella finestra di Finestra Proprietà impostare **Modificatore di ereditarietà** su **Abstract.**

5. Usare lo **strumento Domain Class** per creare le classi seguenti:

    - `Sheep`

    - `Goat`

6. Usare lo strumento **Ereditarietà** per creare `Goat` ed `Sheep` ereditare da `Animal` .

7. Usare lo **strumento di incorporamento** per incorporare `Field` e in `Animal` `Farm` .

8. Potrebbe essere necessario riordinare il diagramma. Per ridurre il numero di elementi duplicati, usare il **comando Porta sottoalbero** qui nel menu di scelta rapida degli elementi foglia.

9. **Trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni.

10. Compilare **il progetto Dsl.**

    > [!NOTE]
    > In questa fase, gli altri progetti non verranno compilati senza errori. Tuttavia, si vuole compilare il progetto Dsl in modo che il relativo assembly sia disponibile per la Creazione guidata origine dati.

## <a name="update-the-ui-project"></a>Aggiornare il progetto dell'interfaccia utente

È ora possibile creare un nuovo controllo utente che visualizza le informazioni archiviate nel modello DSL. Il modo più semplice per connettere il controllo utente al modello è tramite data binding. Il data binding adattatore di rete denominato **ModelingBindingSource** è progettato specificamente per connettere DSL a interfacce non VMSDK.

### <a name="define-your-dsl-model-as-a-data-source"></a>Definire il modello DSL come origine dati

1. Scegliere **Mostra** origini **dati dal** menu Dati .

     Verrà visualizzata la finestra **Origini dati**.

     Scegliere **Aggiungi nuova origine dati.** Verrà **visualizzata la Configurazione guidata origine** dati.

2. Scegliere **Oggetto**, **Avanti.**

     Espandere **Dsl**, **Company.FarmApp** e selezionare **Farm**, che è la classe radice del modello. Scegliere **Fine**.

     In Esplora soluzioni il progetto **dell'interfaccia** utente contiene **ora Properties\DataSources\Farm.datasource**

     Le proprietà e le relazioni della classe del modello vengono visualizzate nella finestra Origini dati.

     ![Finestra Origini dati](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Connessione il modello in un modulo

1. Nel progetto **dell'interfaccia** utente eliminare tutti i file con estensione cs esistenti.

2. Aggiungere un nuovo file **di controllo utente** denominato al progetto `FarmControl` **dell'interfaccia** utente.

3. Nella finestra **Origini dati** scegliere Dettagli dal menu a discesa in **Farm.** 

    Lasciare le impostazioni predefinite per le altre proprietà.

4. Aprire FarmControl.cs nella visualizzazione Progettazione.

    Trascinare **Farm** dalla finestra Origini dati in FarmControl.

    Viene visualizzato un set di controlli, uno per ogni proprietà. Le proprietà della relazione non generano controlli.

5. Eliminare **farmBindingNavigator.** Viene generato automaticamente anche nella finestra `FarmControl` di progettazione, ma non è utile per questa applicazione.

6. Usando la casella degli strumenti, creare due istanze di **DataGridView** e assegnare loro il nome `AnimalGridView` e `FieldGridView` .

   > [!NOTE]
   > Un passaggio alternativo consiste nel trascinare gli elementi Animali e Campi dalla finestra Origini dati nel controllo . Questa azione crea automaticamente griglie dati e associazioni tra la visualizzazione griglia e l'origine dati. Tuttavia, questa associazione non funziona correttamente per i DSL. È quindi meglio creare manualmente le griglie dati e le associazioni.

7. Se la casella degli strumenti non contiene lo **strumento ModelingBindingSource,** aggiungerlo. Scegliere Scegli elementi dal menu **di scelta** rapida della **scheda Dati**. Nella finestra **di dialogo Scegli elementi della** casella degli strumenti selezionare **ModelingBindingSource** nella **.NET Framework** proprietà.

8. Usando la casella degli strumenti, creare due istanze di **ModelingBindingSource** e assegnare loro il nome `AnimalBinding` e `FieldBinding` .

9. Impostare la **proprietà DataSource** di ogni **modelingBindingSource** su **farmBindingSource.**

     Impostare la **proprietà DataMember** su **Animali** o **Campi.**

10. Impostare le **proprietà DataSource** `AnimalGridView` di su e di su `AnimalBinding`  `FieldGridView` `FieldBinding` .

11. Modificare il layout del controllo Farm in base alle proprie preferenze.

    **ModelingBindingSource è** un adattatore che esegue diverse funzioni specifiche delle DSL:

- Esegue il wrapping degli aggiornamenti in una transazione di archiviazione VMSDK.

   Ad esempio, quando l'utente elimina una riga dalla griglia della visualizzazione dati, un'associazione regolare genera un'eccezione di transazione.

- Garantisce che, quando l'utente seleziona una riga, il Finestra Proprietà visualizza le proprietà dell'elemento del modello corrispondente, anziché la riga della griglia dei dati.

  ![Schema dell'associazione DSL](../modeling/media/dslwpf4.png)
  
  Schema dei collegamenti tra origini dati e viste.

### <a name="complete-the-bindings-to-the-dsl"></a>Completare le associazioni al DSL

1. Aggiungere il codice seguente in un file di codice separato nel progetto **dell'interfaccia** utente:

    ```csharp
    using System.ComponentModel;
    using Microsoft.VisualStudio.Modeling;
    using Microsoft.VisualStudio.Modeling.Design;

    namespace Company.FarmApp
    {
      partial class FarmControl
      {
        public IContainer Components { get { return components; } }

        /// <summary>Binds the WinForms data source to the DSL model.
        /// </summary>
        /// <param name="nodelRoot">The root element of the model.</param>
        public void DataBind(ModelElement modelRoot)
        {
          WinFormsDataBindingHelper.PreInitializeDataSources(this);
          this.farmBindingSource.DataSource = modelRoot;
          WinFormsDataBindingHelper.InitializeDataSources(this);
        }
      }
    }
    ```

2. Nel progetto **DslPackage** modificare **DslPackage\DocView.tt** per aggiornare la definizione di variabile seguente:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>Testare il DSL

La soluzione DSL può ora essere compilata ed eseguita, anche se potrebbe essere necessario aggiungere altri miglioramenti in un secondo momento.

1. Compilare ed eseguire la soluzione.

2. Nell'istanza sperimentale di Visual Studio aprire il file **di** esempio.

3. In **FarmApp Explorer** aprire il menu di scelta rapida nel nodo radice **Farm** e scegliere Aggiungi **nuova capra.**

     `Goat1`viene visualizzato nella **visualizzazione Animali.**

    > [!WARNING]
    > È necessario usare il menu di scelta rapida nel **nodo Farm,** non nel **nodo Animali.**

4. Selezionare il **nodo radice farm** e visualizzarne le proprietà.

     Nella visualizzazione modulo modificare il **nome o** **le dimensioni** della farm.

     Quando ci si sposta da ogni campo nel modulo, la proprietà corrispondente cambia nel Finestra Proprietà.

## <a name="enhance-the-dsl"></a>Migliorare il DSL

### <a name="make-the-properties-update-immediately"></a>Aggiornare immediatamente le proprietà

1. Nella visualizzazione progettazione di FarmControl.cs selezionare un campo semplice, ad esempio Name, Size o IsOrganic.

2. Nel Finestra Proprietà espandere **DataBindings** e aprire **(Avanzate)**.

     Nella finestra **di dialogo Formattazione e associazione** avanzata scegliere **OnPropertyChanged** in **Modalità di aggiornamento origine** dati .

3. Compilare ed eseguire la soluzione.

     Verificare che quando si modifica il contenuto del campo, la proprietà corrispondente del modello Farm cambia immediatamente.

### <a name="provide-add-buttons"></a>Specificare i pulsanti Aggiungi

1. Nella visualizzazione progettazione di FarmControl.cs usare la casella degli strumenti per creare un pulsante nel form.

    Modificare il nome e il testo del pulsante, ad esempio in `New Sheep` .

2. Aprire il codice dietro il pulsante, ad esempio facendo doppio clic su di esso.

    Modificarlo come segue:

   ```csharp
   private void NewSheepButton_Click(object sender, EventArgs e)
   {
     using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
     {
       elementOperations.MergeElementGroup(farm,
         new ElementGroup(new Sheep(farm.Partition)));
       t.Commit();
     }
   }

   // The following code is shared with other add buttons:
   private ElementOperations operationsCache = null;
   private ElementOperations elementOperations
   {
     get
     {
       if (operationsCache == null)
       {
         operationsCache = new ElementOperations(farm.Store, farm.Partition);
       }
       return operationsCache;
     }
   }
   private Farm farm
   {
     get { return this.farmBindingSource.DataSource as Farm; }
   }
   ```

    Sarà anche necessario inserire la direttiva seguente:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Aggiungere pulsanti simili per Caprini e Campi.

4. Compilare ed eseguire la soluzione.

5. Verificare che il nuovo pulsante a cui è stato aggiunto un elemento. Il nuovo elemento dovrebbe essere visualizzato sia in FarmApp Explorer che nella visualizzazione griglia dei dati appropriata.

    Dovrebbe essere possibile modificare il nome dell'elemento nella visualizzazione Griglia dati. È anche possibile eliminarlo da qui.

   ![Visualizzazione griglia dati di esempio](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Informazioni sul codice per aggiungere un elemento

Per i pulsanti del nuovo elemento, il codice alternativo seguente è leggermente più semplice.

```csharp
private void NewSheepButton_Click(object sender, EventArgs e)
{
  using (Transaction t = farm.Store.TransactionManager.BeginTransaction("Add sheep"))
  {
    farm.Animals.Add(new Sheep(farm.Partition)); ;
    t.Commit();
  }
}
```

Tuttavia, questo codice non imposta un nome predefinito per il nuovo elemento. Non esegue un'unione personalizzata che potrebbe essere  stata definita nelle direttive di unione degli elementi del DSL e non esegue codice di unione personalizzato che potrebbe essere stato definito.

È pertanto consigliabile usare <xref:Microsoft.VisualStudio.Modeling.ElementOperations> per creare nuovi elementi. Per altre informazioni, vedere [Personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Vedi anche

- [Come definire un Domain-Specific lingua](../modeling/how-to-define-a-domain-specific-language.md)
- [Scrivere codice per personalizzare un Domain-Specific lingua](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
