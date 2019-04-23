---
title: "Procedura: Aggiungere un riferimento all'Output del progetto | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project output references [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, project output references
- SharePoint development in Visual Studio, advanced packaging tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2ae3965647416d7a8e11cf0ea5e24cef1e54a09b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079785"
---
# <a name="how-to-add-a-project-output-reference"></a>Procedura: Aggiungere un riferimento all'output del progetto
  Per distribuire gli assembly di progetto non SharePoint (o file con estensione xap nei progetti Silverlight) in SharePoint, aggiungerli come un riferimento all'output del progetto.

 Questo processo crea una dipendenza di compilazione di soluzioni tra i due progetti. I progetti associati riferimenti all'output del progetto vengono compilati prima della compilazione e distribuzione del progetto SharePoint.

### <a name="to-add-a-project-output-reference"></a>Per aggiungere un riferimento all'output del progetto

1. Caricare una soluzione che contiene almeno un progetto di SharePoint e un progetto non SharePoint.

2. Nelle **Esplora soluzioni**, scegliere un elemento nel nodo del progetto SharePoint.

3. Nel **delle proprietà** finestra, scegliere il **riferimenti all'Output del progetto** proprietà e quindi scegliere i puntini di sospensione (![ellisse di ASP.NET Mobile Designer](../sharepoint/media/mwellipsis.gif "ASP. Ellisse NET Mobile Designer")) accanto al pulsante.

4. Nel **riferimenti all'Output del progetto** finestra di dialogo scegliere la **Add** pulsante.

5. Nel riquadro proprietà, scegliere la freccia accanto al **tipo di distribuzione** proprietà, quindi scegliere un valore appropriato per l'elemento di SharePoint non viene fatto riferimento, ad esempio **ElementFile**.

6. Scegliere la freccia accanto a **nome progetto**, scegliere il nome dell'elemento del progetto non SharePoint e quindi scegliere il **OK** pulsante.

## <a name="see-also"></a>Vedere anche
- [Fornire le informazioni di creazione di pacchetti e distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Procedura: Contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
