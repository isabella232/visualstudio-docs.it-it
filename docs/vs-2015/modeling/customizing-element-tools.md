---
title: Personalizzazione di strumenti elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 6dac48b6-db68-4bcd-8aa2-422c2ad5d28b
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 72457070c63cdf6c76207bd92521ab7944d4318a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199854"
---
# <a name="customizing-element-tools"></a>Personalizzazione di strumenti elemento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In alcune definizioni DSL, si rappresenta un singolo concetto come un gruppo di elementi. Ad esempio, se si crea un modello in cui un componente dispone di un set fisso di porte, si vuole che sempre le porte da creare in contemporanea con i propri componenti padre. Pertanto, è necessario personalizzare lo strumento di creazione di elemento in modo che crei un gruppo di elementi anziché uno solo. A tale scopo, è possibile personalizzare come viene inizializzato lo strumento di creazione di elemento.  
  
 È anche possibile eseguire l'override cosa accade quando lo strumento viene trascinato nel diagramma o un elemento.  
  
## <a name="customizing-the-content-of-an-element-tool"></a>La personalizzazione del contenuto di uno strumento elemento  
 Ogni strumento elemento contiene un'istanza di un <xref:Microsoft.VisualStudio.Modeling.ElementGroupPrototype> (EGP), che contiene una versione serializzata di uno o più elementi del modello e i collegamenti. Per impostazione predefinita, EGP di uno strumento elemento contiene un'istanza della classe specificato per lo strumento. È possibile modificare questa impostazione viene sottoposto a override *Linguaggioutente*`ToolboxHelper.CreateElementToolPrototype`. Questo metodo viene chiamato quando viene caricato il pacchetto DSL.  
  
 Un parametro del metodo è l'ID della classe specificata nella definizione DSL. Quando viene chiamato il metodo con la classe che si è interessati, è possibile aggiungere elementi aggiuntivi in EGP.  
  
 EGP deve includere collegamenti da un elemento principale agli elementi sussidiari l'incorporamento. È inoltre possibile utilizzare i collegamenti di riferimento.  
  
 L'esempio seguente crea un elemento principale e due elementi incorporati. La classe principale viene chiamata resistore e ha due relazioni di incorporamento per gli elementi denominati Terminal. Proprietà del ruolo di incorporamento sono denominate Terminal1 e Terminal2 e hanno una molteplicità di 1..1.  
  
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
