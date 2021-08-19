---
title: Escludere i segni di paragrafo durante la creazione di intervalli a livello di codice
description: Informazioni su come escludere i segni di paragrafo a livello di codice durante la creazione di intervalli in Microsoft Word documento.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b5dbe9a51a41cca82dad43207eb103e51c6f1797
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148064"
---
# <a name="how-to-programmatically-exclude-paragraph-marks-when-creating-ranges"></a>Procedura: Escludere i segni di paragrafo a livello di codice durante la creazione di intervalli
  Ogni volta che si crea un oggetto <xref:Microsoft.Office.Interop.Word.Range> basato su un paragrafo, tutti i caratteri non stampabili, ad esempio i segni di paragrafo, vengono inclusi nell'intervallo. Può essere necessario inserire testo da un paragrafo di origine in un paragrafo di destinazione. Se non si vuole suddividere il paragrafo di destinazione i paragrafi distinti, è necessario prima rimuovere i segni di paragrafo dal paragrafo di origine. Dal momento che all'interno del segno di paragrafo sono memorizzate le informazioni sulla formattazione dei paragrafi, può anche essere necessario escludere tali informazioni durante l'inserimento dell'intervallo in un paragrafo esistente.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 La procedura di esempio riportata di seguito dichiara due variabili stringa, recupera il contenuto del primo e del secondo paragrafo nel documento attivo e ne scambia i contenuti. L'esempio quindi illustra come rimuovere il marcatore di paragrafo dall'intervallo usando il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> e inserendo testo all'interno del paragrafo.

## <a name="to-control-paragraph-structure-when-inserting-text"></a>Per controllare la struttura dei paragrafi durante l'inserimento di testo

1. Creare due variabili intervallo per il primo e il secondo paragrafo e recuperarne il contenuto usando la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> .

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet27":::

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO a livello di applicazione. Questo codice usa il documento attivo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet27":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet27":::

2. Assegnare la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> , scambiando il testo tra i due paragrafi.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet28":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet28":::

3. Selezionare uno per volta tutti gli intervalli e sospendere l'esecuzione del codice per visualizzare i risultati in una finestra di messaggio.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet29":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet29":::

4. Modificare `firstRange` usando il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> in modo che il marcatore di paragrafo non sia più incluso in `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet30":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet30":::

5. Sostituire la parte restante del testo nel primo paragrafo assegnando una nuova stringa alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> dell'intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet31":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet31":::

6. Sostituire il testo in `secondRange`, incluso il segno di paragrafo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet32":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet32":::

7. Selezionare `firstRange` e sospendere l'esecuzione del codice per visualizzare i risultati in una finestra di messaggio, quindi eseguire la stessa operazione con `secondRange`.

     Dal momento che `firstRange` è stato ridefinito in modo da escludere il segno di paragrafo, è stata mantenuta la formattazione originale del paragrafo. È stata tuttavia inserita una frase al posto del segno di paragrafo in `secondRange`, rimuovendo di fatto il paragrafo separato.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet33":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet33":::

     Dal momento che il contenuto originale di entrambi gli intervalli è stato salvato come stringa, è possibile ripristinare la condizione originale del documento.

8. Modificare il `firstRange` testo per includere il segno di paragrafo usando il metodo per la posizione di un <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> carattere.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet34":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet34":::

9. Eliminare `secondRange`. In questo modo, il terzo paragrafo verrà ripristinato nella posizione originale.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet35":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet35":::

10. Ripristinare il testo originale del paragrafo in `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet36":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet36":::

11. Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per inserire il contenuto originale del secondo paragrafo dopo `firstRange`, quindi selezionare `firstRange`.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet37":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet37":::

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="to-control-paragraph-structure-when-inserting-text-in-document-level-customizations"></a>Per controllare la struttura dei paragrafi durante l'inserimento di testo nelle personalizzazioni a livello di documento

1. L'esempio seguente illustra il metodo completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet26":::

## <a name="vsto-add-in-example"></a>VSTO Esempio di componente aggiuntivo

### <a name="to-control-paragraph-structure-when-inserting-text-in-a-vsto-add-in"></a>Per controllare la struttura del paragrafo durante l'inserimento di testo in VSTO componente aggiuntivo

1. L'esempio seguente illustra il metodo completo per VSTO componente aggiuntivo. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet26":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet26":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: Comprimere intervalli o selezioni nei documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Procedura: Inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Parametri facoltativi nelle Office soluzioni](../vsto/optional-parameters-in-office-solutions.md)
