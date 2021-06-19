---
title: Definizione di un criterio di blocco per creare segmenti di sola lettura
description: Informazioni su come definire un criterio per un programma per bloccare parte o tutto un modello DSL (Domain Specific Language) in modo che possa essere letto ma non modificato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385786"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>Definizione di un criterio di blocco per creare segmenti di sola lettura
L'API di immutabilità di Visual Studio Visualization and Modeling SDK consente a un programma di bloccare parte o tutto un modello di linguaggio specifico di dominio (DSL) in modo che possa essere letto ma non modificato. Questa opzione di sola lettura può essere usata, ad esempio, in modo che un utente possa chiedere ai colleghi di annotare ed esaminare un modello DSL, ma può non consentire loro di modificare l'originale.

 Inoltre, in quanto autore di un DSL, è possibile definire criteri *di blocco.* I criteri di blocco definiscono quali blocchi sono consentiti, non consentiti o obbligatori. Ad esempio, quando si pubblica un DSL, è possibile incoraggiare gli sviluppatori di terze parti a estenderlo con nuovi comandi. Ma è anche possibile usare criteri di blocco per impedire loro di modificare lo stato di sola lettura delle parti specificate del modello.

> [!NOTE]
> I criteri di blocco possono essere aggirati tramite reflection. Fornisce un limite chiaro per gli sviluppatori di terze parti, ma non offre una sicurezza avanzata.

 Altre informazioni ed esempi sono disponibili nel sito Web Visual Studio [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) .

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>Impostazione e recupero di blocchi
 È possibile impostare blocchi sull'archivio, su una partizione o su un singolo elemento. Ad esempio, questa istruzione impedirà l'eliminazione di un elemento del modello e impedirà anche la modifica delle relative proprietà:

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 È possibile usare altri valori di blocco per impedire modifiche nelle relazioni, nella creazione di elementi, nello spostamento tra partizioni e nel riordinamento dei collegamenti in un ruolo.

 I blocchi si applicano sia alle azioni dell'utente che al codice programma. Se il codice programma tenta di apportare una modifica, `InvalidOperationException` verrà generata un'eccezione . I blocchi vengono ignorati in un'operazione di annullamento o ripristino.

 È possibile determinare se un elemento dispone di un blocco in un determinato set utilizzando ed è possibile ottenere il set corrente di blocchi su un `IsLocked(Locks)` elemento tramite `GetLocks()` .

 È possibile impostare un blocco senza utilizzare una transazione. Il database di blocco non fa parte dell'archivio. Se si imposta un blocco in risposta a una modifica di un valore nell'archivio, ad esempio in OnValueChanged, è necessario consentire le modifiche che fanno parte di un'operazione di annullamento.

 Questi metodi sono metodi di estensione definiti nello spazio dei <xref:Microsoft.VisualStudio.Modeling.Immutability> nomi .

### <a name="locks-on-partitions-and-stores"></a>Blocchi su partizioni e archivi
 I blocchi possono essere applicati anche alle partizioni e all'archivio. Un blocco impostato su una partizione si applica a tutti gli elementi nella partizione. L'istruzione seguente, ad esempio, impedirà l'eliminazione di tutti gli elementi di una partizione, indipendentemente dagli stati dei relativi blocchi. Tuttavia, altri blocchi, ad esempio `Locks.Property` , possono essere ancora impostati sui singoli elementi:

```csharp
partition.SetLocks(Locks.Delete);
```

 Un blocco impostato nell'archivio si applica a tutti i relativi elementi, indipendentemente dalle impostazioni del blocco sulle partizioni e sugli elementi.

### <a name="using-locks"></a>Uso dei blocchi
 È possibile usare i blocchi per implementare schemi come gli esempi seguenti:

- Non consentire modifiche a tutti gli elementi e a tutte le relazioni, ad eccezione di quelli che rappresentano commenti. In questo modo gli utenti possono annotare un modello senza modificarlo.

- Non consentire modifiche nella partizione predefinita, ma consentire modifiche nella partizione del diagramma. L'utente può ridisporre il diagramma, ma non può modificare il modello sottostante.

- Non consentire modifiche all'archivio, ad eccezione di un gruppo di utenti registrati in un database separato. Per altri utenti, il diagramma e il modello sono di sola lettura.

- Non consentire modifiche al modello se una proprietà booleana del diagramma è impostata su true. Specificare un comando di menu per modificare tale proprietà. In questo modo si garantisce agli utenti di non apportare modifiche accidentalmente.

- Non consente l'aggiunta e l'eliminazione di elementi e relazioni di classi specifiche, ma consente modifiche alle proprietà. In questo modo gli utenti hanno un modulo fisso in cui possono compilare le proprietà.

## <a name="lock-values"></a>Valori di blocco
 I blocchi possono essere impostati su un archivio, una partizione o un singolo ModelElement. Locks è `Flags` un'enumerazione: è possibile combinarne i valori usando "&#124;".

- I blocchi di un ModelElement includono sempre i blocchi della relativa partizione.

- I blocchi di una partizione includono sempre i blocchi dell'archivio.

  Non è possibile impostare un blocco su una partizione o un archivio e allo stesso tempo disabilitare il blocco su un singolo elemento.

|Valore|Significato se `IsLocked(Value)` è true|
|-|-|
|Nessuno|Nessuna restrizione.|
|Proprietà|Le proprietà di dominio degli elementi non possono essere modificate. Questo non si applica alle proprietà generate dal ruolo di una classe di dominio in una relazione.|
|Add|Non è possibile creare nuovi elementi e collegamenti in una partizione o in un archivio.<br /><br /> Non applicabile a `ModelElement` .|
|Sposta|L'elemento non può essere spostato tra partizioni `element.IsLocked(Move)` se è true o se è `targetPartition.IsLocked(Move)` true.|
|Delete|Un elemento non può essere eliminato se questo blocco è impostato sull'elemento stesso o su uno qualsiasi degli elementi a cui l'eliminazione verrebbe propagata, ad esempio gli elementi incorporati e le forme.<br /><br /> È possibile usare `element.CanDelete()` per determinare se un elemento può essere eliminato.|
|Riordinare|L'ordinamento dei collegamenti in un ruolo non può essere modificato.|
|RolePlayer|Il set di collegamenti di origine in questo elemento non può essere modificato. Ad esempio, i nuovi elementi non possono essere incorporati in questo elemento. Ciò non influisce sui collegamenti per i quali questo elemento è la destinazione.<br /><br /> Se questo elemento è un collegamento, l'origine e la destinazione non sono interessate.|
|Tutti|OR bit per bit degli altri valori.|

## <a name="locking-policies"></a>Criteri di blocco
 In quanto autore di un DSL, è possibile definire un *criterio di blocco*. I criteri di blocco moderano il funzionamento di SetLocks(), in modo da impedire l'impostazione di blocchi specifici o l'impostazione di blocchi specifici. In genere, si usano criteri di blocco per sconsigliare a utenti o sviluppatori di violare accidentalmente l'uso previsto di un DSL, nello stesso modo in cui è possibile dichiarare una variabile `private` .

 È anche possibile usare criteri di blocco per impostare blocchi su tutti gli elementi dipendenti dal tipo dell'elemento. Questo perché viene sempre chiamato quando un elemento viene creato o `SetLocks(Locks.None)` deserializzato per la prima volta dal file.

 Tuttavia, non è possibile usare un criterio per variare i blocchi su un elemento durante il suo ciclo di vita. Per ottenere questo effetto, è necessario usare le chiamate a `SetLocks()` .

 Per definire un criterio di blocco, è necessario:

- Creare una classe che implementi <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>.

- Aggiungere questa classe ai servizi disponibili tramite DocData del DSL.

### <a name="to-define-a-locking-policy"></a>Per definire un criterio di blocco
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> ha la definizione seguente:

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 Questi metodi vengono chiamati quando viene effettuata una chiamata `SetLocks()` a in un oggetto Store, Partition o ModelElement. In ogni metodo viene fornito un set proposto di blocchi. È possibile restituire il set proposto oppure aggiungere e sottrarre blocchi.

 Ad esempio:

```csharp
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

 Per assicurarsi che gli utenti possano sempre eliminare elementi, anche se altre chiamate di codice `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 Per non consentire la modifica di tutte le proprietà di ogni elemento di MyClass:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>Per rendere i criteri disponibili come servizio
 Nel progetto aggiungere un nuovo file contenente codice simile `DslPackage` all'esempio seguente:

```csharp
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
