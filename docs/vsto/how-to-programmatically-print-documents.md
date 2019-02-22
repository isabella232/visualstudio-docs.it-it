---
title: 'Procedura: A livello di codice stampa documenti'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 252891f603f974b43fa9a609bd9bbde9dde2f7f3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56654074"
---
# <a name="how-to-programmatically-print-documents"></a>Procedura: A livello di codice stampa documenti
  È possibile stampare un intero documento di Microsoft Office Word o parte di un documento sulla stampante predefinita.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="print-a-document-that-is-part-of-a-document-level-customization"></a>Stampare un documento che fa parte di una personalizzazione a livello di documento

### <a name="to-print-the-entire-document"></a>Per stampare l'intero documento

1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> della classe `ThisDocument` nel progetto per stampare l'intero documento. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` .

     [!code-vb[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#11)]

### <a name="to-print-the-current-page-of-the-document"></a>Per stampare la pagina corrente del documento

1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintOut%2A> della classe `ThisDocument` nel progetto e specificare che una copia della pagina corrente deve essere stampata. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` .

     [!code-vb[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomation#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#12)]

## <a name="print-a-document-by-using-a-vsto-add-in"></a>Stampare un documento usando un componente aggiuntivo VSTO

### <a name="to-print-an-entire-document"></a>Per stampare un intero documento

1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> da stampare. L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#11)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#11](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#11)]

### <a name="to-print-the-current-page-of-a-document"></a>Per stampare la pagina corrente di un documento

1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintOut%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole stampare e specificare che una copia della pagina corrente deve essere stampata. L'esempio di codice seguente stampa il documento attivo. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#12)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#12](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#12)]

## <a name="see-also"></a>Vedere anche
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
