---
title: 'Procedura: spostare a livello di codice gli elementi in Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fced6a5e41d2b79d32575f20d224f75053acb988
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257722"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Procedura: spostare a livello di codice gli elementi in Outlook
  Questo esempio consente di spostare i messaggi di posta elettronica non letta dal **posta in arrivo** in una cartella denominata **Test**. Nell'esempio vengono spostati solo i messaggi che contengono la parola **Test** nel `Subject` campo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Una cartella di posta elettronica di Outlook denominata **Test**.  
  
-   Un messaggio di posta elettronica in arrivo con la parola **Test** nel `Subject` campo.  
  
## <a name="see-also"></a>Vedere anche  
 [Con le cartelle di lavoro](../vsto/working-with-folders.md)   
 [Procedura: recuperare una cartella a livello programmatico in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: eseguire la ricerca a livello di codice all'interno di una cartella specifica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Procedura: eseguire a livello di codice azioni quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  