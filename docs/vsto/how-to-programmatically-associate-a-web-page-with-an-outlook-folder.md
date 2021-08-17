---
title: Associare una pagina Web a una Outlook cartella
description: Informazioni su come associare una pagina Web a Microsoft Office Outlook cartella. In questo esempio viene verificata la presenza di una cartella denominata HtmlView in Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- folders [Office development in Visual Studio], Web pages and
- Outlook [Office development in Visual Studio], Web pages attached to folders
- Web pages [Office development in Visual Studio], Outlook folders
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6fce0a1a6fbe4537e87d88120550bd7a1f7788c07ab84a02f70cb9514c3fac7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394587"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Associare una pagina Web a una Outlook cartella

  In questo esempio viene verificata la presenza di una cartella `HtmlView` denominata in Microsoft Office Outlook. Se la cartella non esiste, il codice crea la cartella e vi assegna una pagina Web. Se la cartella esiste, il codice visualizza il contenuto della cartella.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Vedere anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Procedura: Recuperare una cartella in base al nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: Creare elementi di cartelle personalizzati a livello di codice](../vsto/how-to-programmatically-create-custom-folder-items.md)
