---
title: 'Procedura: associare a livello di codice una pagina web a una cartella di Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
ms.openlocfilehash: 2cb1ef525917288dc44609b899611db884da9073
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256465"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Procedura: associare a livello di codice una pagina web a una cartella di Outlook
  Questo esempio viene verificata una cartella denominata `HtmlView` in Microsoft Office Outlook. Se la cartella non esiste, il codice crea la cartella e la assegna a una pagina Web a. Se la cartella esiste, il codice visualizza il contenuto della cartella.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Con le cartelle di lavoro](../vsto/working-with-folders.md)   
 [Procedura: recuperare una cartella a livello programmatico in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: creare cartelle personalizzate](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  