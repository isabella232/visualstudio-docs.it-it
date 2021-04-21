---
title: Trovare un indirizzo di posta elettronica nei contatti a livello di codice
description: Informazioni su come usare i Visual Studio per trovare a livello di codice un indirizzo di posta elettronica nei contatti di Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], searching
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd977840cd75081d87011540ca00675fb84cee36
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828943"
---
# <a name="how-to-programmatically-search-for-an-email-address-in-contacts"></a>Procedura: Cercare un indirizzo di posta elettronica nei contatti a livello di codice
  Questo esempio cerca una cartella Contatti per i contatti con il nome dominio **example.com** nei relativi indirizzi di posta elettronica.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchEmail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Contatti con il nome dominio **example.com** nei relativi indirizzi di posta elettronica (ad esempio, `somebody@example.com`) e con il nome e il cognome.

## <a name="see-also"></a>Vedi anche
- [Usare gli elementi di contatto](../vsto/working-with-contact-items.md)
- [Procedura: Inviare messaggi di posta elettronica a livello di codice](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Procedura: Accedere ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Procedura: Aggiungere una voce ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)
