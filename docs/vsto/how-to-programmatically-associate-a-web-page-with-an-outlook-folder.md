---
title: 'Procedura: A livello di programmazione associare una pagina web a una cartella di Outlook'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e83f8b7f6bcdb790b5e545aa76426bc05f0735f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817309"
---
# <a name="how-to-programmatically-associate-a-web-page-with-an-outlook-folder"></a>Procedura: A livello di programmazione associare una pagina web a una cartella di Outlook
  Questo esempio viene verificata una cartella denominata `HtmlView` in Microsoft Office Outlook. Se la cartella non esiste, il codice crea la cartella e la assegna a una pagina Web a. Se la cartella esiste, il codice visualizza il contenuto della cartella.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche
- [Con le cartelle di lavoro](../vsto/working-with-folders.md)
- [Procedura: Recuperano una cartella in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: A livello di programmazione creare cartelle personalizzate](../vsto/how-to-programmatically-create-custom-folder-items.md)
