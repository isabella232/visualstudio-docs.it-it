---
title: 'Procedura: Aggiungere un riferimento Project output | Microsoft Docs'
description: Informazioni su come aggiungere un riferimento all'output del progetto in modo da poter distribuire assembly di progetto non SharePoint (o file con estensione xap nei progetti Silverlight) in SharePoint.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d3d7bea0d57e4351fc022b2f4c45ecc1b6423e4b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625152"
---
# <a name="how-to-add-a-project-output-reference"></a>Procedura: Aggiungere un riferimento all'output del progetto
  Per distribuire assembly di progetto non SharePoint (o file con estensione xap nei progetti Silverlight) in SharePoint, aggiungerli come riferimento all'output del progetto.

 Questo processo crea una dipendenza di compilazione della soluzione tra i due progetti. I progetti associati ai riferimenti all'output del progetto vengono compilati prima SharePoint il progetto viene compilato e distribuito.

### <a name="to-add-a-project-output-reference"></a>Per aggiungere un riferimento all'output del progetto

1. Caricare una soluzione che contiene almeno un progetto SharePoint e un progetto non SharePoint progetto.

2. In **Esplora soluzioni** scegliere un elemento nel nodo SharePoint progetto.

3. Nella finestra **Proprietà** scegliere la proprietà Riferimenti Project **output** e quindi fare clic sui puntini di sospensione (![ASP.NET mobile Designer](../sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")) accanto.

4. Nella finestra **Project riferimenti di output** scegliere il **pulsante** Aggiungi.

5. Nel riquadro delle proprietà scegliere la  freccia accanto alla proprietà Tipo di distribuzione e quindi scegliere un valore appropriato per l'elemento non SharePoint a cui si fa riferimento, ad esempio **ElementFile**.

6. Scegliere la freccia accanto Project **Nome**, scegliere il nome dell'elemento di progetto non SharePoint e quindi scegliere **OK.**

## <a name="see-also"></a>Vedi anche
- [Fornire informazioni sulla creazione di pacchetti e sulla distribuzione negli elementi del progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [Procedura: Contrassegnare i controlli come controlli sicuri](../sharepoint/how-to-mark-controls-as-safe-controls.md)
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
