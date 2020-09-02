---
title: Ottenere inizio & caratteri finali negli intervalli a livello di codice
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ranges, retrieving start and end characters
- end characters
- start characters
- documents [Office development in Visual Studio], retrieving ranges
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 485945f235a9161b6dc0584f7018c6f03c6024f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537657"
---
# <a name="how-to-programmatically-retrieve-start-and-end-characters-in-ranges"></a>Procedura: recuperare i caratteri iniziale e finale negli intervalli a livello di codice
  Questo esempio illustra come recuperare le posizioni del carattere delle posizioni iniziale e finale di un intervallo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-in-a-document-level-customization"></a>Per recuperare i caratteri iniziale e finale di un intervallo in una personalizzazione a livello di documento

1. Ottenere i valori delle proprietà <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> . L'esempio di codice seguente ottiene la posizione iniziale e finale della seconda frase nel documento. Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomation#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#25)]

## <a name="to-retrieve-start-and-end-characters-of-a-range-by-using-a-vsto-add-in"></a>Per recuperare i caratteri iniziali e finali di un intervallo usando un componente aggiuntivo VSTO

1. Ottenere i valori delle proprietà <xref:Microsoft.Office.Interop.Word.Range.Start%2A> e <xref:Microsoft.Office.Interop.Word.Range.End%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> . L'esempio di codice seguente ottiene la posizione iniziale e finale della seconda frase nel documento attivo. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#25)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#25](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#25)]

## <a name="see-also"></a>Vedere anche
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)
- [Procedura: comprimere intervalli o selezioni in documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
- [Procedura: escludere i segni di paragrafo a livello di codice durante la creazione di intervalli](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)
- [Procedura: conteggiare i caratteri nei documenti a livello di codice](../vsto/how-to-programmatically-count-characters-in-documents.md)
