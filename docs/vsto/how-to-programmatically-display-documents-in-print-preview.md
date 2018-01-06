---
title: 'Procedura: visualizzare i documenti a livello di codice in anteprima di stampa | Documenti Microsoft'
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
helpviewer_keywords:
- Word [Office development in Visual Studio], displaying documents in print preview
- documents [Office development in Visual Studio], displaying in print preview
ms.assetid: 96c7faea-9c5c-42b4-a009-08894a6d15c9
caps.latest.revision: "39"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 762a068858e7ad79c9a4fe9d02d1d868f150c5a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-display-documents-in-print-preview"></a>Procedura: Visualizzare documenti in un'anteprima di stampa a livello di codice
  Se la soluzione genera un report, è possibile che si voglia far visualizzare il report all'utente in modalità Anteprima di stampa.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="procedures-for-document-level-customizations"></a>Procedure per le personalizzazioni a livello di documento  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.PrintPreview%2A> della classe <xref:Microsoft.Office.Tools.Word.Document> . Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomation#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="procedures-for-vsto-add-ins"></a>Procedure per i componenti aggiuntivi VSTO  
  
#### <a name="to-display-a-document-in-print-preview-by-calling-the-printpreview-method"></a>Per visualizzare un documento in Anteprima di stampa chiamando il metodo PrintPreview  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si vuole visualizzare in anteprima. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#13)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#13](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#13)]  
  
#### <a name="to-display-a-document-in-print-preview-by-setting-the-printpreview-property"></a>Per visualizzare un documento in Anteprima di stampa impostando la proprietà PrintPreview  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Word._Application.PrintPreview%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application> su **true**.  
  
     [!code-vb[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#14)]
     [!code-csharp[Trin_VstcoreWordAutomation#14](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#14)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: stampa di documenti](../vsto/how-to-programmatically-print-documents.md)   
 [Procedura: aprire documenti esistenti](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Procedura: Creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)  
  
  