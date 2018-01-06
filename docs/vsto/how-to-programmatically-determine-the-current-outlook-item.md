---
title: 'Procedura: determinare a livello di codice all''elemento Outlook corrente | Documenti Microsoft'
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
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 112a2c1273b0087eea98736a4e47ac5de8787149
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Procedura: determinare l'elemento corrente di Outlook a livello di codice
  In questo esempio viene utilizzato l'evento di Explorer. SelectionChange per visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato. Il codice visualizza quindi l'elemento selezionato.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   Un appuntamento, contatto e gli elementi di posta elettronica in Microsoft Office Outlook.  
  
## <a name="see-also"></a>Vedere anche  
 [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Procedura: recuperare a livello di codice di una cartella per nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [Procedura: Eseguire la ricerca di un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  