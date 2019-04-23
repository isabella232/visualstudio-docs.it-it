---
title: 'Procedura: Nascondere il testo nei documenti a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 1da471ff1911cdda4a62ef9c150236b3a225342f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110167"
---
# <a name="how-to-programmatically-hide-text-in-documents"></a>Procedura: Nascondere il testo nei documenti a livello di codice
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
 Questo esempio di codice presuppone che il documento contiene un <xref:Microsoft.Office.Tools.Word.Bookmark> controllo (in una personalizzazione a livello di documento) o <xref:Microsoft.Office.Interop.Word.Bookmark> controllo (in un componente aggiuntivo VSTO) denominato `bookmark1`.

## <a name="see-also"></a>Vedere anche
- [Procedura: A livello di codice stampa documenti](../vsto/how-to-programmatically-print-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: A livello di programmazione reimpostare gli intervalli nei documenti di Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: A livello di codice aggiorna il testo di segnalibro](../vsto/how-to-programmatically-update-bookmark-text.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
