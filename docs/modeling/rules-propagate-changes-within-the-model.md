---
title: Le regole propagano le modifiche all'interno del modello
description: Informazioni su come creare una regola dell'archivio per propagare una modifica da un elemento a un altro in Visualization and Modeling SDK (VMSDK).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: f6434d4427371a0e2bd39da7c9979b6c29d521e6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637483"
---
# <a name="rules-propagate-changes-within-the-model"></a>Le regole propagano le modifiche all'interno del modello
È possibile creare una regola dell'archivio per propagare una modifica da un elemento a un altro in Visualization and Modeling SDK (VMSDK). Quando si verifica una modifica a qualsiasi elemento nell'archivio, viene pianificata l'esecuzione delle regole, in genere quando viene eseguito il commit della transazione più esterna. Esistono diversi tipi di regole per tipi diversi di eventi, ad esempio l'aggiunta di un elemento o l'eliminazione. È possibile associare regole a tipi specifici di elementi, forme o diagrammi. Molte funzionalità predefinite sono definite dalle regole: ad esempio, le regole assicurano che un diagramma sia aggiornato quando il modello cambia. È possibile personalizzare il linguaggio specifico di dominio aggiungendo regole personalizzate.

 Le regole dell'archivio sono particolarmente utili per la propagazione delle modifiche all'interno dell'archivio, ad esempio le modifiche agli elementi del modello, alle relazioni, alle forme o ai connettori e alle relative proprietà di dominio. Le regole non vengono eseguite quando l'utente richiama i comandi Annulla o Ripristina. Al contrario, il gestore delle transazioni verifica che il contenuto dell'archivio sia ripristinato allo stato corretto. Se si desidera propagare le modifiche alle risorse esterne all'archivio, usare Store Events.If you want to propagate changes to resources outside the store, use Store Events. Per altre informazioni, vedere [Gestori eventi Propagare modifiche all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Si supponga, ad esempio, di voler specificare che ogni volta che l'utente (o il codice) crea un nuovo elemento di tipo ExampleDomainClass, viene creato un elemento aggiuntivo di un altro tipo in un'altra parte del modello. È possibile scrivere un elemento AddRule e associarlo a ExampleDomainClass. È necessario scrivere codice nella regola per creare l'elemento aggiuntivo.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> Il codice di una regola deve modificare lo stato solo degli elementi all'interno dell'archivio. in altre informazioni, la regola deve modificare solo gli elementi del modello, le relazioni, le forme, i connettori, i diagrammi o le relative proprietà. Per propagare le modifiche alle risorse esterne all'archivio, definire Eventi archivio. Per altre informazioni, vedere [Gestori eventi Propagare modifiche all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Per definire una regola

1. Definire la regola come classe preceduta `RuleOn` dall'attributo . L'attributo associa la regola a una delle classi di dominio, alle relazioni o agli elementi del diagramma. La regola verrà applicata a ogni istanza di questa classe, che può essere astratta.

2. Registrare la regola aggiungendola al set restituito da `GetCustomDomainModelTypes()` nella classe del modello di dominio.

3. Derivare la classe di regole da una delle classi Rule astratte e scrivere il codice del metodo di esecuzione.

   Le sezioni seguenti descrivono questi passaggi in modo più dettagliato.

### <a name="to-define-a-rule-on-a-domain-class"></a>Per definire una regola in una classe di dominio

- In un file di codice personalizzato definire una classe e antefisarla con <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> l'attributo :

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Il tipo di oggetto nel primo parametro può essere una classe di dominio, una relazione di dominio, una forma, un connettore o un diagramma. In genere, si applicano regole alle classi di dominio e alle relazioni.

     È `FireTime` in genere `TopLevelCommit` . In questo modo la regola viene eseguita solo dopo che sono state apportate tutte le modifiche principali della transazione. Le alternative sono Inline, che esegue la regola subito dopo la modifica. e LocalCommit, che esegue la regola alla fine della transazione corrente (che potrebbe non essere la più esterna). È anche possibile impostare la priorità di una regola per influenzarne l'ordinamento nella coda, ma si tratta di un metodo inaffidabile per ottenere il risultato richiesto.

- È possibile specificare una classe astratta come tipo di soggetto.

- La regola si applica a tutte le istanze della classe dell'oggetto .

- Il valore predefinito per `FireTime` è TimeToFire.TopLevelCommit. In questo modo la regola viene eseguita quando viene eseguito il commit della transazione più esterna. Un'alternativa è TimeToFire.Inline. In questo modo la regola verrà eseguita subito dopo l'evento di attivazione.

### <a name="to-register-the-rule"></a>Per registrare la regola

- Aggiungere la classe di regole all'elenco dei tipi restituiti `GetCustomDomainModelTypes` da nel modello di dominio:

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- Se non si è certi del nome della classe del modello di dominio, cercare all'interno del file **Dsl\GeneratedCode\DomainModel.cs**

- Scrivere questo codice in un file di codice personalizzato nel progetto DSL.

### <a name="to-write-the-code-of-the-rule"></a>Per scrivere il codice della regola

- Derivare la classe di regola da una delle classi di base seguenti:

  | Classe base | Trigger |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Viene aggiunto un elemento, un collegamento o una forma.<br /><br /> Usare questa opzione per rilevare nuove relazioni, oltre ai nuovi elementi. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Il valore di una proprietà di dominio viene modificato. L'argomento del metodo fornisce i valori vecchi e nuovi.<br /><br /> Per le forme, questa regola viene attivata quando la proprietà `AbsoluteBounds` predefinita cambia, se la forma viene spostata.<br /><br /> In molti casi, è più comodo eseguire l'override `OnValueChanged` o nel gestore delle `OnValueChanging` proprietà. Questi metodi vengono chiamati immediatamente prima e dopo la modifica. Al contrario, la regola viene in genere eseguita alla fine della transazione. Per altre informazioni, vedere [Gestori delle modifiche del valore della proprietà di dominio](../modeling/domain-property-value-change-handlers.md). **Nota:**  Questa regola non viene attivata quando viene creato o eliminato un collegamento. Scrivere invece un e `AddRule` un per la relazione di `DeleteRule` dominio. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Attivato quando un elemento o un collegamento sta per essere eliminato. La proprietà ModelElement.IsDeleting è true fino alla fine della transazione. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Viene eseguita quando un elemento o un collegamento è stato eliminato. La regola viene eseguita dopo l'esecuzione di tutte le altre regole, tra cui DeletingRules. ModelElement.IsDeleting è false e ModelElement.IsDeleted è true. Per consentire un annullamento successivo, l'elemento non viene effettivamente rimosso dalla memoria, ma viene rimosso da Store.ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Un elemento viene spostato da una partizione dell'archivio a un'altra.<br /><br /> Si noti che questo non è correlato alla posizione grafica di una forma. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Questa regola si applica solo alle relazioni di dominio. Viene attivato se si assegna in modo esplicito un elemento del modello a una delle estremità di un collegamento. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Attivato quando l'ordinamento dei collegamenti da o verso un elemento viene modificato usando i metodi MoveBefore o MoveToIndex in un collegamento. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Eseguito quando viene creata una transazione. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Viene eseguito quando sta per essere eseguito il commit della transazione. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Viene eseguito quando sta per essere eseguito il rollback della transazione. |

- Ogni classe ha un metodo di cui si esegue l'override. Digitare `override` la classe per individuarla. Il parametro di questo metodo identifica l'elemento che viene modificato.

  Si notino i punti seguenti sulle regole:

1. Il set di modifiche in una transazione potrebbe attivare molte regole. In genere, le regole vengono eseguite quando viene eseguito il commit della transazione più esterna. Vengono eseguite in un ordine non specificato.

2. Una regola viene sempre eseguita all'interno di una transazione. Pertanto, non è necessario creare una nuova transazione per apportare modifiche.

3. Le regole non vengono eseguite quando viene eseguito il rollback di una transazione o quando vengono eseguite le operazioni di annullamento o ripristino. Queste operazioni reimpostano tutto il contenuto dello Store allo stato precedente. Pertanto, se la regola modifica lo stato di qualsiasi elemento esterno allo Store, potrebbe non essere sincronizzato con il contenuto dello Store. Per aggiornare lo stato all'esterno dello Store, è meglio usare Eventi. Per altre informazioni, vedere [Gestori eventi Propagare modifiche all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Alcune regole vengono eseguite quando un modello viene caricato da un file. Per determinare se è in corso il caricamento o il salvataggio, usare `store.TransactionManager.CurrentTransaction.IsSerializing` .

5. Se il codice della regola crea altri trigger di regola, verranno aggiunti alla fine dell'elenco di attivazione e verranno eseguiti prima del completamento della transazione. Le regole deletedRules vengono eseguite dopo tutte le altre regole. Una regola può essere eseguita più volte in una transazione, una volta per ogni modifica.

6. Per passare informazioni a e da regole, è possibile archiviare le informazioni in `TransactionContext` . Si tratta solo di un dizionario gestito durante la transazione. Viene eliminato al termine della transazione. Gli argomenti dell'evento in ogni regola forniscono l'accesso ad esso. Tenere presente che le regole non vengono eseguite in un ordine stimabile.

7. Usare le regole dopo aver considerato altre alternative. Ad esempio, se si vuole aggiornare una proprietà quando un valore cambia, è consigliabile usare una proprietà calcolata. Se si desidera vincolare le dimensioni o la posizione di una forma, usare `BoundsRule` . Se si vuole rispondere a una modifica nel valore di una proprietà, aggiungere `OnValueChanged` un gestore alla proprietà . Per altre informazioni, vedere [Risposta e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente viene aggiornata una proprietà quando viene creata un'istanza di una relazione di dominio per collegare due elementi. La regola verrà attivata non solo quando l'utente crea un collegamento in un diagramma, ma anche se il codice del programma crea un collegamento.

 Per testare questo esempio, creare un DSL usando il modello di soluzione Task Flow e inserire il codice seguente in un file nel progetto Dsl. Compilare ed eseguire la soluzione e aprire il file di esempio nel progetto Debug. Disegnare un collegamento di commento tra una forma Commento e un elemento di flusso. Il testo nel commento viene modificato per segnalare l'elemento più recente a cui è stato connesso.

 In pratica, in genere si scrive un elemento DeleteRule per ogni AddRule.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>Vedi anche

- [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)