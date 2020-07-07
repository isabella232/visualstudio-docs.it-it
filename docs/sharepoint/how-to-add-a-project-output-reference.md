---
title: "Procedura: aggiungere un riferimento all'output del progetto | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: bea0f39ae161d8b695f872cb634c35d0cb205c91
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016756"
---
# <a name="how-to-add-a-project-output-reference"></a>Procedura: aggiungere un riferimento all'output del progetto
  Per distribuire gli assembly di progetto non SharePoint (o i file con estensione xap nei progetti Silverlight) in SharePoint, aggiungerli come riferimento all'output del progetto.

 Questo processo crea una dipendenza di compilazione della soluzione tra i due progetti. I progetti associati ai riferimenti di output del progetto vengono compilati prima della compilazione e della distribuzione del progetto SharePoint.

### <a name="to-add-a-project-output-reference"></a>Per aggiungere un riferimento all'output del progetto

1. Caricare una soluzione che contenga almeno un progetto SharePoint e un progetto non SharePoint.

2. In **Esplora soluzioni**scegliere un elemento nel nodo del progetto SharePoint.

3. Nella finestra **Proprietà** scegliere la proprietà **riferimenti output progetto** , quindi scegliere il pulsante con i puntini di sospensione (![ASP.NET Mobile Designer ellisse](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto a esso.

4. Nella finestra di dialogo **riferimenti output progetto** scegliere il pulsante **Aggiungi** .

5. Nel riquadro Proprietà scegliere la freccia accanto alla proprietà tipo di **distribuzione** , quindi scegliere un valore appropriato per l'elemento non SharePoint a cui si fa riferimento, ad esempio **ElementFile**.

6. Scegliere la freccia accanto a **nome progetto**, scegliere il nome dell'elemento di progetto non SharePoint, quindi scegliere il pulsante **OK** .

## <a name="see-also"></a>Vedere anche
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Procedura: contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
