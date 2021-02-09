---
title: 'Procedura: formattare il testo nei documenti a livello di codice'
description: Informazioni su come usare l'oggetto intervallo per formattare il testo in un documento di Microsoft Word a livello di codice.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d5804c7441682a6bedb776558bd2eb5c79605951
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885430"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Procedura: formattare il testo nei documenti a livello di codice
  È possibile usare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> per formattare il testo in un documento di Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 L'esempio seguente seleziona il primo paragrafo del documento e modifica le dimensioni del carattere, il nome del carattere e l'allineamento. Quindi, seleziona l'intervallo e visualizza una finestra messaggio per sospendere l'operazione prima di eseguire la successiva sezione di codice. La sezione successiva chiama tre volte il metodo Undo dell' <xref:Microsoft.Office.Tools.Word.Document> elemento host (per una personalizzazione a livello di documento) o la <xref:Microsoft.Office.Interop.Word.Document> classe (per un componente aggiuntivo VSTO). Applica lo stile del livello di rientro normale, mostrando una finestra di messaggio per sospendere il codice. Il codice chiama quindi il metodo <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> una volta e visualizza una finestra di messaggio.

## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento

### <a name="to-format-text-using-a-document-level-customization"></a>Per formattare il testo usando una personalizzazione a livello di documento

1. L'esempio seguente può essere usato in una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]

## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO

### <a name="to-format-text-using-a-vsto-add-in"></a>Per formattare il testo usando un componente aggiuntivo VSTO

1. L'esempio seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]

## <a name="see-also"></a>Vedi anche
- [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
- [Procedura: inserire testo in documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)
- [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
