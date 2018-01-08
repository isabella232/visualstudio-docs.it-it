---
title: 'Procedura: associare una pagina Web una cartella di Outlook a livello di codice | Documenti Microsoft'
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
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: d2ce7291b992c4d2952853c502ade8fcd70f3791
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Procedura: associare una pagina Web a una cartella di Outlook a livello di codice
  In questo esempio cerca una cartella denominata `HtmlView` in Microsoft Office Outlook. Se la cartella non esiste, il codice viene creata la cartella e assegna una pagina Web. Se la cartella esiste, il codice visualizza il contenuto della cartella.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle cartelle](../vsto/working-with-folders.md)   
 [Procedura: recuperare a livello di codice di una cartella per nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: Creare cartelle personalizzate a livello di codice](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  