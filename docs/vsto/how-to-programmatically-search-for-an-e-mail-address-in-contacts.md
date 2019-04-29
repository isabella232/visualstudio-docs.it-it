---
title: 'Procedura: Eseguire la ricerca a livello di codice per un indirizzo di posta elettronica nei contatti'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 178549a815fd9a17377986a5b19e02db12ec76d1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62962296"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Procedura: Eseguire la ricerca a livello di codice per un indirizzo di posta elettronica nei contatti
  Questo esempio cerca una cartella Contatti per i contatti con il nome dominio **example.com** nei relativi indirizzi di posta elettronica.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_SearchEmail#1](../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Contatti con il nome dominio **example.com** nei relativi indirizzi di posta elettronica (ad esempio, `somebody@example.com`) e con il nome e il cognome.

## <a name="see-also"></a>Vedere anche
- [Lavorare con gli elementi di contatto](../vsto/working-with-contact-items.md)
- [Procedura: A livello di codice Invia messaggio di posta elettronica](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Procedura: Accedere a livello di codice ai contatti di Outlook](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Procedura: A livello di codice aggiungere una voce ai contatti di Outlook](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
