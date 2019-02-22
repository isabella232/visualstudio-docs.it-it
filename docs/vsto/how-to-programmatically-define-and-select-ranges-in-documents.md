---
title: 'Procedura: Definire e selezionare intervalli nei documenti a livello di codice'
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d95690af1b1712aa374a4e9717c8c3bc6ac17fed
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599905"
---
# <a name="how-to-programmatically-define-and-select-ranges-in-documents"></a>Procedura: Definire e selezionare intervalli nei documenti a livello di codice
  È possibile definire un intervallo in un documento di Microsoft Office Word usando un oggetto <xref:Microsoft.Office.Interop.Word.Range>. È possibile selezionare l'intero documento in diversi modi, ad esempio, tramite il <xref:Microsoft.Office.Interop.Word.Range.Select%2A> metodo del <xref:Microsoft.Office.Interop.Word.Range> dell'oggetto oppure usando la proprietà Content del <xref:Microsoft.Office.Tools.Word.Document> classe (in una personalizzazione a livello di documento) o <xref:Microsoft.Office.Interop.Word.Document> classe (in un Componente aggiuntivo VSTO).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="define-a-range"></a>Definire un intervallo
 L'esempio seguente illustra come creare un nuovo oggetto <xref:Microsoft.Office.Interop.Word.Range> che include i primi sette caratteri nel documento attivo, inclusi i caratteri non stampabili. Viene quindi selezionato il testo incluso nell'intervallo.

### <a name="to-define-a-range-in-a-document-level-customization"></a>Per definire un intervallo in una personalizzazione a livello di documento

1.  Aggiungere l'intervallo al documento passando un carattere di inizio e di fine al metodo <xref:Microsoft.Office.Tools.Word.Document.Range%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomation#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#18)]

### <a name="to-define-a-range-by-using-a-vsto-add-in"></a>Per definire un intervallo mediante un componente aggiuntivo VSTO

1.  Aggiungere l'intervallo al documento passando un carattere di inizio e di fine al metodo <xref:Microsoft.Office.Interop.Word._Document.Range%2A> della classe <xref:Microsoft.Office.Interop.Word.Document>. L'esempio di codice seguente aggiunge un intervallo al documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#18)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#18)]

## <a name="select-a-range-in-a-document-level-customization"></a>Selezionare un intervallo in una personalizzazione a livello di documento
 Gli esempi seguenti illustrano come selezionare l'intero documento usando il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> oppure usando la proprietà <xref:Microsoft.Office.Tools.Word.Document.Content%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Per selezionare l'intero documento come un intervallo mediante il metodo Select

1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> che contiene l'intero documento. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomation#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Per selezionare l'intero documento come un intervallo mediante la proprietà Content

1. Usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.Content%2A> per definire un intervallo che include l'intero documento.

    [!code-vb[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomation#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#20)]

   È anche possibile usare i metodi e le proprietà di altri oggetti per definire un intervallo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Per selezionare una frase nel documento attivo

1. Configurare l'intervallo usando la raccolta <xref:Microsoft.Office.Interop.Word.Sentences>. Usare l'indice della frase da selezionare.

    [!code-vb[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomation#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#21)]

   Un altro modo per selezionare una frase consiste nel configurare manualmente i valori di inizio e di fine per l'intervallo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Per selezionare una frase configurando manualmente i valori di inizio e di fine

1.  Creare una variabile di intervallo.

     [!code-vb[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomation#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#23)]

2.  Verificare se sono presenti almeno due frasi del documento, impostare il *avviare* e *End* argomenti dell'intervallo e quindi selezionare l'intervallo.

     [!code-vb[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#24)]

## <a name="select-a-range-by-using-a-vsto-add-in"></a>Selezionare un intervallo usando un componente aggiuntivo VSTO
 Gli esempi seguenti illustrano come selezionare l'intero documento usando il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> oppure usando la proprietà <xref:Microsoft.Office.Interop.Word._Document.Content%2A> della classe <xref:Microsoft.Office.Interop.Word.Document>.

### <a name="to-select-the-entire-document-as-a-range-by-using-the-select-method"></a>Per selezionare l'intero documento come un intervallo mediante il metodo Select

1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> che contiene l'intero documento. L'esempio di codice seguente seleziona i contenuti del documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#19)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#19)]

### <a name="to-select-the-entire-document-as-a-range-by-using-the-content-property"></a>Per selezionare l'intero documento come un intervallo mediante la proprietà Content

1. Usare la proprietà <xref:Microsoft.Office.Interop.Word._Document.Content%2A> per definire un intervallo che include l'intero documento.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#20)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#20)]

   È anche possibile usare i metodi e le proprietà di altri oggetti per definire un intervallo.

### <a name="to-select-a-sentence-in-the-active-document"></a>Per selezionare una frase nel documento attivo

1. Configurare l'intervallo usando la raccolta <xref:Microsoft.Office.Interop.Word.Sentences>. Usare l'indice della frase da selezionare.

    [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#21)]
    [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#21)]

   Un altro modo per selezionare una frase consiste nel configurare manualmente i valori di inizio e di fine per l'intervallo.

### <a name="to-select-a-sentence-by-manually-setting-the-start-and-end-values"></a>Per selezionare una frase configurando manualmente i valori di inizio e di fine

1.  Creare una variabile di intervallo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#23)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#23)]

2.  Verificare se sono presenti almeno due frasi del documento, impostare il *avviare* e *End* argomenti dell'intervallo e quindi selezionare l'intervallo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#24)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#24)]

## <a name="see-also"></a>Vedere anche
- [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)
- [Procedura: A livello di programmazione estendere gli intervalli nei documenti](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: A livello di programmazione estendere gli intervalli nei documenti](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: A livello di programmazione reimpostare gli intervalli nei documenti di Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: A livello di programmazione comprimere intervalli o selezioni in documenti](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Procedura: A livello di programmazione escludere i segni di paragrafo durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
