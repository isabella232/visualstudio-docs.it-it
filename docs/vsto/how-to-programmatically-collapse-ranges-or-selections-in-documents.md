---
title: Comprimi intervalli o selezioni nei documenti a livello di codice
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- selections, collapsing
- documents [Office development in Visual Studio], collapsing ranges
- collapsing selections
- ranges, collapsing
- collapsing ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1575a130a525c169553598fd15acfa8ba8fc397a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546120"
---
# <a name="how-to-programmatically-collapse-ranges-or-selections-in-documents"></a>Procedura: comprimere intervalli o selezioni in documenti a livello di codice
  Se si usa un oggetto <xref:Microsoft.Office.Interop.Word.Range> o <xref:Microsoft.Office.Interop.Word.Selection> , è possibile che si voglia modificare la selezione in un punto di inserimento prima di inserire il testo, per evitare la sovrascrittura del testo esistente. Entrambi gli <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Interop.Word.Selection> oggetti e hanno un metodo Collapse, che usa i valori di <xref:Microsoft.Office.Interop.Word.WdCollapseDirection> enumerazione:

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> comprime la selezione nella parte iniziale. Rappresenta il valore predefinito se non viene specificato un valore di enumerazione.

- <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> comprime la selezione nella parte finale.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-collapse-a-range-and-insert-new-text"></a>Per comprimere un intervallo e inserire nuovo testo

1. Creare un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dal primo paragrafo del documento.

    L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

    [!code-vb[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomation#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#46)]

    L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#46)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#46](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#46)]

2. Usare il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseStart> per comprimere l'intervallo.

    [!code-vb[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#47)]
    [!code-csharp[Trin_VstcoreWordAutomation#47](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#47)]

3. Inserire il nuovo testo.

    [!code-vb[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#48)]
    [!code-csharp[Trin_VstcoreWordAutomation#48](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#48)]

4. Selezionare <xref:Microsoft.Office.Interop.Word.Range>.

    [!code-vb[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#49)]
    [!code-csharp[Trin_VstcoreWordAutomation#49](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#49)]

   Se si usa il valore di enumerazione <xref:Microsoft.Office.Interop.Word.WdCollapseDirection.wdCollapseEnd> , il testo viene inserito all'inizio del paragrafo seguente.

   [!code-vb[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#50)]
   [!code-csharp[Trin_VstcoreWordAutomation#50](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#50)]

   Contrariamente a quanto potrebbe prevedersi, la nuova frase non viene inserita prima del marcatore di paragrafo perché è incluso nell'intervallo originale. Per altre informazioni, vedere [procedura: escludere i segni di paragrafo a livello di codice durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md).

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="to-collapse-a-range-in-a-document-level-customization"></a>Per comprimere un intervallo in una personalizzazione a livello di documento

1. L'esempio seguente illustra il metodo completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomation#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#45)]

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="to-collapse-a-range-in-a-vsto-add-in"></a>Per comprimere un intervallo in un componente aggiuntivo VSTO

1. Nell'esempio seguente viene illustrato il metodo completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#45)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#45](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#45)]

## <a name="see-also"></a>Vedere anche
- [Procedura: inserire testo in documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: escludere i segni di paragrafo a livello di codice durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Procedura: estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
