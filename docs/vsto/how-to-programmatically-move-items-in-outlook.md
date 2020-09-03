---
title: 'Procedura: spostare elementi in Outlook a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], moving items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 97f686a47d18fa91909de489f12f9c7a8c1306d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85519912"
---
# <a name="how-to-programmatically-move-items-in-outlook"></a>Procedura: spostare elementi in Outlook a livello di codice
  Questo esempio Mostra come spostare i messaggi di posta elettronica non letti dalla **posta in arrivo** a una cartella denominata **test**. Nell'esempio vengono spostati solo i messaggi con la parola **test** nel `Subject` campo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_MoveItems#1](../vsto/codesnippet/CSharp/Trin_OL_MoveItems/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Cartella di posta di Outlook denominata **test**.

- Un messaggio di posta elettronica che arriva con la parola **test** nel `Subject` campo.

## <a name="see-also"></a>Vedere anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: eseguire una ricerca all'interno di una cartella specifica a livello di codice](../vsto/how-to-programmatically-search-within-a-specific-folder.md)
- [Procedura: eseguire azioni quando viene ricevuto un messaggio di posta elettronica a livello di codice](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)
