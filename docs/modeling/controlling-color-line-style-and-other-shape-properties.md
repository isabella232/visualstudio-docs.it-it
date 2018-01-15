---
title: "Controllo di colore, stile di linea e altre proprietà della forma | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: dd37ed2ae0e2ac065d5f74c8f91aca6aeb186d7d
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controllo delle proprietà Color, Line Style e altre
Alcune proprietà della forma, ad esempio colore può essere 'esposti' -, collegato a una proprietà di dominio della forma. Altri devono essere controllati direttamente.  
  
## <a name="exposing-a-property"></a>Esposizione di una proprietà  
 Alcune proprietà della forma, ad esempio colore possono essere collegati al valore di una proprietà di dominio.  
  
 Nella definizione del linguaggio DSL, selezionare una forma, un connettore o una classe di diagramma. Nel menu di scelta rapida, scegliere **aggiungere esposti**, quindi scegliere la proprietà desiderata, ad esempio il colore di riempimento.  
  
 A questo punto, la forma ha una proprietà che è possibile impostare nel codice programma o come un utente di dominio.  
  
## <a name="dynamically-updating-an-exposed-property"></a>L'aggiornamento dinamico di una proprietà esposta  
 In genere si desidera impostare la proprietà esposta dipende da un'altra proprietà. Ad esempio, è una forma a rosso ogni volta che una particolare dominio proprietà è minore di zero. Per rendere questa dipendenza, creare un [regola](../modeling/rules-propagate-changes-within-the-model.md). Ad esempio:  
  
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