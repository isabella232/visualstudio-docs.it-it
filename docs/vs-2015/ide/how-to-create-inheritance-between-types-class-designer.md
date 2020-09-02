---
title: 'Procedura: Creare ereditarietà tra tipi (Progettazione classi) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ba27b32cc322da2e14cec86b878a7dd42dae0039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668097"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Procedura: Creare ereditarietà tra tipi (Progettazione classi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per creare una relazione di ereditarietà tra due tipi in un diagramma classi usando Progettazione classi, connettere il tipo di base al tipo o ai tipi derivati corrispondenti. È possibile creare una relazione di ereditarietà tra due classi, tra una classe e un'interfaccia o tra due interfacce.

### <a name="to-create-an-inheritance-between-types"></a>Per creare un'ereditarietà tra tipi

1. Dal progetto in Esplora soluzioni aprire un file del diagramma classi (con estensione cd).

     Se non è disponibile alcun diagramma classi, crearne uno. Vedere [Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).

2. In **Progettazione classi** nella **Casella degli strumenti** fare clic su **Ereditarietà**.

3. Nel diagramma classi tracciare una linea di ereditarietà tra i tipi desiderati, come indicato di seguito:

    - Da una classe derivata a una classe di base

    - Da una classe di implementazione all'interfaccia implementata

    - Da un'interfaccia di estensione all'interfaccia estesa

4. Facoltativamente, quando è disponibile un tipo derivato da un tipo generico, fare clic sulla linea di ereditarietà. Nella finestra **Proprietà** impostare la proprietà **Argomenti di tipo** in modo che corrisponda al tipo da usare come tipo generico.

    > [!NOTE]
    > Se una classe astratta padre include almeno un membro astratto, tutti i membri astratti saranno quindi implementati come classi ereditanti non astratte.
    >
    >  Anche se è possibile visualizzare i tipi generici esistenti, non si possono creare nuovi tipi generici. Non si possono inoltre modificare i parametri di tipo per i tipi generici esistenti.

## <a name="see-also"></a>Vedere anche
 [Inheritance](https://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea) [Nozioni fondamentali sull'ereditarietà](https://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5) dell'ereditarietà [procedura: visualizzare l'ereditarietà tra tipi (Progettazione classi)](../ide/how-to-view-inheritance-between-types-class-designer.md) [Visual C++ classi in Progettazione classi](../ide/visual-cpp-classes-in-class-designer.md)
