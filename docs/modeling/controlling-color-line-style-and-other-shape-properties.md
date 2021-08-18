---
title: Controllare colore, stile di linea e altre proprietà della forma
description: Fornisce informazioni sul controllo delle proprietà della forma, ad esempio il colore e lo stile della linea.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 8f62d78e573f0fa2379fb3c36e91f0db971b8270
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061376"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Controllo delle proprietà Color, Line Style e altre

Alcune proprietà della forma, ad esempio il colore, possono essere "esposte". In altre informazioni, le proprietà possono essere collegate a una proprietà di dominio della forma. Altri devono essere controllati direttamente.

## <a name="exposing-a-property"></a>Esposizione di una proprietà
 Alcune proprietà della forma, ad esempio il colore, possono essere collegate al valore di una proprietà di dominio.

 Nella definizione DSL selezionare una forma, un connettore o una classe di diagramma. Nel menu di scelta rapida scegliere **Aggiungi** esposto e quindi scegliere la proprietà desiderata, ad esempio Colore riempimento.

 La forma dispone ora di una proprietà di dominio che è possibile impostare nel codice del programma o come utente.

## <a name="dynamically-updating-an-exposed-property"></a>Aggiornamento dinamico di una proprietà esposta
 In genere si vuole rendere la proprietà esposta dipendente da un'altra proprietà. Ad esempio, può essere necessario che una forma si trasformi in rosso ogni volta che una determinata proprietà di dominio è minore di zero. Per creare questa dipendenza, creare una [regola](../modeling/rules-propagate-changes-within-the-model.md). Ad esempio:

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