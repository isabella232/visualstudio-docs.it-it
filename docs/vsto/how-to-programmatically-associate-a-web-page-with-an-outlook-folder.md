---
title: 'Procedura: A livello di programmazione associare una pagina web a una cartella di Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1950a75eeee6f99a03346dde53317b30824a35f4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53990659"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Procedura: A livello di programmazione associare una pagina web a una cartella di Outlook
  Questo esempio viene verificata una cartella denominata `HtmlView` in Microsoft Office Outlook. Se la cartella non esiste, il codice crea la cartella e la assegna a una pagina Web a. Se la cartella esiste, il codice visualizza il contenuto della cartella.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Con le cartelle di lavoro](../vsto/working-with-folders.md)   
 [Procedura: Recuperano una cartella in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: A livello di programmazione creare cartelle personalizzate](../vsto/how-to-programmatically-create-custom-folder-items.md)  
