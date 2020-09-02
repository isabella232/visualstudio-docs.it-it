---
title: "Procedura: determinare l'elemento corrente di Outlook a livello di codice"
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 94d7e16b011b153a43e3d1666451a90b0e44c8b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547160"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Procedura: determinare l'elemento corrente di Outlook a livello di codice
  In questo esempio viene usato l' `Explorer.SelectionChange` evento per visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato. Il codice Visualizza quindi l'elemento selezionato.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Gli elementi di appuntamento, di contatto e di posta elettronica in Microsoft Office Outlook.

## <a name="see-also"></a>Vedere anche
- [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)
- [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: eseguire la ricerca di un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
