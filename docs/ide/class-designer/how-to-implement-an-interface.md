---
title: "Procedura: Implementare un'interfaccia (Progettazione classi)"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe8db6c6bd7df5285880f7f860df5bb26db736a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590111"
---
# <a name="how-to-implement-an-interface-in-class-designer"></a>Procedura: Implementare un'interfaccia in Progettazione classi

In **Progettazione classi** è possibile implementare un'interfaccia nel diagramma classi connettendola a una classe che fornisce il codice per i metodi di interfaccia. **Progettazione classi** genera un'implementazione dell'interfaccia e visualizza la relazione tra l'interfaccia e la classe come relazione di ereditarietà. È possibile implementare un'interfaccia tracciando una linea di ereditarietà tra l'interfaccia e la classe oppure trascinando l'interfaccia dalla visualizzazione classi.

> [!TIP]
> È possibile creare le interfacce allo stesso modo in cui vengono creati altri tipi di elemento. Se l'interfaccia esiste ma non viene visualizzata nel diagramma classi, è necessario innanzitutto visualizzarla. Per altre informazioni, vedere [Procedura: Creare tipi usando Progettazione classi](how-to-create-types.md) e [Procedura: Visualizzare i tipi esistenti](how-to-view-existing-types.md).

## <a name="to-implement-an-interface-by-drawing-an-inheritance-line"></a>Per implementare un'interfaccia tracciando una linea di ereditarietà

1. Nel diagramma classi visualizzare l'interfaccia e la classe che implementa l'interfaccia.

2. Tracciare una linea di ereditarietà dalla classe e all'interfaccia.

     Viene visualizzato un simbolo di interfaccia collegato alla classe, mentre un'etichetta con il nome dell'interfaccia identifica la relazione di ereditarietà. Visual Studio genera stub per tutti i membri di interfaccia.

Per altre informazioni, vedere [Procedura: Creare ereditarietà tra tipi](how-to-create-inheritance-between-types.md).

## <a name="to-implement-an-interface-from-the-class-view-window"></a>Per implementare un'interfaccia dalla finestra Visualizzazione classi

1. Nel diagramma classi visualizzare la classe che deve implementare l'interfaccia.

2. Aprire **Visualizzazione classi** e individuare l'interfaccia.

    > [!TIP]
    > Se non è già visualizzata, aprire **Visualizzazione classi** dal menu **Visualizza** o premere **CTRL**+**MAIUSC**+**C**.

3. Trascinare il nodo di interfaccia nella forma della classe nel diagramma.

     Viene visualizzato un simbolo di interfaccia collegato alla classe, mentre un'etichetta con il nome dell'interfaccia identifica la relazione di ereditarietà. Visual Studio genera stub per tutti i membri di interfaccia. A questo punto, l'interfaccia è stata implementata.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare tipi usando Progettazione classi](how-to-create-types.md)
- [Procedura: Visualizzare i tipi esistenti](how-to-view-existing-types.md)
- [Procedura: Creare ereditarietà tra tipi](how-to-create-inheritance-between-types.md)
- [Refactoring di classi e tipi](refactoring-classes-and-types.md)
