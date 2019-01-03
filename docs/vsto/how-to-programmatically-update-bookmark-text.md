---
title: 'Procedura: A livello di codice aggiorna il testo di segnalibro'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cdbecf7ea507fdf630ebd3cc4bf50092826292dc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864336"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Procedura: A livello di codice aggiorna il testo di segnalibro
  È possibile inserire testo in un segnalibro in un documento di Microsoft Office Word in modo da poter recuperare il testo in seguito o sostituire il testo in un segnalibro. Se si sviluppa una personalizzazione a livello di documento, è anche possibile aggiornare il testo in un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> associato a dati. Per altre informazioni, vedere [associare dati a controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'oggetto segnalibro può essere di due tipi diversi:  
  
- Controllo host <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
   I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> estendono gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> nativi permettendo il data binding e l'esposizione di eventi. Per altre informazioni sui controlli host, vedere [elementi Host e host Cenni preliminari sui controlli](../vsto/host-items-and-host-controls-overview.md).  
  
- Oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.  
  
   Gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> non includono eventi né hanno funzionalità di data binding.  
  
  Quando si assegna testo a un segnalibro, il comportamento tra un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> è diverso. Per altre informazioni, vedere [Bookmark (controllo)](../vsto/bookmark-control.md).  
  
## <a name="use-host-controls"></a>Utilizzare i controlli host  
  
### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Per aggiornare il contenuto dei segnalibri mediante un controllo Bookmark  
  
1.  Creare una routine che accetti un argomento `bookmark` per il nome del segnalibro e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.  
  
    > [!NOTE]  
    >  Se si assegna testo alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark>, il segnalibro non viene eliminato.  
  
     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]  
  
2.  Assegnare il *newText* da string al <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> proprietà del <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]  
  
## <a name="use-word-objects"></a>Usare oggetti di Word  
  
### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Per aggiornare il contenuto dei segnalibri mediante un oggetto Bookmark di Word  
  
1.  Creare una routine che includa un argomento `bookmark` per il nome dell'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del segnalibro.  
  
    > [!NOTE]  
    >  Se si assegna testo a un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo di Word, il segnalibro viene eliminato.  
  
     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]  
  
2.  Assegnare il *newText* da string al <xref:Microsoft.Office.Interop.Word.Range.Text%2A> proprietà del segnalibro, l'eliminazione automatica del segnalibro. Riaggiungere quindi il segnalibro alla raccolta <xref:Microsoft.Office.Interop.Word.Bookmarks>.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: A livello di programmazione inserire testo nei documenti di Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Bookmark (controllo)](../vsto/bookmark-control.md)  
