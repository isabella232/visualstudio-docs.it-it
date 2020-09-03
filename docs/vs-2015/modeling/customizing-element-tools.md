---
title: Personalizzazione degli strumenti degli elementi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b6b35bbb0592f7ec9f8defcd9d78dbba5a6a47a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655017"
---
# <a name="customizing-element-tools"></a>Personalizzazione di strumenti elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In alcune definizioni DSL, rappresenta un singolo concetto come gruppo di elementi. Se, ad esempio, si crea un modello in cui un componente dispone di un set fisso di porte, è sempre necessario creare le porte contemporaneamente al componente padre. Pertanto, è necessario personalizzare lo strumento di creazione degli elementi in modo da creare un gruppo di elementi anziché uno solo. A tale scopo, è possibile personalizzare la modalità di inizializzazione dello strumento di creazione degli elementi.

 È anche possibile eseguire l'override di ciò che accade quando lo strumento viene trascinato nel diagramma o in un elemento.

## <a name="customizing-the-content-of-an-element-tool"></a>Personalizzazione del contenuto di uno strumento elemento
 Ogni strumento elemento archivia un'istanza di <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), che contiene una versione serializzata di uno o più elementi e collegamenti del modello. Per impostazione predefinita, il EGP di uno strumento elemento contiene un'istanza della classe specificata per lo strumento. È possibile modificare questa impostazione eseguendo l'override di *linguaggioutente* `ToolboxHelper.CreateElementToolPrototype` . Questo metodo viene chiamato quando viene caricato il pacchetto DSL.

 Un parametro del metodo è l'ID della classe specificata nella definizione DSL. Quando il metodo viene chiamato con la classe a cui si è interessati, è possibile aggiungere elementi aggiuntivi in EGP.

 Il EGP deve includere collegamenti di incorporamento da un elemento principale agli elementi secondari. Può inoltre includere collegamenti di riferimento.

 Nell'esempio seguente viene creato un elemento principale e due elementi incorporati. La classe principale è chiamata resistore ed è costituita da due relazioni di incorporamento per gli elementi denominati Terminal. Le proprietà del ruolo di incorporamento sono denominate Terminal1 e Terminal2 ed entrambe hanno una molteplicità di 1.. 1.

```
using Microsoft.VisualStudio.Modeling; ...
public partial class CircuitDiagramToolboxHelper
{
  protected override ElementGroupPrototype    CreateElementToolPrototype(Store store, Guid domainClassId)
  {
    // A case for each tool to customize:
    if (domainClassId == Resistor.DomainClassId)
    {
      // Set up the prototype elements and links:
      Resistor resistor = new Resistor(store);
      resistor.Terminal1 = new Terminal(store);
      resistor.Terminal2 = new Terminal(store);
      resistor.Terminal1.Name = "T1"; // embedding
      resistor.Terminal2.Name = "T2"; // embedding
      // We could also set up reference links.

      // Create an element group prototype for the toolbox:
      ElementGroup egp = new ElementGroup(store.DefaultPartition);
      egp.AddGraph(resistor, true);
      // We do not have to explicitly include embedded children.
      return egp.CreatePrototype();
    }
    // Element tools for other classes:
    else
      return base.CreateElementToolPrototype(store, domainClassId);
  }
}
```

## <a name="see-also"></a>Vedere anche
 [Personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md)
