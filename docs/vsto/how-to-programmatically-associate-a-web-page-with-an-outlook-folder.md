---
title: Associare una pagina Web a una cartella di Outlook
description: Informazioni su come associare una pagina Web a Microsoft Office cartella di Outlook. In questo esempio viene verificata la presenza di una cartella denominata HtmlView in Outlook.
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
ms.workload:
- office
ms.openlocfilehash: 35fad43f78d654cfaf9e06c1f432c620da830dd4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885573"
---
# <a name="associate-a-web-page-with-an-outlook-folder"></a>Associare una pagina Web a una cartella di Outlook

  In questo esempio viene verificata la presenza di una cartella denominata `HtmlView` in Microsoft Office Outlook. Se la cartella non esiste, il codice crea la cartella e vi assegna una pagina Web. Se la cartella esiste, il codice Visualizza il contenuto della cartella.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_HTMLFolder#1](../vsto/codesnippet/CSharp/Trin_OL_HTMLFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: creare elementi di cartelle personalizzate a livello di codice](../vsto/how-to-programmatically-create-custom-folder-items.md)
