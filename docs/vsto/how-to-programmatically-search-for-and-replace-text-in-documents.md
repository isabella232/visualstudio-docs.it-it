---
title: Trovare e sostituire testo nei documenti a livello di codice
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], searching
- text searches, replacing text
- text searches, documents
- text [Office development in Visual Studio], searching in documents
- text [Office development in Visual Studio], text searches
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 18a50d6d4ef52a0c50be0b72b4cab5706da4e2db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547043"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Procedura: cercare e sostituire testo nei documenti a livello di codice
  L'oggetto <xref:Microsoft.Office.Interop.Word.Find> è un membro degli oggetti <xref:Microsoft.Office.Interop.Word.Selection> e <xref:Microsoft.Office.Interop.Word.Range>, ognuno dei quali può essere usato per cercare testo in documenti di Microsoft Office Word. Il comando di sostituzione è un'estensione del comando di ricerca.

 Usare un oggetto <xref:Microsoft.Office.Interop.Word.Find> per scorrere in ciclo un documento di Microsoft Office Word e cercare testo, formattazione o uno stile specifico e quindi usare la proprietà <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> per sostituire tutti gli elementi trovati.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Usare un oggetto Selection
 Quando si usa un oggetto <xref:Microsoft.Office.Interop.Word.Selection> per trovare testo, tutti i criteri di ricerca specificati vengono applicati solo in base al testo attualmente selezionato. Se <xref:Microsoft.Office.Interop.Word.Selection> è un punto di inserimento, la ricerca viene eseguita nel documento. Quando viene trovato un elemento che corrisponde ai criteri di ricerca, l'elemento viene automaticamente selezionato.

 È importante notare che i criteri <xref:Microsoft.Office.Interop.Word.Find> sono cumulativi, ovvero vengono aggiunti a criteri di ricerca precedenti. Cancellare la formattazione dalle ricerche precedenti usando il metodo <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> prima della ricerca.

### <a name="to-find-text-using-a-selection-object"></a>Per trovare testo usando un oggetto Selection

1. Assegnare una stringa di ricerca a una variabile.

    [!code-vb[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#68)]
    [!code-csharp[Trin_VstcoreWordAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#68)]

2. Cancellare la formattazione dalle ricerche precedenti.

    [!code-vb[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#69)]
    [!code-csharp[Trin_VstcoreWordAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#69)]

3. Eseguire la ricerca e visualizzare una finestra di messaggio con i risultati.

    [!code-vb[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#70)]
    [!code-csharp[Trin_VstcoreWordAutomation#70](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#70)]

   L'esempio seguente mostra il metodo completo.

   [!code-vb[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#67)]
   [!code-csharp[Trin_VstcoreWordAutomation#67](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#67)]

## <a name="use-a-range-object"></a>Usare un oggetto Range
 L'uso di un oggetto <xref:Microsoft.Office.Interop.Word.Range> permette di cercare testo senza alcuna visualizzazione nell'interfaccia utente. L' <xref:Microsoft.Office.Interop.Word.Find> oggetto restituisce **true** se viene trovato un testo corrispondente ai criteri di ricerca e **false** in caso contrario. Ridefinisce inoltre l'oggetto <xref:Microsoft.Office.Interop.Word.Range> in modo che corrisponda ai criteri di ricerca se viene trovato testo.

### <a name="to-find-text-using-a-range-object"></a>Per trovare testo usando un oggetto Range

1. Definire un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dal secondo paragrafo del documento.

    L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

    [!code-vb[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomation#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#72)]

    L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#72)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#72)]

2. Utilizzando la <xref:Microsoft.Office.Interop.Word.Range.Find%2A> proprietà dell' <xref:Microsoft.Office.Interop.Word.Range> oggetto, deselezionare innanzitutto tutte le opzioni di formattazione esistenti, quindi cercare la stringa **Find me**.

    [!code-vb[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#73)]
    [!code-csharp[Trin_VstcoreWordAutomation#73](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#73)]

3. Visualizzare i risultati della ricerca in una finestra di messaggio e selezionare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> per renderla visibile.

    [!code-vb[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#74)]
    [!code-csharp[Trin_VstcoreWordAutomation#74](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#74)]

    Se la ricerca non riesce, viene selezionato il secondo paragrafo, altrimenti vengono visualizzati i criteri di ricerca.

   L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` nel progetto.

   [!code-vb[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomation#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#71)]

   L'esempio seguente mostra il codice completo per un componente aggiuntivo VSTO. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

   [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#71)]
   [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#71)]

## <a name="search-for-and-replace-text-in-documents"></a>Cercare e sostituire testo nei documenti
 Il codice seguente cerca la selezione corrente e sostituisce tutte le occorrenze della stringa **Find me** con la stringa **trovata**.

### <a name="to-search-for-and-replace-text-in-documents"></a>Per cercare e sostituire testo in documenti

1. Aggiungere il codice di esempio seguente alla classe `ThisDocument` o `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#75)]
     [!code-csharp[Trin_VstcoreWordAutomation#75](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#75)]

     La classe <xref:Microsoft.Office.Interop.Word.Find> ha un metodo <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> e anche la classe <xref:Microsoft.Office.Interop.Word.Replacement> ha il proprio metodo <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>. Quando si eseguono operazioni di ricerca e sostituzione, è necessario utilizzare il metodo ClearFormatting di entrambi gli oggetti. Se si usa solo il metodo per l'oggetto <xref:Microsoft.Office.Interop.Word.Find>, il testo di sostituzione potrebbe restituire risultati imprevisti.

2. Usare il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Find> per sostituire ogni elemento trovato. Per specificare gli elementi da sostituire, usare il parametro *Replace* . Questo parametro può avere uno dei valori <xref:Microsoft.Office.Interop.Word.WdReplace> seguenti:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> sostituisce tutti gli elementi trovati.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> non sostituisce alcun elemento trovato.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> sostituisce il primo elemento trovato.

## <a name="see-also"></a>Vedere anche
- [Procedura: impostare le opzioni di ricerca in Word a livello di codice](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Procedura: scorrere in ciclo gli elementi trovati nei documenti a livello di codice](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
