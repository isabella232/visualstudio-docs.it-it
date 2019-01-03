---
title: Creazione di un linguaggio specifico di dominio basato su Windows Form
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 75c50780a8ad48fdd4766576e3d6fe94a580b777
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53869927"
---
# <a name="creating-a-windows-forms-based-domain-specific-language"></a>Creazione di un linguaggio specifico di dominio basato su Windows Form
È possibile usare Windows Form per visualizzare lo stato di un modello di linguaggio specifico di dominio (DSL), invece di usare un diagramma DSL. In questo argomento illustra l'associazione di un Windows Form a un linguaggio DSL, utilizzando la visualizzazione e Visual Studio SDK di modellazione.

 ![Linguaggio specifico di dominio&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png) istanza di un DSL, che mostra un'interfaccia utente Form di Windows ed Esplora modelli.

## <a name="creating-a-windows-forms-dsl"></a>Creazione di un controllo Windows Form DSL
 Il **Progettazione Windows Form minimo** modello DSL consente di creare un DSL minimo che è possibile modificare in base alle proprie esigenze.

#### <a name="to-create-a-minimal-winforms-dsl"></a>Per creare un DSL WinForms minimo

1. Creare un DSL dal **Progettazione Windows Form minimo** modello.

    In questa procedura dettagliata, si presuppone che i nomi seguenti:


   | | |
   |-|-|
   | Nome di soluzione e DSL | FarmApp |
   | Spazio dei nomi | Company.FarmApp |


2. Provare a usare l'esempio iniziale forniti dal modello:

   1.  Trasforma tutti i modelli.

   2.  Compilare ed eseguire il codice di esempio (**CTRL+F5**).

   3.  Nell'istanza sperimentale di Visual Studio, aprire il `Sample` file nel progetto di debug.

        Si noti che viene visualizzato in un controllo Windows Form.

        È anche possibile visualizzare gli elementi del modello visualizzato nella finestra di esplorazione.

        Aggiungere alcuni elementi nel form o finestra di esplorazione e notare che vengono visualizzati nella sezione delle altre opzioni.

   Nell'istanza principale di Visual Studio, si noti che i punti seguenti circa soluzione DSL:

-   `DslDefinition.dsl` non contiene alcun elemento diagramma. Questo avviene perché non si utilizzerà i diagrammi DSL per visualizzare i modelli di istanza di questo DSL. Al contrario, si assocerà un Form Windows al modello e gli elementi nel form verranno visualizzato il modello.

-   Oltre al `Dsl` e `DslPackage` progetti, la soluzione contiene un terzo progetto denominato `UI.` **UI** progetto contiene la definizione di un controllo Windows Form. `DslPackage` dipende `UI`, e `UI` dipende `Dsl`.

-   Nel `DslPackage` progetto `UI\DocView.cs` contiene il codice che visualizza il controllo Windows Form che è definito nel `UI` progetto.

-   Il `UI` progetto contiene un esempio reale di un controllo modulo associato per il linguaggio DSL. Tuttavia, non funzionerà dopo avere modificato la definizione DSL. Il `UI` progetto contiene:

    -   Una classe di Windows Form denominata `ModelViewControl`.

    -   Un file denominato `DataBinding.cs` che contiene una definizione parziale aggiuntiva di `ModelViewControl`. Per visualizzare il contenuto, in **Esplora soluzioni**, aprire il menu di scelta rapida per il file e scegliere **Visualizza codice**.

### <a name="about-the-ui-project"></a>Sul progetto dell'interfaccia utente
 Quando si aggiorna il file di definizione DSL per definire il proprio DSL, è necessario aggiornare il controllo nel `UI` progetto per visualizzare il linguaggio DSL. A differenza di `Dsl` e `DslPackage` progetti, il codice di esempio `UI` progetto non viene generato da `DslDefinitionl.dsl`. È possibile aggiungere i file con estensione tt per generare il codice se si desidera, sebbene questa procedura non è descritta in questa procedura dettagliata.

## <a name="updating-the-dsl-definition"></a>L'aggiornamento della definizione DSL
 Nell'esempio di che definizione DSL viene usata in questa procedura dettagliata.

 ![Linguaggio specifico di dominio&#45;Wpf&#45;1](../modeling/media/dsl-wpf-1.png)

#### <a name="to-update-the-dsl-definition"></a>Per aggiornare la definizione DSL

1.  Aprire dsldefinition. DSL nella finestra di progettazione DSL.

2.  Elimina **ExampleElement**

3.  Rinominare il **ExampleModel** della classe di dominio per `Farm`.

     Assegnare le proprietà di dominio aggiuntivo denominate `Size` typu **Int32**, e `IsOrganic` di tipo **booleano**.

    > [!NOTE]
    >  Se si elimina la classe di dominio radice e quindi creare una nuova radice, sarà necessario reimpostare la proprietà di classe radice dell'Editor. Nelle **DSL Explorer**, selezionare **Editor**. Quindi, nella finestra Proprietà impostare **classe radice** a `Farm`.

4.  Usare la **della classe di dominio denominato** lo strumento per creare le classi di dominio seguenti:

    -   `Field` -Impostarne una proprietà di dominio aggiuntivo denominata `Size`.

    -   `Animal` -Nella finestra Proprietà impostare **modificatore di ereditarietà** al **astratta**.

5.  Usare la **della classe di dominio** lo strumento per creare le classi seguenti:

    -   `Sheep`

    -   `Goat`

6.  Usare la **ereditarietà** dello strumento per rendere `Goat` e `Sheep` ereditare `Animal`.

7.  Usare la **incorporamento** dello strumento per incorporare `Field` e `Animal` sotto `Farm`.

8.  È possibile ordinare il diagramma. Per ridurre il numero di elementi duplicati, usare il **portare sottoalbero qui** dal menu di scelta rapida di elementi foglia.

9. **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni.

10. Compilare il **Dsl** progetto.

    > [!NOTE]
    >  In questa fase, gli altri progetti non verranno compilato senza errori. Tuttavia, si vuole compilare il progetto Dsl in modo che l'assembly è disponibile per la creazione guidata origine dati.

## <a name="updating-the-ui-project"></a>L'aggiornamento del progetto dell'interfaccia utente
 A questo punto è possibile creare un nuovo controllo utente che verrà visualizzate le informazioni che viene archiviate nel modello DSL. Il modo più semplice per connettere il controllo utente per il modello è tramite le associazioni dati. Il data binding di tipo di adattatore denominato **ModelingBindingSource** è progettato specificamente per la connessione di linguaggi specifici di dominio per le interfacce non VMSDK.

#### <a name="to-define-your-dsl-model-as-a-data-source"></a>Per definire il modello DSL come origine dati

1.  Nel **Data** menu, scegliere **Mostra origini dati**.

     Verrà visualizzata la finestra **Origini dati**.

     Scegli **Aggiungi nuova origine dati**. Viene avviata la **Configurazione guidata origine dati**.

2.  Scegli **oggetti**, **successivo**.

     Espandere **Dsl**, **Company.FarmApp**e selezionare **Farm**, che è la classe radice del modello. Scegliere **Fine**.

     In Esplora soluzioni, il **UI** progetto contiene ora **Properties\DataSources\Farm.datasource**

     Le proprietà e relazioni della classe modello vengono visualizzati nella finestra Origini dei dati.

     ![DslWpf&#45;3](../modeling/media/dslwpf-3.png)

#### <a name="to-connect-your-model-to-a-form"></a>Per connettere il modello a un form

1. Nel **dell'interfaccia utente** progetto, eliminare tutti i file con estensione cs esistente.

2. Aggiungere un nuovo **UserControl** file denominato `FarmControl` per il **dell'interfaccia utente** progetto.

3. Nel **Zdroje dat** finestra, nel menu a discesa **Farm**, scegliere **dettagli**.

    Lasciare le impostazioni predefinite per le altre proprietà.

4. Aprire FarmControl.cs nella visualizzazione progettazione.

    Trascinare **Farm** dalla finestra Origini dati FarmControl.

    Un set di controlli viene visualizzata, una per ogni proprietà. Le proprietà della relazione non generano controlli.

5. Eliminare **farmBindingNavigator**. Viene generato anche automaticamente nel `FarmControl` progettazione, ma non è utile per questa applicazione.

6. Usando la casella degli strumenti, creare due istanze di **DataGridView**e denominarli `AnimalGridView` e `FieldGridView`.

   > [!NOTE]
   >  Un'alternativa consiste nel trascinare gli elementi di animali e campi dalla finestra Origini dati nel controllo. Questa azione crea automaticamente le griglie dei dati e le associazioni tra la visualizzazione griglia e l'origine dati. Tuttavia, questa associazione non funziona correttamente per linguaggi specifici di dominio. Pertanto è preferibile creare le griglie dei dati e le associazioni manualmente.

7. Se la casella degli strumenti non contiene il **ModelingBindingSource** dello strumento, aggiungerlo. Menu di scelta rapida del **Data** scheda, scegliere **Scegli elementi**. Nel **Scegli elementi della casella degli strumenti** finestra di dialogo, seleziona **ModelingBindingSource** dal **scheda Framework .NET**.

8. Usando la casella degli strumenti, creare due istanze di **ModelingBindingSource**e denominarli `AnimalBinding` e `FieldBinding`.

9. Impostare il **DataSource** proprietà di ciascuno **ModelingBindingSource** al **farmBindingSource**.

     Impostare il **DataMember** proprietà **animali** oppure **campi**.

10. Impostare il **DataSource** proprietà di `AnimalGridView` al `AnimalBinding`e di `FieldGridView` per `FieldBinding`.

11. Modificare il layout del controllo Farm a piacimento.

    Il **ModelingBindingSource** è un adattatore che esegue diverse funzioni che sono specifiche per linguaggi specifici di dominio:

- Esegue il wrapping degli aggiornamenti in una transazione di Store VMSDK.

   Ad esempio, quando l'utente elimina una riga nella griglia di visualizzazione dei dati, un'associazione regolare comporta un'eccezione di transazione.

- Assicura che, quando l'utente seleziona una riga, la finestra proprietà vengono visualizzate le proprietà dell'elemento del modello corrispondente, anziché sulla riga della griglia di dati.

  ![DslWpf4](../modeling/media/dslwpf4.png) dello Schema dei collegamenti tra le origini dati e viste.

#### <a name="to-complete-the-bindings-to-the-dsl"></a>Per completare le associazioni per il linguaggio DSL

1.  Aggiungere il codice seguente in un file di codice separato nella **dell'interfaccia utente** progetto:

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

2.  Nel **DslPackage** del progetto, modificare **DslPackage\DocView.tt** per aggiornare la definizione di variabile seguente:

    ```csharp
    string viewControlTypeName = "FarmControl";
    ```

## <a name="testing-the-dsl"></a>Il linguaggio DSL di test
 La soluzione di linguaggio specifico di dominio può ora compila ed Esegui, anche se è possibile aggiungere altri miglioramenti in un secondo momento.

#### <a name="to-test-the-dsl"></a>Per testare il linguaggio DSL

1.  Compilare ed eseguire la soluzione.

2.  Nell'istanza sperimentale di Visual Studio, aprire il **esempio** file.

3.  Nel **FarmApp Explorer**, aprire il menu di scelta rapida nel **Farm** nodo radice, quindi scegliere **aggiungere nuovo Goat**.

     `Goat1` viene visualizzato nei **animali** visualizzazione.

    > [!WARNING]
    >  È necessario usare il menu di scelta rapida nel **Farm** nodo, non il **animali** nodo.

4.  Selezionare il **Farm** nodo radice e visualizzarne le proprietà.

     Nella visualizzazione form, modificare il **Name** oppure **dimensioni** della farm.

     Quando si esce ogni campo nel form, le modifiche alle proprietà corrispondenti nella finestra Proprietà.

## <a name="enhancing-the-dsl"></a>Miglioramento del DSL

#### <a name="to-make-the-properties-update-immediately"></a>Per rendere le proprietà di aggiornamento immediato

1.  Nella visualizzazione progettazione di FarmControl.cs, selezionare un campo semplice, ad esempio nome, dimensioni o IsOrganic.

2.  Nella finestra Proprietà, espandere **DataBindings** e aprire **(avanzate)**.

     Nel **formattazione e associazione avanzata** finestra di dialogo, sotto **modalità aggiornamento origine dati**, scegliere **OnPropertyChanged**.

3.  Compilare ed eseguire la soluzione.

     Verificare che quando si modifica il contenuto del campo, la proprietà corrispondente di immediatamente la modifica del modello Farm.

#### <a name="to-provide-add-buttons"></a>Per fornire pulsanti Aggiungi

1. Nella visualizzazione progettazione di FarmControl.cs, usare la casella degli strumenti per creare un pulsante nel form.

    Modificare il nome e il testo del pulsante, ad esempio a `New Sheep`.

2. Aprire il codice dietro il pulsante (ad esempio facendovi doppio).

    Modificare come indicato di seguito:

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

    È necessario anche inserire la direttiva seguente:

   ```csharp

   using Microsoft.VisualStudio.Modeling;
   ```

3. Aggiungere pulsanti simile per caprini e i campi.

4. Compilare ed eseguire la soluzione.

5. Verificare che il nuovo pulsante Aggiunge un elemento. Il nuovo elemento deve essere visualizzato in entrambe le soluzioni FarmApp o nella visualizzazione griglia dei dati appropriati.

    Dovrebbe essere possibile modificare il nome dell'elemento nella visualizzazione griglia dei dati. È anche possibile eliminarlo da tale posizione.

   ![Linguaggio specifico di dominio&#45;Wpf&#45;2](../modeling/media/dsl-wpf-2.png)

### <a name="about-the-code-to-add-an-element"></a>Informazioni sul codice per aggiungere un elemento
 Per i pulsanti del nuovo elemento, il seguente codice alternativo è leggermente più semplice.

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

 Tuttavia, questo codice non impostare un nome predefinito per il nuovo elemento. Non può essere eseguito alcun merge personalizzato che è stata definita nel **direttive di unione elementi** del linguaggio DSL, e non può essere eseguito qualsiasi codice personalizzato di tipo merge che potrebbe essere stato definito.

 Pertanto è consigliabile usare <xref:Microsoft.VisualStudio.Modeling.ElementOperations> per creare nuovi elementi. Per altre informazioni, vedere [spostamento e la creazione degli elementi di personalizzazione](../modeling/customizing-element-creation-and-movement.md).

## <a name="see-also"></a>Vedere anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)