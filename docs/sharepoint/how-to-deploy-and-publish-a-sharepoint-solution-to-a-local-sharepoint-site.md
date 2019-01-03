---
title: 'Procedura: Distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8dd0dd78ca8f6b6f9791a657546cabc0d098b563
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53835324"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>Procedura: Distribuire e pubblicare una soluzione di SharePoint in un sito di SharePoint locale
  È possibile distribuire o pubblicare soluzioni SharePoint in un server SharePoint locale nel computer di sviluppo. Le copie di processo di distribuzione di *wsp* file nel server SharePoint, installa la soluzione e quindi attiva le funzionalità. La pubblicazione di elaborare solo copie il *wsp* file nel server SharePoint e lo installa. È necessario attivare manualmente per abilitarlo in SharePoint.  
  
## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>Per distribuire una soluzione di SharePoint al server SharePoint locale  
  
1.  Nelle **Esplora soluzioni**, scegliere il progetto che si desidera distribuire.  
  
2.  Nella barra dei menu, scegliere **compilare**, **Distribuisci soluzione**.  
  
     Il *wsp* file viene creato e installato nel server SharePoint locale. Inoltre, vengono attivate le funzionalità.  
  
## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>Per pubblicare una soluzione di SharePoint in un server SharePoint locale  
  
1.  Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto di SharePoint che si desidera pubblicare e quindi scegliere **Publish**.  
  
2.  Nel **Publish** finestra di dialogo scegliere la **pubblicare nel File System** pulsante di opzione.  
  
3.  Nel **percorso di destinazione** casella di testo, immettere un percorso locale e quindi scegliere il **Publish** pulsante.  
  
     Viene visualizzato lo stato della pubblicazione in Visual Studio **Output** finestra. Quando il processo viene completato, la soluzione (*wsp*) file viene installato nel server SharePoint locale. Tuttavia, deve ancora essere attivato da utilizzare in SharePoint. Se il file della soluzione esiste già, un errore si verifica e chiede se si desidera sovrascrivere il file esistente. Per informazioni sull'aggiornamento del pacchetto, vedere la sezione sull'aggiornamento di pacchetti remoti in [come: Distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## <a name="see-also"></a>Vedere anche
 [Procedura: Distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Creare pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Procedura: Personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Procedura: Aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
