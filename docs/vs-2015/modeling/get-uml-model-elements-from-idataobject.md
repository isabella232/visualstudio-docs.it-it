---
title: Ottenere elementi del modello UML da IDataObject | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API, copy and paste
ms.assetid: e0b9cec8-3b93-4a24-8bd3-3e086501d387
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 66b4ffc312af89aa5852a1f4dad62fd328176df3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666081"
---
# <a name="get-uml-model-elements-from-idataobject"></a>Ottenere elementi di modelli UML da IDataObject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando l'utente trascina elementi da qualsiasi origine in un diagramma, gli elementi trascinati vengono codificati in un oggetto `System.Windows.Forms.IDataObject`. La codifica dipende dal tipo di oggetto di origine. Nel frammento seguente viene illustrato come recuperare gli elementi quando l'origine è un diagramma UML.

> [!NOTE]
> La maggior parte delle operazioni che è necessario eseguire sui modelli UML può essere eseguita usando i tipi in definiti negli assembly **Microsoft. VisualStudio. Uml. Interfaces** e **Microsoft. VisualStudio. ArchitectureTools. Extensibility**. Tuttavia, a tale scopo, è necessario usare alcune classi che fanno parte dell'implementazione di strumenti di modellazione UML. Ad esempio, `ShapeElement` in questo frammento non equivale a `IShape` UML. Per ridurre il rischio di collocare il modello UML e diagrammi in uno stato incoerente, è preferibile evitare di usare i metodi su queste classi di implementazione, a eccezione dei casi in cui non è disponibile alcuna alternativa.

## <a name="code-sample"></a>Esempio di codice
 Il progetto deve fare riferimento agli assembly di [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] seguenti:

 **Microsoft. VisualStudio. Modeling. Sdk. versione**

 **Microsoft. VisualStudio. Modeling. Sdk. Diagrams. versione**

 **System. Windows. Forms**

```
using Microsoft.VisualStudio.Modeling;
  // for ElementGroupPrototype
using Microsoft.VisualStudio.Modeling.Diagrams;
  // for ShapeElement, DiagramDragEventArgs, DiagramPointEventArgs
… 
  /// <summary>
  /// Retrieves UML IElements from drag arguments.
  /// Works for drags from UML diagrams.
  /// </summary>
  private IEnumerable<IElement> GetModelElementsFromDragEvent
                  (DiagramDragEventArgs dragEvent)
  {
     //ElementGroupPrototype is the container for
     //dragged and copied elements and toolbox items.
     ElementGroupPrototype prototype =
        dragEvent.Data.
        GetData(typeof(ElementGroupPrototype))
                     as ElementGroupPrototype;
     // Locate the originals in the implementation store.
     IElementDirectory implementationDirectory =
        dragEvent.DiagramClientView.Diagram.Store.ElementDirectory;

     return  prototype.ProtoElements.Select(
       prototypeElement =>
       {
          ModelElement element = implementationDirectory
                .FindElement(prototypeElement.ElementId);
          ShapeElement shapeElement = element as ShapeElement;
          if (shapeElement != null)
          {
            // Dragged from a diagram.
            return shapeElement.ModelElement as IElement;
          }
          else
          {
            // Dragged from UML Model Explorer.
            return element as IElement;
          }
        });
    }
```

 Per ulteriori informazioni su `ElementGroupPrototype` e `Store` in cui vengono implementati gli strumenti di modellazione UML, vedere [modellazione di SDK per Visual Studio-linguaggi specifici del dominio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="see-also"></a>Vedere anche
 [Programmazione con l'API UML](../modeling/programming-with-the-uml-api.md) [definire un comando di menu in un diagramma di modellazione](../modeling/define-a-menu-command-on-a-modeling-diagram.md)
