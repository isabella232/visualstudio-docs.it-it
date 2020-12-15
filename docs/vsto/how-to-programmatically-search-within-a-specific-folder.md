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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fa569a2c301cb495f109a612d817937159c257c6
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524548"
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
