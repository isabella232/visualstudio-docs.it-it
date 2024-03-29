---
title: 'Procedura: Inviare messaggi di posta elettronica a livello di codice'
description: Usare Visual Studio per inviare a livello di codice un messaggio di posta elettronica da Microsoft Outlook. Questo esempio invia un messaggio di posta elettronica ai contatti con il nome di dominio example.com.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], sending e-mail
- Outlook [Office development in Visual Studio], creating e-mail
- Outlook [Office development in Visual Studio], sending e-mail
- e-mail [Office development in Visual Studio], sending
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c1a8f2fb5843ccb39808250ef847e8e5b4355960
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122115239"
---
# <a name="how-to-programmatically-send-email"></a>Procedura: Inviare messaggi di posta elettronica a livello di codice
  Questo esempio invia un messaggio di posta elettronica ai contatti con il nome di **dominio example.com** negli indirizzi di posta elettronica.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- I contatti con il nome di **dominio example.com** negli indirizzi di posta elettronica.

## <a name="robust-programming"></a>Programmazione efficiente
 Non rimuovere il codice di filtro che cerca il nome di **dominio example.com**. Se si rimuove il filtro, la soluzione invierà messaggi di posta elettronica a tutti i contatti.

## <a name="see-also"></a>Vedi anche
- [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)
- [Procedura: Creare un elemento di posta elettronica a livello di codice](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Procedura: Accedere ai contatti Outlook a livello di codice](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Procedura: Eseguire azioni a livello di codice quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
