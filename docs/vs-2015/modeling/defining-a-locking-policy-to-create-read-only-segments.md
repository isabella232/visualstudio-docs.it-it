---
title: Definizione di un criterio di blocco per creare segmenti di sola lettura | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5acbb4d2966e89f7913fa1479b882fad5c9650f7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295812"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definizione di un criterio di blocco per creare segmenti di sola lettura
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'API di immutabilità del [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] SDK di visualizzazione e modellazione consente a un programma di bloccare parte o tutto un modello DSL (Domain-Specific Language) in modo che possa essere letto ma non modificato. Questa opzione di sola lettura può essere usata, ad esempio, in modo che un utente possa chiedere ai colleghi di annotare ed esaminare un modello DSL, ma non di modificare l'originale.

 Inoltre, come autore di un linguaggio DSL, è possibile definire un *criterio di blocco.* Un criterio di blocco definisce quali blocchi sono consentiti, non consentiti o obbligatori. Ad esempio, quando si pubblica un linguaggio DSL, è possibile incoraggiare gli sviluppatori di terze parti a estenderlo con nuovi comandi. Tuttavia, è anche possibile usare un criterio di blocco per impedire che modifichi lo stato di sola lettura delle parti specificate del modello.

> [!NOTE]
> Un criterio di blocco può essere eluso tramite reflection. Fornisce un limite chiaro per gli sviluppatori di terze parti, ma non offre una protezione avanzata.

 Ulteriori informazioni ed esempi sono disponibili nel sito Web di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Visualization and Modeling SDK](https://go.microsoft.com/fwlink/?LinkId=186128) .

## <a name="setting-and-getting-locks"></a>Impostazione e recupero di blocchi
 È possibile impostare blocchi nell'archivio, in una partizione o in un singolo elemento. Questa istruzione, ad esempio, impedisce l'eliminazione di un elemento del modello e impedisce inoltre la modifica delle proprietà:

```
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 È possibile utilizzare altri valori di blocco per impedire modifiche nelle relazioni, creazione di elementi, spostamento tra partizioni e riordinamento di collegamenti in un ruolo.

 I blocchi si applicano sia alle azioni utente che al codice programma. Se il codice programma tenta di apportare una modifica, verrà generata un'`InvalidOperationException`. I blocchi vengono ignorati in un'operazione di annullamento o ripetizione.

 È possibile scoprire se un elemento ha un blocco in un determinato set usando `IsLocked(Locks)` ed è possibile ottenere il set di blocchi corrente su un elemento usando `GetLocks()`.

 È possibile impostare un blocco senza utilizzare una transazione. Il database di blocco non fa parte dell'archivio. Se si imposta un blocco in risposta a una modifica di un valore nell'archivio, ad esempio in OnValueChanged, è necessario consentire le modifiche che fanno parte di un'operazione di annullamento.

 Questi metodi sono metodi di estensione definiti nello spazio dei nomi <xref:Microsoft.VisualStudio.Modeling.Immutability>.

### <a name="locks-on-partitions-and-stores"></a>Blocchi su partizioni e archivi
 I blocchi possono anche essere applicati alle partizioni e all'archivio. Un blocco impostato in una partizione si applica a tutti gli elementi della partizione. Pertanto, ad esempio, l'istruzione seguente impedisce l'eliminazione di tutti gli elementi di una partizione, indipendentemente dagli Stati dei propri blocchi. Tuttavia, altri blocchi come `Locks.Property` possono comunque essere impostati su singoli elementi:

```
partition.SetLocks(Locks.Delete);
```

 Un blocco impostato sull'archivio si applica a tutti i relativi elementi, indipendentemente dalle impostazioni di tale blocco sulle partizioni e sugli elementi.

### <a name="using-locks"></a>Utilizzo di blocchi
 È possibile utilizzare i blocchi per implementare schemi come gli esempi seguenti:

- Non consentire le modifiche a tutti gli elementi e le relazioni ad eccezione di quelli che rappresentano commenti. Ciò consente agli utenti di aggiungere annotazioni a un modello senza modificarlo.

- Non consentire le modifiche nella partizione predefinita, ma consentire le modifiche nella partizione del diagramma. L'utente può ridisporre il diagramma, ma non può modificare il modello sottostante.

- Non consentire le modifiche all'archivio ad eccezione di un gruppo di utenti registrati in un database separato. Per gli altri utenti, il diagramma e il modello sono di sola lettura.

- Non consentire le modifiche al modello se una proprietà booleana del diagramma è impostata su true. Consente di specificare un comando di menu per modificare la proprietà. Ciò consente di garantire agli utenti che non apportano modifiche accidentali.

- Non consente l'aggiunta e l'eliminazione di elementi e relazioni di determinate classi, ma consentono le modifiche alle proprietà. In questo modo gli utenti hanno un formato fisso in cui possono compilare le proprietà.

## <a name="lock-values"></a>Valori di blocco
 I blocchi possono essere impostati in un archivio, una partizione o un singolo ModelElement. Locks è un'enumerazione `Flags`: è possibile combinare i valori con&#124;''.

- I blocchi di un ModelElement includono sempre i blocchi della relativa partizione.

- I blocchi di una partizione includono sempre i blocchi dell'archivio.

  Non è possibile impostare un blocco su una partizione o un archivio e contemporaneamente disabilitare il blocco su un singolo elemento.

|Valore|Indica se `IsLocked(Value)` è true|
|-----------|------------------------------------------|
|Nessuna|Nessuna restrizione.|
|Proprietà|Impossibile modificare le proprietà di dominio degli elementi. Questa operazione non si applica alle proprietà generate dal ruolo di una classe di dominio in una relazione.|
|Aggiungi|Non è possibile creare nuovi elementi e collegamenti in una partizione o in un archivio.<br /><br /> Non applicabile a `ModelElement`.|
|Sposta|Non è possibile spostare l'elemento tra partizioni se `element.IsLocked(Move)` è true o se `targetPartition.IsLocked(Move)` è true.|
|Elimina|Non è possibile eliminare un elemento se questo blocco è impostato sull'elemento stesso o su uno degli elementi a cui l'eliminazione propagherà, ad esempio elementi e forme incorporati.<br /><br /> È possibile utilizzare `element.CanDelete()` per individuare se un elemento può essere eliminato.|
|Riordinare|Non è possibile modificare l'ordine dei collegamenti in un RolePlayer.|
|RolePlayer|Il set di collegamenti originati in questo elemento non può essere modificato. Ad esempio, non è possibile incorporare nuovi elementi in questo elemento. Questa operazione non influisce sui collegamenti per i quali questo elemento è la destinazione.<br /><br /> Se questo elemento è un collegamento, l'origine e la destinazione non sono interessate.|
|Tutte|OR bit per bit degli altri valori.|

## <a name="locking-policies"></a>Criteri di blocco
 Come autore di un linguaggio DSL, è possibile definire un *criterio di blocco*. Un criterio di blocco modera l'operazione di blocchi (), in modo che sia possibile impedire l'impostazione di blocchi specifici o richiedere l'impostazione di blocchi specifici. In genere, è possibile usare un criterio di blocco per impedire a utenti o sviluppatori di contravvenendo accidentalmente l'uso previsto di un linguaggio DSL, nello stesso modo in cui è possibile dichiarare una variabile `private`.

 È anche possibile usare un criterio di blocco per impostare i blocchi su tutti gli elementi che dipendono dal tipo dell'elemento. Questo perché `SetLocks(Locks.None)` viene sempre chiamato quando un elemento viene creato o deserializzato per la prima volta da un file.

 Tuttavia, non è possibile usare un criterio per variare i blocchi di un elemento durante la sua vita. Per ottenere questo risultato, è necessario utilizzare le chiamate a `SetLocks()`.

 Per definire un criterio di blocco, è necessario:

- Creare una classe che implementi <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

- Aggiungere questa classe ai servizi disponibili tramite DocData del linguaggio DSL.

### <a name="to-define-a-locking-policy"></a>Per definire un criterio di blocco
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> presenta la seguente definizione:

```
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Questi metodi vengono chiamati quando viene effettuata una chiamata a `SetLocks()` in un archivio, una partizione o ModelElement. In ogni metodo viene fornito un set di blocchi proposto. È possibile restituire il set proposto oppure è possibile aggiungere e sottrarre blocchi.

 Ad esempio:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }

```

 Per assicurarsi che gli utenti possano sempre eliminare gli elementi, anche se altre chiamate al codice `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Per non consentire la modifica di tutte le proprietà di ogni elemento di MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Per rendere disponibili i criteri come servizio
 Nel progetto `DslPackage` aggiungere un nuovo file contenente codice simile al seguente esempio:

```
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
