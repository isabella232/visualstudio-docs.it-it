---
title: Le regole propagano le modifiche all'interno del modello
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 808eecab2b4f468b730b6c58cce32d08ca523d0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660315"
---
# <a name="rules-propagate-changes-within-the-model"></a>Le regole propagano le modifiche all'interno del modello
È possibile creare una regola di archiviazione per propagare una modifica da un elemento a un altro nell'SDK di visualizzazione e modellazione (VMSDK). Quando si verifica una modifica a qualsiasi elemento nell'archivio, le regole vengono pianificate per l'esecuzione, in genere quando viene eseguito il commit della transazione più esterna. Esistono diversi tipi di regole per diversi tipi di eventi, ad esempio l'aggiunta o l'eliminazione di un elemento. È possibile alleghi regole a tipi specifici di elementi, forme o diagrammi. Molte funzionalità predefinite sono definite da regole: ad esempio, le regole assicurano che un diagramma venga aggiornato quando il modello viene modificato. È possibile personalizzare il linguaggio specifico di dominio aggiungendo regole personalizzate.

 Le regole di archiviazione sono particolarmente utili per la propagazione delle modifiche all'interno dell'archivio, ovvero modifiche a elementi del modello, relazioni, forme o connettori e alle relative proprietà del dominio. Quando l'utente richiama i comandi Annulla o Ripeti, le regole non vengono eseguite. Il gestore delle transazioni verifica invece che il contenuto dell'archivio venga ripristinato nello stato corretto. Se si desidera propagare le modifiche alle risorse all'esterno dello Store, utilizzare gli eventi di archiviazione. Per ulteriori informazioni, vedere [i gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

 Si supponga, ad esempio, di voler specificare che ogni volta che l'utente (o il codice) crea un nuovo elemento di tipo ExampleDomainClass, viene creato un elemento aggiuntivo di un altro tipo in un'altra parte del modello. È possibile scrivere un AddRule e associarlo a ExampleDomainClass. Scrivere il codice nella regola per creare l'elemento aggiuntivo.

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
> Il codice di una regola deve modificare lo stato solo degli elementi all'interno dell'archivio; ovvero la regola deve modificare solo gli elementi del modello, le relazioni, le forme, i connettori, i diagrammi o le relative proprietà. Se si desidera propagare le modifiche alle risorse all'esterno dell'archivio, definire gli eventi dell'archivio. Per ulteriori informazioni, vedere [i gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

### <a name="to-define-a-rule"></a>Per definire una regola

1. Definire la regola come una classe preceduta dall'attributo `RuleOn`. L'attributo associa la regola a una delle classi di dominio, relazioni o elementi del diagramma. La regola verrà applicata a ogni istanza di questa classe, che può essere astratta.

2. Registrare la regola aggiungendola al set restituito da `GetCustomDomainModelTypes()` nella classe del modello di dominio.

3. Derivare la classe Rule da una delle classi di regole astratte e scrivere il codice del metodo di esecuzione.

   Le sezioni seguenti descrivono questi passaggi in modo più dettagliato.

### <a name="to-define-a-rule-on-a-domain-class"></a>Per definire una regola in una classe di dominio

- In un file di codice personalizzato definire una classe e precedere l'attributo <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute>:

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- Il tipo di oggetto nel primo parametro può essere una classe di dominio, una relazione di dominio, una forma, un connettore o un diagramma. In genere, le regole vengono applicate alle relazioni e alle classi di dominio.

     Il `FireTime` è in genere `TopLevelCommit`. In questo modo si garantisce che la regola venga eseguita solo dopo che sono state apportate tutte le modifiche primarie della transazione. Le alternative sono inline, che esegue la regola subito dopo la modifica. e LocalCommit, che esegue la regola alla fine della transazione corrente (che potrebbe non essere quella più esterna). È anche possibile impostare la priorità di una regola in modo da influire sull'ordinamento nella coda, ma si tratta di un metodo non affidabile per ottenere il risultato richiesto.

- È possibile specificare una classe astratta come tipo di oggetto.

- La regola si applica a tutte le istanze della classe Subject.

- Il valore predefinito per `FireTime` è TimeToFire. TopLevelCommit. In questo modo la regola viene eseguita quando viene eseguito il commit della transazione più esterna. Un'alternativa è TimeToFire. inline. In questo modo la regola viene eseguita subito dopo l'evento di attivazione.

### <a name="to-register-the-rule"></a>Per registrare la regola

- Aggiungere la classe Rule all'elenco di tipi restituiti da `GetCustomDomainModelTypes` nel modello di dominio:

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

- Se non si è certi del nome della classe del modello di dominio, cercare nel file **Dsl\GeneratedCode\DomainModel.cs**

- Scrivere questo codice in un file di codice personalizzato nel progetto DSL.

### <a name="to-write-the-code-of-the-rule"></a>Per scrivere il codice della regola

- Derivare la classe Rule da una delle classi base seguenti:

  | Classe base | Trigger |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | Viene aggiunto un elemento, un collegamento o una forma.<br /><br /> Usare questa funzionalità per rilevare nuove relazioni, oltre ai nuovi elementi. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | Viene modificato un valore della proprietà di dominio. L'argomento Method fornisce i valori vecchi e nuovi.<br /><br /> Per le forme, questa regola viene attivata quando la proprietà `AbsoluteBounds` predefinita viene modificata, se la forma viene spostata.<br /><br /> In molti casi, è più pratico eseguire l'override di `OnValueChanged` o `OnValueChanging` nel gestore della proprietà. Questi metodi vengono chiamati immediatamente prima e dopo la modifica. Al contrario, la regola viene in genere eseguita alla fine della transazione. Per altre informazioni, vedere [gestori delle modifiche dei valori delle proprietà del dominio](../modeling/domain-property-value-change-handlers.md). **Nota:**  Questa regola non viene attivata quando viene creato o eliminato un collegamento. Scrivere invece un `AddRule` e un `DeleteRule` per la relazione di dominio. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | Attivato quando un elemento o un collegamento sta per essere eliminato. La proprietà ModelElement. IsTrue è true fino alla fine della transazione. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | Eseguita quando un elemento o un collegamento è stato eliminato. La regola viene eseguita dopo l'esecuzione di tutte le altre regole, incluso DeletingRules. ModelElement. IsTrue è false e ModelElement. l'eliminazione è true. Per consentire un'operazione di annullamento successiva, l'elemento non viene effettivamente rimosso dalla memoria, ma viene rimosso da Store. ElementDirectory. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | Un elemento viene spostato da una partizione di archivio a un'altra.<br /><br /> (Si noti che questo non è correlato alla posizione grafica di una forma). |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | Questa regola si applica solo alle relazioni di dominio. Viene attivato se si assegna in modo esplicito un elemento del modello a una delle estremità di un collegamento. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | Attivato quando l'ordinamento dei collegamenti a o da un elemento viene modificato usando i metodi MoveBefore o MoveToIndex su un collegamento. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | Eseguito quando viene creata una transazione. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | Eseguita quando sta per essere eseguito il commit della transazione. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | Eseguito quando si sta per eseguire il rollback della transazione. |

- Ogni classe dispone di un metodo di cui è stato eseguito l'override. Digitare `override` nella classe per individuarlo. Il parametro di questo metodo identifica l'elemento da modificare.

  Si notino le seguenti considerazioni sulle regole:

1. Il set di modifiche in una transazione potrebbe attivare numerose regole. In genere, le regole vengono eseguite quando viene eseguito il commit della transazione più esterna. Vengono eseguite in un ordine non specificato.

2. Una regola viene sempre eseguita all'interno di una transazione. Pertanto, non è necessario creare una nuova transazione per apportare modifiche.

3. Le regole non vengono eseguite quando viene eseguito il rollback di una transazione o quando vengono eseguite le operazioni di annullamento o ripristino. Queste operazioni ripristinano lo stato precedente di tutto il contenuto dell'archivio. Pertanto, se la regola modifica lo stato di qualsiasi elemento all'esterno dell'archivio, potrebbe non mantenersi sincronizzato con il contenuto dell'archivio. Per aggiornare lo stato all'esterno dell'archivio, è preferibile usare gli eventi. Per ulteriori informazioni, vedere [i gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

4. Alcune regole vengono eseguite quando un modello viene caricato da un file. Per determinare se è in corso il caricamento o il salvataggio, utilizzare `store.TransactionManager.CurrentTransaction.IsSerializing`.

5. Se il codice della regola crea più trigger di regola, verranno aggiunti alla fine dell'elenco di attivazione e verranno eseguiti prima del completamento della transazione. DeletedRules vengono eseguiti dopo tutte le altre regole. Una regola può essere eseguita molte volte in una transazione, una volta per ogni modifica.

6. Per passare informazioni a e da regole, è possibile archiviare le informazioni nel `TransactionContext`. Si tratta semplicemente di un dizionario mantenuto durante la transazione. Viene eliminato al termine della transazione. Gli argomenti dell'evento in ogni regola forniscono l'accesso. Tenere presente che le regole non vengono eseguite in un ordine prevedibile.

7. Usare le regole dopo aver valutato le altre alternative. Se, ad esempio, si desidera aggiornare una proprietà quando un valore viene modificato, è consigliabile utilizzare una proprietà calcolata. Se si desidera vincolare le dimensioni o la posizione di una forma, utilizzare un `BoundsRule`. Se si desidera rispondere a una modifica in un valore di proprietà, aggiungere un gestore di `OnValueChanged` alla proprietà. Per ulteriori informazioni, vedere [risposta a e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

## <a name="example"></a>Esempio
 Nell'esempio seguente viene aggiornata una proprietà quando viene creata un'istanza di una relazione di dominio per collegare due elementi. La regola verrà attivata non solo quando l'utente crea un collegamento in un diagramma, ma anche se il codice programma crea un collegamento.

 Per testare questo esempio, creare un linguaggio DSL usando il modello di soluzione flusso attività e inserire il codice seguente in un file nel progetto DSL. Compilare ed eseguire la soluzione e aprire il file di esempio nel progetto di debug. Disegnare un collegamento commento tra una forma commento e un elemento Flow. Il testo del commento cambia in modo da creare un report sull'elemento più recente a cui si è connessi.

 In pratica, in genere si scrive un DeleteRule per ogni AddRule.

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

## <a name="see-also"></a>Vedere anche

- [I gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)