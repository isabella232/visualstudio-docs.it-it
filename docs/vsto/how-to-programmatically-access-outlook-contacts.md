---
title: 'Procedura: Accedere ai contatti di Outlook a livello di codice'
description: Informazioni su come accedere ai contatti di Outlook a livello di codice. In questo esempio vengono trovati tutti i contatti i cui cognome contengono una stringa di ricerca specificata.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 08e9d9ea69985a26a9688152f5c3b028caf75300
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828904"
---
# <a name="how-to-programmatically-access-outlook-contacts"></a>Procedura: Accedere ai contatti di Outlook a livello di codice
  In questo esempio vengono trovati tutti i contatti i cui cognome contengono una stringa di ricerca specificata.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_AccessContacts.trin_ol_accesscontacts/thisaddin.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_AccessContacts/thisaddin.vb" id="Snippet1":::


## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Contatti i cui cognome contengono la stringa **"Na"** (ad esempio, Tzipi Butnaru) nella **cartella** Contatti.

## <a name="see-also"></a>Vedi anche
- [Usare gli elementi di contatto](../vsto/working-with-contact-items.md)
- [Procedura: Aggiungere una voce ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
- [Procedura: Cercare un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
- [Procedura: Cercare un indirizzo di posta elettronica nei contatti a livello di codice](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)
- [Procedura: Eliminare contatti di Outlook a livello di codice](../vsto/how-to-programmatically-delete-outlook-contacts.md)
