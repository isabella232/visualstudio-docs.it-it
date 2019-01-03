---
title: "Procedura: Eseguire la ricerca a livello di codice all'interno di una cartella specifica"
ms.date: 02/02/2017
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
ms.openlocfilehash: 1427f0ab69cab2c23a0eeb7638bbc6e21778c55a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915494"
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
