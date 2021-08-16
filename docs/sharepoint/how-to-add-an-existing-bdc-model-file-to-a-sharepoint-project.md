---
title: 'Procedura: Aggiungere un file di modello BDC esistente a un SharePoint Project | Microsoft Docs'
titleSuffix: ''
description: Aggiungere un file di modello BDC (Business Data Connectivity) esistente a un progetto SharePoint in Visual Studio, in modo da poter personalizzare, creare un pacchetto e ridistribuire un modello BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 7a9c84c417e9541d4376935a1fe979d8c608e75d6204e126ac3aa2dd44ac2213
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367590"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Procedura: Aggiungere un file di modello BDC esistente a un SharePoint progetto
  È possibile personalizzare, creare un pacchetto e ridistribuire un modello BDC (Business Data Connectivity) usando Visual Studio per aggiungere il file di modello (*bdcm*) a qualsiasi progetto SharePoint farm. Per altre informazioni, vedere [Creare un modello di connettività dei dati aziendali.](../sharepoint/creating-a-business-data-connectivity-model.md)

### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Per aggiungere un file del modello di integrazione applicativa dei dati a un progetto SharePoint

1. In **Esplora soluzioni** scegliere la cartella per un SharePoint progetto.

2. Sulla barra dei menu scegliere **Project**  >  **Aggiungi elemento esistente**.

3. Nella finestra **di dialogo Aggiungi** elemento esistente passare al percorso del file di definizione del modello che si vuole aggiungere al progetto, scegliere il file e quindi scegliere il **pulsante** Aggiungi.

    Se il modello non definisce un sistema *line-of-business (LOB)* di tipo assembly .NET, viene visualizzata la finestra di dialogo Aggiungi assembly **.NET LobSystem.**

4. Se la finestra di dialogo viene visualizzata, effettuare una delle seguenti operazioni:

   - Se si vuole scrivere codice personalizzato e usare una finestra di progettazione  per definire i metadati per il modello importato, scegliere il pulsante Sì, assegnare un nome al sistema e quindi scegliere **il pulsante OK.**

   - In caso contrario, **scegliere il pulsante** No e quindi scegliere il pulsante **OK.**

     **L'elemento Modello di connettività dei** dati di business viene aggiunto al progetto.

## <a name="see-also"></a>Vedi anche
- [Creare un modello di connettività dei dati aziendali](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: Creare un modello BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: Usare un file di risorse per specificare nomi, proprietà e autorizzazioni localizzati](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [Procedura: Includere un assembly personalizzato in una funzionalità BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione dei dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
