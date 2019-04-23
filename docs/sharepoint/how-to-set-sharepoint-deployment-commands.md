---
title: 'Procedura: Set SharePoint Deployment Commands | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7664dfcfe11d7ab7dc6ab03045533bbd9e69fb9c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60077784"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procedura: Impostare i comandi di distribuzione di SharePoint
  È possibile personalizzare il processo di distribuzione, impostare i comandi di pre e post-distribuzione. Questi comandi vengono eseguiti prima e dopo altre azioni di distribuzione durante il debug di soluzioni di SharePoint da Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Per aggiungere un comando di pre-distribuzione

1. Nella barra dei menu, scegliere **Project** > **\<*ProjectName*> proprietà**.

2. Scegliere il **SharePoint** scheda.

3. Nel **riga di comando di pre-distribuzione** testo immettere i comandi di MS-DOS o MSBuild per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory prima che venga completata la distribuzione, immettere **dir**.

### <a name="to-add-a-post-deployment-command"></a>Per aggiungere un comando post-distribuzione

1. Nella barra dei menu, scegliere **Project** > **\<*ProjectName*> proprietà**.

2. Scegliere il **SharePoint** scheda.

3. Nel **riga di comando di post-distribuzione** testo immettere i comandi di MS-DOS o MSBuild per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory dopo la distribuzione è completata, immettere **dir**. Per usare una variabile di MSBuild per copiare l'assembly dalla directory di compilazione, immettere **copiare c:\DeploymentDirectory TargetPath**.

## <a name="see-also"></a>Vedere anche
- [Il pacchetto e distribuire soluzioni di SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
