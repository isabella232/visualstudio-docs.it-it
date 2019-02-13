---
title: "Procedura: Visualizzare un'associazione di raccolte (Progettazione classi)"
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.classdesigner.collectionassociationline
- vs.classdesigner.ShowAssociationException
helpviewer_keywords:
- collection associations
- collections, collection associations
- Class Designer [Visual Studio], collection associations
ms.assetid: 54e39838-2fc9-4dc2-85b6-7e88a743108e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e734b84bb8c386c60f3fef9061d74b8b31277cec
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55910949"
---
# <a name="how-to-visualize-a-collection-association-in-class-designer"></a>Procedura: Visualizzare un'associazione di raccolte in Progettazione classi

Le proprietà e i campi che sono raccolte di altri tipi possono essere visualizzati nel diagramma classi come associazione di raccolte. A differenza di un'associazione normale che visualizza un campo o una proprietà come linea che collega la classe proprietaria al tipo di campo, un'associazione di raccolte viene visualizzata come una linea che collega la classe proprietaria al tipo raccolto.

## <a name="to-create-a-collection-association"></a>Per creare un'associazione di raccolte

1.  Nel codice creare una proprietà o un campo il cui tipo è una raccolta fortemente tipizzata.

2.  Nel diagramma classi espandere la classe in modo che siano visualizzati le proprietà e i campi.

3.  Nella classe fare clic con il pulsante destro del mouse sul campo o proprietà e scegliere **Mostra come associazione di raccolte**.

La proprietà o il campo viene visualizzato come una linea di associazione che si collega al tipo raccolto.

## <a name="see-also"></a>Vedere anche

- [Procedura: Creare associazioni tra tipi](how-to-create-associations-between-types.md)
- [Progettazione di classi e tipi](designing-and-viewing-classes-and-types.md)
