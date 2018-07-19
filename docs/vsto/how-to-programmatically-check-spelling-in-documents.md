---
title: 'Procedura: a livello di codice il controllo ortografico nei documenti'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], checking spelling
- spelling checker, documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e916b16caaaa3944fcdf522ffd320198d9972b52
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35256718"
---
# <a name="how-to-programmatically-check-spelling-in-documents"></a>Procedura: a livello di codice il controllo ortografico nei documenti
  Per controllare l'ortografia in un documento, usare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> (metodo). Questo metodo restituisce un valore booleano che indica se il parametro fornito sia stato digitato correttamente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-check-spelling-and-display-results-in-a-message-box"></a>Per controllare l'ortografia e visualizzazione dei risultati in una finestra di messaggio  
  
1.  Chiamare il <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> (metodo) e passarlo a un intervallo di testo per cercare gli errori di ortografia. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#113)]
     [!code-csharp[Trin_VstcoreWordAutomation#113](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#113)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  