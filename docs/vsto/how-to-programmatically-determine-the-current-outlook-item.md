---
title: 'Procedura: Determinare a livello di codice elemento Outlook corrente'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 5566538b428502c8e63e752463b0271daeac2918
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052506"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Procedura: Determinare a livello di codice elemento Outlook corrente
  Questo esempio viene usato il `Explorer.SelectionChange` evento per visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato. Il codice consente di visualizzare l'elemento selezionato.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Appuntamento, contatto e gli elementi di posta elettronica in Microsoft Office Outlook.

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)
- [Procedura: Recuperano una cartella in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: Eseguire la ricerca a livello di codice di un contatto specifico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
