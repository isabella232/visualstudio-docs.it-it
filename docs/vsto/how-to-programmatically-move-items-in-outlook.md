---
title: 'Procedura: Spostare elementi in Outlook a livello di codice'
description: Informazioni su come spostare elementi in Microsoft Outlook a livello di codice. Questo esempio sposta i messaggi di posta elettronica non letti dalla posta in arrivo in una cartella denominata Test.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b8e951ab393d09506ad4f2d593962ea1826eff09
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826733"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Procedura: Spostare elementi in Outlook a livello di codice
  Questo esempio sposta i messaggi di posta elettronica non letti **dalla** posta in arrivo in una cartella denominata **Test**. L'esempio sposta solo i messaggi con la **parola Test** nel `Subject` campo .

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Una cartella di posta di Outlook denominata **Test**.

- Messaggio di posta elettronica che arriva con la **parola Test** nel `Subject` campo .

## <a name="see-also"></a>Vedi anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Procedura: Recuperare una cartella in base al nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: Eseguire ricerche a livello di codice all'interno di una cartella specifica](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Procedura: Eseguire azioni a livello di codice quando viene ricevuto un messaggio di posta elettronica](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
