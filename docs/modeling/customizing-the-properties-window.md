---
title: Personalizzazione della finestra Proprietà
description: Informazioni su come personalizzare l'aspetto e il comportamento della finestra delle proprietà nel linguaggio specifico di dominio (DSL) in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Domain-Specific Language, Properties window
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4e1bd54850264c33c5317a4395f219689a8e8634
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385799"
---
# <a name="customize-the-properties-window"></a>Personalizzare la Finestra Proprietà

È possibile personalizzare l'aspetto e il comportamento della finestra delle proprietà nel linguaggio specifico di dominio (DSL) in Visual Studio. Nella definizione DSL si definiscono le proprietà di dominio in ogni classe di dominio. Per impostazione predefinita, quando si seleziona un'istanza della classe, in un diagramma o in Esplora modelli, ogni proprietà di dominio viene elencata nella finestra delle proprietà. In questo modo è possibile visualizzare e modificare i valori delle proprietà di dominio, anche se non sono stati mappati ai campi di forma nel diagramma.

## <a name="names-descriptions-and-categories"></a>Nomi, descrizioni e categorie

**Nome e nome visualizzato**. Nella definizione di una proprietà di dominio, il nome visualizzato della proprietà è il nome visualizzato in fase di esecuzione nella finestra delle proprietà. Al contrario, il nome viene usato quando si scrive il codice del programma per aggiornare la proprietà . Il nome deve essere un nome alfanumerico CLR corretto, ma il nome visualizzato può contenere spazi.

Quando si imposta il nome di una proprietà nella definizione DSL, il relativo nome visualizzato viene impostato automaticamente su una copia del nome. Se si scrive un nome con distinzione tra maiuscole e minuscole, ad esempio "FuelGauge", il nome visualizzato conterrà automaticamente uno spazio: "Fuel Gauge". Tuttavia, è possibile impostare il nome visualizzato in modo esplicito su un altro valore.

**Descrizione**. La descrizione di una proprietà di dominio viene visualizzata in due posizioni:

- Nella parte inferiore della finestra delle proprietà quando l'utente seleziona la proprietà. È possibile usarlo per spiegare all'utente cosa rappresenta la proprietà.

- Nel codice del programma generato. Se si usano le funzionalità della documentazione per estrarre la documentazione dell'API, questa verrà visualizzata come descrizione di questa proprietà nell'API.

**Categoria**. Una categoria è un'intestazione nel Finestra Proprietà.

## <a name="expose-style-features"></a>Esporre le funzionalità di stile

Alcune delle funzionalità dinamiche degli elementi grafici possono essere rappresentate o *esposte* come proprietà di dominio. Una funzionalità esposta in questo modo può essere aggiornata dall'utente e può essere più facilmente aggiornata dal codice del programma.

Fare clic con il pulsante destro del mouse su una classe di forma in Definizione DSL, scegliere **Aggiungi** esposto e quindi scegliere una funzionalità.

Nelle forme è possibile esporre le proprietà **FillColor**, **OutlineColor**, **TextColor**, **OutlineDashStyle**, **OutlineThickness** e **FillGradientMode.** Nei connettori è possibile esporre le **proprietà** `,` **Color TextColor**, **DashStyle** **e Thickness.** Nei diagrammi è possibile esporre le **proprietà FillColor** **e TextColor.**

## <a name="forwarding-display-properties-of-related-elements"></a>Inoltro: visualizzare le proprietà degli elementi correlati

Quando l'utente del DSL seleziona un elemento in un modello, le proprietà dell'elemento vengono visualizzate nella finestra delle proprietà. Tuttavia, è anche possibile visualizzare le proprietà degli elementi correlati specificati. Ciò è utile se è stato definito un gruppo di elementi che funzionano insieme. Ad esempio, è possibile definire un elemento main e un elemento plug-in facoltativo. Se l'elemento principale viene mappato a una forma e l'altro no, è utile visualizzare tutte le relative proprietà come se fossero in un elemento.

Questo effetto è denominato *inoltro di proprietà* e si verifica automaticamente in diversi casi. In altri casi, è possibile ottenere l'inoltro delle proprietà definendo un descrittore di tipo di dominio.

### <a name="default-property-forwarding-cases"></a>Case di inoltro delle proprietà predefinite

Quando l'utente seleziona una forma o un connettore o un elemento in Esplora risorse, vengono visualizzate le proprietà seguenti nel Finestra Proprietà:

- Proprietà di dominio definite nella classe di dominio dell'elemento del modello, incluse quelle definite nelle classi di base. Un'eccezione è la proprietà di dominio per cui è stato impostato **Is Browsable** su `False` .

- Nomi di elementi collegati tramite relazioni con una molteplicità di 0..1. In questo modo è possibile visualizzare gli elementi collegati facoltativamente, anche se non è stato definito un mapping del connettore per la relazione.

- Proprietà di dominio della relazione di incorporamento destinata all'elemento. Poiché le relazioni di incorporamento in genere non vengono visualizzate in modo esplicito, ciò consente all'utente di visualizzarne le proprietà.

- Proprietà di dominio definite nella forma o nel connettore selezionato.

### <a name="add-property-forwarding"></a>Aggiungere l'inoltro di proprietà

Per inoltrare una proprietà, definire un descrittore di tipo di dominio. Se si ha una relazione di dominio tra due classi di dominio, è possibile usare un descrittore di tipo di dominio per impostare una proprietà di dominio nella prima classe sul valore di una proprietà di dominio nella seconda classe di dominio. Ad esempio, se si ha una relazione tra una classe di dominio **Book** e una classe di dominio  **Author,** è possibile usare un descrittore di tipo di dominio per fare in modo che la proprietà **Name** dell'autore di un libro venga visualizzata nel Finestra Proprietà quando l'utente seleziona il libro.

> [!NOTE]
> L'inoltro delle proprietà influisce Finestra Proprietà quando l'utente modifica un modello. Non definisce una proprietà di dominio nella classe ricevente. Se si vuole accedere alla proprietà di dominio inoltrata in altre parti della definizione DSL o nel codice del programma, è necessario accedere all'elemento di inoltro.

La procedura seguente presuppone che sia stato creato un DSL. I primi passaggi riepilogano i prerequisiti.

#### <a name="forward-a-property-from-another-element"></a>Inoltrare una proprietà da un altro elemento

1. Creare una soluzione contenente almeno due classi, che [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] in questo esempio sono denominate **Book** e **Author**. Deve essere presente una relazione di entrambi i tipi tra **Book** e **Author.**

    La molteplicità del ruolo di origine (il ruolo sul lato **Libro)** deve essere 0..1  o 1..1, in modo che ogni libro abbia un **autore.**

2. In **Esplora DSL fare** clic con il pulsante destro del mouse sulla classe di dominio **Book** e quindi scegliere Aggiungi **nuovo DomainTypeDescriptor**.

    Un nodo denominato **Paths of Custom Property Descriptors (Percorsi** dei descrittori di proprietà personalizzati) viene visualizzato sotto il nodo Custom Type **Descriptor (Descrittore di tipo** personalizzato).

3. Fare clic con il pulsante destro del mouse sul nodo **Custom Type Descriptor** e quindi scegliere **Aggiungi nuovo PropertyPath**.

    Nel nodo Percorsi dei descrittori **di proprietà** personalizzati viene visualizzato un nuovo percorso di proprietà.

4. Selezionare il nuovo percorso della proprietà e nella **finestra Proprietà** impostare Percorso su **Proprietà** sul percorso dell'elemento del modello appropriato.

    È possibile modificare il percorso in una visualizzazione albero facendo clic sulla freccia giù a destra di questa proprietà. Per altre informazioni sui percorsi di dominio, vedere [Sintassi del percorso di dominio](../modeling/domain-path-syntax.md). Dopo la modifica, il percorso dovrebbe essere simile a **BookReferencesAuthor.Author/! Creare**.

5. Impostare **Proprietà** sulla **proprietà di** dominio Name di **Author**.

6. Impostare **Nome visualizzato** su Nome **autore**.

7. Trasformare tutti i modelli, compilare ed eseguire il DSL.

8. In un diagramma modello creare un libro, un autore e collegarli usando la relazione di riferimento. Selezionare l'elemento book e nella Finestra Proprietà verrà visualizzato Nome autore oltre alle proprietà del libro. Modificare il nome dell'autore collegato o collegare il libro a un altro autore e osservare che il nome dell'autore del libro cambia.

## <a name="custom-property-editors"></a>Editor di proprietà personalizzate

La finestra delle proprietà offre un'esperienza di modifica predefinita appropriata per il tipo di ogni proprietà di dominio. Ad esempio, per un tipo enumerato, l'utente visualizza un elenco a discesa e, per una proprietà numerica, l'utente può immettere cifre. Questo vale solo per i tipi predefiniti. Se si specifica un tipo esterno, l'utente potrà visualizzare i valori della proprietà, ma non modificarli.

È tuttavia possibile specificare gli editor e i tipi seguenti:

1. Un altro editor usato con un tipo standard. Ad esempio, è possibile specificare un editor del percorso file per una proprietà stringa.

2. Tipo esterno per la proprietà di dominio e un editor per la proprietà.

3. Un editor .NET, ad esempio l'editor del percorso file, oppure è possibile creare un editor di proprietà personalizzato.

   Conversione tra un tipo esterno e un tipo, ad esempio String, con un editor predefinito.

   In un DSL  un tipo esterno è qualsiasi tipo che non è uno dei tipi semplici (ad esempio Boolean o Int32) o String.

### <a name="define-a-domain-property-that-has-an-external-type"></a>Definire una proprietà di dominio con un tipo esterno

1. In **Esplora soluzioni** aggiungere un riferimento all'assembly (DLL) che contiene il tipo esterno nel **progetto Dsl.**

    L'assembly può essere un assembly .NET o un assembly fornito dall'utente.

2. Aggiungere il tipo **all'elenco Tipi di** dominio, a meno che non sia già stato fatto.

   1. Aprire DslDefinition.dsl e in **Esplora DSL** fare clic con il pulsante destro del mouse sul nodo radice e quindi scegliere **Aggiungi nuovo tipo esterno**.

        Nel nodo Tipi di dominio viene visualizzata **una nuova** voce.

       > [!WARNING]
       > La voce di menu si trova nel nodo radice DSL, non nel **nodo Tipi di** dominio.

   2. Impostare il nome e lo spazio dei nomi del nuovo tipo nel Finestra Proprietà.

3. Aggiungere una proprietà di dominio a una classe di dominio nel modo consueto.

    Nel Finestra Proprietà selezionare il tipo esterno dall'elenco a discesa nel **campo Tipo.**

   In questa fase gli utenti possono visualizzare i valori della proprietà, ma non modificarli. I valori visualizzati vengono ottenuti dalla `ToString()` funzione . È possibile scrivere codice di programma che imposta il valore della proprietà, ad esempio in un comando o in una regola.

### <a name="set-a-property-editor"></a>Impostare un editor di proprietà

Aggiungere un attributo CLR alla proprietà di dominio nel formato seguente:

```csharp
[System.ComponentModel.Editor (
   typeof(AnEditor),
   typeof(System.Drawing.Design.UITypeEditor))]
```

È possibile impostare l'attributo in una proprietà usando la **voce Attributo** personalizzato nella Finestra Proprietà.

Il tipo `AnEditor` di deve essere derivato dal tipo specificato nel secondo parametro. Il secondo parametro deve essere <xref:System.Drawing.Design.UITypeEditor> o <xref:System.ComponentModel.ComponentEditor> . Per altre informazioni, vedere <xref:System.ComponentModel.EditorAttribute>.

È possibile specificare un editor personalizzato o un editor .NET, ad esempio <xref:System.Windows.Forms.Design.FileNameEditor> o <xref:System.Drawing.Design.ImageEditor> . Ad esempio, usare la procedura seguente per avere una proprietà in cui l'utente può immettere un nome di file.

#### <a name="define-a-file-name-domain-property"></a>Definire una proprietà di dominio del nome file

1. Aggiungere una proprietà di dominio a una classe di dominio nella definizione DSL.

2. Selezionare la nuova proprietà. Nel campo **Attributo personalizzato** della Finestra Proprietà immettere l'attributo seguente. Per immettere questo attributo, fare clic sui puntini di **sospensione [...]** e quindi immettere separatamente il nome dell'attributo e i parametri:

    ```csharp
    [System.ComponentModel.Editor (
       typeof(System.Windows.Forms.Design.FileNameEditor)
       , typeof(System.Drawing.Design.UITypeEditor))]

    ```

3. Lasciare l'impostazione predefinita di Stringa per Il tipo della proprietà **di dominio.**

4. Per testare l'editor, verificare che gli utenti possano aprire l'editor dei nomi file per modificare la proprietà del dominio.

    1. Premere CTRL+F5 o F5. Nella soluzione di debug aprire un file di test. Creare un elemento della classe di dominio e selezionarlo.

    2. Nella finestra Finestra Proprietà selezionare la proprietà del dominio. Il campo del valore mostra i puntini di **sospensione [...]**.

    3. Fare clic sui puntini di sospensione. Verrà visualizzata una finestra di dialogo file. Selezionare un file e chiudere la finestra di dialogo. Il percorso del file è ora il valore della proprietà domain.

### <a name="define-your-own-property-editor"></a>Definire un editor di proprietà personalizzato

È possibile definire un editor personalizzato. Questa operazione consente all'utente di modificare un tipo definito dall'utente o di modificare un tipo standard in modo speciale. Ad esempio, è possibile consentire all'utente di immettere una stringa che rappresenta una formula.

Per definire un editor, scrivere una classe derivata da <xref:System.Drawing.Design.UITypeEditor> . La classe deve eseguire l'override di:

- <xref:System.Drawing.Design.UITypeEditor.EditValue%2A>, per interagire con l'utente e aggiornare il valore della proprietà.

- <xref:System.Drawing.Design.UITypeEditor.GetEditStyle%2A>, per specificare se l'editor aprirà una finestra di dialogo o fornirà un menu a discesa.

È anche possibile fornire una rappresentazione grafica del valore della proprietà che verrà visualizzato nella griglia delle proprietà. A tale scopo, eseguire l'override `GetPaintValueSupported` di e `PaintValue` .  Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

> [!NOTE]
> Aggiungere il codice in un file di codice separato nel **progetto Dsl.**

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

Per usare questo editor, impostare **l'attributo personalizzato** di una proprietà di dominio su:

```csharp
[System.ComponentModel.Editor (
   typeof(MyNamespace.TextFileNameEditor)
   , typeof(System.Drawing.Design.UITypeEditor))]
```

Per altre informazioni, vedere <xref:System.Drawing.Design.UITypeEditor>.

## <a name="provide-a-drop-down-list-of-values"></a>Specificare un elenco a discesa di valori

È possibile fornire un elenco di valori tra cui un utente può scegliere.

> [!NOTE]
> Questa tecnica fornisce un elenco di valori che possono cambiare in fase di esecuzione. Se si vuole fornire un elenco che non cambia, prendere in considerazione l'uso di un tipo enumerato come tipo della proprietà di dominio.

Per definire un elenco di valori standard, aggiungere alla proprietà di dominio un attributo CLR nel formato seguente:

```csharp
[System.ComponentModel.TypeConverter
(typeof(MyTypeConverter))]
```

Definire una classe che deriva da <xref:System.ComponentModel.TypeConverter>. Aggiungere il codice in un file separato nel **progetto Dsl.** Ad esempio:

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
