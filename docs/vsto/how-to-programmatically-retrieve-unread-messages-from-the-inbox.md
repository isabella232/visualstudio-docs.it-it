---
title: Ottenere i messaggi non letti dalla posta in arrivo a livello di codice
description: Informazioni su come usare Visual Studio per recuperare a livello di codice i messaggi non letti dalla posta in arrivo in Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- e-mail [Office development in Visual Studio], unread mail
- Outlook [Office development in Visual Studio], unread mail
- unread e-mail
- mail items [Office development in Visual Studio], unread mail
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b6dae629c008c04f7ee9fb66b9dbc5f8f31e53d4
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528265"
---
# <a name="how-to-programmatically-retrieve-unread-messages-from-the-inbox"></a>Procedura: recuperare messaggi non letti dalla posta in arrivo a livello di codice
  Questo esempio recupera i messaggi di posta elettronica non letti dalla **posta in arrivo** di Outlook e visualizza il numero di elementi.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-vb[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_RL_UnreadItems/thisaddin.vb#1)]
 [!code-csharp[Trin_Outlook_RL_UnreadItems#1](../vsto/codesnippet/CSharp/Trin_Outlook_RL_UnreadItems/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche
- [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Procedura: creare un elemento di posta elettronica a livello di codice](../vsto/how-to-programmatically-create-an-e-mail-item.md)
- [Procedura: inviare messaggi di posta elettronica a livello di codice](../vsto/how-to-programmatically-send-e-mail-programmatically.md)
- [Procedura: eseguire azioni quando viene ricevuto un messaggio di posta elettronica a livello di codice](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
