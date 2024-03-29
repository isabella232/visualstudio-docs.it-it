---
title: "Procedura: determinare a livello di codice l'elemento Outlook corrente"
description: Informazioni su come determinare a livello di codice l'elemento microsoft Outlook corrente. In questo esempio viene utilizzato l'evento Explorer.SelectionChange.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 9d2f6ba1230ce306f742468d96c47dfdcf17b8d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122083233"
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>Procedura: determinare a livello di codice l'elemento Outlook corrente
  In questo esempio viene utilizzato l'evento per visualizzare il `Explorer.SelectionChange` nome della cartella corrente e alcune informazioni sull'elemento selezionato. Il codice visualizza quindi l'elemento selezionato.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs" id="Snippet1":::

## <a name="compile-the-code"></a>Compilare il codice
 L'esempio presenta i requisiti seguenti:

- Appuntamenti, contatti ed elementi di posta elettronica in Microsoft Office Outlook.

## <a name="see-also"></a>Vedi anche
- [Outlook panoramica del modello a oggetti](../vsto/outlook-object-model-overview.md)
- [Procedura: Recuperare una cartella in base al nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
- [Procedura: Cercare un contatto specifico a livello di codice](../vsto/how-to-programmatically-search-for-a-specific-contact.md)
