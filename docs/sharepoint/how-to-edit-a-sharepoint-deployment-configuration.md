---
title: 'Procedura: modificare una configurazione di distribuzione di SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9640d98522c74fb33f8845e255511a807e03961e
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118964"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Procedura: modificare una configurazione di distribuzione di SharePoint
  È possibile creare una configurazione di distribuzione o modificare una configurazione di distribuzione esistente. Ad esempio, si potrebbe eseguire un singolo passaggio o modificare l'ordine dei passaggi del processo di distribuzione. È possibile creare o modificare le configurazioni di distribuzione poiché non è possibile modificare le configurazioni predefinite e a livello di codice aggiunte.  
  
## <a name="create-a-sharepoint-deployment-configuration"></a>Creare una configurazione di distribuzione di SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Per creare una configurazione di distribuzione di SharePoint  
  
1.  Nelle **Esplora soluzioni**, scegliere un progetto SharePoint e quindi nella barra dei menu, scegliere **Project**, * NomeProgetto ***proprietà**.  
  
2.  Nel **SharePoint** scheda, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuova configurazione distribuzione** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **nome** testo casella, immettere un nome per la configurazione della distribuzione.  
  
4.  Nel **passaggi di distribuzione disponibili** riquadro, scegliere i passaggi che si desidera aggiungere alla configurazione della distribuzione, scegliere il (**>**), quindi scegliere il **OK** pulsante.  
  
    > [!NOTE]  
    >  Se è stato configurato un comando di pre-distribuzione o post-distribuzione, questi passaggi da eseguire solo se sono state aggiunte a una configurazione di distribuzione personalizzato.  
  
## <a name="change-the-active-deployment-configuration"></a>Modificare la configurazione distribuzione attiva  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Per modificare la configurazione distribuzione attiva  
  
1.  Nelle **Esplora soluzioni**, scegliere un progetto SharePoint e quindi nella barra dei menu, scegliere **Project** > **\<*NomeProgetto*> Proprietà**.  
  
2.  Scegliere il **SharePoint** scheda.  
  
3.  Nel **configurazione distribuzione attiva** casella di riepilogo, scegliere il nome della configurazione di distribuzione che si desidera utilizzare.  
  
## <a name="see-also"></a>Vedere anche
 [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
