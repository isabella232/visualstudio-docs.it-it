---
title: Le regole propagano le modifiche apportate all'interno del modello | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 265d04306b4747a4e5bc04b879b9635e81ed8102
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831198"
---
# <a name="rules-propagate-changes-within-the-model"></a>Le regole propagano le modifiche all'interno del modello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile creare una regola di archivio per propagare una modifica da un elemento a un altro in Visualization and Modeling SDK (VMSDK). Quando viene apportata una modifica a qualsiasi elemento nella finestra di Store, le regole vengono pianificate da eseguire, in genere quando viene eseguito il commit della transazione più esterna. Esistono diversi tipi di regole per diversi tipi di eventi, ad esempio aggiungendo un elemento o l'eliminazione. È possibile collegare regole a tipi specifici di elementi, forme o i diagrammi. Molte funzionalità incorporate sono definite da regole: ad esempio, le regole di assicurano che un diagramma viene aggiornato quando viene modificato il modello. È possibile personalizzare il linguaggio specifico di dominio tramite l'aggiunta di regole personalizzate.  

 Le regole di Store sono particolarmente utili per la propagazione delle modifiche all'interno dell'archivio, vale a dire, le modifiche a elementi del modello, relazioni, forme o connettori e il dominio delle proprietà. Le regole non vengono eseguiti quando l'utente richiama i comandi di annullamento o ripristino. Al contrario, il gestore delle transazioni consente di assicurarsi che il contenuto dell'archivio viene ripristinato allo stato corretto. Se si desidera propagare le modifiche alle risorse all'esterno dell'archivio, usare gli eventi Store. Per altre informazioni, vedere [gestori di propagare le modifiche di fuori il modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  

 Si supponga, ad esempio, che si desidera specificare che ogni volta che l'utente (o il codice) crea un nuovo elemento di tipo ExampleDomainClass, viene creato un ulteriore elemento di un altro tipo in un'altra parte del modello. È possibile scrivere un AddRule e associarlo a ExampleDomainClass. Scrivere codice nella regola per creare l'elemento aggiuntiva.  

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

    // Code here propagates change as required – for example:  
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
>  Il codice di una regola deve modificare lo stato solo degli elementi all'interno di Store; vale a dire, la regola deve modificare solo gli elementi del modello, relazioni, forme, connettori, diagrammi o le relative proprietà. Se si desidera propagare le modifiche alle risorse all'esterno dell'archivio, definire gli eventi Store. Per altre informazioni, vedere [gestori propagare le modifiche apportate di fuori il modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md)  

### <a name="to-define-a-rule"></a>Per definire una regola  

1. Definire la regola come preceduto da una classe di `RuleOn` attributo. L'attributo associa la regola con le classi di dominio, relazioni o gli elementi del diagramma. La regola verrà applicata a tutte le istanze di questa classe, che può essere astratta.  

2. Registrare la regola, aggiungerla al set restituito da `GetCustomDomainModelTypes()` della classe di modello di dominio.  

3. Derivare la classe di regola da una delle classi astratte regola e scrivere il codice del metodo di esecuzione.  

   Le sezioni seguenti descrivono questi passaggi in maggiore dettaglio.  

### <a name="to-define-a-rule-on-a-domain-class"></a>Per definire una regola in una classe di dominio  

-   In un file di codice personalizzato, definire una classe e prefisso di <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> attributo:  

    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  

    ```  

-   Il tipo di oggetto nel primo parametro può essere una classe di dominio, relazione di dominio, la forma, connettore o diagramma. In genere, viene applicato le regole per le relazioni e le classi di dominio.  

     Il `FireTime` è in genere `TopLevelCommit`. Ciò garantisce che la regola viene eseguita solo dopo aver apportate tutte le modifiche principali della transazione. Le alternative sono Inline, che viene eseguita la regola subito dopo la modifica. e LocalCommit, che esegue la regola alla fine della transazione corrente (che potrebbe non essere più esterna). È anche possibile impostare la priorità di una regola per influire sul relativo ordine nella coda, ma questo è un metodo affidabile per ottenere il risultato desiderato.  

-   È possibile specificare una classe astratta come tipo di oggetto.  

-   La regola si applica a tutte le istanze della classe dell'oggetto.  

-   Il valore predefinito per `FireTime` è TimeToFire.TopLevelCommit. In questo modo la regola deve essere eseguito quando viene eseguito il commit della transazione più esterna. In alternativa, è TimeToFire.Inline. In questo modo la regola deve essere eseguito subito dopo l'evento di attivazione.  

### <a name="to-register-the-rule"></a>Per registrare la regola  

-   Aggiungere la classe di regola per l'elenco dei tipi restituiti da `GetCustomDomainModelTypes` nel modello di dominio:  

    ```  
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

-   Se non è certi del nome della classe del modello di dominio, Cerca all'interno del file **Dsl\GeneratedCode\DomainModel.cs**  

-   Scrivere il codice in un file di codice personalizzato nel progetto DSL.  

### <a name="to-write-the-code-of-the-rule"></a>Per scrivere il codice della regola  

- Derivare la classe di regola da una delle classi base seguenti:  


  |                             Classe base                              |                                                                                                                                                                                                                                                                                                                                                                              Trigger                                                                                                                                                                                                                                                                                                                                                                              |
  |---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |           <xref:Microsoft.VisualStudio.Modeling.AddRule>            |                                                                                                                                                                                                                                                                                                                        Viene aggiunto un elemento, un collegamento o una forma.<br /><br /> Questa procedura guidata consente di rilevare relazioni nuove, oltre a nuovi elementi.                                                                                                                                                                                                                                                                                                                        |
  |          <xref:Microsoft.VisualStudio.Modeling.ChangeRule>          | Il valore di una proprietà di dominio viene modificato. L'argomento del metodo fornisce i valori vecchi e nuovi.<br /><br /> Per le forme, questa regola viene attivata quando l'elemento predefinito `AbsoluteBounds` le modifiche alle proprietà, se la forma viene spostata.<br /><br /> In molti casi, risulta più semplice eseguire l'override `OnValueChanged` o `OnValueChanging` nel gestore della proprietà. Questi metodi vengono chiamati immediatamente prima e dopo la modifica. Al contrario, la regola viene in genere eseguito alla fine della transazione. Per altre informazioni, vedere [gestori di Modifica valore proprietà di dominio](../modeling/domain-property-value-change-handlers.md). **Nota:** questa regola non viene generata quando viene creato o eliminato un collegamento. Invece di scrivere un' `AddRule` e un `DeleteRule` della relazione di dominio. |
  |         <xref:Microsoft.VisualStudio.Modeling.DeletingRule>         |                                                                                                                                                                                                                                                                                                             Attivato quando un elemento o un collegamento sta per essere eliminato. La proprietà ModelElement.IsDeleting vale fino alla fine della transazione.                                                                                                                                                                                                                                                                                                              |
  |          <xref:Microsoft.VisualStudio.Modeling.DeleteRule>          |                                                                                                                                                                                                       Eseguito quando un elemento o un collegamento è stato eliminato. La regola viene eseguita dopo che sono state eseguite tutte le altre regole, tra cui DeletingRules. ModelElement.IsDeleting è false e ModelElement.IsDeleted è true. Per consentire una successiva operazione di annullamento, l'elemento non viene effettivamente rimosso dalla memoria, ma viene rimosso dal Store.ElementDirectory.                                                                                                                                                                                                       |
  |           <xref:Microsoft.VisualStudio.Modeling.MoveRule>           |                                                                                                                                                                                                                                                                                                           Un elemento viene spostato da un archivio di partizione a altra.<br /><br /> Si noti che questo non è correlato alla posizione di una forma grafica.                                                                                                                                                                                                                                                                                                            |
  |     <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>     |                                                                                                                                                                                                                                                                                                                 Questa regola si applica solo alle relazioni di dominio. Viene attivato se si assegna in modo esplicito un elemento del modello a un'estremità di un collegamento.                                                                                                                                                                                                                                                                                                                 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> |                                                                                                                                                                                                                                                                                                                   Attivazione eseguita quando l'ordine dei collegamenti verso o da un elemento viene modificato utilizzando i metodi MoveBefore o MoveToIndex su un collegamento.                                                                                                                                                                                                                                                                                                                    |
  |   <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>   |                                                                                                                                                                                                                                                                                                                                                              Eseguito quando viene creata una transazione.                                                                                                                                                                                                                                                                                                                                                              |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>   |                                                                                                                                                                                                                                                                                                                                                      Eseguito quando la transazione sta per essere eseguito il commit.                                                                                                                                                                                                                                                                                                                                                      |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>  |                                                                                                                                                                                                                                                                                                                                                     Eseguito quando la transazione sta per essere eseguito il rollback.                                                                                                                                                                                                                                                                                                                                                     |


- Ogni classe dispone di un metodo che si esegue l'override. Tipo `override` nella classe per individuarlo. Il parametro di questo metodo identifica l'elemento che viene modificato.  

  Si noti che i punti seguenti sulle regole:  

1.  Il set di modifiche in una transazione può attivare molte regole. In genere, le regole vengono eseguite quando viene eseguito il commit della transazione più esterna. Vengono eseguiti in un ordine non specificato.  

2.  Una regola viene sempre eseguita all'interno di una transazione. Pertanto, non è necessario creare una nuova transazione per apportare modifiche.  

3.  Le regole non vengono eseguite quando viene eseguito il rollback di una transazione, o quando vengono eseguite le operazioni di annullamento o ripristino. Queste operazioni Reimposta tutto il contenuto della finestra di Store allo stato precedente. Pertanto, se la regola viene modificato lo stato di qualsiasi elemento all'esterno di Store, potrebbe non tenere synchronism con il Store del contenuto. Per aggiornare lo stato di fuori di Store, è preferibile utilizzare gli eventi. Per altre informazioni, vedere [gestori di propagare le modifiche di fuori il modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  

4.  Alcune regole vengono eseguiti quando un modello viene caricato dal file. Per determinare se il caricamento o salvataggio è in corso, usare `store.TransactionManager.CurrentTransaction.IsSerializing`.  

5.  Se il codice della regola crea ulteriori regola viene attivata, essi verranno aggiunti alla fine dell'elenco di generazione dell'evento e verrà eseguiti prima del completamento della transazione. DeletedRules vengono eseguiti dopo tutte le altre regole. Una regola può eseguire più volte in una transazione, una volta per ogni modifica.  

6.  Per passare informazioni da e verso le regole, è possibile archiviare le informazioni nel `TransactionContext`. Si tratta semplicemente un dizionario che viene mantenuto durante la transazione. Viene eliminato al termine della transazione. Gli argomenti dell'evento in ogni regola forniscono l'accesso a esso. Tenere presente che le regole non vengono eseguite in un ordine prevedibile.  

7.  Usare le regole dopo aver considerato altre alternative. Se si desidera aggiornare una proprietà quando viene modificato un valore, si consideri ad esempio usando una proprietà calcolata. Se si desidera vincolare le dimensioni o il percorso di una forma, utilizzare un `BoundsRule`. Se si desidera rispondere a una modifica nel valore della proprietà, aggiungere un `OnValueChanged` gestore alla proprietà. Per altre informazioni, vedere [procedura: rispondere a e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  

## <a name="example"></a>Esempio  
 Nell'esempio seguente aggiorna una proprietà quando viene creata un'istanza di una relazione di dominio per collegare due elementi. La regola verrà attivata non solo quando l'utente crea un collegamento in un diagramma, ma anche se il codice del programma crea un collegamento.  

 Per testare questo esempio, creare un linguaggio DSL utilizzando il modello di soluzione flusso attività, inserire il codice seguente in un file nel progetto Dsl. Compilare ed eseguire la soluzione e aprire il file di esempio nel progetto di debug. Creare un collegamento commento tra una forma di commento e un elemento del flusso. Report sull'elemento più recente è stata connessa a viene modificato il testo del commento.  

 In pratica, si scriverebbe in genere un DeleteRule per ogni AddRule.  

```  
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
 [I gestori eventi propagano le modifiche apportate all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme](../modeling/boundsrules-constrain-shape-location-and-size.md)



