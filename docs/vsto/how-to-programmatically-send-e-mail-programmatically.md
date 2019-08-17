---
title: 'Procedura: Inviare messaggi di posta elettronica a livello di codice'
ms.date: 08/14/2019
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 72d033add2ba8320b14eebd5af700ab225d34410
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551762"
---
# <a name="how-to-programmatically-send-email"></a>Procedura: Inviare messaggi di posta elettronica a livello di codice
  Questo esempio Invia un messaggio di posta elettronica ai contatti che hanno il nome di dominio **example.com** nei rispettivi indirizzi di posta elettronica.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_ProgramEmail#1](../vsto/codesnippet/CSharp/Trin_OL_ProgramEMail/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Contatti con il nome di dominio **example.com** nei rispettivi indirizzi di posta elettronica.

## <a name="robust-programming"></a>Programmazione efficiente
 Non rimuovere il codice di filtro che cerca il nome di dominio **example.com**. Se si rimuove il filtro, la soluzione invierà messaggi di posta elettronica a tutti i contatti.

## <a name="see-also"></a>Vedere anche
- [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)
- [Procedura: Creare un elemento di posta elettronica a livello di codice](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Procedura: Accedere ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Procedura: Eseguire azioni a livello di codice quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
