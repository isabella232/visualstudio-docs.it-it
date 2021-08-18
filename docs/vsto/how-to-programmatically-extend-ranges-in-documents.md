---
title: 'Procedura: Estendere gli intervalli nei documenti a livello di codice'
description: Informazioni su come estendere a livello di codice gli intervalli di punti di inizio e di fine in Microsoft Word documento a livello di documento o di applicazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, extending
- documents [Office development in Visual Studio], extending ranges
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 7297a638b22ca031ae4c728675a054a3430a2cf8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148025"
---
# <a name="how-to-programmatically-extend-ranges-in-documents"></a>Procedura: Estendere gli intervalli nei documenti a livello di codice
  Una volta definito un oggetto <xref:Microsoft.Office.Interop.Word.Range> in un documento di Microsoft Office Word, è possibile modificare i punti iniziale e finale usando i metodi <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> . I metodi <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> e <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> accettano gli stessi due argomenti, *Unit* e *Count*. I metodi *Count* rappresenta il numero di unità da spostare, mentre l'argomento *Unit* può rappresentare uno dei seguenti valori <xref:Microsoft.Office.Interop.Word.WdUnits> :

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCharacter>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdWord>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSentence>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdParagraph>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdSection>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdStory>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdCell>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdColumn>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdRow>

- <xref:Microsoft.Office.Interop.Word.WdUnits.wdTable>

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  L'esempio seguente definisce un intervallo di sette caratteri. La posizione iniziale dell'intervallo viene quindi spostata sette caratteri dopo la posizione iniziale originale. Dal momento che anche la posizione finale dell'intervallo era sette caratteri dopo la posizione iniziale, il risultato è un intervallo composto da zero caratteri. All'interno del codice, la posizione finale viene spostata sette caratteri dopo la posizione finale corrente.

## <a name="to-extend-a-range"></a>Per estendere un intervallo

1. Definire un intervallo di caratteri. Per altre informazioni, vedere Procedura: Definire e selezionare intervalli nei [documenti a livello di codice.](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet39":::

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet39":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet39":::

2. Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveStart%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per spostare la posizione iniziale dell'intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet40":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet40":::

3. Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per spostare la posizione finale dell'intervallo.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet41":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet41":::

## <a name="document-level-customization-code"></a>Codice di personalizzazione a livello di documento

### <a name="to-extend-a-range-in-a-document-level-customization"></a>Per estendere un intervallo in una personalizzazione a livello di documento

1. L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet38":::

## <a name="vsto-add-in-code"></a>Codice di componente aggiuntivo VSTO

### <a name="to-extend-a-range-in-an-application-level-vsto-add-in"></a>Per estendere un intervallo in un componente aggiuntivo VSTO a livello di applicazione

1. L'esempio seguente mostra il codice completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet38":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet38":::

## <a name="see-also"></a>Vedi anche
- [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: Comprimere intervalli o selezioni nei documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: Recuperare a livello di codice i caratteri iniziale e finale negli intervalli](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: Escludere i segni di paragrafo a livello di codice durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
