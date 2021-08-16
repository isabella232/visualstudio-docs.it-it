---
title: "Procedura: Eseguire ricerche a livello di codice all'interno di una cartella specifica"
description: Informazioni su come usare i Visual Studio per eseguire ricerche a livello di codice all'interno di una cartella Outlook Microsoft specifica.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: dd14e88b64eff4c4273282bcc743b3acbb2ca6fa51ffff90b93db1bd8ffd0416
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394251"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procedura: Eseguire ricerche a livello di codice all'interno di una cartella specifica
  In questo esempio di codice vengono utilizzati i metodi e per cercare testo nel campo oggetto dei messaggi di posta `Find` elettronica presenti nella posta in `FindNext` **arrivo.** Questo metodo usa un filtro di stringa per cercare la lettera T come lettera iniziale del `Subject` testo.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="example"></a>Esempio
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs" id="Snippet1":::

## <a name="see-also"></a>Vedere anche
- [Usare le cartelle](../vsto/working-with-folders.md)
- [Outlook panoramica del modello a oggetti](../vsto/outlook-object-model-overview.md)
- [Procedura: Recuperare una cartella in base al nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)
