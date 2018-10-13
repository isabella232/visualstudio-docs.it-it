---
title: Controllare colore, stile di linea e altre proprietà della forma | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c06d0066-24aa-4c65-b91c-c2089b81ec8d
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b5694e81721bcc16b13c1857a07072fcaef00a08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285480"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controllo delle proprietà Color, Line Style e altre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alcune proprietà della forma, ad esempio colore può essere 'esposta', vale a dire, collegato a una proprietà di dominio della forma. Altri utenti devono essere controllati direttamente.  
  
## <a name="exposing-a-property"></a>Esposizione di una proprietà  
 Alcune proprietà della forma, ad esempio colore può essere collegata al valore della proprietà del dominio.  
  
 Nella definizione DSL, selezionare una forma, connettore o classe diagramma. Nel menu di scelta rapida, scegliere **Aggiungi esposta**, quindi scegliere Proprietà desiderata, ad esempio il colore di riempimento.  
  
 A questo punto, la forma presenta una proprietà di dominio che è possibile impostare nel codice programma o un utente.  
  
## <a name="dynamically-updating-an-exposed-property"></a>Aggiornamento dinamico di una proprietà esposta  
 In genere si vuole rendere la proprietà esposta dipende da un'altra proprietà. Ad esempio, è possibile una forma per divengono rossi ogni volta che una proprietà di dominio specifico è minore di zero. Per rendere questa dipendenza, creare un [regola](../modeling/rules-propagate-changes-within-the-model.md). Ad esempio:  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Diagrams;  
namespace ExampleNamespace  
{  
 // Attribute associates the rule with class:  
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class CarShapeAddRule : AddRule  
 {  
 // Override the abstract method:  
 public override void ElementAdded(ElementAddedEventArgs e)  
 {  
 base.ElementAdded(e);  
 CarShape shape = e.ModelElement as CarShape;  
 Store store = shape.Store;  
 // Ignore this call if we're currently loading a model:  
 if (store.TransactionManager.CurrentTransaction.IsSerializing)   
  return;  
 Car car = shape.ModelElement as Car;  
 // Code here propagates change as required - for example:  
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;   
 }  
}  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
 protected override Type[] GetCustomDomainModelTypes()  
 {  
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
  types.Add(typeof(CarShapeAddRule));  
  // If you add more rules, list them here.   
  return types.ToArray();  
 }  
 }  
}  
```



