---
title: 'Procedura: impostare i comandi di distribuzione di SharePoint | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, deploying
ms.assetid: 289c8c33-a603-434e-889f-a0d0a1736ecb
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d5692195f340ce347df0bc6f8ad2d60225f24e6d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Procedura: impostare i comandi di distribuzione di SharePoint
  È possibile personalizzare il processo di distribuzione mediante l'impostazione di comandi pre-distribuzione e post-distribuzione. Questi comandi vengono eseguiti prima e dopo le altre azioni di distribuzione durante il debug di soluzioni di SharePoint da Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Per aggiungere un comando di pre-distribuzione  
  
1.  Sulla barra dei menu scegliere **Progetto**, *Proprietà***NomeProgetto**.  
  
2.  Scegliere il **SharePoint** scheda.  
  
3.  Nel **riga di comando pre-distribuzione** testo immettere comandi MS-DOS o MSBuild per personalizzare questo passaggio.  
  
     Ad esempio, per elencare il contenuto della directory prima della distribuzione è stata completata, immettere **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Per aggiungere un comando di post-distribuzione  
  
1.  Sulla barra dei menu scegliere **Progetto**, *Proprietà***NomeProgetto**.  
  
2.  Scegliere il **SharePoint** scheda.  
  
3.  Nel **riga di comando post-distribuzione** testo immettere comandi MS-DOS o MSBuild per personalizzare questo passaggio.  
  
     Ad esempio, per elencare il contenuto della directory dopo la distribuzione è completata, immettere **dir**. Per utilizzare una variabile di MSBuild per copiare l'assembly dalla directory di compilazione, immettere **copiare $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  