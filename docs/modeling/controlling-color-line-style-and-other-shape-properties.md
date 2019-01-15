---
title: Controllo delle proprietà Color, Line Style e altre
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ea0b73470bc9f3bed76328c55d823cef3c5b8e9e
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269319"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controllo delle proprietà Color, Line Style e altre

Alcune proprietà della forma, ad esempio colore può essere 'esposto'. Vale a dire, la proprietà può essere collegata a una proprietà di dominio della forma. Altri utenti devono essere controllati direttamente.

## <a name="exposing-a-property"></a>Esposizione di una proprietà
 Alcune proprietà della forma, ad esempio colore può essere collegata al valore della proprietà del dominio.

 Nella definizione DSL, selezionare una forma, connettore o classe diagramma. Nel relativo menu di scelta rapida, scegliere **Aggiungi esposta**, quindi scegliere Proprietà desiderata, ad esempio il colore di riempimento.

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