---
title: "Procedura: eseguire una ricerca all'interno di una cartella specifica a livello di codice"
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
ms.openlocfilehash: a9c7861698e678ca6d8332e3940c3ae49ff423f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877876"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procedura: eseguire una ricerca all'interno di una cartella specifica a livello di codice
  Questo esempio di codice usa `Find` i `FindNext` metodi e per cercare il testo nel campo oggetto dei messaggi di posta elettronica presenti nella **posta in arrivo**. Questo metodo utilizza un filtro di stringa per verificare la lettera T come lettera iniziale del `Subject` testo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]

## <a name="see-also"></a>Vedere anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Panoramica del modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)
- [Procedura: recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
