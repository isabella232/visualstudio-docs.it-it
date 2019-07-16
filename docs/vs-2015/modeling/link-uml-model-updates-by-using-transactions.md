---
title: Collegare aggiornamenti di modelli UML tramite transazioni | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f938e08d2bc9363be5e3f9e1ac247dea36f25a80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191716"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Collegare aggiornamenti di modelli UML tramite transazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si definisce un'estensione per le finestre di progettazione UML in Visual Studio, è possibile raggruppare diverse modifiche in una singola transazione denominata un *contesto di annullamento collegato*. Per individuare le versioni di Visual Studio che supportano i modelli UML, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Per impostazione predefinita, ogni modifica apportata a un modello dal codice può essere annullata separatamente dall'utente. Ad esempio, se si definisce un comando di menu che scambia i nomi di due classi UML, un utente può richiamare il comando e quindi eseguire una singola operazione di annullamento. In tal modo si annullerebbe la modifica di un solo nome, ma non dell'altro, lasciando il modello in uno stato non desiderato.  
  
 Per evitare questo problema, il codice può eseguire una serie di modifiche all'interno di una transazione. In questo modo le modifiche sembreranno all'utente una singola modifica. Un successivo comando di annullamento annullerà l'intera serie.  
  
 Un ulteriore vantaggio è che il codice può annullare un insieme di modifiche parzialmente completo generando un'eccezione o interrompendo la transazione.  
  
## <a name="to-group-changes-into-a-single-transaction"></a>Per raggruppare le modifiche in una singola transazione  
 Assicurarsi che i riferimenti del progetto includano questo assembly .NET:  
  
 **Microsoft.VisualStudio.Modeling.Sdk.[version].dll**  
  
 All'interno della classe dichiarare una proprietà importata con il tipo <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext>:  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 In un metodo che modifica il modello includere le modifiche in una transazione:  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 Tenere presente quanto segue:  
  
- È necessario includere sempre `Commit()` alla fine della transazione. Se una transazione viene eliminata senza essere sottoposta a commit, sarà possibile eseguirne il rollback. Il modello verrà quindi ripristinato allo stato che aveva all'inizio della transazione.  
  
- Se si verifica un'eccezione non rilevata all'interno della transazione, sarà possibile eseguirne il rollback. Un modello frequente è racchiudere il blocco `using` della transazione all'interno di un blocco `try…catch`.  
  
- È possibile annidare le transazioni.  
  
- È possibile specificare qualsiasi nome non vuoto a `BeginTransaction()`.  
  
- Solo l'archivio di modello UML è interessato da queste transazioni. Le transazioni di modellazione non influiscono su variabili, archivi esterni, quali file e database, diagrammi livello e modelli del codice.  
  
## <a name="example"></a>Esempio  
  
```  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.Interfaces;  
    using Microsoft.VisualStudio.Uml.Classes;  
    using Microsoft.VisualStudio.Uml.Extensions;  
    using System.Linq;  
    using System.ComponentModel.Composition;  
 ...  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  public void Execute(IMenuCommand command)  
  {  
    var selectedShapes =  
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
    string firstName = firstElement.Name;  
    // Perform changes inside a transaction so that undo  
    // works as a single change.  
    using (ILinkedUndoTransaction transaction =   
      LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
        firstElement.Name = lastElement.Name;  
        lastElement.Name = firstName;  
        transaction.Commit();  
    }  
 }  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md)   
 [Definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)
