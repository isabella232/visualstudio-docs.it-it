---
title: "Procedura: visualizzare un'associazione di raccolte (Progettazione classi)"
description: Informazioni su come visualizzare un'associazione di raccolte in Progettazione classi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b1e5be53f829949cfffbdc7db727b1117aa9de8
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901076"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Procedura: Visualizzare un'associazione di raccolte in Progettazione classi

Le proprietà e i campi che sono raccolte di altri tipi possono essere visualizzati nel diagramma classi come associazione di raccolte. A differenza di un'associazione normale che visualizza un campo o una proprietà come linea che collega la classe proprietaria al tipo di campo, un'associazione di raccolte viene visualizzata come una linea che collega la classe proprietaria al tipo raccolto.

## <a name="to-create-a-collection-association"></a>Per creare un'associazione di raccolte

1. Nel codice creare una proprietà o un campo il cui tipo è una raccolta fortemente tipizzata.

2. Nel diagramma classi espandere la classe in modo che siano visualizzati le proprietà e i campi.

3. Nella classe fare clic con il pulsante destro del mouse sul campo o proprietà e scegliere **Mostra come associazione di raccolte**.

La proprietà o il campo viene visualizzato come una linea di associazione che si collega al tipo raccolto.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare associazioni tra tipi](how-to-create-associations-between-types.md)
- [Progettazione di classi e tipi](designing-and-viewing-classes-and-types.md)
