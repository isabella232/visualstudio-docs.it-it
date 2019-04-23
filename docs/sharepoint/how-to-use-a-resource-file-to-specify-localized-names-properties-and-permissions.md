---
title: 'Procedura: Usare un File di risorse per specificare nomi localizzati, proprietà e autorizzazioni | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 2be88a29d3e9e3da9d1963aa1226ffca0a0a2bbd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066533"
---
# <a name="how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions"></a>Procedura: Usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni
  Utilizzando un file di risorse, è possibile fornire nomi localizzati, definire proprietà e applicare autorizzazioni per oggetti definiti in un modello di integrazione applicativa dei dati. Per specificare queste informazioni, si aggiunge un **risorse di integrazione applicativa dei dati aziendali** elemento a un progetto che contiene un **Business Data Connectivity Model** elemento. Specificare nomi, proprietà e autorizzazioni modificando l'XML del file di risorse.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Per aggiungere un file di risorse di integrazione applicativa dei dati a un progetto SharePoint

1. Nelle **Esplora soluzioni**, espandere la cartella del progetto SharePoint e quindi scegliere la cartella che contiene il modello di integrazione applicativa dei dati.

2. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

3. Espandere la **SharePoint** nodo, quindi scegliere il **2010** nodo.

4. Nel **Aggiungi nuovo elemento** finestra di dialogo, scegliere **elemento risorse di connettività dei dati di Business**.

5. Nel **Name** casella, specificare il nome del file di risorse e quindi scegliere il **Add** pulsante.

     Un file di risorse con estensione bdcr verrà aggiunto al progetto e aperto per la modifica.

6. Aggiungere l'XML per definire i nomi localizzati, le proprietà e le autorizzazioni che si desidera applicare al modello di integrazione applicativa dei dati.

     Per informazioni su come definire questi elementi, vedere [modello e i file di risorse](http://go.microsoft.com/fwlink/?LinkID=169283).

## <a name="see-also"></a>Vedere anche
- [Procedura: Aggiungere un file di modello di integrazione applicativa dei dati esistente a un progetto SharePoint](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: Creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: Includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione di dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
