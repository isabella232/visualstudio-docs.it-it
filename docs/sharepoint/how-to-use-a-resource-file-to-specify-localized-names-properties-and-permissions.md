---
title: Come usare un file di risorse in un SharePoint progetto | Microsoft Docs
titleSuffix: ''
description: Utilizzare un file di risorse in un progetto SharePoint in modo che sia possibile specificare nomi localizzati, definire proprietà e applicare autorizzazioni per gli oggetti definiti in un modello BDC.
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a909462908c26e6ed1af7fbf6458a54b57e901f1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156266"
---
# <a name="how-to-use-a-resource-file-in-a-sharepoint-project"></a>Come usare un file di risorse in un SharePoint progetto

  Utilizzando un file di risorse, è possibile fornire nomi localizzati, definire proprietà e applicare autorizzazioni per oggetti definiti in un modello di integrazione applicativa dei dati. Per specificare queste informazioni, aggiungere un elemento della risorsa di connettività dei dati di **business** a un progetto che contiene un **elemento del modello di connettività dei dati di** business. Specificare nomi, proprietà e autorizzazioni modificando l'XML del file di risorse.

### <a name="to-add-a-bdc-resource-file-to-a-sharepoint-project"></a>Per aggiungere un file di risorse BDC a un SharePoint progetto

1. In **Esplora soluzioni** espandere la cartella per il progetto SharePoint e quindi scegliere la cartella che contiene il modello BDC.

2. Nella barra dei menu scegliere **Project**  >  **Aggiungi nuovo elemento**.

3. Espandere il **SharePoint** e quindi scegliere il **nodo 2010.**

4. Nella finestra **di dialogo Aggiungi nuovo elemento** scegliere Elemento risorsa **connettività dati business**.

5. Nella casella **Nome** specificare il nome del file di risorse e quindi scegliere il **pulsante** Aggiungi.

     Un file di risorse con estensione bdcr verrà aggiunto al progetto e aperto per la modifica.

6. Aggiungere l'XML per definire i nomi localizzati, le proprietà e le autorizzazioni che si desidera applicare al modello di integrazione applicativa dei dati.

     Per informazioni su come definire questi elementi, vedere File [di modello e di risorse.](/previous-versions/office/developer/sharepoint-2010/aa674515(v=office.14))

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere un file di modello BDC esistente a un SharePoint progetto](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [Creare un modello di connettività dei dati aziendali](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Procedura: Creare un modello BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Procedura: Includere un assembly personalizzato in una funzionalità BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [Integrazione dei dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
