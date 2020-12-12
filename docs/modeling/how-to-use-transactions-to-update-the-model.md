---
title: 'Procedura: utilizzare le transazioni per aggiornare il modello'
description: Informazioni sulle transazioni che assicurano che le modifiche apportate all'archivio vengano considerate come un gruppo e come utilizzare le transazioni per aggiornare il modello.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69a50ebdc7fff425224a454a491f05846105159d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363835"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Procedura: utilizzare le transazioni per aggiornare il modello
Le transazioni assicurano che le modifiche apportate all'archivio vengano considerate come un gruppo. È possibile eseguire il commit o il rollback delle modifiche raggruppate come singola unità.

 Ogni volta che il codice del programma modifica, aggiunge o Elimina qualsiasi elemento nell'archivio nell'SDK di visualizzazione e modellazione di Visual Studio, questa operazione deve essere eseguita all'interno di una transazione. Quando si verifica la modifica, deve essere presente un'istanza attiva di <xref:Microsoft.VisualStudio.Modeling.Transaction> associata all'archivio. Questo vale per tutti gli elementi del modello, le relazioni, le forme, i diagrammi e le relative proprietà.

 Il meccanismo di transazione consente di evitare gli stati incoerenti. Se si verifica un errore durante una transazione, viene eseguito il rollback di tutte le modifiche. Se l'utente esegue un comando Undo, ogni transazione recente viene considerata come un singolo passaggio. L'utente non può annullare parti di una modifica recente, a meno che non vengano esplicitamente inserite in transazioni separate.

## <a name="opening-a-transaction"></a>Apertura di una transazione
 Il metodo più pratico per gestire una transazione è costituito da un' `using` istruzione racchiusa in un' `try...catch` istruzione:

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

 Se si verifica un'eccezione che impedisce l'esecuzione finale `Commit()` durante le modifiche, verrà ripristinato lo stato precedente dell'archivio. Ciò consente di verificare che gli errori non lascino il modello in uno stato incoerente.

 È possibile apportare un numero qualsiasi di modifiche all'interno di una transazione. È possibile aprire nuove transazioni all'interno di una transazione attiva. È necessario eseguire il commit o il rollback delle transazioni nidificate prima della fine della transazione contenitore. Per ulteriori informazioni, vedere l'esempio relativo alla <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> Proprietà.

 Per rendere permanenti le modifiche, è necessario che `Commit` la transazione sia stata eliminata. Se si verifica un'eccezione non rilevata all'interno della transazione, l'archivio verrà reimpostato sullo stato prima delle modifiche.

## <a name="rolling-back-a-transaction"></a>Rollback di una transazione
 Per assicurarsi che lo stato dell'archivio rimanga o venga ripristinato prima della transazione, è possibile usare una di queste tattiche:

1. Genera un'eccezione non rilevata nell'ambito della transazione.

2. Eseguire il rollback della transazione in modo esplicito:

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>Le transazioni non influiscono sugli oggetti non di archivio
 Le transazioni regolano solo lo stato dell'archivio. Non possono annullare le modifiche parziali apportate a elementi esterni, ad esempio file, database o oggetti dichiarati con tipi normali al di fuori della definizione DSL.

 Se un'eccezione potrebbe lasciare invariata una modifica di questo tipo con l'archivio, è necessario gestire tale possibilità nel gestore di eccezioni. Un modo per assicurarsi che le risorse esterne rimangano sincronizzate con gli oggetti di archiviazione consiste nell'associare ogni oggetto esterno a un elemento dell'archivio usando i gestori eventi. Per ulteriori informazioni, vedere [i gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).

## <a name="rules-fire-at-the-end-of-a-transaction"></a>Le regole vengono attivate alla fine di una transazione
 Alla fine di una transazione, prima che la transazione venga eliminata, vengono generate le regole associate agli elementi nell'archivio. Ogni regola è un metodo applicato a un elemento del modello che è stato modificato. Sono ad esempio presenti regole di correzione che aggiornano lo stato di una forma quando viene modificato l'elemento del modello e che creano una forma quando viene creato un elemento del modello. Nessun ordine di attivazione specificato. Una modifica apportata da una regola può generare un'altra regola.

 È possibile definire regole personalizzate. Per ulteriori informazioni sulle regole, vedere [risposta a e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

 Le regole non vengono attivate dopo un'operazione di annullamento, ripetizione o rollback.

## <a name="transaction-context"></a>Contesto di transazione
 Ogni transazione dispone di un dizionario in cui è possibile archiviare le informazioni desiderate:

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 Questa operazione è particolarmente utile per il trasferimento delle informazioni tra le regole.

## <a name="transaction-state"></a>Stato della transazione
 In alcuni casi è necessario evitare la propagazione di una modifica se la modifica è causata da un'operazione di rollback o di una transazione. Questo può accadere, ad esempio, se si scrive un gestore del valore di una proprietà in grado di aggiornare un altro valore nell'archivio. Poiché l'operazione di annullamento Reimposta tutti i valori dell'archivio sugli stati precedenti, non è necessario calcolare i valori aggiornati. Usare il codice seguente:

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 È possibile attivare le regole quando l'archivio viene inizialmente caricato da un file. Per evitare di rispondere a queste modifiche, usare:

```csharp
if (!this.Store.InSerializationTransaction) {...}
```
