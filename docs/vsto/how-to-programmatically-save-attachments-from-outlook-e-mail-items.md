---
title: Salva gli allegati da elementi di posta elettronica di Outlook a livello di codice
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], attachments
- e-mail [Office development in Visual Studio], attachments
- saving e-mail attachments
- mail items [Office development in Visual Studio], attachments
- attachments [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9fbe6099a8928397a7d885ac72c4f34da2da6af0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545886"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Procedura: salvare allegati da elementi di posta elettronica di Outlook a livello di codice

In questo esempio gli allegati di posta elettronica vengono salvati in una cartella specificata quando si riceve posta nella posta in arrivo.

> [!IMPORTANT]
> Questo esempio funziona solo se si aggiunge una cartella denominata **TestFileSave** alla radice della directory C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche

- [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)
- [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: eseguire azioni quando viene ricevuto un messaggio di posta elettronica a livello di codice](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Procedura: eseguire una ricerca all'interno di una cartella specifica a livello di codice](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
