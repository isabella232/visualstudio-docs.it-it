---
title: 'Procedura: aggiungere un File di modello di integrazione applicativa dei dati esistente a un progetto SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.ImportDialog
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], import a model
- Business Data Connectivity service [SharePoint development in Visual Studio], reuse a model
- BDC [SharePoint development in Visual Studio], import a model
- BDC [SharePoint development in Visual Studio], remove a model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f7508cf8c66343894c16da7ff840bd275abb65c
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755898"
---
# <a name="how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project"></a>Procedura: aggiungere un file di modello di integrazione applicativa dei dati esistente a un progetto SharePoint
  È possibile personalizzare, creare un pacchetto e ridistribuire un modello di integrazione applicativa dei dati (BDC) usando Visual Studio per aggiungere il file del modello (*bdcm*) a qualsiasi progetto farm di SharePoint. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
### <a name="to-add-a-bdc-model-file-to-a-sharepoint-project"></a>Per aggiungere un file del modello di integrazione applicativa dei dati a un progetto SharePoint  
  
1.  Nelle **Esplora soluzioni**, scegliere la cartella per un progetto SharePoint.  
  
2.  Nella barra dei menu, scegliere **Project** > **Aggiungi elemento esistente**.  
  
3.  Nel **Aggiungi elemento esistente** finestra di dialogo, selezionare il percorso del file di definizione del modello che si desidera aggiungere al progetto, scegliere il file e quindi scegliere il **Add** pulsante.  
  
     Se il modello non definisce una *sistema Line-of-Business (LOB) di tipo assembly .NET*, il **LobSystem di assembly .NET aggiungere** verrà visualizzata la finestra di dialogo.  
  
4.  Se la finestra di dialogo viene visualizzata, effettuare una delle seguenti operazioni:  
  
    -   Se si desidera scrivere codice personalizzato e usare una finestra di progettazione per definire i metadati per il modello importato, scegliere il **Yes** pulsante, assegnare un nome di sistema e quindi scegliere il **OK** pulsante.  
  
    -   In caso contrario, scegliere il **No** pulsante e quindi scegliere il **OK** pulsante.  
  
     Il **Business Data Connectivity Model** elemento viene aggiunto al progetto.  
  
## <a name="see-also"></a>Vedere anche
 [Creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md)   
 [Procedura: usare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)   
 [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)   
 [Integrazione di dati aziendali in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
 
