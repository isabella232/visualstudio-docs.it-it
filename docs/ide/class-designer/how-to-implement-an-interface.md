---
title: "Procedura: implementare un'interfaccia (Progettazione classi)"
description: Informazioni su come implementare un'interfaccia nel diagramma classi connetterla a una classe che fornisce il codice per i metodi dell'interfaccia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- interfaces [Visual Studio], implementing
- interfaces [Visual Studio]
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a992800a6155aaa8afdd9ae2491b977885199ddd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124191"
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
    > Se **Visualizzazione classi** non è aperto, **aprire** Visualizzazione classi dal **menu** Visualizza o premere CTRL  +  + **MAIUSC+C.**

3. Trascinare il nodo di interfaccia nella forma della classe nel diagramma.

     Viene visualizzato un simbolo di interfaccia collegato alla classe, mentre un'etichetta con il nome dell'interfaccia identifica la relazione di ereditarietà. Visual Studio genera stub per tutti i membri di interfaccia. A questo punto, l'interfaccia è stata implementata.

## <a name="see-also"></a>Vedi anche

- [Procedura: Creare tipi usando Progettazione classi](how-to-create-types.md)
- [Procedura: Visualizzare tipi esistenti](how-to-view-existing-types.md)
- [Procedura: Creare ereditarietà tra tipi](how-to-create-inheritance-between-types.md)
- [Refactoring di classi e tipi](refactoring-classes-and-types.md)
