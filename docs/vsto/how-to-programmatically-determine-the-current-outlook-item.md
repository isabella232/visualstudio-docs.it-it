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
ms.openlocfilehash: 3608f516eb9206bc5b4c232c227d3e49c2414be7
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599753"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Procedura: Determinare a livello di codice elemento Outlook corrente
  Questo esempio viene usato il `Explorer.SelectionChange` evento per visualizzare il nome della cartella corrente e alcune informazioni sull'elemento selezionato. Il codice consente di visualizzare l'elemento selezionato.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

-   Appuntamento, contatto e gli elementi di posta elettronica in Microsoft Office Outlook.

## <a name="see-also"></a>Vedere anche
- [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)
- [Procedura: Recuperano una cartella in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: Eseguire la ricerca a livello di codice di un contatto specifico](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
