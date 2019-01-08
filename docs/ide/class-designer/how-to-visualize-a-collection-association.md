---
title: "Procedura: Visualizzare un'associazione di raccolte (Progettazione classi)"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2957492224f4d69a9536b4dfd6f47c136f72b0c
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684064"
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
