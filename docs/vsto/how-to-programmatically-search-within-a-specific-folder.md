---
title: "Procedura: Eseguire ricerche a livello di codice all'interno di una cartella specifica"
description: Informazioni su come usare Visual Studio per eseguire ricerche a livello di codice all'interno di una cartella specifica di Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b25880420e23b82f6f63ab28ef5f1f93429bdd8c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824757"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procedura: Eseguire ricerche a livello di codice all'interno di una cartella specifica
  In questo esempio di codice vengono utilizzati i metodi e per cercare testo nel campo dell'oggetto dei messaggi di posta elettronica `Find` presenti nella cartella Posta in `FindNext` **arrivo**. Questo metodo usa un filtro di stringa per verificare la presenza della lettera T come lettera iniziale del `Subject` testo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Vedere anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)
- [Procedura: Recuperare una cartella in base al nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
