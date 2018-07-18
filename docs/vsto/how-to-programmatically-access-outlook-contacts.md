---
title: 'Procedura: accedere a livello di codice ai contatti di Outlook'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6ee09e0d0a51675bc00b19aedd0508276cb0cb09
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255941"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Procedura: accedere a livello di codice ai contatti di Outlook
  Questo esempio vengono trovati tutti i contatti il cui cognome contengano una stringa di ricerca specificato.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]  
  
## <a name="compile-the-code"></a>Compilare il codice  
 L'esempio presenta i requisiti seguenti:  
  
-   I contatti il cui cognome contengono la stringa "**Na"** , ad esempio, Tzipi Butnaru, nelle **contatti** cartella.  
  
## <a name="see-also"></a>Vedere anche  
 [Lavorare con gli elementi di contatto](../vsto/working-with-contact-items.md)   
 [Procedura: aggiungere a livello di codice una voce ai contatti di Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [Procedura: eseguire la ricerca a livello di codice di un contatto specifico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [Procedura: eseguire la ricerca a livello di codice per un indirizzo di posta elettronica nei contatti](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [Procedura: eliminare a livello di programmazione i contatti di Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  