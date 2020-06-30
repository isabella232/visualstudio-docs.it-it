---
title: 'Procedura: visualizzare i commenti del foglio di codice a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0fc84e2726cd7a70b8fc59b0f1ac2b3377f9c4af
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543364"
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Procedura: visualizzare i commenti del foglio di codice a livello di codice
  A livello di codice è possibile visualizzare e nascondere i commenti nei fogli di lavoro di Microsoft Office Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Per visualizzare tutti i commenti in un foglio di lavoro in una personalizzazione a livello di documento

1. Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .

     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]

## <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Per visualizzare tutti i commenti in un foglio di lavoro in un componente aggiuntivo VSTO a livello di applicazione

1. Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]

## <a name="see-also"></a>Vedere anche
- [Usare i fogli di lavoro](../vsto/working-with-worksheets.md)
- [Procedura: aggiungere ed eliminare commenti in un foglio di codice a livello di codice](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)
- [Cenni preliminari sugli elementi e sui controlli host](../vsto/host-items-and-host-controls-overview.md)
