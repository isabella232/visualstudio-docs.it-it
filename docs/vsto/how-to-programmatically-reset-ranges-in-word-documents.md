---
title: 'Procedura: A livello di programmazione reimpostare gli intervalli nei documenti di Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], resetting ranges
- ranges, resetting in documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 622d807da832c4c07baf8b62c902c2b1d25cc14d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072071"
---
# <a name="how-to-programmatically-reset-ranges-in-word-documents"></a>Procedura: A livello di programmazione reimpostare gli intervalli nei documenti di Word
  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> per ridimensionare un intervallo esistente in un documento di Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-reset-an-existing-range"></a>Per reimpostare un intervallo esistente

1. Impostare un intervallo iniziale iniziando con i primi sette caratteri nel documento.

     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.

     [!code-vb[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomation#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#43)]

     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO. Questo codice usa il documento attivo.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#43)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#43](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#43)]

2. Usare <xref:Microsoft.Office.Interop.Word.Range.SetRange%2A> per iniziare l'intervallo in corrispondenza della seconda frase e terminarla alla fine della quinta frase.

     [!code-vb[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#44)]
     [!code-csharp[Trin_VstcoreWordAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#44)]

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="to-reset-an-existing-range-in-a-document-level-customization"></a>Per reimpostare un intervallo esistente in una personalizzazione a livello di documento

1. L'esempio seguente mostra l'esempio completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomation#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#42)]

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="to-reset-an-existing-range-in-a-vsto-add-in"></a>Per reimpostare un intervallo esistente in un componente aggiuntivo VSTO

1. Nell'esempio seguente viene illustrato un esempio completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#42)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#42](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#42)]

## <a name="see-also"></a>Vedere anche
- [Procedura: A livello di programmazione estendere gli intervalli nei documenti](../vsto/how-to-programmatically-extend-ranges-in-documents.md)
- [Procedura: Definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Procedura: A livello di programmazione comprimere intervalli o selezioni in documenti](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)
