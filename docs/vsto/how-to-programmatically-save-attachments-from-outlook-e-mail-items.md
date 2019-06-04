---
title: 'Procedura: A livello di codice salva gli allegati da elementi di posta elettronica di Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: d222924e753db1b476a5d7729e2c794a8ab305e2
ms.sourcegitcommit: c6249a8f3054db881ba62f4e80bf006d440f5a2d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66462113"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Procedura: A livello di codice salva gli allegati da elementi di posta elettronica di Outlook

In questo esempio gli allegati di posta elettronica vengono salvati in una cartella specificata quando si riceve posta nella posta in arrivo.

> [!IMPORTANT]
> Questo esempio funziona solo se si aggiunge una cartella denominata **TestFileSave** alla radice dell'unità C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio

[!code-csharp[Trin_OL_SaveAttachments#1](../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche

- [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)
- [Procedura: Recuperano una cartella in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: A livello di programmazione eseguire azioni quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Procedura: Eseguire la ricerca a livello di codice all'interno di una cartella specifica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
