---
title: 'Procedura: utilizzare le transazioni per aggiornare il modello'
description: Le transazioni assicurano che le modifiche apportate all'archivio siano considerate come un gruppo e come usare le transazioni per aggiornare il modello.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8b1d0914c83a8cc36a389006560401619fab1ef7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122150638"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Procedura: utilizzare le transazioni per aggiornare il modello
Le transazioni assicurano che le modifiche apportate all'archivio siano considerate come un gruppo. È possibile eseguire il commit o il rollback delle modifiche raggruppate come singola unità.

 Ogni volta che il codice del programma modifica, aggiunge o elimina qualsiasi elemento nell'archivio in Visual Studio Visualization and Modeling SDK, deve eseguire questa operazione all'interno di una transazione. Quando si verifica la modifica, deve essere presente un'istanza attiva di <xref:Microsoft.VisualStudio.Modeling.Transaction> associata all'archivio. Questo vale per tutti gli elementi del modello, le relazioni, le forme, i diagrammi e le relative proprietà.

 Il meccanismo di transazione consente di evitare stati incoerenti. Se si verifica un errore durante una transazione, viene eseguito il rollback di tutte le modifiche. Se l'utente esegue un comando Annulla, ogni transazione recente viene considerata come un singolo passaggio. L'utente non può annullare parti di una modifica recente, a meno che non vengano esplicitamente inserite in transazioni separate.

## <a name="opening-a-transaction"></a>Apertura di una transazione
 Il metodo più pratico per gestire una transazione è con `using` un'istruzione racchiusa in `try...catch` un'istruzione :

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 Se si verifica un'eccezione che impedisce l'esecuzione finale durante le modifiche, lo `Commit()` Store verrà reimpostato sullo stato precedente. Ciò consente di assicurarsi che gli errori non lascino il modello in uno stato incoerente.

 È possibile apportare un numero qualsiasi di modifiche all'interno di una transazione. È possibile aprire nuove transazioni all'interno di una transazione attiva. Le transazioni annidate devono eseguire il commit o il rollback prima della fine della transazione che lo contiene. Per altre informazioni, vedere l'esempio per la <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> proprietà .

 Per rendere permanenti le modifiche, è `Commit` necessario che la transazione venga eliminata. Se si verifica un'eccezione che non viene rilevata all'interno della transazione, l'archivio verrà reimpostato sullo stato precedente alle modifiche.

## <a name="rolling-back-a-transaction"></a>Rollback di una transazione
 Per assicurarsi che l'archivio rimanga nello stato precedente alla transazione o ne venga ripristinato lo stato, è possibile usare una di queste strategie:

1. Generare un'eccezione che non viene intercettata nell'ambito della transazione.

2. Eseguire il rollback della transazione in modo esplicito:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Le transazioni non influiscono sugli oggetti non di archiviazione
 Le transazioni regolano solo lo stato dell'archivio. Non possono annullare le modifiche parziali apportate a elementi esterni, ad esempio file, database o oggetti dichiarati con tipi ordinari all'esterno della definizione DSL.

 Se un'eccezione potrebbe lasciare tale modifica incoerente con l'archivio, è necessario gestire tale possibilità nel gestore di eccezioni. Un modo per assicurarsi che le risorse esterne rimangano sincronizzate con gli oggetti Store è quello di accoppiare ogni oggetto esterno a un elemento nell'archivio usando gestori eventi. Per altre informazioni, vedere [Propagare modifiche all'esterno del modello da parte dei gestori eventi.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Le regole vengono applicate alla fine di una transazione
 Alla fine di una transazione, prima dell'eliminazione della transazione, vengono attivato le regole associate agli elementi nell'archivio. Ogni regola è un metodo applicato a un elemento del modello modificato. Ad esempio, esistono regole di "correzione" che aggiornano lo stato di una forma quando il relativo elemento del modello viene modificato e che creano una forma quando viene creato un elemento del modello. Non è stato specificato alcun ordine di attivazione. Una modifica apportata da una regola può essere applicata a un'altra regola.

 È possibile definire regole personalizzate. Per altre informazioni sulle regole, vedere [Risposta e propagazione delle modifiche.](../modeling/responding-to-and-propagating-changes.md)

 Le regole non vengono applicate dopo un'operazione di annullamento, un'operazione di ripristino o un comando di rollback.

## <a name="transaction-context"></a>Contesto di transazione
 Ogni transazione ha un dizionario in cui è possibile archiviare le informazioni desiderate:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Ciò è particolarmente utile per il trasferimento di informazioni tra le regole.

## <a name="transaction-state"></a>Stato della transazione
 In alcuni casi è necessario evitare di propagare una modifica se la modifica è causata dall'annullamento o dal nuovo annullamento di una transazione. Ciò può verificarsi, ad esempio, se si scrive un gestore del valore della proprietà in grado di aggiornare un altro valore nello Store. Poiché l'operazione di annullamento reimposta tutti i valori nell'archivio sui rispettivi stati precedenti, non è necessario calcolare i valori aggiornati. Usare questo codice:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 Le regole possono essere applicate quando l'archivio viene caricato inizialmente da un file. Per evitare di rispondere a queste modifiche, usare:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
