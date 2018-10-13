---
title: Creare elementi e relazioni nei modelli UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: d0e68a3701d4455c0a627bd275eaab2cd857abc1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49198549"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Creare elementi e relazioni nei modelli UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nel codice programma per un'estensione a Visual Studio, è possibile creare ed eliminare elementi e relazioni.  
  
## <a name="create-a-model-element"></a>Creare un elemento del modello  
  
### <a name="namespace-imports"></a>Importazioni di spazi dei nomi  
 È necessario includere le istruzioni `using` seguenti.  
  
 I metodi di creazione sono definiti come metodi di estensione in questo spazio dei nomi:  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Ottenere il proprietario dell'elemento per il quale si vuole creare una condizione  
 Un modello costituisce un singolo albero, in modo che ogni elemento abbia un proprietario, ad eccezione della radice del modello. La radice del modello è di tipo `IModel`, che è un tipo di `IPackage`.  
  
 Se si sta creando un elemento che verrà visualizzato in un diagramma specifico, ad esempio il diagramma corrente dell'utente, è necessario in genere crearlo nel pacchetto che è collegato a tale diagramma. Ad esempio:  
  
```  
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;  
```  
  
 In questa tabella è riepilogata le proprietà di elementi del modello comuni:  
  
|Elemento da creare|Owner|  
|---------------------------|-----------|  
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|  
|`IAttribute, IOperation`|`IClass, IInterface`|  
|`IPart, IPort`|`IComponent`|  
|`IAction, IObjectNode`|`IActivity`|  
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|  
  
### <a name="invoke-the-create-method-on-the-owner"></a>Richiamare il metodo di creazione sul proprietario  
 Il nome del metodo è nel formato: `Create` *TipoProprietario*`()`. Ad esempio:  
  
```  
IUseCase usecase1 = linkedPackage.CreateUseCase();  
```  
  
 Alcuni tipi presentano metodi di creazione più complessi, in particolare nei diagrammi sequenza. Visualizzare [diagrammi di sequenza UML modificare usando l'API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Per alcuni tipi di elemento è possibile modificarne il proprietario nel corso della durata dell'elemento usando `SetOwner(newOwner)`.  
  
### <a name="set-the-name-and-other-properties"></a>Impostare il nome e altre proprietà  
  
```  
usecase1.Name = "user logs in";  
```  
  
### <a name="example"></a>Esempio  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Extensions;  
...  
 void InstantiateObserverPattern (IPackage package, string namePrefix)  
 {    IInterface observer = package.CreateInterface();  
      observer.Name = namePrefix + "Observer";  
      IOperation operation = observer.CreateOperation();  
      operation.Name = "Update";  
      IClass subject = package.CreateClass();  
      subject.Name = namePrefix + "Subject"; ...  
```  
  
## <a name="create-an-association"></a>Creare un'associazione  
  
#### <a name="to-create-an-association"></a>Per creare un'associazione  
  
1.  Ottenere il proprietario dell'associazione, che in genere è il pacchetto o un modello contenente la fine dell'origine della relazione.  
  
2.  Richiamare il metodo di creazione sul proprietario.  
  
3.  Impostare le proprietà della relazione, ad esempio il relativo nome.  
  
     Ad esempio:  
  
    ```  
    IAssociation association = subject.Package.CreateAssociation(subject, observer);  
    association .Name = "Observes";  
    ```  
  
4.  Impostare le proprietà di ogni classe della relazione. Esistono sempre due `MemberEnds`. Ad esempio:  
  
    ```  
    association .MemberEnds[0].Name = "subject";   // role name  
    association .MemberEnds[1].Name = "observers"; // role name  
    association .MemberEnds[1].SetBounds("0..*");           
                // multiplicity defaults to "1"  
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;  
    ```  
  
## <a name="create-a-generalization"></a>Creare una generalizzazione  
  
```  
IGeneralization generalization =   
  subclass.CreateGeneralization(superClass);  
```  
  
## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Eliminare un elemento, una relazione o una generalizzazione dal modello  
  
```  
anElement.Delete();  
```  
  
 Quando si elimina un elemento dal modello:  
  
-   Vengono eliminate anche tutte le relazioni che si collegano ad esso.  
  
-   Vengono eliminate anche tutte le forme che l'hanno rappresentato in un diagramma.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere modelli e diagrammi UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md)



