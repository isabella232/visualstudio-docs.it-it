---
title: Convalida in un linguaggio specifico di dominio
description: Informazioni su come definire vincoli di convalida per verificare che il modello creato dall'utente sia significativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, constraints
- Domain-Specific Language, validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6de3a8940c845b29d2d0c7454b7c585f4676dba0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388334"
---
# <a name="validation-in-a-domain-specific-language"></a>Convalida in un linguaggio specifico di dominio
Gli autori di un linguaggio specifico di dominio possono definire vincoli di convalida per verificare che il modello creato dall'utente sia significativo. Ad esempio, se il linguaggio specifico di dominio consente agli utenti di disegnare l'albero genealogico di determinate persone e dei relativi antenati, è possibile scrivere un vincolo per garantire che le date di nascita dei figli siano successive a quelle dei genitori.

 È possibile fare in modo che i vincoli di convalida vengono eseguiti quando il modello viene salvato, quando viene aperto e quando l'utente esegue in modo esplicito il **comando di** menu Convalida. È anche possibile eseguire la convalida sotto il controllo del programma, ad esempio in risposta alla modifica di un valore di proprietà o di una relazione.

 La convalida è particolarmente importante se si scrivono modelli di testo o altri strumenti che elaborano i modelli degli utenti. Garantisce infatti che i modelli siano conformi alle precondizioni previste da questi strumenti.

> [!WARNING]
> È anche possibile consentire la definizione di vincoli di convalida in estensioni separate del linguaggio specifico di dominio, unitamente a comandi di menu e gestori movimenti dell'estensione. Gli utenti potranno quindi scegliere di installare queste estensioni in aggiunta al linguaggio specifico di dominio. Per altre informazioni, vedere [Estendere il DSL usando MEF.](../modeling/extend-your-dsl-by-using-mef.md)

## <a name="running-validation"></a>Esecuzione della convalida
 Quando un utente modifica un modello, ovvero un'istanza del linguaggio specifico di dominio, la convalida viene eseguita in seguito alle azioni seguenti:

- Fare clic con il pulsante destro del mouse sul diagramma e **scegliere Convalida tutto.**

- Fare clic con il pulsante destro del mouse sul nodo principale nella finestra di esplorazione del DSL e **scegliere Convalida tutto**

- L'utente salva il modello.

- L'utente apre il modello.

- È anche possibile scrivere codice programma che esegue la convalida, ad esempio includendolo in un comando di menu oppure in risposta a una modifica.

  Eventuali errori di convalida verranno visualizzati nella **finestra Elenco** errori. L'utente può fare doppio clic su un messaggio di errore per selezionare gli elementi del modello che sono la causa dell'errore.

## <a name="defining-validation-constraints"></a>Definizione dei vincoli di convalida
 Per definire vincoli di convalida, è possibile aggiungere metodi di convalida alle classi di dominio o alle relazioni del linguaggio specifico di dominio. Durante l'esecuzione della convalida, avviata dall'utente o controllata dal programma, vengono eseguiti alcuni o tutti i metodi di convalida. Ogni metodo viene applicato a ogni istanza della propria classe e possono essere presenti diversi metodi di convalida in ogni classe.

 Ogni metodo di convalida segnala gli eventuali errori trovati.

> [!NOTE]
> I metodi di convalida segnalano gli errori, ma non modificano il modello. Per modificare o impedire determinate modifiche, vedere [Alternative alla convalida.](#alternatives)

#### <a name="to-define-a-validation-constraint"></a>Per definire un vincolo di convalida

1. Abilitare la convalida nel **nodo Editor\Convalida:**

   1. Aprire **Dsl\DslDefinition.dsl**.

   2. In Esplora DSL espandere il nodo **Editor** e selezionare **Convalida.**

   3. Nella finestra Finestra Proprietà impostare le **proprietà Uses**  su `true` . È più pratico impostare tutte queste proprietà.

   4. Fare **clic su Trasforma tutti i** modelli nella barra **Esplora soluzioni** strumenti.

2. Scrivere le definizioni di classe parziali per una o più classi di dominio o relazioni di dominio Scrivere queste definizioni in un nuovo file di codice nel **progetto Dsl.**

3. Aggiungere questo attributo all'inizio di ogni classe:

   ```csharp
   [ValidationState(ValidationState.Enabled)]
   ```

   - Per impostazione predefinita, questo attributo abiliterà inoltre la convalida per le classi derivate. Per disabilitare la convalida per una classe derivata specifica, è possibile usare `ValidationState.Disabled`.

4. Aggiungere i metodi di convalida alle classi. Al metodo di convalida è possibile assegnare un nome qualsiasi, ma deve includere un parametro di tipo <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationContext>.

    Deve inoltre essere preceduto da uno o più attributi `ValidationMethod`:

   ```csharp
   [ValidationMethod (ValidationCategories.Open | ValidationCategories.Save | ValidationCategories.Menu ) ]
   ```

    Gli attributi ValidationCategories indicano quando viene eseguito il metodo.

   Ad esempio:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;

// Allow validation methods in this class:
[ValidationState(ValidationState.Enabled)]
// In this DSL, ParentsHaveChildren is a domain relationship
// from Person to Person:
public partial class ParentsHaveChildren
{
  // Identify the method as a validation method:
  [ValidationMethod
  ( // Specify which events cause the method to be invoked:
    ValidationCategories.Open // On file load.
  | ValidationCategories.Save // On save to file.
  | ValidationCategories.Menu // On user menu command.
  )]
  // This method is applied to each instance of the
  // type (and its subtypes) in a model:
  private void ValidateParentBirth(ValidationContext context)
  {
    // In this DSL, the role names of this relationship
    // are "Child" and "Parent":
     if (this.Child.BirthYear < this.Parent.BirthYear
        // Allow user to leave the year unset:
        && this.Child.BirthYear != 0)
      {
        context.LogError(
             // Description:
                       "Child must be born after Parent",
             // Unique code for this error:
                       "FAB001ParentBirthError",
              // Objects to select when user double-clicks error:
                       this.Child,
                       this.Parent);
    }
  }
```

 Notare gli aspetti seguenti su questo codice:

- È possibile aggiungere metodi di convalida a classi di dominio o relazioni di dominio. Il codice per questi tipi si trova in **Dsl\Generated Code\Domain \* .cs**.

- Ogni metodo di convalida viene applicato a ogni istanza delle relative classi e sottoclassi. Nel caso di una relazione di dominio ogni istanza è un collegamento tra due elementi del modello.

- I metodi di convalida non vengono applicati in qualsiasi ordine specificato e ogni metodo non viene applicato alle istanze della propria classe in qualsiasi ordine prevedibile.

- È in genere preferibile evitare che un metodo di convalida aggiorni il contenuto dell'archivio perché potrebbe causare risultati incoerenti. Il metodo deve invece segnalare eventuali errori chiamando `context.LogError`, `LogWarning` o `LogInfo`.

- Nella chiamata a LogError è possibile fornire un elenco di elementi di modello o collegamenti di relazione che verranno selezionati quando l'utente fa doppio clic sul messaggio di errore.

- Per informazioni su come leggere il modello nel codice programma, vedere Esplorazione e aggiornamento [di un modello nel codice programma.](../modeling/navigating-and-updating-a-model-in-program-code.md)

  L'esempio si applica al seguente modello di dominio. La relazione ParentsHaveChildren include ruoli denominati Child e Parent.

  ![Diagramma delle definizioni DSL &#45; albero del gruppo](../modeling/media/familyt_person.png)

## <a name="validation-categories"></a>Categorie di convalida
 Nell'attributo <xref:Microsoft.VisualStudio.Modeling.Validation.ValidationMethodAttribute> viene specificato quando eseguire il metodo di convalida.

|Categoria|Esecuzione|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Quando l'utente richiama il comando di menu Convalida.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Quando viene aperto il file di modello.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Quando viene salvato il file di modello. Se sono presenti errori di convalida, l'utente potrà scegliere se annullare l'operazione di salvataggio.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Quando viene salvato il file di modello. Se sono presenti errori di metodi in questa categoria, l'utente viene avvertito che potrebbe risultare impossibile riaprire il file.<br /><br /> Usare questa categoria per i metodi di convalida che verificano l'esistenza di nomi o ID duplicati o altre condizioni che potrebbero causare errori di caricamento.|
|<xref:Microsoft.VisualStudio.Modeling.Validation.ValidationCategories>|Quando viene chiamato il metodo ValidateCustom. Le convalide in questa categoria possono essere richiamate solo dal codice programma.<br /><br /> Per altre informazioni, vedere [Categorie di convalida personalizzate.](#custom)|

## <a name="where-to-place-validation-methods"></a>Dove inserire i metodi di convalida
 È spesso possibile ottenere lo stesso effetto inserendo un metodo di convalida in un tipo diverso. Ad esempio, è possibile aggiungere un metodo alla classe Person invece della relazione ParentsHaveChildren e fare in modo che esegua l'iterazione tramite i collegamenti:

```
[ValidationState(ValidationState.Enabled)]
public partial class Person
{[ValidationMethod
 ( ValidationCategories.Open
 | ValidationCategories.Save
 | ValidationCategories.Menu
 )
]
  private void ValidateParentBirth(ValidationContext context)
  {
    // Iterate through ParentHasChildren links:
    foreach (Person parent in this.Parents)
    {
        if (this.BirthYear <= parent.BirthYear)
        { ...
```

 **Aggregazione dei vincoli di convalida.**  Per applicare la convalida in un ordine prevedibile, definire un singolo metodo di convalida in una classe proprietario, ad esempio l'elemento radice del modello. Questa tecnica consente inoltre di aggregare più segnalazioni in un unico messaggio.

 Presenta però alcuni svantaggi, in quanto il metodo combinato è più difficile da gestire e i vincoli devono includere tutti gli stessi attributi `ValidationCategories`. Se possibile, è quindi consigliabile mantenere ogni vincolo in un metodo separato.

 **Passaggio di valori nella cache del contesto.**  Il parametro del contesto include un dizionario in cui è possibile inserire valori arbitrari. Il dizionario viene mantenuto per tutta la durata della convalida. Un particolare metodo di convalida potrebbe, ad esempio, mantenere un conteggio degli errori nel contesto e usarlo per evitare di visualizzare nella finestra degli errori un numero elevato di messaggi ripetuti. Ad esempio:

```csharp
List<ParentsHaveChildren> erroneousLinks;
if (!context.TryGetCacheValue("erroneousLinks", out erroneousLinks))
erroneousLinks = new List<ParentsHaveChildren>();
erroneousLinks.Add(this);
context.SetCacheValue("erroneousLinks", erroneousLinks);
if (erroneousLinks.Count < 5) { context.LogError( ... ); }
```

## <a name="validation-of-multiplicities"></a>Convalida delle molteplicità
 I metodi di convalida per verificare la molteplicità minima vengono generati automaticamente per il linguaggio specifico di dominio. Il codice viene scritto in **Dsl\Generated Code\MultiplicityValidation.cs**. Questi metodi hanno effetto quando si abilita la convalida nel nodo **Editor\Convalida** in Esplora DSL.

 Se si imposta la molteplicità di un ruolo di una relazione di dominio su 1..* o 1..1, ma l'utente non crea un collegamento di questa relazione, verrà visualizzato un messaggio di errore di convalida.

 Ad esempio, se il DSL include le classi Person e Town e una relazione PersonLivesIn Town con una relazione **1.. \\** * con il ruolo Città, quindi per ogni persona senza Città verrà visualizzato un messaggio di errore.

## <a name="running-validation-from-program-code"></a>Esecuzione della convalida dal codice programma
 È possibile eseguire la convalida creando o accedendo a un oggetto ValidationController. Se si vuole che gli errori siano visualizzati all'utente nella finestra degli errori, usare validationController collegato a DocData del diagramma. Ad esempio, se si intende scrivere un comando di menu, `CurrentDocData.ValidationController` è disponibile nella classe del set di comandi:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
partial class MyLanguageCommandSet
{
  private void OnMenuMyContextMenuCommand(object sender, EventArgs e)
  {
   ValidationController controller = this.CurrentDocData.ValidationController;
...
```

 Per altre informazioni, vedere [Procedura: Aggiungere un comando al menu di scelta rapida.](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)

 È anche possibile creare un controller di convalida separato e gestire gli errori manualmente. Ad esempio:

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
using Microsoft.VisualStudio.Modeling.Shell;
...
Store store = ...;
VsValidationController validator = new VsValidationController(s);
// Validate all elements in the Store:
if (!validator.Validate(store, ValidationCategories.Save))
{
  // Deal with errors:
  foreach (ValidationMessage message in validator.ValidationMessages) { ... }
}
```

## <a name="running-validation-when-a-change-occurs"></a>Esecuzione della convalida in caso di modifica
 Se si vuole che l'utente venga avvertito immediatamente nel caso in cui il modello non è più valido, è possibile definire un evento dell'archivio che esegue la convalida. Per altre informazioni sugli eventi di archiviazione, vedere [Gestori eventi Propagare modifiche all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Oltre al codice di convalida, aggiungere un file di codice personalizzato al progetto **DslPackage,** con contenuto simile all'esempio seguente. Questo codice usa il controller `ValidationController` allegato al documento. Questo controller visualizza gli errori di convalida nell'Visual Studio degli errori.

```csharp
using System;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Validation;
namespace Company.FamilyTree
{
  partial class FamilyTreeDocData // Change name to your DocData.
  {
    // Register the store event handler:
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded();
      DomainClassInfo observedLinkInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(ParentsHaveChildren));
      DomainClassInfo observedClassInfo = this.Store.DomainDataDirectory
         .FindDomainClass(typeof(Person));
      EventManagerDirectory events = this.Store.EventManagerDirectory;
      events.ElementAdded
         .Add(observedLinkInfo, new EventHandler<ElementAddedEventArgs>(ParentLinkAddedHandler));
      events.ElementDeleted.Add(observedLinkInfo, new EventHandler<ElementDeletedEventArgs>(ParentLinkDeletedHandler));
      events.ElementPropertyChanged.Add(observedClassInfo, new EventHandler<ElementPropertyChangedEventArgs>(BirthDateChangedHandler));
    }
    // Handler will be called after transaction that creates a link:
    private void ParentLinkAddedHandler(object sender,
                                ElementAddedEventArgs e)
    {
      this.ValidationController.Validate(e.ModelElement,
           ValidationCategories.Save);
    }
    // Called when a link is deleted:
    private void ParentLinkDeletedHandler(object sender,
                                ElementDeletedEventArgs e)
    {
      // Don't apply validation to a deleted item!
      // - Validate store to refresh the error list.
      this.ValidationController.Validate(this.Store,
           ValidationCategories.Save);
    }
    // Called when any property of a Person element changes:
    private void BirthDateChangedHandler(object sender,
                      ElementPropertyChangedEventArgs e)
    {
      Person person = e.ModelElement as Person;
      // Not interested in changes in other properties:
      if (e.DomainProperty.Id != Person.BirthYearDomainPropertyId)
          return;

      // Validate all parent links to and from the person:
      this.ValidationController.Validate(
        ParentsHaveChildren.GetLinksToParents(person)
        .Concat(ParentsHaveChildren.GetLinksToChildren(person))
        , ValidationCategories.Save);
    }
  }
}
```

 I gestori vengono inoltre chiamati dopo operazioni Undo o Redo che influiscono su collegamenti o elementi.

## <a name="custom-validation-categories"></a><a name="custom"></a> Categorie di convalida personalizzate
 Oltre alle categorie di convalida standard, come Menu e Open, è possibile definire categorie personalizzate e richiamarle dal codice programma. L'utente non può invece richiamarle direttamente.

 Le categorie personalizzate vengono in genere usate per definire una categoria che verifica se il modello soddisfa le precondizioni di un determinato strumento.

 Per aggiungere un metodo di convalida a una determinata categoria, specificare prima del nome un attributo simile al seguente:

```csharp
[ValidationMethod(CustomCategory = "PreconditionsForGeneratePartsList")]
[ValidationMethod(ValidationCategory.Menu)]
private void TestForCircularLinks(ValidationContext context)
{...}
```

> [!NOTE]
> Prima di un metodo è possibile specificare il numero desiderato di attributi `[ValidationMethod()]`. È possibile aggiungere un metodo sia a categorie standard che personalizzate.

 Per richiamare una convalida personalizzata:

```csharp

// Invoke all validation methods in a custom category:
validationController.ValidateCustom
  (store, // or a list of model elements
   "PreconditionsForGeneratePartsList");
```

## <a name="alternatives-to-validation"></a><a name="alternatives"></a> Alternative alla convalida
 I vincoli di convalida segnalano gli errori, ma non modificano il modello. Se, invece, si vuole evitare che il modello non sia più valido, è possibile usare altre tecniche,

 che però non sono consigliate. È in genere preferibile lasciare che sia l'utente a decidere come correggere un modello non valido.

 **Adattare la modifica per ottenere nuovamente un modello valido.**  Se ad esempio un utente imposta una proprietà su un valore superiore a quello massimo consentito, è possibile ripristinare la proprietà sul valore massimo, definendo a tale scopo una regola. Per altre informazioni, vedere [Regole propagare le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

 **Eseguire il rollback della transazione se si prova a effettuare una modifica non valida.** È anche possibile definire una regola a questo scopo, ma in alcuni casi è possibile eseguire l'override di un gestore di proprietà **OnValueChanging()** o eseguire l'override di un metodo come Per eseguire il rollback di una transazione, usare Per altre informazioni, vedere Gestori delle modifiche del valore della proprietà di dominio `OnDeleted().` `this.Store.TransactionManager.CurrentTransaction.Rollback().` . [](../modeling/domain-property-value-change-handlers.md)

> [!WARNING]
> Assicurarsi di informare l'utente dell'adattamento della modifica o del rollback. Ad esempio, usare `System.Windows.Forms.MessageBox.Show("message").`

## <a name="see-also"></a>Vedi anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)
