---
title: 'Procedura: Modificare una configurazione SharePoint distribuzione | Microsoft Docs'
description: Informazioni su come creare una SharePoint di distribuzione o modificare una configurazione di distribuzione esistente.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 295c756457cbc8326bcd80d3b92c2ad233d2cb7a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115525"
---
# <a name="how-to-edit-a-sharepoint-deployment-configuration"></a>Procedura: Modificare una configurazione SharePoint distribuzione
  È possibile creare una configurazione di distribuzione o modificare una configurazione di distribuzione esistente. Ad esempio, è possibile eseguire un singolo passaggio o modificare l'ordine dei passaggi nel processo di distribuzione. È possibile creare o modificare le configurazioni di distribuzione perché le configurazioni predefinite e aggiunte a livello di codice non possono essere modificate.

## <a name="create-a-sharepoint-deployment-configuration"></a>Creare una configurazione SharePoint distribuzione locale

#### <a name="to-create-a-sharepoint-deployment-configuration"></a>Per creare una configurazione SharePoint distribuzione

1. In **Esplora soluzioni** scegliere un SharePoint progetto e quindi, sulla barra dei menu, **scegliere** Project proprietà _ProjectName_.

2. Nella scheda **SharePoint** scegliere il **pulsante** Nuovo.

     Verrà **visualizzata la finestra di dialogo Aggiungi** nuova configurazione distribuzione .

3. Nella casella **di testo** Nome immettere un nome per la configurazione della distribuzione.

4. Nel riquadro **Passaggi di distribuzione** disponibili scegliere i passaggi da aggiungere alla configurazione di distribuzione, scegliere il pulsante ( ) e quindi scegliere **>** **OK.**

    > [!NOTE]
    > Se è stato configurato un comando pre-distribuzione o un comando post-distribuzione, questi passaggi vengono eseguiti solo se vengono aggiunti a una configurazione di distribuzione personalizzata.

## <a name="change-the-active-deployment-configuration"></a>Modificare la configurazione della distribuzione attiva

#### <a name="to-change-the-active-deployment-configuration"></a>Per modificare la configurazione di distribuzione attiva

1. In **Esplora soluzioni** scegliere un progetto SharePoint progetto e quindi scegliere Project   >  **\<*ProjectName*> proprietà**.

2. Scegliere la **SharePoint** impostazioni.

3. Nella casella **di riepilogo Configurazione distribuzione** attiva scegliere il nome della configurazione di distribuzione che si vuole usare.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
