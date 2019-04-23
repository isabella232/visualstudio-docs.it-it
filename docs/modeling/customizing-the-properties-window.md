---
title: Personalizzazione della finestra Proprietà
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d053bcd5e8b1824334f9953ac14881fdc0315be
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083336"
---
# <a name="customizing-the-properties-window"></a>Personalizzazione della finestra Proprietà
Nel linguaggio specifico di dominio (DSL) in Visual Studio, è possibile personalizzare l'aspetto e il comportamento della finestra Proprietà. Nella definizione DSL, si definiscono le proprietà di dominio in ogni classe di dominio. Per impostazione predefinita, quando si seleziona un'istanza della classe, in un diagramma o in Esplora modelli, ogni proprietà di dominio è elencato nella finestra Proprietà. Ciò consente di visualizzare e modificare i valori delle proprietà di dominio, anche se non li mappata a campi della forma nel diagramma.

## <a name="names-descriptions-and-categories"></a>I nomi, descrizioni e le categorie
 **Nome e il nome visualizzato**. Nella definizione di una proprietà di dominio, il nome visualizzato della proprietà è il nome visualizzato in fase di esecuzione nella finestra Proprietà. Al contrario, il nome viene usato quando si scrive codice programma per aggiornare la proprietà. Il nome deve essere un nome alfanumerico CLR corretto, ma il nome visualizzato può contenere spazi.

 Quando si imposta il nome di una proprietà nella definizione DSL, il nome visualizzato è automaticamente impostato su una copia del nome. Se si scrive un nome di maiuscole e minuscole Pascal, ad esempio "FuelGauge", il nome visualizzato includerà automaticamente uno spazio: "Indicatore del carburante". Tuttavia, è possibile impostare il nome visualizzato in modo esplicito a un altro valore.

 **Descrizione**. La descrizione della proprietà del dominio viene visualizzato in due posizioni:

- Nella parte inferiore della finestra Proprietà quando l'utente seleziona la proprietà. È possibile usarlo per spiegare all'utente ciò che rappresenta la proprietà.

- Nel codice di programma generato. Se si usano le funzionalità per la documentazione per estrarre la documentazione dell'API, verrà visualizzato come la descrizione di questa proprietà nell'API.

  **Categoria**. Una categoria è un'intestazione nella finestra Proprietà.

## <a name="exposing-style-features"></a>Esporre le caratteristiche di stile
 Alcune delle funzionalità dinamica degli elementi grafici possono essere rappresentati o *esposti* come proprietà di dominio. Una funzionalità che è stato esposto in questo modo può essere aggiornata dall'utente e possono più essere facilmente aggiornate dal codice programma.

 Fare doppio clic su una classe di forma nella definizione DSL, scegliere **Aggiungi esposta**, quindi scegliere una funzionalità.

 Sulle forme è possibile esporre il **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**,  **OutlineThickness** e **FillGradientMode** proprietà. Informazioni sui connettori, è possibile esporre il **colore**`,`**TextColor**, **DashStyle**, e **spessore** proprietà. Nei diagrammi, è possibile esporre il **FillColor** e **TextColor** proprietà.

## <a name="forwarding-displaying-properties-of-related-elements"></a>Inoltro: Visualizzazione delle proprietà degli elementi correlati
 Quando l'utente del linguaggio DSL seleziona un elemento in un modello, le proprietà dell'elemento vengono visualizzate nella finestra Proprietà. Tuttavia, è inoltre possibile visualizzare le proprietà degli elementi correlati specificati. Ciò è utile se è stato definito un gruppo di elementi che lavorano in combinazione. Ad esempio, è possibile definire un principale e un elemento facoltativo del plug-in. Se l'elemento principale viene eseguito il mapping a una forma e l'altro non lo è, è utile visualizzare tutte le relative proprietà come se fossero per un solo elemento.

 Questo effetto è denominato *inoltro proprietà*, e ciò avviene automaticamente in molte situazioni. In altri casi, è possibile ottenere proprietà di inoltro mediante la definizione di un descrittore di tipi di dominio.

### <a name="default-property-forwarding-cases"></a>Casi di inoltro di proprietà predefiniti
 Quando l'utente seleziona una forma o connettore o da un elemento in Esplora risorse, le proprietà seguenti vengono visualizzate nella finestra Proprietà:

- Le proprietà di dominio definite nella classe di dominio dell'elemento del modello, inclusi quelli che sono definiti nelle classi di base. Un'eccezione riguarda le proprietà di dominio per cui è stato impostato **è visualizzabile** a `False`.

- I nomi degli elementi collegati tramite relazioni che hanno una molteplicità di 0..1. Fornisce un metodo pratico per visualizzare, facoltativamente, collegata elementi, anche se non è stato definito un mapping di connettori per la relazione.

- Proprietà di dominio della relazione di incorporamento che ha come destinazione l'elemento. Poiché le relazioni di incorporamento in genere non vengono visualizzate in modo esplicito, ciò consente all'utente di visualizzare le relative proprietà.

- Proprietà di dominio definite nella forma selezionata o il connettore.

### <a name="adding-property-forwarding"></a>Aggiunta di inoltro di proprietà
 Per inoltrare una proprietà, si definisce un descrittore di tipi di dominio. Se si dispone di una relazione di dominio tra due classi di dominio, è possibile utilizzare un descrittore di tipi di dominio per impostare una proprietà di dominio nella prima classe per il valore della proprietà del dominio nella classe di dominio di secondo. Ad esempio, se si dispone di una relazione tra un **libro** della classe di dominio e un **autore** della classe di dominio, è possibile usare un descrittore di tipi di dominio per rendere il **nome** proprietà di un Del libro **autore** vengono visualizzate nella finestra Proprietà quando l'utente seleziona il libro.

> [!NOTE]
>  L'inoltro di proprietà interessa solo la finestra Proprietà quando l'utente modifica un modello. Non definisce una proprietà di dominio nella classe ricevente. Se si vuole accedere alla proprietà di dominio inoltrati in altre parti della definizione del linguaggio specifico di dominio o nel codice programma, è necessario accedere all'elemento di inoltro.

 La procedura seguente si presuppone che sia stato creato un modello DSL. I primi passaggi riepilogano i prerequisiti.

##### <a name="to-forward-a-property-from-another-element"></a>Per inoltrare una proprietà da un altro elemento

1. Creare un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione che contiene almeno due classi, che in questo esempio vengono chiamate **libro** e **autore**. Deve essere presente una relazione di entrambi i tipi tra **libro** e **autore**.

    La molteplicità del ruolo di origine (il ruolo del **libro** lato) deve essere 0..1 1 o 1, in modo che ogni **libro** presenta uno **autore**.

2. In **DSL Explorer**, fare doppio clic il **libro** della classe di dominio e quindi fare clic su **aggiungere nuovo DomainTypeDescriptor**.

    Un nodo denominato **percorsi di descrittori di proprietà personalizzate** viene visualizzata sotto il **descrittore di tipo personalizzato** nodo.

3. Fare doppio clic il **descrittore di tipo personalizzato** nodo e quindi fare clic su **aggiungere nuovo PropertyPath**.

    Un nuovo percorso della proprietà viene visualizzata sotto il **percorsi di descrittori di proprietà personalizzato** nodo.

4. Selezionare il nuovo percorso della proprietà e il **proprietà** impostare nella finestra **percorso proprietà** al percorso dell'elemento del modello appropriato.

    È possibile modificare il percorso in una visualizzazione albero, fare clic sulla freccia in giù a destra di questa proprietà. Per altre informazioni sui percorsi di dominio, vedere [sintassi del percorso di dominio](../modeling/domain-path-syntax.md). Quando è stato modificato, il percorso dovrebbe essere simile **BookReferencesAuthor.Author/! Autore**.

5. Impostare **proprietà** per il **Name** proprietà del dominio **autore**.

6. Impostare **NomeVisualizzato** al **autore nome**.

7. Trasforma tutti i modelli, compilare ed eseguire il linguaggio DSL.

8. In un diagramma del modello, creare un libro, un autore e collegarle usando la relazione di riferimento. Selezionare l'elemento "book" e nella finestra proprietà si dovrebbe essere il nome dell'autore oltre alle proprietà del libro. Modificare il nome dell'autore collegato, o collegare il libro a un altro autore e osservare che il nome dell'autore del libro è stato modificato.

## <a name="custom-property-editors"></a>Editor di proprietà personalizzati
 Finestra delle proprietà fornisce un valore appropriato predefinito funzioni di modifica per il tipo di ogni proprietà di dominio. Ad esempio, per un tipo enumerato, l'utente visualizza un elenco di riepilogo a discesa e per una proprietà numerica, l'utente può immettere cifre. Questo vale solo per i tipi incorporati. Se si specifica un tipo esterno, l'utente sarà in grado di visualizzare i valori della proprietà, ma non modificarlo.

 Tuttavia, è possibile specificare gli editor e i tipi seguenti:

1. Un altro editor che viene usato con un tipo standard. Ad esempio, è possibile specificare un editor di percorso di file per una proprietà di stringa.

2. Un tipo esterno per la proprietà di dominio e un editor per tale.

3. Un editor di .NET, ad esempio l'editor di percorso di file, oppure è possibile creare una proprietà personalizzata dell'editor.

    La conversione tra un tipo esterno e un tipo, ad esempio stringa, che dispone di un editor predefinito.

   In un linguaggio DSL, un' *tipo esterno* è qualsiasi tipo che non è uno dei tipi semplici (ad esempio, booleano o Int32) o stringa.

#### <a name="to-define-a-domain-property-that-has-an-external-type"></a>Per definire una proprietà di dominio che dispone di un tipo esterno

1. Nelle **Esplora soluzioni**, aggiungere un riferimento all'assembly (DLL) che contiene il tipo esterno, nelle **Dsl** progetto.

    L'assembly può essere un assembly .NET o un assembly fornito dall'utente.

2. Aggiungere il tipo per il **tipi di dominio** elencare, a meno che non si è già stato fatto.

   1. Aprire dsldefinition. DSL e nella **DSL Explorer**, fare clic sul nodo radice e quindi fare clic su **Aggiungi nuovo tipo esterno**.

        Una nuova voce viene visualizzata sotto il **tipi di dominio** nodo.

       > [!WARNING]
       >  La voce di menu per il nodo radice DSL, non il **tipi di dominio** nodo.

   2. Nella finestra Proprietà, impostare il nome e lo spazio dei nomi del nuovo tipo.

3. Aggiungere una proprietà di dominio a una classe di dominio nel modo usuale.

    Nella finestra Proprietà, selezionare il tipo esterno nell'elenco a discesa nel **tipo** campo.

   In questa fase, gli utenti possono visualizzare i valori della proprietà, ma non possono modificarlo. I valori visualizzati sono ottenuti dal `ToString()` (funzione). È possibile scrivere codice programma che imposta il valore della proprietà, ad esempio in un comando o una regola.

### <a name="setting-a-property-editor"></a>L'impostazione di un Editor di proprietà
 Aggiungere un attributo CLR per la proprietà di dominio, nel formato seguente:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

 È possibile impostare l'attributo su una proprietà utilizzando il **attributo personalizzato** voce nella finestra Proprietà.

 Il tipo di `AnEditor` deve essere derivato dal tipo specificato nel secondo parametro. Il secondo parametro deve essere <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.ComponentEditor>. Per altre informazioni, vedere <xref:System.ComponentModel.EditorAttribute>.

 È possibile specificare il proprio editor o un editor forniti nel [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], ad esempio <xref:System.Windows.Forms.Design.FileNameEditor> o <xref:System.Drawing.Design.ImageEditor>. Ad esempio, usare la procedura seguente per disporre di una proprietà in cui l'utente può immettere un nome di file.

##### <a name="to-define-a-file-name-domain-property"></a>Per definire una proprietà di dominio del nome file

1. Aggiungere una proprietà di dominio a una classe di dominio nella definizione DSL.

2. Selezionare la nuova proprietà. Nel **attributo personalizzato** campo nella finestra Proprietà, immettere il seguente attributo. Per immettere questo attributo, fare clic sui puntini di sospensione **[...]**  e quindi immettere il nome dell'attributo e i parametri separatamente:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Lasciare il tipo della proprietà del dominio usata l'impostazione predefinita del **stringa**.

4. Per testare l'editor, verificare che gli utenti possono aprire l'editor di nome file per modificare le proprietà di dominio.

    1. Premere CTRL+F5 o F5. Nella soluzione di debug, aprire un file di test. Creare un elemento della classe di dominio e selezionarlo.

    2. Nella finestra Proprietà, selezionare la proprietà di dominio. Il campo del valore Mostra i puntini di sospensione **[...]** .

    3. Fare clic sui puntini di sospensione. Viene visualizzata una finestra di dialogo file. Selezionare un file e chiudere la finestra di dialogo. Il percorso del file è ora il valore della proprietà del dominio.

### <a name="defining-your-own-property-editor"></a>Che definisce il proprio editor di proprietà
 È possibile definire il proprio editor. È consigliabile impostare tale per consentire all'utente di modificare un tipo che sono stati definiti o per modificare un tipo standard in modo speciale. Ad esempio, è possibile consentire all'utente di immettere una stringa che rappresenta una formula.

 Si definisce un editor scrivendo una classe derivata da <xref:System.Drawing.Design.UITypeEditor>. È necessario eseguire l'override della classe:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, per interagire con l'utente e aggiornare il valore della proprietà.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, per specificare se l'editor verrà aperta una finestra di dialogo o fornire un menu di scelta rapida.

  È anche possibile fornire una rappresentazione grafica del valore della proprietà che verrà visualizzato nella griglia delle proprietà. A tale scopo, eseguire l'override `GetPaintValueSupported`, e `PaintValue`.  Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
>  Aggiungere il codice in un file di codice separato nella **Dsl** progetto.

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

 Per usare questo editor, impostare il **attributo personalizzato** della proprietà del dominio per:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

 Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

## <a name="providing-a-drop-down-list-of-values"></a>Che fornisce un elenco di riepilogo a discesa di valori
 È possibile fornire un elenco di valori per un utente di scegliere.

> [!NOTE]
>  Questa tecnica offre un elenco di valori che possono cambiare in fase di esecuzione. Se si desidera fornire un elenco che non cambia, è consigliabile invece con il tipo della proprietà di dominio di un tipo enumerato.

 Per definire un elenco di valori standard, si aggiunge alla proprietà del dominio un attributo CLR che ha il formato seguente:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

 Definire una classe che deriva da <xref:System.ComponentModel.TypeConverter>. Aggiungere il codice in un file separato nel **Dsl** progetto. Ad esempio:

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