---
title: 'Procedura: Inserire testo nei documenti di Word a livello di codice'
description: Informazioni su come inserire testo in un documento Microsoft Word a livello di codice usando Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 08/14/2019
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, inserting text in documents
- text [Office development in Visual Studio], inserting in documents
- ranges, replacing text in documents
- documents [Office development in Visual Studio], inserting text
- text [Office development in Visual Studio], replacing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c2acc09b04ba08543faa449788f61f7fa72c8c72
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122026187"
---
# <a name="how-to-programmatically-insert-text-into-word-documents"></a>Procedura: Inserire testo nei documenti di Word a livello di codice
  Esistono tre modi principali per inserire il testo nei documenti di Microsoft Office Word:

- Inserire il testo in un intervallo.

- Sostituire il testo in un intervallo con il nuovo testo.

- Usare il metodo <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Selection> per inserire il testo in corrispondenza del cursore o della selezione.

> [!NOTE]
> È anche possibile inserire il testo nei controlli contenuto e nei segnalibri. Per altre informazioni, vedere [Controlli contenuto e](../vsto/content-controls.md) Controllo [Segnalibro](../vsto/bookmark-control.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="insert-text-in-a-range"></a>Inserire testo in un intervallo
 Usare la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> per inserire il testo in un documento.

### <a name="to-insert-text-in-a-range"></a>Per inserire il testo in un intervallo

1. Specificare un intervallo all'inizio di un documento e inserire il testo **New Text**.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet51":::

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet51":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet51":::

2. Selezionare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> , che è stato espanso da un carattere alla lunghezza del testo inserito.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet52":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet52":::

## <a name="replace-text-in-a-range"></a>Sostituire il testo in un intervallo
 Se l'intervallo specificato contiene testo, tutto il testo dell'intervallo viene sostituito con il testo inserito.

### <a name="to-replace-text-in-a-range"></a>Per sostituire il testo in un intervallo

1. Creare un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dai primi 12 caratteri nel documento.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet53":::

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet53":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet53":::

2. Sostituire questi caratteri con la stringa **New Text**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet54":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet54":::

3. Selezionare l'intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet55":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet55":::

## <a name="insert-text-using-typetext"></a>Inserire testo usando TypeText
 Il metodo <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> inserisce il testo in corrispondenza della selezione. <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A> si comporta in modo diverso a seconda delle opzioni impostate nel computer dell'utente. Il codice nella procedura seguente dichiara una variabile dell'oggetto <xref:Microsoft.Office.Interop.Word.Selection> e disattiva l'opzione **Overtype** , se attivata. Se l'opzione **Overtype** è attivata, l'eventuale testo accanto al cursore viene sovrascritto.

### <a name="to-insert-text-using-the-typetext-method"></a>Per inserire il testo usando il metodo TypeText

1. Dichiarare una variabile oggetto <xref:Microsoft.Office.Interop.Word.Selection>.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet57":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet57":::

2. Disattivare l'opzione **Overtype** se attivata.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet58":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet58":::

3. Verificare se la selezione corrente si trova in corrispondenza del punto di inserimento.

    In questo caso, il codice inserisce una frase usando <xref:Microsoft.Office.Interop.Word.Selection.TypeText%2A>, quindi un segno di paragrafo usando il metodo <xref:Microsoft.Office.Interop.Word.Selection.TypeParagraph%2A> .

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet59":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet59":::

4. Il codice nel blocco **ElseIf** verifica che la selezione sia una selezione normale. In questo caso, un altro blocco **If** verifica che l'opzione **ReplaceSelection** sia attivata. In questo caso, il codice usa il metodo <xref:Microsoft.Office.Interop.Word.Selection.Collapse%2A> della selezione per comprimere la selezione in un punto di inserimento all'inizio del blocco di testo selezionato. Inserire il testo e un segno di paragrafo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet60":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet60":::

5. Se la selezione non è un punto di inserimento o un blocco di testo selezionato, il codice nel blocco **Else** non esegue alcuna operazione.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet61":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet61":::

   È anche possibile usare il metodo dell'oggetto , che simula la funzionalità <xref:Microsoft.Office.Interop.Word.Selection.TypeBackspace%2A> <xref:Microsoft.Office.Interop.Word.Selection> del tasto **Backspace** sulla tastiera. Tuttavia, per l'inserimento e la modifica del testo, l'oggetto <xref:Microsoft.Office.Interop.Word.Range> offre un maggiore controllo.

   L'esempio seguente mostra il codice completo. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` o `ThisAddIn` nel progetto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet56":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet56":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Formattare il testo nei documenti a livello di codice](../vsto/how-to-programmatically-format-text-in-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
