---
title: 'Procedura: A livello di programmazione ripristinare le selezioni dopo le ricerche'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- searches, restoring selection after
- documents [Office development in Visual Studio], restoring selections
- selections, restoring after a search
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ae27f4e24ac367741bcdf2dfa2bae8598c6c7d99
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53865609"
---
# <a name="how-to-programmatically-restore-selections-after-searches"></a>Procedura: A livello di programmazione ripristinare le selezioni dopo le ricerche
  Se si trova e Sostituisci testo in un documento, è possibile ripristinare la selezione dell'utente originale dopo la ricerca è stata completata.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Il codice della procedura di esempio usa due <xref:Microsoft.Office.Interop.Word.Range> oggetti. Uno archivi corrente <xref:Microsoft.Office.Interop.Word.Selection>, e uno di essi imposta l'intero documento da usare come intervallo di ricerca.  
  
## <a name="to-restore-the-users-original-selection-after-a-search"></a>Per ripristinare la selezione dell'utente originale dopo una ricerca  
  
1. Creare il <xref:Microsoft.Office.Interop.Word.Range> oggetti per il documento e la selezione corrente.  
  
    [!code-vb[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#83)]
    [!code-csharp[Trin_VstcoreWordAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#83)]  
  
2. Eseguire la ricerca e sostituzione.  
  
    [!code-vb[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#84)]
    [!code-csharp[Trin_VstcoreWordAutomation#84](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#84)]  
  
3. Selezionare l'intervallo di inizio per ripristinare la selezione dell'utente originale.  
  
    [!code-vb[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#85)]
    [!code-csharp[Trin_VstcoreWordAutomation#85](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#85)]  
  
   L'esempio seguente mostra il metodo completo.  
  
## <a name="example"></a>Esempio  
 [!code-vb[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#82)]
 [!code-csharp[Trin_VstcoreWordAutomation#82](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#82)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Procedura: A livello di codice impostare le opzioni di ricerca in Word](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Procedura: Ciclo a livello di programmazione tramite gli elementi trovati nei documenti](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
