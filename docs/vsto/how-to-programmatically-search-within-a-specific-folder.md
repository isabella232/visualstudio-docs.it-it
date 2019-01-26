---
title: "Procedura: Eseguire la ricerca a livello di codice all'interno di una cartella specifica"
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: d9a08451b186cdc3ca1526441e906cf3c9e5d4c9
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866844"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procedura: Eseguire la ricerca a livello di codice all'interno di una cartella specifica
  Questo esempio di codice Usa il `Find` e `FindNext` metodi per eseguire la ricerca di testo nel campo oggetto dei messaggi di posta elettronica nel **posta in arrivo**. Questo metodo Usa un filtro di stringa da verificare per la lettera T come lettera iniziale del `Subject` testo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Con le cartelle di lavoro](../vsto/working-with-folders.md)   
 [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Procedura: Recuperano una cartella in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
