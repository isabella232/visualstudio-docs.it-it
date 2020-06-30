---
title: 'Procedura: nascondere il testo nei documenti a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], hiding text
- text [Office development in Visual Studio], hiding in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4dae19d196f830e5187fa395473c0a5482cb1d03
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543312"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Procedura: nascondere il testo nei documenti a livello di codice
  È possibile nascondere testo in un documento impostando la proprietà <xref:Microsoft.Office.Interop.Word._Font.Hidden%2A> di un controllo <xref:Microsoft.Office.Interop.Word.Range.Font%2A> per un intervallo di testo determinato.

 Ad esempio, è possibile nascondere temporaneamente il testo all'interno di un <xref:Microsoft.Office.Tools.Word.Bookmark> (in una personalizzazione a livello di documento) o un <xref:Microsoft.Office.Interop.Word.Bookmark> (in un componente aggiuntivo VSTO) prima di inviare un documento a una stampante.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-hide-text-in-a-bookmark-control-while-printing-the-document"></a>Per nascondere testo in un controllo Bookmark mentre si stampa il documento

1. Creare una routine che nasconda tutto il testo che rientra in un intervallo specificato.

     [!code-vb[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#105)]
     [!code-csharp[Trin_VstcoreWordAutomation#105](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#105)]

2. Creare una routine che scopra tutto il testo che rientra in un intervallo specificato.

     [!code-vb[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#106)]
     [!code-csharp[Trin_VstcoreWordAutomation#106](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#106)]

3. Passare l'intervallo di un segnalibro al metodo `HideText` , stampare il documento e quindi passare lo stesso intervallo al metodo `UnhideText` .

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento. Per usare questo esempio, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomation#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#107)]

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare l'esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#107)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#107](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#107)]

## <a name="compile-the-code"></a>Compilare il codice
 Questo esempio di codice presuppone che il documento contenga un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo (in una personalizzazione a livello di documento) o un <xref:Microsoft.Office.Interop.Word.Bookmark> controllo (in un componente aggiuntivo VSTO) denominato `bookmark1` .

## <a name="see-also"></a>Vedere anche
- [Procedura: stampare documenti a livello di codice](../vsto/how-to-programmatically-print-documents.md)
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: aggiornare il testo del segnalibro a livello di codice](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
