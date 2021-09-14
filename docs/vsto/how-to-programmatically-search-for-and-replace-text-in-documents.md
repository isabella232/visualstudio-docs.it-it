---
title: Trovare e sostituire testo nei documenti a livello di codice
description: Informazioni su come usare Visual Studio per cercare e sostituire testo in un documento Microsoft Word codice.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: efd725b094ac720f954a0075093ed683e965674d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633915"
---
# <a name="how-to-programmatically-search-for-and-replace-text-in-documents"></a>Procedura: Cercare e sostituire testo nei documenti a livello di codice
  L'oggetto <xref:Microsoft.Office.Interop.Word.Find> è un membro degli oggetti <xref:Microsoft.Office.Interop.Word.Selection> e <xref:Microsoft.Office.Interop.Word.Range>, ognuno dei quali può essere usato per cercare testo in documenti di Microsoft Office Word. Il comando di sostituzione è un'estensione del comando di ricerca.

 Usare un oggetto <xref:Microsoft.Office.Interop.Word.Find> per scorrere in ciclo un documento di Microsoft Office Word e cercare testo, formattazione o uno stile specifico e quindi usare la proprietà <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> per sostituire tutti gli elementi trovati.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-a-selection-object"></a>Usare un oggetto Selection
 Quando si usa un oggetto <xref:Microsoft.Office.Interop.Word.Selection> per trovare testo, tutti i criteri di ricerca specificati vengono applicati solo in base al testo attualmente selezionato. Se <xref:Microsoft.Office.Interop.Word.Selection> è un punto di inserimento, la ricerca viene eseguita nel documento. Quando viene trovato un elemento che corrisponde ai criteri di ricerca, l'elemento viene automaticamente selezionato.

 È importante notare che i criteri <xref:Microsoft.Office.Interop.Word.Find> sono cumulativi, ovvero vengono aggiunti a criteri di ricerca precedenti. Cancellare la formattazione dalle ricerche precedenti usando il metodo <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> prima della ricerca.

### <a name="to-find-text-using-a-selection-object"></a>Per trovare testo usando un oggetto Selection

1. Assegnare una stringa di ricerca a una variabile.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet68":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet68":::

2. Cancellare la formattazione dalle ricerche precedenti.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet69":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet69":::

3. Eseguire la ricerca e visualizzare una finestra di messaggio con i risultati.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet70":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet70":::

   L'esempio seguente mostra il metodo completo.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet67":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet67":::

## <a name="use-a-range-object"></a>Usare un oggetto Range
 L'uso di un oggetto <xref:Microsoft.Office.Interop.Word.Range> permette di cercare testo senza alcuna visualizzazione nell'interfaccia utente. L'oggetto restituisce True se viene trovato testo che corrisponde ai criteri di <xref:Microsoft.Office.Interop.Word.Find> ricerca e **False** in caso contrario.  Ridefinisce inoltre l'oggetto <xref:Microsoft.Office.Interop.Word.Range> in modo che corrisponda ai criteri di ricerca se viene trovato testo.

### <a name="to-find-text-using-a-range-object"></a>Per trovare testo usando un oggetto Range

1. Definire un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dal secondo paragrafo del documento.

    L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet72":::

    L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet72":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet72":::

2. Usando la <xref:Microsoft.Office.Interop.Word.Range.Find%2A> proprietà <xref:Microsoft.Office.Interop.Word.Range> dell'oggetto , cancellare prima le opzioni di formattazione esistenti e quindi cercare la stringa find **me**.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet73":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet73":::

3. Visualizzare i risultati della ricerca in una finestra di messaggio e selezionare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> per renderla visibile.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet74":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet74":::

    Se la ricerca non riesce, viene selezionato il secondo paragrafo, altrimenti vengono visualizzati i criteri di ricerca.

   L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento. Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` nel progetto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet71":::

   L'esempio seguente mostra il codice completo per un componente aggiuntivo VSTO. Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.

   :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet71":::
   :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet71":::

## <a name="search-for-and-replace-text-in-documents"></a>Cercare e sostituire testo nei documenti
 Il codice seguente cerca la selezione corrente e sostituisce tutte le occorrenze della stringa **find me** con la stringa **Found**.

### <a name="to-search-for-and-replace-text-in-documents"></a>Per cercare e sostituire testo in documenti

1. Aggiungere il codice di esempio seguente alla classe `ThisDocument` o `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet75":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet75":::

     La classe <xref:Microsoft.Office.Interop.Word.Find> ha un metodo <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> e anche la classe <xref:Microsoft.Office.Interop.Word.Replacement> ha il proprio metodo <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>. Quando si eseguono operazioni di ricerca e sostituzione, è necessario usare il metodo ClearFormatting di entrambi gli oggetti. Se si usa solo il metodo per l'oggetto <xref:Microsoft.Office.Interop.Word.Find>, il testo di sostituzione potrebbe restituire risultati imprevisti.

2. Usare il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Find> per sostituire ogni elemento trovato. Per specificare gli elementi da sostituire, usare il *parametro Replace.* Questo parametro può avere uno dei valori <xref:Microsoft.Office.Interop.Word.WdReplace> seguenti:

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> sostituisce tutti gli elementi trovati.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> non sostituisce alcun elemento trovato.

    - <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> sostituisce il primo elemento trovato.

## <a name="see-also"></a>Vedi anche
- [Procedura: Impostare le opzioni di ricerca in Word a livello di codice](../vsto/how-to-programmatically-set-search-options-in-word.md)
- [Procedura: Eseguire un ciclo a livello di codice tra gli elementi trovati nei documenti](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: Ripristinare le selezioni a livello di codice dopo le ricerche](../vsto/how-to-programmatically-restore-selections-after-searches.md)
- [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)
