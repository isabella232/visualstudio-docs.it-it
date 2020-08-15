---
title: Creazione di un linguaggio specifico di dominio basato su Windows Form
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c52b3bd352c2ecb2272ad8e229a0fe52a9ee5b41
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238361"
---
# <a name="create-a-windows-forms-based-domain-specific-language"></a>Creare un Domain-Specific Language basato su Windows Forms

È possibile utilizzare Windows Forms per visualizzare lo stato di un modello di linguaggio specifico di dominio (DSL), anziché utilizzare un diagramma DSL. In questo argomento viene illustrata l'associazione di un Windows Form a un linguaggio DSL mediante l'SDK di visualizzazione e modellazione di Visual Studio.

La figura seguente mostra un'interfaccia utente di Windows Form e Esplora modelli per un'istanza DSL:

![Istanza DSL in Visual Studio](../modeling/media/dsl-wpf-2.png)

## <a name="create-a-windows-forms-dsl"></a>Creare un Windows Forms DSL

Il modello DSL **WinForm designer minimo** crea un DSL minimo che è possibile modificare in base alle proprie esigenze.

1. Creare un linguaggio DSL dal modello **minimo di Winform designer** .

    In questa procedura dettagliata vengono considerati i nomi seguenti:

    - Nome della soluzione e del DSL: `FarmApp`
    - Namespace `Company.FarmApp`

2. Provare a usare l'esempio iniziale fornito dal modello:

   1. Trasforma tutti i modelli.

   2. Compilare ed eseguire l'esempio (**CTRL** + **F5**).

   3. Nell'istanza sperimentale di Visual Studio aprire il `Sample` file nel progetto di debug.

        Si noti che viene visualizzato in un controllo Windows Forms.

        È inoltre possibile visualizzare gli elementi del modello visualizzati nella finestra di esplorazione.

        Aggiungere alcuni elementi nel form o nella finestra di esplorazione e notare che vengono visualizzati nell'altra visualizzazione.

   Nell'istanza principale di Visual Studio si notino i punti seguenti sulla soluzione DSL:

- `DslDefinition.dsl` non contiene elementi del diagramma. Ciò è dovuto al fatto che non si utilizzeranno diagrammi DSL per visualizzare i modelli di istanza di questo DSL. Al contrario, si eseguirà il binding di un Windows Form al modello e gli elementi nel form visualizzeranno il modello.

- Oltre ai `Dsl` `DslPackage` progetti e, la soluzione contiene un terzo progetto denominato `UI.` **UI** Project contiene la definizione di un controllo Windows Forms. `DslPackage` dipende da `UI` e dipende da `UI` `Dsl` .

- Nel `DslPackage` progetto, `UI\DocView.cs` contiene il codice che visualizza il Windows Forms controllo definito nel `UI` progetto.

- Il `UI` progetto contiene un esempio funzionante di un controllo Form associato al linguaggio DSL. Tuttavia, non funzionerà dopo aver modificato la definizione DSL. Il `UI` progetto contiene:

  - Classe Windows Forms denominata `ModelViewControl` .

  - File denominato `DataBinding.cs` che contiene una definizione parziale aggiuntiva di `ModelViewControl` . Per visualizzarne il contenuto, in **Esplora soluzioni**aprire il menu di scelta rapida per il file e scegliere **Visualizza codice**.

### <a name="about-the-ui-project"></a>Informazioni sul progetto dell'interfaccia utente

Quando si aggiorna il file di definizione DSL per definire il proprio linguaggio DSL, sarà necessario aggiornare il controllo nel `UI` progetto per visualizzare il linguaggio DSL. A differenza dei `Dsl` `DslPackage` progetti e, il `UI` progetto di esempio non viene generato da `DslDefinitionl.dsl` . Se lo si desidera, è possibile aggiungere file con estensione tt per generare il codice, anche se questo non è trattato in questa procedura dettagliata.

## <a name="update-the-dsl-definition"></a>Aggiornare la definizione DSL

In questa procedura dettagliata viene usata la definizione DSL riportata di seguito.

![DSL&#45;WPF&#45;1](../modeling/media/dsl-wpf-1.png)

1. Aprire DslDefinition. DSL nella finestra di progettazione DSL.

2. Elimina **esempioelement**

3. Rinominare la classe di dominio **ExampleModel** in `Farm` .

     Assegnare a esso proprietà del dominio aggiuntive denominate `Size` di tipo **Int32**e `IsOrganic` di tipo **booleano**.

    > [!NOTE]
    > Se si elimina la classe di dominio radice e quindi si crea una nuova radice, sarà necessario reimpostare la proprietà della classe radice dell'editor. In **DSL Explorer**selezionare **Editor**. Quindi, nella Finestra Proprietà impostare la **classe radice** su `Farm` .

4. Utilizzare lo strumento **classe di dominio denominato** per creare le classi di dominio seguenti:

    - `Field` -Assegnare a questa proprietà di dominio aggiuntiva denominata `Size` .

    - `Animal` -Nella Finestra Proprietà impostare il **modificatore di ereditarietà** su **abstract**.

5. Utilizzare lo strumento **classe di dominio** per creare le classi seguenti:

    - `Sheep`

    - `Goat`

6. Utilizzare lo strumento **ereditarietà** per creare `Goat` ed `Sheep` ereditare da `Animal` .

7. Usare lo strumento di **incorporamento** per incorporare `Field` e `Animal` in `Farm` .

8. Potrebbe essere necessario ordinare il diagramma. Per ridurre il numero di elementi duplicati, usare il comando **Bring subtree qui** dal menu di scelta rapida degli elementi foglia.

9. **Trasforma tutti i modelli** nella barra degli strumenti di Esplora soluzioni.

10. Compilare il progetto **DSL** .

    > [!NOTE]
    > In questa fase, gli altri progetti non vengono compilati senza errori. Tuttavia, si vuole compilare il progetto DSL in modo che il relativo assembly sia disponibile per la creazione guidata origine dati.

## <a name="update-the-ui-project"></a>Aggiornare il progetto dell'interfaccia utente

A questo punto è possibile creare un nuovo controllo utente che visualizzerà le informazioni archiviate nel modello DSL. Il modo più semplice per connettere il controllo utente al modello è tramite associazioni dati. Il tipo di adattatore data binding denominato **ModelingBindingSource** è progettato specificamente per connettere DSLs a interfacce non VMSDK.

### <a name="define-your-dsl-model-as-a-data-source"></a>Definire il modello DSL come origine dati

1. Scegliere **Mostra origini dati**dal menu **dati** .

     Verrà visualizzata la finestra **Origini dati**.

     Scegliere **Aggiungi nuova origine dati**. Verrà avviata la **Configurazione guidata origine dati** .

2. Scegliere **oggetto**, **Avanti**.

     Espandere **DSL**, **Company. FarmApp**e selezionare **Farm**, ovvero la classe radice del modello. Scegliere **Fine**.

     In Esplora soluzioni il progetto dell' **interfaccia utente** contiene ora **Properties\DataSources\Farm.DataSource**

     Le proprietà e le relazioni della classe del modello vengono visualizzate nella finestra Origini dati.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

### <a name="connect-your-model-to-a-form"></a>Connettere il modello a un modulo

1. Nel progetto dell' **interfaccia utente** eliminare tutti i file con estensione CS esistenti.

2. Aggiungere un nuovo file di **controllo utente** denominato `FarmControl` al progetto dell' **interfaccia utente** .

3. Nella finestra **origini dati** fare clic su **Dettagli**nel menu a discesa della **Farm**.

    Lasciare le impostazioni predefinite per le altre proprietà.

4. Aprire FarmControl.cs nella visualizzazione progettazione.

    Trascinare **Farm** dalla finestra Origini dati in FarmControl.

    Viene visualizzato un set di controlli, uno per ogni proprietà. Le proprietà della relazione non generano controlli.

5. Elimina **farmBindingNavigator**. Viene anche generato automaticamente nella finestra di `FarmControl` progettazione, ma non è utile per questa applicazione.

6. Utilizzando la casella degli strumenti, creare due istanze di **DataGridView**e denominarle `AnimalGridView` e `FieldGridView` .

   > [!NOTE]
   > Un passaggio alternativo consiste nel trascinare gli elementi Animals e Fields dalla finestra Origini dati nel controllo. Questa azione crea automaticamente le griglie di dati e le associazioni tra la visualizzazione griglia e l'origine dati. Tuttavia, questa associazione non funziona correttamente per DSLs. Pertanto, è preferibile creare manualmente le griglie di dati e le associazioni.

7. Se la casella degli strumenti non contiene lo strumento **ModelingBindingSource** , aggiungerla. Nel menu di scelta rapida della scheda **dati** scegliere **Scegli elementi**. Nella finestra di dialogo **Scegli elementi della casella degli strumenti** selezionare **ModelingBindingSource** nella scheda **.NET Framework** .

8. Utilizzando la casella degli strumenti, creare due istanze di **ModelingBindingSource**e denominarle `AnimalBinding` e `FieldBinding` .

9. Impostare la proprietà **DataSource** di ogni **ModelingBindingSource** su **farmBindingSource**.

     Impostare la proprietà **DataMember** su **Animals** o **Fields**.

10. Impostare le proprietà **DataSource** di `AnimalGridView` su `AnimalBinding` e di  `FieldGridView` su `FieldBinding` .

11. Modificare il layout del controllo della farm a piacimento.

    **ModelingBindingSource** è un adapter che esegue diverse funzioni specifiche di DSLs:

- Esegue il wrapping degli aggiornamenti in una transazione di archivio VMSDK.

   Ad esempio, quando l'utente elimina una riga dalla griglia della visualizzazione dati, un'associazione regolare genera un'eccezione di transazione.

- Garantisce che, quando l'utente seleziona una riga, il Finestra Proprietà Visualizza le proprietà dell'elemento del modello corrispondente, invece della riga della griglia dei dati.

  ![](../modeling/media/dslwpf4.png)Schema DslWpf4 dei collegamenti tra le origini dati e le visualizzazioni.

### <a name="complete-the-bindings-to-the-dsl"></a>Completare le associazioni al linguaggio DSL

1. Aggiungere il codice seguente in un file di codice separato nel progetto **dell'interfaccia utente** :

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

2. Nel progetto **DslPackage** modificare **DslPackage\DocView.TT** per aggiornare la definizione di variabile seguente:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="test-the-dsl"></a>Testare il linguaggio DSL

La soluzione DSL ora può essere compilata ed eseguita, anche se è opportuno aggiungere ulteriori miglioramenti in un secondo momento.

1. Compilare ed eseguire la soluzione.

2. Nell'istanza sperimentale di Visual Studio aprire il file di **esempio** .

3. In **FarmApp Explorer**aprire il menu di scelta rapida nel nodo radice della **Farm** e scegliere **Aggiungi nuova capra**.

     `Goat1` viene visualizzato nella visualizzazione **Animals** .

    > [!WARNING]
    > È necessario utilizzare il menu di scelta rapida del nodo della **Farm** , non il nodo **Animals** .

4. Selezionare il nodo radice della **Farm** e visualizzarne le proprietà.

     Nella visualizzazione Form modificare il **nome** o le **dimensioni** della farm.

     Quando si esce da ogni campo nel form, la proprietà corrispondente viene modificata nella Finestra Proprietà.

## <a name="enhance-the-dsl"></a>Migliorare il linguaggio DSL

### <a name="make-the-properties-update-immediately"></a>Aggiornare immediatamente le proprietà

1. Nella visualizzazione progettazione di FarmControl.cs selezionare un campo semplice, ad esempio nome, dimensioni o organico.

2. Nella Finestra Proprietà espandere **DataBindings** e aprire **(avanzate)**.

     Nella finestra di dialogo **formattazione e associazione avanzata** , in **modalità di aggiornamento origine dati**, scegliere **OnPropertyChanged**.

3. Compilare ed eseguire la soluzione.

     Verificare che, quando si modifica il contenuto del campo, la proprietà corrispondente del modello della farm venga modificata immediatamente.

### <a name="provide-add-buttons"></a>Specificare i pulsanti Aggiungi

1. Nella visualizzazione progettazione di FarmControl.cs utilizzare la casella degli strumenti per creare un pulsante nel form.

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

    Sarà inoltre necessario inserire la direttiva seguente:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Aggiungere pulsanti simili per capre e campi.

4. Compilare ed eseguire la soluzione.

5. Verificare che il pulsante nuovo aggiunga un elemento. Il nuovo elemento verrà visualizzato in FarmApp Explorer e nella visualizzazione griglia dati appropriata.

    Dovrebbe essere possibile modificare il nome dell'elemento nella visualizzazione griglia dei dati. È anche possibile eliminarlo da questa posizione.

   ![DSL&#45;WPF&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Informazioni sul codice per l'aggiunta di un elemento

Per i pulsanti nuovo elemento, il codice alternativo seguente è leggermente più semplice.

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

Tuttavia, questo codice non imposta un nome predefinito per il nuovo elemento. Non esegue alcun merge personalizzato che potrebbe essere stato definito nelle **direttive di Unione degli elementi** del linguaggio DSL e non esegue alcun codice di merge personalizzato che potrebbe essere stato definito.

È quindi consigliabile usare <xref:Microsoft.VisualStudio.Modeling.ElementOperations> per creare nuovi elementi. Per altre informazioni, vedere [personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Vedere anche

- [Come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md)
- [Scrivere codice per personalizzare un Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)
