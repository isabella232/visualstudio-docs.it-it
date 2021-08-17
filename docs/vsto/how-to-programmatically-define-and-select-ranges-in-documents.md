---
title: 'Procedura: Definire e selezionare intervalli nei documenti a livello di codice'
description: Informazioni su come definire e selezionare intervalli a livello di Microsoft Word documenti usando l'oggetto Range.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], selecting sentences
- documents [Office development in Visual Studio], ranges
- sentences, selecting in documents
- ranges, selecting in documents
- ranges, defining in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 98b7e6aa0d95322fb3a69263d487ba0ce21e5d9f5c7c8b4606c12cbdd489655d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121394462"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Procedura: Definire e selezionare intervalli nei documenti a livello di codice
  È possibile definire un intervallo in un documento di Microsoft Office Word usando un oggetto <xref:Microsoft.Office.Interop.Word.Range>. È possibile selezionare l'intero documento in diversi modi, ad esempio usando il metodo dell'oggetto o la proprietà Content della classe (in una personalizzazione a livello di documento) o della classe (in un componente aggiuntivo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> <xref:Microsoft.Office.Interop.Word.Range> <xref:Microsoft.Office.Tools.Word.Document> <xref:Microsoft.Office.Interop.Word.Document> VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Definire un intervallo
 L'esempio seguente illustra come creare un nuovo oggetto <xref:Microsoft.Office.Interop.Word.Range> che include i primi sette caratteri nel documento attivo, inclusi i caratteri non stampabili. Viene quindi selezionato il testo incluso nell'intervallo.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Per definire un intervallo in una personalizzazione a livello di documento

1. Aggiungere l'intervallo al documento passando un carattere di inizio e di fine al metodo <xref:Microsoft.Office.Tools.Word.Document.Range%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet18":::

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Per definire un intervallo mediante un componente aggiuntivo VSTO

1. Aggiungere l'intervallo al documento passando un carattere di inizio e di fine al metodo <xref:Microsoft.Office.Interop.Word._Document.Range%2A> della classe <xref:Microsoft.Office.Interop.Word.Document>. L'esempio di codice seguente aggiunge un intervallo al documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet18":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet18":::

## <a name="select-a-range-in-a-document-level-customization"></a>Selezionare un intervallo in una personalizzazione a livello di documento
 Gli esempi seguenti illustrano come selezionare l'intero documento usando il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> oppure usando la proprietà <xref:Microsoft.Office.Tools.Word.Document.Content%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Per selezionare l'intero documento come un intervallo mediante il metodo Select

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> che contiene l'intero documento. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Per selezionare l'intero documento come un intervallo mediante la proprietà Content

1. Usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.Content%2A> per definire un intervallo che include l'intero documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet20":::

   È anche possibile usare i metodi e le proprietà di altri oggetti per definire un intervallo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Per selezionare una frase nel documento attivo

1. Configurare l'intervallo usando la raccolta <xref:Microsoft.Office.Interop.Word.Sentences>. Usare l'indice della frase da selezionare.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet21":::

   Un altro modo per selezionare una frase consiste nel configurare manualmente i valori di inizio e di fine per l'intervallo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Per selezionare una frase configurando manualmente i valori di inizio e di fine

1. Creare una variabile di intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet23":::

2. Verificare se nel documento sono presenti almeno due frasi, impostare gli argomenti *Start* e *End* dell'intervallo e quindi selezionare l'intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet24":::

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Selezionare un intervallo usando un VSTO componente aggiuntivo
 Gli esempi seguenti illustrano come selezionare l'intero documento usando il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> oppure usando la proprietà <xref:Microsoft.Office.Interop.Word._Document.Content%2A> della classe <xref:Microsoft.Office.Interop.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Per selezionare l'intero documento come un intervallo mediante il metodo Select

1. Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> che contiene l'intero documento. L'esempio di codice seguente seleziona i contenuti del documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet19":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet19":::

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Per selezionare l'intero documento come un intervallo mediante la proprietà Content

1. Usare la proprietà <xref:Microsoft.Office.Interop.Word._Document.Content%2A> per definire un intervallo che include l'intero documento.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet20":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet20":::

   È anche possibile usare i metodi e le proprietà di altri oggetti per definire un intervallo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Per selezionare una frase nel documento attivo

1. Configurare l'intervallo usando la raccolta <xref:Microsoft.Office.Interop.Word.Sentences>. Usare l'indice della frase da selezionare.

    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet21":::
    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet21":::

   Un altro modo per selezionare una frase consiste nel configurare manualmente i valori di inizio e di fine per l'intervallo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Per selezionare una frase configurando manualmente i valori di inizio e di fine

1. Creare una variabile di intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet23":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet23":::

2. Verificare se nel documento sono presenti almeno due frasi, impostare gli argomenti *Start* e *End* dell'intervallo e quindi selezionare l'intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet24":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet24":::

## <a name="see-also"></a>Vedi anche
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: Recuperare a livello di codice i caratteri iniziale e finale negli intervalli](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: Comprimere intervalli o selezioni nei documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Procedura: Escludere i segni di paragrafo a livello di codice durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
