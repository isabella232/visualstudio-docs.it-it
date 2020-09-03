---
title: 'Procedura: accedere ai contatti di Outlook a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: 2f6d64512af660392c10082e3bcd3c26b6bc6885
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520094"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Procedura: accedere ai contatti di Outlook a livello di codice
  Questo esempio trova tutti i contatti il cui cognome contiene una stringa di ricerca specificata.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Contatti i cui ultimi nomi contengono la stringa "**na"** (ad esempio, Tzipi Butnaru) nella cartella **Contacts** .

## <a name="see-also"></a>Vedere anche
- [Usare gli elementi di contatto](../vsto/working-with-contact-items.md)
- [Procedura: aggiungere una voce ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Procedura: eseguire la ricerca di un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Procedura: eseguire la ricerca di un indirizzo di posta elettronica nei contatti a livello di codice](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Procedura: eliminare contatti di Outlook a livello di codice](../vsto/how-to-programmatically-delete-outlook-contacts.md)
