---
title: 'Procedura: modificare una configurazione di distribuzione di SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: bff1895b-d3fe-4ec0-ba91-f8884dc35957
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 408d7801e883e85e37d721c342dba691702d77cf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Procedura: modificare una configurazione di distribuzione SharePoint
  È possibile creare una configurazione di distribuzione o modificare una configurazione di distribuzione esistente. Ad esempio, è Impossibile eseguire un singolo passaggio o modificare l'ordine dei passaggi del processo di distribuzione. Si desidera, creare o modificare le configurazioni di distribuzione perché non è possibile modificare le configurazioni predefinite e aggiunte a livello di codice.  
  
## <a name="creating-a-sharepoint-deployment-configuration"></a>Creazione di una configurazione di distribuzione di SharePoint  
  
#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Per creare una configurazione di distribuzione di SharePoint  
  
1.  In **Esplora**, scegliere un progetto SharePoint e quindi nella barra dei menu scegliere **progetto**, *ProjectName***proprietà**.  
  
2.  Nel **SharePoint** scheda, scegliere il **New** pulsante.  
  
     Il **Aggiungi nuova configurazione distribuzione** viene visualizzata la finestra di dialogo.  
  
3.  Nel **nome** testo, immettere un nome per la configurazione della distribuzione.  
  
4.  Nel **passaggi di distribuzione disponibili** riquadro, scegliere i passaggi che si desidera aggiungere alla configurazione della distribuzione, scegliere il (**>**) e quindi scegliere il **OK** pulsante.  
  
    > [!NOTE]  
    >  Se è stato configurato un comando di pre-distribuzione o post-distribuzione, questi passaggi eseguiti solo se vengono aggiunti a una configurazione di distribuzione personalizzata.  
  
## <a name="changing-the-active-deployment-configuration"></a>La modifica della configurazione di distribuzione attiva  
  
#### <a name="to-change-the-active-deployment-configuration"></a>Per modificare la configurazione distribuzione attiva  
  
1.  In **Esplora**, scegliere un progetto SharePoint e quindi nella barra dei menu scegliere **progetto**, *ProjectName***proprietà**.  
  
2.  Scegliere il **SharePoint** scheda.  
  
3.  Nel **configurazione distribuzione attiva** nella casella di riepilogo, scegliere il nome della configurazione di distribuzione che si desidera utilizzare.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  