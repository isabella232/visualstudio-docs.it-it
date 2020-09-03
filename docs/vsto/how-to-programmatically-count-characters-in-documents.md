---
title: 'Procedura: conteggiare i caratteri nei documenti a livello di codice'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81ee7c3d798ae2c38ed80b261a6d87190daa59a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546068"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Procedura: conteggiare i caratteri nei documenti a livello di codice
  Il primo carattere in un documento è nella posizione del carattere 0, che rappresenta il punto di inserimento. La posizione dell'ultimo carattere è uguale al numero totale di caratteri nel documento. È possibile determinare il numero di caratteri in un documento usando la proprietà <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Characters> .

 Tutti i caratteri del documento vengono contati, inclusi gli spazi, i segni di paragrafo e altri caratteri che sono normalmente nascosti. Anche un nuovo documento vuoto restituisce un numero di un solo carattere perché contiene un segno di paragrafo.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Per visualizzare il numero di caratteri in una personalizzazione a livello di documento

1. Selezionare l'intero documento.

     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]

2. Visualizzare il numero di caratteri del documento in una finestra di messaggio.

     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Per visualizzare il numero di caratteri in un componente aggiuntivo VSTO

1. Selezionare l'intero documento. L'esempio di codice seguente seleziona il documento attivo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]

2. Visualizzare il numero di caratteri del documento in una finestra di messaggio.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]

## <a name="see-also"></a>Vedere anche
- [Procedura: recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
