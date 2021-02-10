---
title: 'Procedura: impostare i comandi di distribuzione di SharePoint | Microsoft Docs'
description: Informazioni su come personalizzare il processo di distribuzione impostando i comandi di pre-distribuzione e post-distribuzione di SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 72938f316be22cd9b2eab2d7dab893c9370fb0ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965850"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procedura: impostare i comandi di distribuzione di SharePoint
  È possibile personalizzare il processo di distribuzione impostando i comandi di pre-distribuzione e post-distribuzione. Questi comandi vengono eseguiti prima e dopo altre azioni di distribuzione quando si esegue il debug di soluzioni SharePoint da Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Per aggiungere un comando pre-distribuzione

1. Sulla barra dei menu scegliere   >  **\<*ProjectName*> Proprietà** progetto.

2. Scegliere la scheda **SharePoint** .

3. Nella casella di testo **riga di comando pre-distribuzione** immettere i comandi MS-DOS o MSBuild per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory prima del completamento della distribuzione, immettere **dir**.

### <a name="to-add-a-post-deployment-command"></a>Per aggiungere un comando post-distribuzione

1. Sulla barra dei menu scegliere   >  **\<*ProjectName*> Proprietà** progetto.

2. Scegliere la scheda **SharePoint** .

3. Nella casella di testo **riga di comando post-distribuzione** immettere i comandi MS-DOS o MSBuild per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory dopo il completamento della distribuzione, immettere **dir**. Per usare una variabile MSBuild per copiare l'assembly dalla directory di compilazione, immettere **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
