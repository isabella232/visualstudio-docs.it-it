---
title: 'Procedura: A livello di programmazione visualizzare commenti in un foglio di lavoro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c246eae0465c64598aae1191c4053f8ba266b6ff
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831563"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Procedura: A livello di programmazione visualizzare commenti in un foglio di lavoro
  A livello di codice è possibile visualizzare e nascondere i commenti nei fogli di lavoro di Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Per visualizzare tutti i commenti in un foglio di lavoro in una personalizzazione a livello di documento  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Per visualizzare tutti i commenti in un foglio di lavoro in un componente aggiuntivo VSTO a livello di applicazione  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>Vedere anche  
 [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: Aggiungere ed eliminare commenti in foglio di lavoro a livello di codice](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)  
