---
title: 'Procedura: modificare una configurazione di distribuzione di SharePoint | Microsoft Docs'
description: Informazioni su come creare una configurazione di distribuzione di SharePoint o modificare una configurazione di distribuzione esistente.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.Project.DeploymentConfig
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 59354537f0c1f22534395da1e0ed3db3929a14a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913646"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Procedura: modificare una configurazione di distribuzione di SharePoint
  È possibile creare una configurazione di distribuzione o modificare una configurazione di distribuzione esistente. Ad esempio, è possibile eseguire un singolo passaggio o modificare l'ordine dei passaggi nel processo di distribuzione. Potrebbe essere necessario creare o modificare le configurazioni di distribuzione perché non è possibile modificare le configurazioni predefinite e aggiunte a livello di codice.

## <a name="create-a-sharepoint-deployment-configuration"></a>Creare una configurazione di distribuzione di SharePoint

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Per creare una configurazione di distribuzione di SharePoint

1. In **Esplora soluzioni** scegliere un progetto SharePoint, quindi nella barra dei menu scegliere **progetto**,**Proprietà** _NomeProgetto_.

2. Nella scheda **SharePoint** scegliere il pulsante **nuovo** .

     Verrà visualizzata la finestra di dialogo **Aggiungi nuova configurazione di distribuzione** .

3. Nella casella di testo **nome** immettere un nome per la configurazione della distribuzione.

4. Nel riquadro **passaggi di distribuzione disponibili** scegliere i passaggi da aggiungere alla configurazione della distribuzione, scegliere il **>** pulsante (), quindi scegliere il pulsante **OK** .

    > [!NOTE]
    > Se è stato configurato un comando di pre-distribuzione o un comando post-distribuzione, questi passaggi vengono eseguiti solo se vengono aggiunti a una configurazione di distribuzione personalizzata.

## <a name="change-the-active-deployment-configuration"></a>Modificare la configurazione di distribuzione attiva

#### <a name="to-change-the-active-deployment-configuration"></a>Per modificare la configurazione della distribuzione attiva

1. In **Esplora soluzioni** scegliere un progetto SharePoint, quindi nella barra dei menu scegliere   >  **\<*ProjectName*> Proprietà** progetto.

2. Scegliere la scheda **SharePoint** .

3. Nella casella di riepilogo **Configurazione distribuzione attiva** scegliere il nome della configurazione di distribuzione che si desidera utilizzare.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
