---
title: 'Procedura: spostare elementi in Outlook | Documenti Microsoft'
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
helpviewer_keywords: Outlook folders [Office development in Visual Studio], moving items
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: b77524d5f297ada0e4821e229d9bb981518f9730
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Procedura: spostare elementi in Outlook a livello di codice
  In questo esempio sposta i messaggi di posta elettronica non letta dal **posta in arrivo** in una cartella denominata **Test**. Nell'esempio vengono spostati solo i messaggi che contengono la parola **Test** nel `Subject` campo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Una cartella di posta elettronica di Outlook denominata **Test**.  
  
-   Un messaggio di posta elettronica in arrivo con la parola **Test** nel `Subject` campo.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle cartelle](../vsto/working-with-folders.md)   
 [Procedura: recuperare a livello di codice di una cartella per nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: eseguire la ricerca a livello di codice all'interno di una cartella specifica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [Procedura: Eseguire azioni a livello di codice quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  