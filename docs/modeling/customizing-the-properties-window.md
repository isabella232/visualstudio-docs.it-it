---
title: Personalizzazione della finestra Proprietà
description: Informazioni su come personalizzare l'aspetto e il comportamento della finestra Proprietà nel linguaggio specifico di dominio (DSL) in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3f7d4ac76b8b10fde0c193e3eda73cec611c1441
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362874"
---
# <a name="customize-the-properties-window"></a>Personalizzare il Finestra Proprietà

È possibile personalizzare l'aspetto e il comportamento della finestra Proprietà nel linguaggio specifico di dominio (DSL) in Visual Studio. Nella definizione DSL è possibile definire le proprietà di dominio per ogni classe di dominio. Per impostazione predefinita, quando si seleziona un'istanza della classe, in un diagramma o in Esplora modelli, ogni proprietà del dominio viene elencata nella finestra Proprietà. In questo modo è possibile visualizzare e modificare i valori delle proprietà di dominio, anche se non sono stati mappati ai campi di forma nel diagramma.

## <a name="names-descriptions-and-categories"></a>Nomi, descrizioni e categorie

**Nome e nome visualizzato**. Nella definizione di una proprietà di dominio, il nome visualizzato della proprietà è il nome che viene visualizzato in fase di esecuzione nella finestra Proprietà. Al contrario, il nome viene usato quando si scrive il codice programma per aggiornare la proprietà. Il nome deve essere un nome di CLR alfanumerico corretto, ma il nome visualizzato può contenere spazi.

Quando si imposta il nome di una proprietà nella definizione DSL, il nome visualizzato viene impostato automaticamente su una copia del nome. Se si scrive un nome con case Pascal, ad esempio "FuelGauge", il nome visualizzato conterrà automaticamente uno spazio: "contatore carburante". Tuttavia, è possibile impostare il nome visualizzato in modo esplicito su un altro valore.

**Descrizione**. La descrizione di una proprietà di dominio viene visualizzata in due posizioni:

- Nella parte inferiore della finestra Proprietà quando l'utente seleziona la proprietà. È possibile usarlo per spiegare all'utente la proprietà rappresentata dalla proprietà.

- Nel codice del programma generato. Se si usano le funzionalità di documentazione per estrarre la documentazione dell'API, questa verrà visualizzata come descrizione della proprietà nell'API.

**Categoria**. Una categoria è un'intestazione nel Finestra Proprietà.

## <a name="expose-style-features"></a>Esporre le funzionalità di stile

Alcune delle funzionalità dinamiche degli elementi grafici possono essere rappresentate o *esposte* come proprietà del dominio. Una funzionalità esposta in questo modo può essere aggiornata dall'utente e può essere aggiornata più facilmente dal codice del programma.

Fare clic con il pulsante destro del mouse su una classe Shape nella definizione DSL, scegliere **Aggiungi esposto**, quindi scegliere una funzionalità.

Nelle forme è possibile esporre le proprietà **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** e **FillGradientMode** . Sui connettori è possibile esporre le proprietà **color** `,` **TextColor**, **DashStyle** e **Thickness** . Nei diagrammi è possibile esporre le proprietà **FillColor** e **TextColor** .

## <a name="forwarding-display-properties-of-related-elements"></a>Inoltring: visualizzare le proprietà degli elementi correlati

Quando l'utente del linguaggio DSL seleziona un elemento in un modello, le proprietà dell'elemento vengono visualizzate nella finestra Proprietà. Tuttavia, è anche possibile visualizzare le proprietà degli elementi correlati specificati. Questa funzione è utile se è stato definito un gruppo di elementi che interagiscono. È ad esempio possibile definire un elemento principale e un elemento plug-in facoltativo. Se l'elemento principale viene mappato a una forma e l'altro non lo è, è utile visualizzare tutte le relative proprietà come se si trovassero in un elemento.

Questo effetto è denominato *inoltring di proprietà* e si verifica automaticamente in diversi casi. In altri casi, è possibile ottenere l'inoltri delle proprietà definendo un descrittore di tipo di dominio.

### <a name="default-property-forwarding-cases"></a>Case di invio proprietà predefinite

Quando l'utente seleziona una forma o un connettore o un elemento nella finestra di esplorazione, nel Finestra Proprietà vengono visualizzate le proprietà seguenti:

- Proprietà del dominio definite nella classe di dominio dell'elemento del modello, incluse quelle definite nelle classi di base. Un'eccezione è rappresentata dalle proprietà del dominio per le quali è stato impostato l'oggetto da **sfogliare** `False` .

- Nomi degli elementi collegati tramite relazioni che hanno una molteplicità pari a 0.. 1. Questo fornisce un metodo pratico per visualizzare gli elementi collegati facoltativamente, anche se non è stato definito un mapping del connettore per la relazione.

- Proprietà di dominio della relazione di incorporamento che ha come destinazione l'elemento. Poiché le relazioni di incorporamento non vengono in genere visualizzate in modo esplicito, ciò consente all'utente di visualizzare le relative proprietà.

- Proprietà del dominio definite nella forma o nel connettore selezionato.

### <a name="add-property-forwarding"></a>Aggiungi inoltri proprietà

Per l'invio di una proprietà, è necessario definire un descrittore del tipo di dominio. Se si dispone di una relazione di dominio tra due classi di dominio, è possibile utilizzare un descrittore del tipo di dominio per impostare una proprietà di dominio nella prima classe sul valore di una proprietà di dominio nella seconda classe di dominio. Se, ad esempio, si dispone di una relazione tra una classe di dominio **book** e una classe di dominio **Author** , è possibile utilizzare un descrittore del tipo di dominio per fare in modo che la proprietà **Name** di un **autore** del libro venga visualizzata nel finestra Proprietà quando l'utente seleziona il libro.

> [!NOTE]
> L'invio di proprietà influiscono solo sul Finestra Proprietà quando l'utente sta modificando un modello. Non definisce una proprietà di dominio per la classe ricevente. Se si desidera accedere alla proprietà del dominio di cui è stato inviato in altre parti della definizione DSL o nel codice del programma, è necessario accedere all'elemento di invio.

Nella procedura seguente si presuppone che sia stato creato un linguaggio DSL. I primi passaggi riepilogano i prerequisiti.

#### <a name="forward-a-property-from-another-element"></a>Inoltri una proprietà da un altro elemento

1. Creare una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione che contenga almeno due classi, che in questo esempio sono denominate **libro** e **autore**. Deve essere presente una relazione di tipo tra **book** e **Author**.

    La molteplicità del ruolo di origine (il ruolo sul lato **libro** ) dovrebbe essere 0.. 1 o 1.. 1, in modo che ogni **libro** abbia un solo **autore**.

2. In **DSL Explorer** fare clic con il pulsante destro del mouse sulla classe di dominio **book** , quindi scegliere **Aggiungi nuovo DomainTypeDescriptor**.

    Un nodo denominato **percorsi di descrittori di proprietà personalizzati** viene visualizzato nel nodo **descrittore di tipo personalizzato** .

3. Fare clic con il pulsante destro del mouse sul nodo **descrittore di tipo personalizzato** , quindi scegliere **Aggiungi nuovo PropertyPath**.

    Viene visualizzato un nuovo percorso proprietà sotto i **percorsi del nodo descrittori di proprietà personalizzati** .

4. Selezionare il nuovo percorso della proprietà e nella finestra **Proprietà** impostare **percorso su Proprietà** sul percorso dell'elemento del modello appropriato.

    È possibile modificare il percorso in una visualizzazione albero facendo clic sulla freccia in giù a destra della proprietà. Per ulteriori informazioni sui percorsi di dominio, vedere [sintassi del percorso di dominio](../modeling/domain-path-syntax.md). Una volta modificato, il percorso dovrebbe essere simile a **BookReferencesAuthor. Author/! Autore**.

5. Impostare **Property** sulla proprietà Domain **Name** di **Author**.

6. Impostare **nome visualizzato** sul **nome dell'autore**.

7. Trasformare tutti i modelli, compilare ed eseguire il linguaggio DSL.

8. In un diagramma del modello creare un libro, un autore e collegarli usando la relazione di riferimento. Selezionare l'elemento book e nella Finestra Proprietà dovrebbe essere visualizzato nome autore oltre alle proprietà del libro. Modificare il nome dell'autore collegato oppure collegare il libro a un altro autore e osservare che il nome dell'autore del libro cambia.

## <a name="custom-property-editors"></a>Editor di proprietà personalizzati

La finestra delle proprietà fornisce un'esperienza di modifica predefinita appropriata per il tipo di ogni proprietà di dominio. Per un tipo enumerato, ad esempio, l'utente visualizza un elenco a discesa e, per una proprietà numerica, l'utente può immettere cifre. Questa operazione è valida solo per i tipi incorporati. Se si specifica un tipo esterno, l'utente sarà in grado di visualizzare i valori della proprietà, ma non di modificarlo.

Tuttavia, è possibile specificare gli editor e i tipi seguenti:

1. Un altro editor utilizzato con un tipo standard. Ad esempio, è possibile specificare un editor di percorsi di file per una proprietà di stringa.

2. Un tipo esterno per la proprietà di dominio e un editor per esso.

3. Un editor .NET, ad esempio l'Editor percorso file, oppure è possibile creare un editor di proprietà personalizzato.

   Una conversione tra un tipo esterno e un tipo, ad esempio String, che include un editor predefinito.

   In un linguaggio DSL, un *tipo esterno* è qualsiasi tipo che non sia uno dei tipi semplici (ad esempio booleano o Int32) o stringa.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Definire una proprietà di dominio con un tipo esterno

1. In **Esplora soluzioni** aggiungere un riferimento all'assembly (dll) che contiene il tipo esterno nel progetto **DSL** .

    L'assembly può essere un assembly .NET o un assembly fornito dall'utente.

2. Aggiungere il tipo all'elenco dei **tipi di dominio** , a meno che non sia già stato fatto.

   1. Aprire DslDefinition. DSL e in **DSL Explorer** fare clic con il pulsante destro del mouse sul nodo radice e quindi scegliere **Aggiungi nuovo tipo esterno**.

        Una nuova voce viene visualizzata sotto il nodo **tipi di dominio** .

       > [!WARNING]
       > La voce di menu si trova sul nodo radice DSL, non sul nodo **tipi di dominio** .

   2. Impostare il nome e lo spazio dei nomi del nuovo tipo nel Finestra Proprietà.

3. Aggiungere una proprietà di dominio a una classe di dominio nel modo consueto.

    Nella Finestra Proprietà selezionare il tipo esterno dall'elenco a discesa nel campo **tipo** .

   In questa fase, gli utenti possono visualizzare i valori della proprietà, ma non modificarli. I valori visualizzati vengono ottenuti dalla `ToString()` funzione. È possibile scrivere il codice programma che imposta il valore della proprietà, ad esempio in un comando o in una regola.

### <a name="set-a-property-editor"></a>Impostare un editor di proprietà

Aggiungere un attributo CLR alla proprietà di dominio, nel formato seguente:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

È possibile impostare l'attributo su una proprietà usando la voce di **attributo personalizzata** nel finestra Proprietà.

Il tipo di `AnEditor` deve essere derivato dal tipo specificato nel secondo parametro. Il secondo parametro deve essere <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.ComponentEditor> . Per altre informazioni, vedere <xref:System.ComponentModel.EditorAttribute>.

È possibile specificare un editor personalizzato o un editor .NET, ad esempio <xref:System.Windows.Forms.Design.FileNameEditor> o <xref:System.Drawing.Design.ImageEditor> . Ad esempio, usare la procedura seguente per avere una proprietà in cui l'utente può immettere un nome file.

#### <a name="define-a-file-name-domain-property"></a>Definire una proprietà del dominio del nome file

1. Aggiungere una proprietà di dominio a una classe di dominio nella definizione DSL.

2. Selezionare la nuova proprietà. Nel campo **attributo personalizzato** della finestra Proprietà immettere l'attributo seguente. Per immettere questo attributo, fare clic sui puntini di sospensione **[...]** , quindi immettere il nome dell'attributo e i parametri separatamente:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Lasciare il tipo della proprietà di dominio con l'impostazione predefinita della **stringa**.

4. Per testare l'editor, verificare che gli utenti possano aprire l'editor del nome file per modificare la proprietà del dominio.

    1. Premere CTRL + F5 o F5. Nella soluzione di debug aprire un file di test. Creare un elemento della classe di dominio e selezionarlo.

    2. Nella Finestra Proprietà selezionare la proprietà di dominio. Il campo del valore Mostra i puntini di sospensione **[...]**.

    3. Fare clic sui puntini di sospensione. Verrà visualizzata una finestra di dialogo file. Selezionare un file e chiudere la finestra di dialogo. Il percorso del file è ora il valore della proprietà di dominio.

### <a name="define-your-own-property-editor"></a>Definire un editor di proprietà personalizzato

È possibile definire un editor personalizzato. Questa operazione può essere eseguita per consentire all'utente di modificare un tipo definito o di modificare un tipo standard in modo speciale. Ad esempio, è possibile consentire all'utente di immettere una stringa che rappresenta una formula.

Per definire un editor, è necessario scrivere una classe derivata da <xref:System.Drawing.Design.UITypeEditor> . La classe deve eseguire l'override di:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, per interagire con l'utente e aggiornare il valore della proprietà.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, per specificare se l'editor apre una finestra di dialogo o fornisce un menu a discesa.

È anche possibile fornire una rappresentazione grafica del valore della proprietà che verrà visualizzato nella griglia delle proprietà. A tale scopo, eseguire l'override di `GetPaintValueSupported` e `PaintValue` .  Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Aggiungere il codice in un file di codice separato nel progetto **DSL** .

Ad esempio:

```csharp
internal class TextFileNameEditor : System.Windows.Forms.Design.FileNameEditor
{
  protected override void InitializeDialog(System.Windows.Forms.OpenFileDialog openFileDialog)
  {
    base.InitializeDialog(openFileDialog);
    openFileDialog.Filter = "Text files(*.txt)|*.txt|All files (*.*)|*.*";
    openFileDialog.Title = "Select a text file";
  }
}
```

Per utilizzare questo editor, impostare l' **attributo personalizzato** di una proprietà di dominio su:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Fornire un elenco a discesa di valori

È possibile specificare un elenco di valori da cui un utente può scegliere.

> [!NOTE]
> Questa tecnica fornisce un elenco di valori che possono cambiare in fase di esecuzione. Se si desidera fornire un elenco che non cambia, considerare invece l'utilizzo di un tipo enumerato come tipo della proprietà del dominio.

Per definire un elenco di valori standard, aggiungere alla proprietà di dominio un attributo CLR con il formato seguente:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Definire una classe che deriva da <xref:System.ComponentModel.TypeConverter>. Aggiungere il codice in un file separato nel progetto **DSL** . Ad esempio:

```csharp
/// <summary>
/// Type converter that provides a list of values
/// to be displayed in the property grid.
/// </summary>
/// <remarks>This type converter returns a list
/// of the names of all "ExampleElements" in the
/// current store.</remarks>
public class MyTypeConverter : System.ComponentModel.TypeConverter
{
  /// <summary>
  /// Return true to indicate that we return a list of values to choose from
  /// </summary>
  /// <param name="context"></param>
  public override bool GetStandardValuesSupported
    (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Returns true to indicate that the user has
  /// to select a value from the list
  /// </summary>
  /// <param name="context"></param>
  /// <returns>If we returned false, the user would
  /// be able to either select a value from
  /// the list or type in a value that is not in the list.</returns>
  public override bool GetStandardValuesExclusive
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    return true;
  }

  /// <summary>
  /// Return a list of the values to display in the grid
  /// </summary>
  /// <param name="context"></param>
  /// <returns>A list of values the user can choose from</returns>
  public override StandardValuesCollection GetStandardValues
      (System.ComponentModel.ITypeDescriptorContext context)
  {
    // Try to get a store from the current context
    // "context.Instance"  returns the element(s) that
    // are currently selected i.e. whose values are being
    // shown in the property grid.
    // Note that the user could have selected multiple objects,
    // in which case context.Instance will be an array.
    Store store = GetStore(context.Instance);

    List<string> values = new List<string>();

    if (store != null)
    {
      values.AddRange(store.ElementDirectory
        .FindElements<ExampleElement>()
        .Select<ExampleElement, string>(e =>
      {
        return e.Name;
      }));
    }
    return new StandardValuesCollection(values);
  }

  /// <summary>
  /// Attempts to get to a store from the currently selected object(s)
  /// in the property grid.
  /// </summary>
  private Store GetStore(object gridSelection)
  {
    // We assume that "instance" will either be a single model element, or
    // an array of model elements (if multiple items are selected).

    ModelElement currentElement = null;

    object[] objects = gridSelection as object[];
    if (objects != null && objects.Length > 0)
    {
      currentElement = objects[0] as ModelElement;
    }
    else
    {
        currentElement = gridSelection as ModelElement;
    }

    return (currentElement == null) ? null : currentElement.Store;
  }

}
```

## <a name="see-also"></a>Vedere anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
