---
title: Salvare allegati da elementi Outlook posta elettronica a livello di codice
description: Informazioni su come usare i Visual Studio per salvare allegati da elementi di posta elettronica di Microsoft Outlook a livello di codice.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e635d1ddba2d7032820fee6e5979b402b2d38360
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710059"
---
# <a name="how-to-programmatically-save-attachments-from-outlook-email-items"></a>Procedura: Salvare allegati da elementi di posta elettronica Outlook a livello di codice

In questo esempio gli allegati di posta elettronica vengono salvati in una cartella specificata quando si riceve posta nella posta in arrivo.

> [!IMPORTANT]
> Questo esempio funziona solo se si aggiunge una cartella denominata **TestFileSave** nella radice della directory C.

[!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio

:::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SaveAttachments/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Vedere anche

- [Usare gli elementi di posta elettronica](../vsto/working-with-mail-items.md)
- [Procedura: Recuperare una cartella in base al nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: Eseguire azioni a livello di codice quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
- [Procedura: Eseguire ricerche a livello di codice all'interno di una cartella specifica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
