---
title: 'Procedura: Impostare i SharePoint di distribuzione | Microsoft Docs'
description: Informazioni su come personalizzare il processo di distribuzione impostando SharePoint comandi di pre-distribuzione e post-distribuzione.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: dc3ad57702b7063edd0c03f305a8ffc3722eebd6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130949"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procedura: Impostare i comandi SharePoint distribuzione
  È possibile personalizzare il processo di distribuzione impostando i comandi di pre-distribuzione e post-distribuzione. Questi comandi vengono eseguiti prima e dopo altre azioni di distribuzione quando si esegue il debug SharePoint soluzioni da Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Per aggiungere un comando di pre-distribuzione

1. Sulla barra dei menu scegliere **Project**  >  **\<*ProjectName*> proprietà**.

2. Scegliere la **SharePoint** dati.

3. Nella casella **di testo Riga di comando** pre-distribuzione immettere MS-DOS o MSBuild comandi per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory prima del completamento della distribuzione, immettere **dir**.

### <a name="to-add-a-post-deployment-command"></a>Per aggiungere un comando post-distribuzione

1. Sulla barra dei menu scegliere **Project**  >  **\<*ProjectName*> proprietà**.

2. Scegliere la **SharePoint** dati.

3. Nella casella **di testo Riga di comando** post-distribuzione immettere MS-DOS o MSBuild comandi per personalizzare questo passaggio.

     Ad esempio, per elencare il contenuto della directory al termine della distribuzione, immettere **dir**. Per usare una MSBuild per copiare l'assembly dalla directory di compilazione, immettere **copy $(TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Vedi anche
- [Creare pacchetti e distribuire SharePoint soluzioni](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
