---
title: 'Procedura: Modificare una configurazione di distribuzione di SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 98cdc452663fd32508496c1fc52a49033a0b4381
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54870061"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Procedura: Modificare una configurazione di distribuzione di SharePoint
  È possibile creare una configurazione di distribuzione o modificare una configurazione di distribuzione esistente. Ad esempio, si potrebbe eseguire un singolo passaggio o modificare l'ordine dei passaggi del processo di distribuzione. È possibile creare o modificare le configurazioni di distribuzione poiché non è possibile modificare le configurazioni predefinite e a livello di codice aggiunte.  
  
## <a name="create-a-sharepoint-deployment-configuration"></a>Creare una configurazione di distribuzione di SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Per creare una configurazione di distribuzione di SharePoint  
  
1.  Nelle **Esplora soluzioni**, scegliere un progetto SharePoint e quindi nella barra dei menu, scegliere **Project**, _ProjectName_**proprietà**.  
  
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
