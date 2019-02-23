---
title: 'Procedura: Accedere a livello di codice ai contatti di Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c46df4218a12c0f9a155567aeee0c007d0a19c53
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598206"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Procedura: Accedere a livello di codice ai contatti di Outlook
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
- [Lavorare con gli elementi di contatto](../vsto/working-with-contact-items.md)
- [Procedura: A livello di codice aggiungere una voce ai contatti di Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Procedura: Eseguire la ricerca a livello di codice di un contatto specifico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Procedura: Eseguire la ricerca a livello di codice per un indirizzo di posta elettronica nei contatti](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Procedura: A livello di codice eliminare contatti di Outlook](../vsto/how-to-programmatically-delete-outlook-contacts.md)
