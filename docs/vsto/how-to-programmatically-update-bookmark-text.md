---
title: 'Procedura: aggiornare il testo del segnalibro a livello di codice'
description: Informazioni su come usare Visual Studio per inserire il testo a livello di codice in un segnalibro segnaposto in un documento di Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- bookmarks, updating text
- text [Office development in Visual Studio], updating in bookmarks
- Bookmark control, updating contents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cf38843d2ce7f617d44793769e6ca236c2683805
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934728"
---
# <a name="how-to-programmatically-update-bookmark-text"></a>Procedura: aggiornare il testo del segnalibro a livello di codice
  È possibile inserire testo in un segnalibro in un documento di Microsoft Office Word in modo da poter recuperare il testo in seguito o sostituire il testo in un segnalibro. Se si sviluppa una personalizzazione a livello di documento, è anche possibile aggiornare il testo in un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> associato a dati. Per altre informazioni, vedere [associare i dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L'oggetto segnalibro può essere di due tipi diversi:

- Controllo host <xref:Microsoft.Office.Tools.Word.Bookmark>.

   I controlli <xref:Microsoft.Office.Tools.Word.Bookmark> estendono gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> nativi permettendo il data binding e l'esposizione di eventi. Per ulteriori informazioni sui controlli host, vedere [Cenni preliminari sugli elementi host e sui controlli host](../vsto/host-items-and-host-controls-overview.md).

- Oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo.

   Gli oggetti <xref:Microsoft.Office.Interop.Word.Bookmark> non includono eventi né hanno funzionalità di data binding.

  Quando si assegna testo a un segnalibro, il comportamento tra un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> è diverso. Per altre informazioni, vedere [Bookmark Control](../vsto/bookmark-control.md).

## <a name="use-host-controls"></a>Usare i controlli host

### <a name="to-update-bookmark-contents-using-a-bookmark-control"></a>Per aggiornare il contenuto dei segnalibri mediante un controllo Bookmark

1. Creare una routine che accetti un argomento `bookmark` per il nome del segnalibro e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A>.

    > [!NOTE]
    > Se si assegna testo alla proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> o <xref:Microsoft.Office.Tools.Word.Bookmark.FormattedText%2A> di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark>, il segnalibro non viene eliminato.

     [!code-vb[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#63)]
     [!code-csharp[Trin_VstcoreWordAutomation#63](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#63)]

2. Assegnare la stringa *newText* alla <xref:Microsoft.Office.Tools.Word.Bookmark.Text%2A> proprietà di <xref:Microsoft.Office.Tools.Word.Bookmark> .

     [!code-vb[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#64)]
     [!code-csharp[Trin_VstcoreWordAutomation#64](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#64)]

## <a name="use-word-objects"></a>Usare oggetti di Word

### <a name="to-update-bookmark-contents-using-a-word-bookmark-object"></a>Per aggiornare il contenuto dei segnalibri mediante un oggetto Bookmark di Word

1. Creare una routine che includa un argomento `bookmark` per il nome dell'oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> e un argomento `newText` per la stringa da assegnare alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> del segnalibro.

    > [!NOTE]
    > Se si assegna testo a un oggetto <xref:Microsoft.Office.Interop.Word.Bookmark> nativo di Word, il segnalibro viene eliminato.

     [!code-vb[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#65)]
     [!code-csharp[Trin_VstcoreWordAutomation#65](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#65)]

2. Assegnare la stringa *newText* alla <xref:Microsoft.Office.Interop.Word.Range.Text%2A> proprietà del segnalibro, che elimina automaticamente il segnalibro. Riaggiungere quindi il segnalibro alla raccolta <xref:Microsoft.Office.Interop.Word.Bookmarks>.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     [!code-vb[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomation#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#66)]

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#66)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#66](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#66)]

## <a name="see-also"></a>Vedi anche
- [Procedura: inserire testo in documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Segnalibro (controllo)](../vsto/bookmark-control.md)
