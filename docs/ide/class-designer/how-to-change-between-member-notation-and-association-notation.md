---
title: Modifica tra la notazione di associazione & membro
description: Informazioni su come modificare il modo in cui il diagramma classi rappresenta una relazione di associazione Progettazione classi tra due tipi, dalla notazione membro alla notazione di associazione e viceversa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 3b97ff04abdbed42b9adb1a5fd2b41d4feca9931
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124217"
---
# <a name="how-to-change-between-member-notation-and-association-notation-in-class-designer"></a>Procedura: Passare dalla notazione membro alla notazione associazione in Progettazione classi

In Progettazione classi è possibile modificare il modo in cui il diagramma classi rappresenta una relazione di associazione tra **due** tipi, dalla notazione membro alla notazione di associazione e viceversa. I membri visualizzati come linee di associazione spesso offrono una visualizzazione utile della correlazione tra tipi.

> [!NOTE]
> Le relazioni di associazione possono essere rappresentate come proprietà del membro o campo. Per passare dalla notazione membro alla notazione associazione, un tipo deve avere un membro di un altro tipo. Per passare dalla notazione associazione alla notazione membro, i due tipi devono essere collegati da una linea di associazione. Per altre informazioni, vedere [Procedura: Creare associazioni tra tipi](how-to-create-associations-between-types.md). Se il progetto contiene più diagrammi di classi, le modifiche apportate al modo in cui un diagramma visualizza le relazioni di associazione influiscono solo tale diagramma. Per modificare il modo in cui un altro diagramma visualizza le relazioni di associazione, aprire o visualizzare tale diagramma ed seguire questi passaggi.

## <a name="to-change-member-notation-to-association-notation"></a>Per passare dalla notazione membro alla notazione associazione

1. Dal nodo del progetto in Esplora soluzioni, aprire il file del diagramma classi (con estensione CD).

2. Nella forma tipo del diagramma classi, fare doppio clic su proprietà del membro o sul campo che rappresenta l'associazione e scegliere **Mostra come associazione**.

    > [!TIP]
    > Se non sono visibili campi o proprietà nella forma tipo, i raggruppamenti nella forma potrebbero essere compressi. Per espandere la forma tipo, fare doppio clic sul nome del raggruppamento o fare clic con il pulsante destro del mouse sulla forma tipo e scegliere **Espandi**.

    Il membro scompare dal raggruppamento della forma tipo e viene visualizzata una linea di associazione per connettere i due tipi. La linea di associazione è contrassegnata con il nome della proprietà o del campo.

## <a name="to-change-association-notation-to-member-notation"></a>Per passare dalla notazione associazione alla notazione membro

Nel diagramma classi, fare clic con il pulsante destro del mouse sulla linea di associazione e scegliere **Mostra come proprietà** o **Mostra come campo**, come appropriato. La linea di associazione scompare e la proprietà viene visualizzata nel raggruppamento appropriato all'interno della forma tipo nel diagramma.

## <a name="see-also"></a>Vedi anche

- [Procedura: Creare ereditarietà tra tipi](how-to-create-inheritance-between-types.md)
- [Procedura: Visualizzare l'ereditarietà tra tipi](how-to-view-inheritance-between-types.md)
- [Visualizzazione di tipi e relazioni](designing-and-viewing-classes-and-types.md)
- [Procedura: Visualizzare un'associazione di raccolte](how-to-visualize-a-collection-association.md)
