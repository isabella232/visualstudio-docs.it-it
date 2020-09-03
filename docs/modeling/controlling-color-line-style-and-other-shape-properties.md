---
title: Controllo delle proprietà Color, Line Style e altre
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eee36ad0361f40f23c29c5672b155fc5e5405dbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546679"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controllo delle proprietà Color, Line Style e altre

Alcune proprietà della forma, ad esempio il colore, possono essere "esposte". Ovvero le proprietà possono essere collegate a una proprietà di dominio della forma. Altri devono essere controllati direttamente.

## <a name="exposing-a-property"></a>Esposizione di una proprietà
 Alcune proprietà della forma, ad esempio il colore, possono essere collegate al valore di una proprietà di dominio.

 Nella definizione DSL selezionare una classe forma, connettore o diagramma. Nel menu di scelta rapida scegliere **Aggiungi esposto**, quindi scegliere la proprietà desiderata, ad esempio colore riempimento.

 La forma dispone ora di una proprietà di dominio che è possibile impostare nel codice programma o come utente.

## <a name="dynamically-updating-an-exposed-property"></a>Aggiornamento dinamico di una proprietà esposta
 In genere si vuole rendere la proprietà esposta dipendente da un'altra proprietà. Ad esempio, è possibile che una forma diventi rossa ogni volta che una particolare proprietà di dominio è minore di zero. Per rendere questa dipendenza, creare una [regola](../modeling/rules-propagate-changes-within-the-model.md). Ad esempio:

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