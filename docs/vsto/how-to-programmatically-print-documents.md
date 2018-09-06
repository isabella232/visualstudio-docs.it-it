---
title: 'Procedura: stampare i documenti a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], printing documents
- documents [Office development in Visual Studio], printing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6c1e34e723618d24870d76dd961e7f4c484bc6fd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671878"
---
# <a name="how-to-programmatically-print-documents"></a>Procedura: stampare i documenti a livello di codice
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
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  