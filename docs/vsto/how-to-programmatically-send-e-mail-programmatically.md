---
title: 'Procedura: inviare messaggi di posta elettronica a livello di codice'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c56527f18857ad3c4ac82060ffd5794b72ac017c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543260"
---
# <a name="how-to-programmatically-send-email"></a>Procedura: inviare messaggi di posta elettronica a livello di codice
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
- [Procedura: creare un elemento di posta elettronica a livello di codice](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Procedura: accedere ai contatti di Outlook a livello di codice](../vsto/how-to-programmatically-access-outlook-contacts.md)
- [Procedura: eseguire azioni quando viene ricevuto un messaggio di posta elettronica a livello di codice](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
