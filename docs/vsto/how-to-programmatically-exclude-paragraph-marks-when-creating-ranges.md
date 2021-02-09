---
title: Escludere i segni di paragrafo quando si creano intervalli a livello di codice
description: Informazioni su come è possibile escludere i segni di paragrafo a livello di codice durante la creazione di intervalli in un documento di Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], excluding paragraphs
- ranges, excluding paragraph marks in Word
- documents [Office development in Visual Studio], paragraph marks
- paragraphs, controlling structure
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 898eae77928908dfc077ddf80d2659328ec6475d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885482"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Procedura: escludere i segni di paragrafo a livello di codice durante la creazione di intervalli
  Ogni volta che si crea un oggetto <xref:Microsoft.Office.Interop.Word.Range> basato su un paragrafo, tutti i caratteri non stampabili, ad esempio i segni di paragrafo, vengono inclusi nell'intervallo. Può essere necessario inserire testo da un paragrafo di origine in un paragrafo di destinazione. Se non si vuole suddividere il paragrafo di destinazione i paragrafi distinti, è necessario prima rimuovere i segni di paragrafo dal paragrafo di origine. Dal momento che all'interno del segno di paragrafo sono memorizzate le informazioni sulla formattazione dei paragrafi, può anche essere necessario escludere tali informazioni durante l'inserimento dell'intervallo in un paragrafo esistente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 La procedura di esempio riportata di seguito dichiara due variabili stringa, recupera il contenuto del primo e del secondo paragrafo nel documento attivo e ne scambia i contenuti. L'esempio quindi illustra come rimuovere il marcatore di paragrafo dall'intervallo usando il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> e inserendo testo all'interno del paragrafo.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Per controllare la struttura dei paragrafi durante l'inserimento di testo

1. Creare due variabili intervallo per il primo e il secondo paragrafo e recuperarne il contenuto usando la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     [!code-vb[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomation#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#27)]

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO a livello di applicazione. Questo codice usa il documento attivo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#27)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#27)]

2. Assegnare la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , scambiando il testo tra i due paragrafi.

     [!code-vb[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#28)]
     [!code-csharp[Trin_VstcoreWordAutomation#28](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#28)]

3. Selezionare uno per volta tutti gli intervalli e sospendere l'esecuzione del codice per visualizzare i risultati in una finestra di messaggio.

     [!code-vb[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#29)]
     [!code-csharp[Trin_VstcoreWordAutomation#29](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#29)]

4. Modificare `firstRange` usando il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> in modo che il marcatore di paragrafo non sia più incluso in `firstRange`.

     [!code-vb[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#30)]
     [!code-csharp[Trin_VstcoreWordAutomation#30](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#30)]

5. Sostituire la parte restante del testo nel primo paragrafo assegnando una nuova stringa alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> dell'intervallo.

     [!code-vb[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#31)]
     [!code-csharp[Trin_VstcoreWordAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#31)]

6. Sostituire il testo in `secondRange`, incluso il segno di paragrafo.

     [!code-vb[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#32)]
     [!code-csharp[Trin_VstcoreWordAutomation#32](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#32)]

7. Selezionare `firstRange` e sospendere l'esecuzione del codice per visualizzare i risultati in una finestra di messaggio, quindi eseguire la stessa operazione con `secondRange`.

     Dal momento che `firstRange` è stato ridefinito in modo da escludere il segno di paragrafo, è stata mantenuta la formattazione originale del paragrafo. È stata tuttavia inserita una frase al posto del segno di paragrafo in `secondRange`, rimuovendo di fatto il paragrafo separato.

     [!code-vb[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#33)]
     [!code-csharp[Trin_VstcoreWordAutomation#33](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#33)]

     Dal momento che il contenuto originale di entrambi gli intervalli è stato salvato come stringa, è possibile ripristinare la condizione originale del documento.

8. Modificare nuovamente `firstRange` per includere il segno di paragrafo usando il <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> metodo per la posizione di un carattere.

     [!code-vb[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#34)]
     [!code-csharp[Trin_VstcoreWordAutomation#34](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#34)]

9. Eliminare `secondRange`. In questo modo, il terzo paragrafo verrà ripristinato nella posizione originale.

     [!code-vb[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#35)]
     [!code-csharp[Trin_VstcoreWordAutomation#35](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#35)]

10. Ripristinare il testo originale del paragrafo in `firstRange`.

     [!code-vb[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#36)]
     [!code-csharp[Trin_VstcoreWordAutomation#36](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#36)]

11. Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per inserire il contenuto originale del secondo paragrafo dopo `firstRange`, quindi selezionare `firstRange`.

     [!code-vb[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#37)]
     [!code-csharp[Trin_VstcoreWordAutomation#37](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#37)]

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Per controllare la struttura dei paragrafi durante l'inserimento di testo nelle personalizzazioni a livello di documento

1. L'esempio seguente illustra il metodo completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomation#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#26)]

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Per controllare la struttura dei paragrafi durante l'inserimento di testo in un componente aggiuntivo VSTO

1. Nell'esempio seguente viene illustrato il metodo completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#26)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#26)]

## <a name="see-also"></a>Vedi anche
- [Procedura: estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: comprimere intervalli o selezioni in documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Procedura: inserire testo in documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Procedura: reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
