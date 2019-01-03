---
title: 'Procedura: A livello di codice Invia messaggio di posta elettronica'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 91e59cc8d7bd0115a59c71f13e8e2dc200336b29
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840421"
---
# <a name="how-to-programmatically-send-email"></a>Procedura: A livello di codice Invia messaggio di posta elettronica  
  In questo esempio invia un messaggio di posta elettronica per i contatti con il nome di dominio **example.com** nei relativi indirizzi di posta elettronica.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 L'esempio presenta i requisiti seguenti:  
  
-   I contatti con il nome di dominio **example.com** nei relativi indirizzi di posta elettronica.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Non rimuovere il codice di filtro che cerca il nome di dominio **example.com**. Se si rimuove il filtro, la soluzione invierà messaggi di posta elettronica a tutti i contatti.  
  
## <a name="see-also"></a>Vedere anche  
 [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)   
 [Procedura: A livello di codice crea un elemento di posta elettronica](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [Procedura: Accedere a livello di codice ai contatti di Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [Procedura: A livello di programmazione eseguire azioni quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
