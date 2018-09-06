---
title: "Procedura: eseguire la ricerca a livello di codice all'interno di una cartella specifica"
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook folders [Office development in Visual Studio], searching
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 64df4180e533f254927ae134ed005b0626dfdde8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35672911"
---
# <a name="how-to-programmatically-search-within-a-specific-folder"></a>Procedura: eseguire la ricerca a livello di codice all'interno di una cartella specifica
  Questo esempio di codice Usa il `Find` e `FindNext` metodi per eseguire la ricerca di testo nel campo oggetto dei messaggi di posta elettronica nel **posta in arrivo**. Questo metodo Usa un filtro di stringa da verificare per la lettera T come lettera iniziale del `Subject` testo.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>Esempio  
 [!code-csharp[Trin_OL_SearchFolder#1](../vsto/codesnippet/CSharp/Trin_OL_SearchFolder/thisaddin.cs#1)]  
  
## <a name="see-also"></a>Vedere anche  
 [Con le cartelle di lavoro](../vsto/working-with-folders.md)   
 [Cenni preliminari sul modello a oggetti di Outlook](../vsto/outlook-object-model-overview.md)   
 [Procedura: recuperare una cartella a livello programmatico in base al nome](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)  
  
  