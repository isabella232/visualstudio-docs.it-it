---
title: "Procedura: Visualizzare un'associazione di raccolte (Progettazione classi) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 434cfc541da3c670d8d444b9a4259b33476a17d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670517"
---
# <a name="how-to-visualize-a-collection-association-class-designer"></a>Procedura: visualizzare un'associazione di raccolte (Progettazione classi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le proprietà e i campi che sono raccolte di altri tipi possono essere visualizzati nel diagramma classi come associazione di raccolte. A differenza di un'associazione normale che visualizza un campo o una proprietà come linea che collega la classe proprietaria al tipo di campo, un'associazione di raccolte viene visualizzata come una linea che collega la classe proprietaria al tipo raccolto.

### <a name="to-create-a-collection-association"></a>Per creare un'associazione di raccolte

1. Nel codice creare una proprietà o un campo il cui tipo è una raccolta fortemente tipizzata.

2. Nel diagramma classi espandere la classe in modo che siano visualizzati le proprietà e i campi.

3. Nella classe fare clic con il pulsante destro del mouse sul campo o proprietà e scegliere **Mostra come associazione di raccolte**.

     La proprietà o il campo viene visualizzato come una linea di associazione che si collega al tipo raccolto.

## <a name="see-also"></a>Vedere anche
 [Procedura: creare associazioni tra tipi (Progettazione classi)](../ide/how-to-create-associations-between-types-class-designer.md) [progettazione di classi e tipi (Progettazione classi)](../ide/designing-classes-and-types-class-designer.md) [visualizzazione di tipi e relazioni (Progettazione classi)](../ide/viewing-types-and-relationships-class-designer.md)
