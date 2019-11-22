---
title: Definire vincoli di convalida per i modelli UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, validation constraints
ms.assetid: 87b3b0da-122d-4121-9318-200c38ff49d0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3dd76deb3b72d3b12d3b5892c2e5664273425c4c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295839"
---
# <a name="define-validation-constraints-for-uml-models"></a>Definire vincoli di convalida per i modelli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile definire vincoli di convalida che verificano se il modello soddisfa una condizione specificata. Ad esempio, si può definire un vincolo che assicura che un utente non crei un ciclo di relazioni di ereditarietà. Il vincolo viene richiamato quando l'utente cerca di aprire o di salvare il modello e può essere richiamato anche manualmente. Se il vincolo non riesce, alla finestra di errore viene aggiunto un messaggio definito dall'utente. È possibile creare un pacchetto di questi vincoli in un progetto[VSIX](https://go.microsoft.com/fwlink/?LinkId=160780)(Visual Studio Integration Extension) e distribuirlo ad altri utenti di Visual Studio.

 Si possono definire anche vincoli che convalidano il modello a fronte di risorse esterne, ad esempio un database. Se si vuole convalidare il codice del programma rispetto a un diagramma livello, vedere [aggiungere la convalida dell'architettura personalizzata ai diagrammi livello](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).

 Per informazioni sulle versioni di Visual Studio che supportano modelli UML, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="requirements"></a>Requisiti
 Vedere [Requisiti](../modeling/extend-uml-models-and-diagrams.md#Requirements).

 Per informazioni sulle versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="applying-validation-constraints"></a>Applicazione dei vincoli di convalida
 I vincoli di convalida vengono applicati in tre casi: quando si salva un modello, quando si apre un modello e quando si fa clic su **Convalida modello UML** nel menu **Architettura** . In ogni caso, verranno applicati solo i vincoli definiti per il caso specifico, anche se di solito si definisce ogni vincolo in modo che venga applicato in più di un caso.

 Gli errori di convalida vengono segnalati nell'apposita finestra di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Fare doppio clic su un errore per selezionare gli elementi del modello errati.

 Per altre informazioni sull'applicazione della convalida, vedere [convalidare il modello UML](../modeling/validate-your-uml-model.md).

## <a name="defining-a-validation-extension"></a>Definizione di un'estensione di convalida
 Per creare un'estensione di convalida per una finestra di progettazione UML, è necessario creare una classe che definisca i vincoli di convalida e incorporare la classe in un'estensione VSIX (Visual Studio Integration Extension). L'estensione VSIX è un contenitore che può installare il vincolo. Esistono due metodi alternativi per definire un'estensione di convalida:

- **Creare un'estensione di convalida nella relativa estensione VSIX con un modello di progetto.** Questo è il metodo più rapido. Usarlo se non si vuole combinare i vincoli di convalida con altri tipi di estensione, ad esempio comandi di menu, elementi della casella degli strumenti personalizzati o gestori di movimento. È possibile definire più vincoli in una classe.

- **Creare la classe di convalida separata e progetti VSIX.** Usare questo metodo per combinare diversi tipi di estensione nella stessa estensione VSIX. Ad esempio, se il comando di menu prevede che il modello rispetti dei vincoli specifici, è possibile incorporarlo nella stessa estensione VSIX come metodo di convalida.

#### <a name="to-create-a-validation-extension-in-its-own-vsix"></a>Per creare un'estensione di convalida nella relativa estensione VSIX

1. Nella finestra di dialogo **Nuovo progetto** , in **Progetti di modellazione**, selezionare **Estensione di convalida**.

2. Aprire il file **.cs** nel nuovo progetto e modificare la classe per poter implementare il vincolo di convalida.

    Per altre informazioni, vedere [Valutazione del vincolo di convalida](#Implementing).

   > [!IMPORTANT]
   > Assicurarsi che i file **.cs** contengano l'istruzione seguente `using` :
   >
   >  `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

3. È possibile aggiungere altri vincoli definendo nuovi metodi. Per identificare un metodo come metodo di convalida, deve essere contrassegnato con gli attributi esattamente come il metodo di convalida iniziale.

4. Testare i vincoli premendo F5. Per altre informazioni, vedere [Esecuzione di un vincolo di convalida](#Executing).

5. Installare il comando di menu in un altro computer copiando il file **bin\\\*\\\*. vsix** compilato dal progetto. Per altre informazioni, vedere [Installazione e disinstallazione di un'estensione](#Installing).

   Quando si aggiungono altri file **.cs** , in genere vengono richieste le istruzioni `using` seguenti:

```csharp
using System.Collections.Generic;
using System.ComponentModel.Composition;
using System.Linq;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Uml.Classes;

```

 Ecco la procedura alternativa:

#### <a name="to-create-a-separate-validation-constraint-in-a-class-library-project"></a>Per creare un vincolo di convalida separato in un progetto di libreria di classi

1. Creare un progetto di libreria di classi, aggiungendolo a una soluzione VSIX esistente oppure creando una nuova soluzione.

    1. Nel menu **File** , scegliere **Nuovo**, **Progetto**.

    2. In **Modelli installati**espandere **Visual C#** o **Visual Basic**e quindi scegliere **Libreria di classi**nella colonna centrale.

2. Creare un progetto VSIX salvo il caso in cui la soluzione ne contenga già uno:

    1. In **Esplora soluzioni**scegliere  **Aggiungi**, **Nuovo progetto**dal menu di scelta rapida della soluzione.

    2. In **Modelli installati**espandere **Visual C#** o **Visual Basic**, quindi scegliere **Extensibility**. Nella colonna centrale fare clic su **Progetto VSIX**.

3. Impostare il progetto VSIX come progetto di avvio della soluzione.

    - In Esplora soluzioni scegliere **Imposta come progetto di avvio** dal menu di scelta rapida del progetto VSIX.

4. In **source.extension.vsixmanifest**, in **Contenuto**, aggiungere il progetto di libreria di classi come componente MEF:

    1. Nella scheda **Metadati** impostare un nome per il progetto VSIX.

    2. Nella scheda **Destinazioni di installazione** impostare le versioni di Visual Studio come destinazioni.

    3. Nella scheda **Asset** scegliere **Nuovo**e nella finestra di dialogo impostare le opzioni seguenti:

         **Tipo** = **Componente MEF**

         **Origine** = **Progetto nella soluzione corrente**

         **Progetto** = *Progetto di libreria di classi*

#### <a name="to-define-the-validation-class"></a>Per definire la classe di convalida

1. Questa procedura non è necessaria se si è creata una classe di convalida con l'estensione VSIX dal modello di progetto di convalida.

2. Nel progetto della classe di convalida aggiungere riferimenti agli assembly [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] seguenti:

     `Microsoft.VisualStudio.Modeling.Sdk.[version]`

     `Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml`

     `Microsoft.VisualStudio.Uml.Interfaces`

     `System.ComponentModel.Composition`

3. Aggiungere un file al progetto di libreria di classi contenente codice simile al seguente esempio.

    - Ogni vincolo di convalida è contenuto in un metodo contrassegnato con un attributo specifico. Il metodo accetta un parametro di un tipo di elemento del modello. Quando la convalida viene richiamata, il framework di convalida applicherà ogni metodo di convalida a ogni elemento del modello conforme al tipo di parametro.

    - È possibile inserire questi metodi in qualsiasi classe e spazio dei nomi. Modificarli secondo le proprie preferenze.

    ```
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using System.Linq;
    using Microsoft.VisualStudio.Modeling.Validation;
    using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;
    using Microsoft.VisualStudio.Uml.Classes;
    // You might also need the other Microsoft.VisualStudio.Uml namespaces.

    namespace Validation
    {
      public class MyValidationExtensions
      {
        // SAMPLE VALIDATION METHOD.
        // All validation methods have the following attributes.
        [Export(typeof(System.Action<ValidationContext, object>))]
        [ValidationMethod(
           ValidationCategories.Save
         | ValidationCategories.Open
         | ValidationCategories.Menu)]
        public void ValidateClassNames
          (ValidationContext context,
           // This type determines what elements
           // will be validated by this method:
           IClass elementToValidate)
        {
          // A validation method should not change the model.

          List<string> attributeNames = new List<string>();
          foreach (IProperty attribute in elementToValidate.OwnedAttributes)
          {
            string name = attribute.Name;
            if (!string.IsNullOrEmpty(name) && attributeNames.Contains(name))
            {
              context.LogError(
                string.Format("Duplicate attribute name '{0}' in class {1}", name, elementToValidate.Name),
                "001", elementToValidate);
            }
            attributeNames.Add(name);
          }

        }
        // Add more validation methods for different element types.
      }
    }
    ```

## <a name="Executing"></a>Esecuzione di un vincolo di convalida
 A scopo di test, eseguire i metodi di convalida in modalità debug.

#### <a name="to-test-the-validation-constraint"></a>Per testare il vincolo di convalida

1. Premere **F5**o scegliere **Avvia debug** dal menu **Debug**.

     Viene avviata un'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

     **Risoluzione dei problemi**: se non viene avviata una nuova istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] :

    - Se si hanno più progetti, assicurarsi che il progetto VSIX sia impostato come progetto di avvio della soluzione.

    - In Esplora soluzioni scegliere **Proprietà**dal menu di scelta rapida del progetto di avvio o dell'unico progetto. Nell'editor delle proprietà del progetto selezionare la scheda **debug** . Assicurarsi che la stringa nel campo **Avvia programma esterno** sia il percorso completo di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], in genere:

         `C:\Program Files\Microsoft Visual Studio [version]\Common7\IDE\devenv.exe`

2. Nell'istanza sperimentale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]aprire o creare un progetto di modellazione e aprire o creare un diagramma di modellazione.

3. Per configurare un test per il vincolo di esempio fornito nella sezione precedente:

    1. Aprire un diagramma classi.

    2. Creare una classe e aggiungere due attributi con lo stesso nome.

4. Dal menu di scelta rapida in qualsiasi punto del diagramma scegliere **Convalida**.

5. Eventuali errori nel modello verranno segnalati nella finestra degli errori.

6. Fare doppio clic sulla segnalazione errori. Se gli elementi citati nel report sono visibili nella schermata, saranno evidenziati.

     **Risoluzione dei problemi**: se il comando **Convalida** non appare nel menu, verificare che:

    - Il progetto di convalida sia elencato come componente MEF nella scheda **Asset** in **source.extensions.manifest** nel progetto VSIX.

    - Gli attributi `Export` e `ValidationMethod` corretti siano aggiunti ai metodi di convalida.

    - `ValidationCategories.Menu` è incluso nell'argomento per l'attributo `ValidationMethod` e viene composto con altri valori utilizzando OR logico (&#124;).

    - I parametri di tutti gli attributi `Import` e `Export` siano validi.

## <a name="Implementing"></a>Valutazione del vincolo
 Il metodo di convalida dovrebbe determinare se il vincolo di convalida che si vuole applicare sia true o false. Se è true, non dovrebbe fare nulla. Se è false, dovrebbe segnalare un errore usando i metodi forniti dal parametro `ValidationContext` .

> [!NOTE]
> I metodi di convalida non dovrebbero modificare il modello. Non è garantito quando o in quale ordine verranno eseguiti i vincoli. Se è necessario passare informazioni tra due esecuzioni consecutive di un metodo di convalida all'interno dell'esecuzione di una convalida, è possibile usare la cache del contesto descritta in [Coordinamento di più convalide](#ContextCache).

 Ad esempio, per essere certi che ogni tipo (classe, interfaccia o enumeratore) abbia un nome di almeno tre caratteri, si può usare questo metodo:

```
public void ValidateTypeName(ValidationContext context, IType type)
{
  if (!string.IsNullOrEmpty(type.Name) && type.Name.Length < 3)
  {
    context.LogError(
      string.Format("Type name {0} is too short", type.Name),
               "001", type);
   }
 }
```

 Vedere [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md) per informazioni sui metodi e sui tipi utilizzabili per esplorare e leggere il modello.

### <a name="about-validation-constraint-methods"></a>Informazioni sui metodi dei vincoli di convalida
 Ogni vincolo di convalida è definito da un metodo nel seguente formato:

```
[Export(typeof(System.Action<ValidationContext, object>))]
 [ValidationMethod(ValidationCategories.Save
  | ValidationCategories.Menu
  | ValidationCategories.Open)]
public void ValidateSomething
  (ValidationContext context, IClassifier elementToValidate)
{...}
```

 Gli attributi e i parametri di ogni metodo di convalida sono i seguenti:

|||
|-|-|
|`[Export(typeof(System.Action <ValidationContext, object>))]`|Definisce il metodo come vincolo di convalida usando Managed Extensibility Framework (MEF).|
|`[ValidationMethod (ValidationCategories.Menu)]`|Specifica quando la convalida verrà eseguita. Utilizzare OR bit per&#124;bit () se si desidera combinare più di un'opzione.<br /><br /> `Menu` = richiamato dal menu Convalida.<br /><br /> `Save` = richiamato al salvataggio del modello.<br /><br /> `Open` = richiamato all'apertura del modello. `Load` = richiamato al salvataggio del modello, ma in caso di violazione avvisa l'utente che potrebbe non essere possibile riaprire il modello. Chiamato anche in fase di caricamento, prima che il modello venga analizzato.|
|`public void ValidateSomething`<br /><br /> `(ValidationContext context,`<br /><br /> `IElement element)`|Sostituire il secondo parametro `IElement` con il tipo di elemento a cui si vuole applicare il vincolo. Il metodo del vincolo verrà richiamato su tutti gli elementi nel tipo specificato.<br /><br /> Il nome del metodo non è importante.|

 È possibile definire tutti i metodi di convalida che si vuole, con tipi diversi nel secondo parametro. Quando la convalida viene richiamata, ogni metodo di convalida verrà chiamato su ogni elemento del modello conforme al tipo di parametro.

### <a name="reporting-validation-errors"></a>Creazione di report per gli errori di convalida
 Per creare una segnalazione errori, usare i metodi forniti da `ValidationContext`:

 `context.LogError("error string", errorCode, elementsWithError);`

- `"error string"` viene visualizzato nell'elenco errori di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- `errorCode` è una stringa che dovrebbe identificare l'errore in modo univoco

- `elementsWithError` identifica gli elementi del modello. Quando l'utente fa doppio clic sulla segnalazione errori, verrà selezionata la forma che rappresenta questo elemento.

  `LogError(),` `LogWarning()` e `LogMessage()` inserire i messaggi in sezioni diverse dell'elenco errori.

## <a name="how-validation-methods-are-applied"></a>Come vengono applicati i metodi di convalida
 La convalida viene applicata a ogni elemento del modello, incluse le relazioni e le parti di elementi più grandi, ad esempio gli attributi di una classe e i parametri di un'operazione.

 Ogni metodo di convalida viene applicato a ogni elemento conforme al tipo nel secondo parametro, vale a dire che, ad esempio, se si definisce un metodo di convalida con un secondo parametro di `IUseCase` e un altro con il supertipo `IElement`, entrambi i metodi verranno applicati a ogni caso d'uso del modello.

 La gerarchia dei tipi viene riepilogata nei [tipi di elemento del modello UML](../modeling/uml-model-element-types.md).

 È anche possibile accedere agli elementi seguendo le relazioni. Ad esempio, se si dovesse definire un metodo di convalida per `IClass`, si potrebbero riprodurre a ciclo continuo le relative proprietà:

```
public void ValidateTypeName(ValidationContext context, IClass c)
{
   foreach (IProperty property in c.OwnedAttributes)
   {
       if (property.Name.Length < 3)
       {
            context.LogError(
                 string.Format(
                        "Property name {0} is too short",
                        property.Name),
                 "001", property);
        }
   }
}
```

### <a name="creating-a-validation-method-on-the-model"></a>Creazione di un metodo di convalida per il modello
 Per essere certi che un metodo di convalida venga chiamato una sola volta durante ogni esecuzione di convalida, è possibile convalidare `IModel`:

```
using Microsoft.VisualStudio.Uml.AuxiliaryConstructs; ...
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{  foreach (IElement element in model.OwnedElements)
   { ...
```

### <a name="validating-shapes-and-diagrams"></a>Convalida di forme e diagrammi
 I metodi di convalida non vengono richiamati per alcuni elementi visualizzati come diagrammi e forme, perché lo scopo principale dei metodi di convalida è convalidare il modello. Tuttavia è possibile accedere al diagramma corrente usando il contesto del diagramma.

 Nella classe di convalida dichiarare `DiagramContext` come proprietà importata:

```
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;
...
[Import]
public IDiagramContext DiagramContext { get; set; }
```

 In un metodo di convalida, è possibile usare `DiagramContext` per accedere al diagramma attualmente con stato attivo, se presente:

```
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu)]
public void ValidateModel(ValidationContext context, IModel model)
{
  IDiagram focusDiagram = DiagramContext.CurrentDiagram;
  if (focusDiagram != null)
  {
    foreach (IShape<IUseCase> useCaseShape in
              focusDiagram.GetChildShapes<IUseCase>())
    { ...
```

 Per registrare un errore, è necessario ottenere l'elemento del modello rappresentato dalla forma, perché non è possibile passare una forma a `LogError`:

```
IUseCase useCase = useCaseShape.Element;
context.LogError(... , usecase);
```

### <a name="ContextCache"></a>Coordinamento di più convalide
 Quando la convalida viene richiamata, ad esempio dall'utente da un menu del diagramma, ogni metodo di convalida viene applicato a ogni elemento del modello, vale a dire che, in una singola chiamata del framework di convalida, lo stesso metodo può essere applicato più volte a elementi diversi.

 Questo comportamento è un problema per le convalide che coinvolgono le relazioni tra gli elementi. Ad esempio, si potrebbe scrivere una convalida che inizia da un caso d'uso e attraversa le relazioni **include** per verificare che non siano presenti cicli. Quando però il metodo viene applicato a ogni caso d'uso in un modello con molti collegamenti **include** , è probabile che le stesse aree del modello vengano elaborate più volte.

 Per evitare questa situazione, esiste una cache di contesto in cui le informazioni vengono conservate durante l'esecuzione di una convalida. È possibile usarla per passare le informazioni da un'esecuzione all'altra dei metodi di convalida. Ad esempio, si potrebbe archiviare un elenco degli elementi già coinvolti nell'esecuzione di questa convalida. La cache viene creata all'inizio dell'esecuzione di ogni convalida e non può essere usata per passare informazioni da un'esecuzione di convalida all'altra.

|||
|-|-|
|`context.SetCacheValue<T> (name, value)`|Archivia un valore|
|`context.TryGetCacheValue<T> (name, out value)`|Ottiene un valore. Se riesce, restituisce true.|
|`context.GetValue<T>(name)`|Ottiene un valore.|
|`Context.GetValue<T>()`|Ottiene un valore del tipo specificato.|

## <a name="Installing"></a>Installazione e disinstallazione di un'estensione
 È possibile installare un'estensione di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] sia nel proprio computer che in altri.

#### <a name="to-install-an-extension"></a>Per installare un'estensione

1. Nel computer trovare il file **.vsix** compilato dal progetto VSIX.

    1. In **Esplora soluzioni**scegliere **Apri cartella in Esplora risorse**dal menu di scelta rapida del progetto VSIX.

    2. Individuare il file **bin\\\*\\** _progettoutente_ **. vsix**

2. Copiare il file **.vsix** nel computer di destinazione in cui si vuole installare l'estensione. Può trattarsi del computer in uso o di un altro computer.

    - Nel computer di destinazione deve essere installata una delle edizioni di [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] specificate in **source.extension.vsixmanifest**.

3. Nel computer di destinazione aprire il file **.vsix** .

     **Visual Studio Extension Installer** si apre e installa l'estensione.

4. Avviare o riavviare [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

#### <a name="to-uninstall-an-extension"></a>Per disinstallare un'estensione

1. Nel menu **Strumenti** scegliere **Estensioni e aggiornamenti**.

2. Espandere **Estensioni installate**.

3. Selezionare l'estensione e quindi scegliere **Disinstalla**.

   Raramente, un'estensione errata non viene caricata e crea un report nella finestra degli errori, ma non viene visualizzata in Gestione estensioni. In tal caso, è possibile rimuovere l'estensione eliminando il file dal percorso seguente, in cui *% LocalAppData%* è in genere *driveName*: \Users\\*username*\AppData\Local:

   *% LocalAppData%* **\Microsoft\VisualStudio\\[versione] \Extensions**

## <a name="Example"></a> Esempio
 In questo esempio vengono trovati i cicli nella relazione di dipendenza tra gli elementi.

 La convalida verrà eseguita sia durante il salvataggio che sul comando di menu Convalida.

```
/// <summary>
/// Verify that there are no loops in the dependency relationsips.
/// In our project, no element should be a dependent of itself.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">Element to start validation from.</param>
[Export(typeof(System.Action<ValidationContext, object>))]
[ValidationMethod(ValidationCategories.Menu
     | ValidationCategories.Save | ValidationCategories.Open)]
public void NoDependencyLoops(ValidationContext context, INamedElement element)
{
    // The validation framework will call this method
    // for every element in the model. But when we follow
    // the dependencies from one element, we will validate others.
    // So we keep a list of the elements that we don't need to validate again.
    // The list is kept in the context cache so that it is passed
    // from one execution of this method to another.
    List<INamedElement> alreadySeen = null;
    if (!context.TryGetCacheValue("No dependency loops", out alreadySeen))
    {
       alreadySeen = new List<INamedElement>();
       context.SetCacheValue("No dependency loops", alreadySeen);
    }

    NoDependencyLoops(context, element,
                new INamedElement[0], alreadySeen);
}

/// <summary>
/// Log an error if there is any loop in the dependency relationship.
/// </summary>
/// <param name="context">Validation context for logs.</param>
/// <param name="element">The element to be validated.</param>
/// <param name="dependants">Elements we've followed in this recursion.</param>
/// <param name="alreadySeen">Elements that have already been validated.</param>
/// <returns>true if no error was detected</returns>
private bool NoDependencyLoops(ValidationContext context,
    INamedElement element, INamedElement[] dependants,
    List<INamedElement> alreadySeen)
{
    if (dependants.Contains(element))
    {
        context.LogError(string.Format("{0} should not depend on itself", element.Name),
        "Fabrikam.UML.NoGenLoops", // unique code for this error
        dependants.SkipWhile(e => e != element).ToArray());
            // highlight elements that are in the loop
        return false;
    }
    INamedElement[] dependantsPlusElement =
        new INamedElement[dependants.Length + 1];
    dependants.CopyTo(dependantsPlusElement, 0);
    dependantsPlusElement[dependantsPlusElement.Length - 1] = element;

    if (alreadySeen.Contains(element))
    {
        // We have already validated this when we started
        // from another element during this validation run.
        return true;
    }
    alreadySeen.Add(element);

    foreach (INamedElement supplier in element.GetDependencySuppliers())
    {
        if (!NoDependencyLoops(context, supplier,
             dependantsPlusElement, alreadySeen))
        return false;
    }
    return true;
}
```

## <a name="see-also"></a>Vedere anche
 [Definire e installare un'estensione di modellazione](../modeling/define-and-install-a-modeling-extension.md) [programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)
