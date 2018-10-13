---
title: 'Procedura: utilizzare le transazioni per aggiornare il modello | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e24436a5-7f97-401b-bc83-20d188d10d5b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 50f9d491ed52098edb8a8ccd1a7b2f9c8834447e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236860"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>Procedura: utilizzare le transazioni per aggiornare il modello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le transazioni assicurarsi che le modifiche apportate all'archivio siano considerate come un gruppo. Le modifiche che sono raggruppate possono essere eseguito il commit o rollback come unità singola.  
  
 Ogni volta che il codice del programma modifica, aggiunge o elimina qualsiasi elemento di Store in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK, l'operazione deve essere eseguita all'interno di una transazione. Deve esistere un'istanza attiva del <xref:Microsoft.VisualStudio.Modeling.Transaction> associata con il Store quando avviene la modifica. Questo vale per tutti gli elementi del modello, relazioni, forme, diagrammi e le relative proprietà.  
  
 Il meccanismo di transazione ti aiuta a evitare stati incoerenti. Se si verifica un errore durante una transazione, vengano eseguito il rollback di tutte le modifiche. Se l'utente esegue un comando di annullamento, ogni transazione recente viene considerato come un unico passaggio. L'utente non è possibile annullare le parti di una modifica recente, a meno che non è esplicitamente posizionarli in transazioni separate.  
  
## <a name="opening-a-transaction"></a>Apertura di una transazione  
 Il metodo più pratico di gestione di una transazione è con un `using` istruzione racchiusa tra una `try...catch` istruzione:  
  
```  
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
  
 Se un'eccezione che impedisce l'elemento finale `Commit()` si verifica durante le modifiche, verrà reimpostato il Store allo stato precedente. Ciò consente di assicurarsi che gli errori non lascino il modello in uno stato incoerente.  
  
 È possibile apportare qualsiasi numero di modifiche all'interno di una transazione. È possibile aprire nuove transazioni all'interno di una transazione attiva. Le transazioni nidificate devono eseguire il commit o il rollback prima della scadenza delle transazioni che lo contiene. Per altre informazioni, vedere l'esempio per il <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> proprietà.  
  
 Per rendere permanenti le modifiche, è consigliabile `Commit` la transazione prima di eliminarlo. Se si verifica un'eccezione non rilevata all'interno della transazione, la Store verrà reimpostato sullo stato precedente le modifiche.  
  
## <a name="rolling-back-a-transaction"></a>Esecuzione del rollback di una transazione  
 Per garantire che la Store rimane in o viene ripristinata allo stato antecedente la transazione, è possibile usare una di queste strategie:  
  
1.  Generare un'eccezione non rilevata all'interno dell'ambito della transazione.  
  
2.  In modo esplicito il rollback della transazione:  
  
    ```  
    this.Store.TransactionManager.CurrentTransaction.Rollback();  
    ```  
  
## <a name="transactions-do-not-affect-non-store-objects"></a>Operazioni non modificano gli oggetti Non Store  
 Le transazioni controllano solo lo stato del Store. È possibile annullare le modifiche parziali che sono state apportate a elementi esterni, ad esempio file, database o oggetti dichiarati con i tipi comuni all'esterno della definizione DSL.  
  
 Se un'eccezione potrebbe lasciare tale modifica non coerente con il Store, deve affrontare tale possibilità nel gestore eccezioni. Un modo per assicurarsi che le risorse esterne rimangano sincronizzate con gli oggetti Store è l'accoppiamento di ogni oggetto esterno a un elemento nell'archivio tramite gestori degli eventi. Per altre informazioni, vedere [gestori di propagare le modifiche di fuori il modello di eventi](../modeling/event-handlers-propagate-changes-outside-the-model.md).  
  
## <a name="rules-fire-at-the-end-of-a-transaction"></a>Attivare le regole alla fine di una transazione  
 Alla fine di una transazione, prima che la transazione viene eliminata, vengono attivate le regole associate agli elementi nell'archivio. Ogni regola è un metodo che viene applicato a un elemento del modello che è stato modificato. Ad esempio, sono presenti regole "correggo" che aggiornano lo stato di una forma quando l'elemento del modello è stato modificato e che crea una forma quando viene creato un elemento del modello. Non esiste un ordine di generazione dell'evento specificato. Una modifica apportata da una regola può essere attivati da un'altra regola.  
  
 È possibile definire regole personalizzate. Per altre informazioni sulle regole, vedere [procedura: rispondere a e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  
  
 Le regole non vengono attivati dopo che un'operazione di annullamento, ripetizione o un comando di rollback.  
  
## <a name="transaction-context"></a>Contesto di transazione  
 Ogni transazione ha un dizionario in cui è possibile archiviare le informazioni desiderate:  
  
 `store.TransactionManager`  
  
 `.CurrentTransaction.TopLevelTransaction`  
  
 `.Context.Add(aKey, aValue);`  
  
 Ciò è particolarmente utile per il trasferimento di informazioni tra le regole.  
  
## <a name="transaction-state"></a>Stato della transazione  
 In alcuni casi che è necessario evitare la propagazione di una modifica se la modifica è causata dall'operazione di annullamento o ripetizione di una transazione. Questa situazione può verificarsi, ad esempio, se si scrive un gestore di valore di proprietà che è possibile aggiornare un altro valore nella Store. Poiché l'operazione di annullamento consente di reimpostare tutti i valori di Store gli stati precedenti, non è necessario calcolare i valori aggiornati. Usare questo codice:  
  
```  
if (!this.Store.InUndoRedoOrRollback) {...}  
```  
  
 Le regole possono essere generato quando viene caricato nell'archivio inizialmente da un file. Per evitare di rispondere a queste modifiche, usare:  
  
```  
if (!this.Store.InSerializationTransaction) {...}  
  
```



