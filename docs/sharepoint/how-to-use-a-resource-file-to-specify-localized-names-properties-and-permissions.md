---
title: Come usare un file di risorse in un progetto SharePoint | Microsoft Docs
titleSuffix: ''
description: Utilizzare un file di risorse in un progetto SharePoint in modo da poter fornire nomi localizzati, definire proprietà e applicare autorizzazioni per gli oggetti definiti in un modello di integrazione applicativa dei dati.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], localize strings
- BDC [SharePoint development in Visual Studio], resource file
- Business Data Connectivity service [SharePoint development in Visual Studio], resource strings
- BDC [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], properties
- Business Data Connectivity service [SharePoint development in Visual Studio], resource file
- BDC [SharePoint development in Visual Studio], resource strings
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ecc2bfab37e534e4edc005273ab5fc826b771228
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304358"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Come usare un file di risorse in un progetto SharePoint

  Utilizzando un file di risorse, è possibile fornire nomi localizzati, definire proprietà e applicare autorizzazioni per oggetti definiti in un modello di integrazione applicativa dei dati. Per specificare queste informazioni, è necessario aggiungere un elemento di **risorsa di connettività dei dati aziendali** a un progetto che contiene un elemento del **modello di integrazione applicativa dei dati** . Specificare nomi, proprietà e autorizzazioni modificando l'XML del file di risorse.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Per aggiungere un file di risorse BDC a un progetto SharePoint

1. In **Esplora soluzioni** espandere la cartella per il progetto SharePoint, quindi scegliere la cartella che contiene il modello di integrazione applicativa dei dati.

2. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

3. Espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere **risorsa integrazione applicativa dei dati**.

5. Nella casella **nome** specificare il nome del file di risorse, quindi scegliere il pulsante **Aggiungi** .

     Un file di risorse con estensione bdcr verrà aggiunto al progetto e aperto per la modifica.

6. Aggiungere l'XML per definire i nomi localizzati, le proprietà e le autorizzazioni che si desidera applicare al modello di integrazione applicativa dei dati.

     Per informazioni su come definire questi elementi, vedere [file di modello e di risorse](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14)).

## <a name="see-also"></a>Vedere anche
- [Procedura: aggiungere un file modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
