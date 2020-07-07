---
title: 'Procedura: impostare i comandi di distribuzione di SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c2329efef64e7d8605f8483ff7dce3107cd702fa
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015507"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procedura: impostare i comandi di distribuzione di SharePoint
  È possibile personalizzare il processo di distribuzione impostando i comandi di pre-distribuzione e post-distribuzione. Questi comandi vengono eseguiti prima e dopo altre azioni di distribuzione quando si esegue il debug di soluzioni SharePoint da Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Per aggiungere un comando pre-distribuzione

1. Sulla barra dei menu scegliere **Project**  >  ** \<*ProjectName*> Proprietà**progetto.

2. Scegliere la scheda **SharePoint** .

3. Nella casella di testo **riga di comando pre-distribuzione** immettere i comandi MS-DOS o MSBuild per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory prima del completamento della distribuzione, immettere **dir**.

### <a name="to-add-a-post-deployment-command"></a>Per aggiungere un comando post-distribuzione

1. Sulla barra dei menu scegliere **Project**  >  ** \<*ProjectName*> Proprietà**progetto.

2. Scegliere la scheda **SharePoint** .

3. Nella casella di testo **riga di comando post-distribuzione** immettere i comandi MS-DOS o MSBuild per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory dopo il completamento della distribuzione, immettere **dir**. Per usare una variabile MSBuild per copiare l'assembly dalla directory di compilazione, immettere **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Vedere anche
- [Creare pacchetti e distribuire soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
