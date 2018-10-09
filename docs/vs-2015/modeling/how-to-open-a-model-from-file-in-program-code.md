---
title: 'Procedura: aprire un modello da File nel codice del programma | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7d68697-5418-4263-bdb2-48401924ea71
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d0884148a6e3f390654842b5e35a9e53643ea17d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518395"
---
# <a name="how-to-open-a-model-from-file-in-program-code"></a>Procedura: aprire un modello da file nel codice del programma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: aprire un modello da File nel codice programma](https://docs.microsoft.com/visualstudio/modeling/how-to-open-a-model-from-file-in-program-code).  
  
È possibile aprire modelli di linguaggio specifico di dominio in qualsiasi applicazione.  
  
 Da un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensione, è possibile usare ModelBus per questo scopo. ModelBus fornisce un meccanismo standard per fare riferimento a un modello o elementi in un modello e per trovare il modello se è stato spostato. Per altre informazioni, vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).  
  
## <a name="target-framework"></a>Framework di destinazione  
 Impostare il **framework di destinazione** del progetto dell'applicazione per **.NET Framework 4**.  
  
#### <a name="to-set-the-target-framework"></a>Per impostare il framework di destinazione  
  
1.  Aprire il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto per l'applicazione in cui si vuole leggere un modello DSL.  
  
2.  Nelle **Esplora soluzioni**, fare clic sul progetto e quindi fare clic su **proprietà**.  
  
3.  Nella finestra delle proprietà del progetto, nella **Application** scheda, impostare il **framework di destinazione** campo **.NET Framework 4**.  
  
> [!NOTE]
>  Potrebbe essere necessario eseguire questa operazione anche se si seleziona **.NET Framework 4** nella finestra di dialogo di creazione progetto. Il framework di destinazione non deve essere **.NET Framework 4 Client Profile**.  
  
## <a name="references"></a>Riferimenti  
 È necessario aggiungere questi riferimenti per il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto di applicazione:  
  
-   `Microsoft.VisualStudio.Modeling.Sdk.11.0`  
  
    -   Se non viene visualizzato nel **.NET** scheda il **aggiungere riferimenti** della finestra di dialogo fare clic sul **Sfoglia** scheda e passare a `%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Common\Assemblies\`.  
  
-   L'assembly DSL, che si troveranno nella cartella bin del progetto DSL. Il nome è in genere nel formato: *Società_utente*. *YourProject*`.Dsl.dll`.  
  
## <a name="important-classes-in-the-dsl"></a>Classi importanti nel DSL  
 Prima di poter scrivere il codice che legge il linguaggio DSL, è necessario conoscere i nomi di alcune delle classi generate per il linguaggio DSL. Nella soluzione DSL, aprire il **Dsl** del progetto ed esaminare le **GeneratedCode** cartella. In alternativa, fare doppio clic su assembly nel progetto DSL **riferimenti**, quindi aprire lo spazio dei nomi DSL in **Visualizzatore oggetti**.  
  
 Queste sono le classi che è necessario identificare:  
  
-   *YourDslRootClass* -si tratta del nome della classe radice nel `DslDefinition.dsl`.  
  
-   *Proprionomedsl* `SerializationHelper` -questa classe è definita in `SerializationHelper.cs` nel progetto DSL.  
  
-   *Proprionomedsl* `DomainModel` -questa classe è definita in `DomainModel.cs` nel progetto DSL.  
  
## <a name="reading-from-a-file"></a>La lettura da un File  
 Nell'esempio seguente è progettato per la lettura di un linguaggio DSL in cui le classi importanti sono i seguenti:  
  
-   FamilyTreeModel  
  
-   FamilyTreeSerializationHelper  
  
-   FamilyTreeDomainModel  
  
 L'altra classe di dominio in questo linguaggio DSL è una persona.  
  
```  
using System;  
using Microsoft.VisualStudio.Modeling;  
using Company.FamilyTree; // Your DSL namespace  
  
namespace StandaloneReadDslConsole  
{ class Program  
  { static void Main(string[] args)  
    {  
      // The path of a DSL model file:  
      string dslModel = @"C:\FamilyTrees\Tudor.ftree";  
      // Set up the Store to read your type of model:  
      Store store = new Store(  
        typeof(Company.FamilyTree.FamilyTreeDomainModel));  
      // The Model type generated by the DSL:  
      FamilyTreeModel familyTree;  
      // All Store changes must be in a Transaction:  
      using (Transaction t =   
        store.TransactionManager.BeginTransaction("Load model"))  
      {  
        familyTree =   
           FamilyTreeSerializationHelper.Instance.  
              LoadModel(store, dslModel, null, null, null);  
        t.Commit(); // Don't forget this!  
      }  
      // Now we can read the model:  
      foreach (Person p in familyTree.People)  
      {  
        Console.WriteLine(p.Name);   
        foreach (Person child in p.Children)  
        {  
          Console.WriteLine("    " + child.Name);  
        }  
} } } }  
```  
  
## <a name="saving-to-a-file"></a>Salvataggio in un File  
 Le seguenti aggiunte al codice precedente apporta una modifica al modello e quindi salvarlo in un file.  
  
```  
using (Transaction t =  
  store.TransactionManager.BeginTransaction("update model"))  
{  
  // Create a new model element:  
  Person p = new Person(store);  
  // Set its embedding relationship:  
  p.FamilyTreeModel = familyTree;  
  // - same as: familyTree.People.Add(p);  
  // Set its properties:  
  p.Name = "Edward VI";  
  t.Commit(); // Don't forget this!  
}  
// Save the model:  
try  
{  
  SerializationResult result = new SerializationResult();  
  FamilyTreeSerializationHelper.Instance  
    .SaveModel(result, familyTree, @"C:\FamilyTrees\Tudor-upd.ftree");  
  // Report any error:  
  if (result.Failed)  
  {  
    foreach (SerializationMessage message in result)  
    {  
      Console.WriteLine(message);  
    }  
  }  
}  
catch (System.IO.IOException ex)  
{ ... }  
```


