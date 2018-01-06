---
title: 'Procedura: invio di posta elettronica a livello di codice | Documenti Microsoft'
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
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 39a0ebee37c57630649f680d14aa8fef22833225
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-send-e-mail"></a>Procedura: invio di posta elettronica a livello di codice  
  Questo esempio viene inviato un messaggio di posta elettronica per i contatti con il nome di dominio **example.com** indirizzi di posta elettronica.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>Compilazione del codice  
 L'esempio presenta i requisiti seguenti:  
  
-   I contatti con il nome di dominio **example.com** indirizzi di posta elettronica.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Non rimuovere il codice di filtro che cerca il nome di dominio **example.com**. Se si rimuove il filtro, la soluzione invierà messaggi di posta elettronica a tutti i contatti.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo di elementi di posta elettronica](../vsto/working-with-mail-items.md)   
 [Procedura: creare a livello di programmazione un elemento di posta elettronica](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Procedura: accedere a livello di codice ai contatti di Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Procedura: Eseguire azioni a livello di codice quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  