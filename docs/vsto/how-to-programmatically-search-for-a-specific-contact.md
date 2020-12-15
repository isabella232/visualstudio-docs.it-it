---
title: 'Procedura: eseguire la ricerca di un contatto specifico a livello di codice'
description: Informazioni su come usare Visual Studio per cercare un contatto specifico a livello di codice in Microsoft Outlook.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6813a137558a245c66d4b24deac07b1a6a77796a
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524611"
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>Procedura: eseguire la ricerca di un contatto specifico a livello di codice
  Questo esempio cerca una cartella Contatti di Outlook per un contatto specifico in base al nome e al cognome. L'esempio presuppone che un contatto denominato **John Evans** esista nella cartella Contatti.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]

## <a name="see-also"></a>Vedere anche
- [Usare gli elementi di contatto](../vsto/working-with-contact-items.md)
- [Introduzione alla programmazione di componenti aggiuntivi VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
