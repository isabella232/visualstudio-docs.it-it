---
title: 'Procedura: eseguire la ricerca a livello di codice all''interno di una cartella specifica | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Outlook folders [Office development in Visual Studio], searching
ms.assetid: 8f2cdc8b-f757-412c-aa2b-ebd5bc52f697
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6397f6e90423640697aa57d7fdf2a1c85303d0f9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procedura: eseguire la ricerca in una cartella specifica a livello di codice
  Nell'esempio viene utilizzata la `Find` e `FindNext` metodi per cercare testo nel campo soggetto di messaggi di posta elettronica presenti il **posta in arrivo**. Questo metodo utilizza un filtro di stringa per verificare la lettera T come lettera iniziale del `Subject` testo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo delle cartelle](../vsto/working-with-folders.md)   
 [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Procedura: Recuperare una cartella per nome a livello di codice](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  