---
title: 'Procedura: formattazione del testo nei documenti a livello di codice'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formatting [Office development in Visual Studio]
- documents [Office development in Visual Studio], formatting text
- text [Office development in Visual Studio], formatting in documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: baf6f49b0347aa4a770b4f7a47c7fa8195d5ede5
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2018
ms.locfileid: "35257410"
---
# <a name="how-to-programmatically-format-text-in-documents"></a>Procedura: formattazione del testo nei documenti a livello di codice
  È possibile usare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> per formattare il testo in un documento di Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 L'esempio seguente seleziona il primo paragrafo del documento e modifica le dimensioni del carattere, il nome del carattere e l'allineamento. Quindi, seleziona l'intervallo e visualizza una finestra messaggio per sospendere l'operazione prima di eseguire la successiva sezione di codice. Nella sezione successiva chiama il metodo Undo del <xref:Microsoft.Office.Tools.Word.Document> elemento host (per una personalizzazione a livello di documento) o <xref:Microsoft.Office.Interop.Word.Document> classe (per un componente aggiuntivo VSTO) tre volte. Applica lo stile del livello di rientro normale, mostrando una finestra di messaggio per sospendere il codice. Il codice chiama quindi il metodo <xref:Microsoft.Office.Tools.Word.Document.Undo%2A> una volta e visualizza una finestra di messaggio.  
  
## <a name="document-level-customization-example"></a>Esempio di personalizzazione a livello di documento  
  
### <a name="to-format-text-using-a-document-level-customization"></a>Per formattare il testo usando una personalizzazione a livello di documento  
  
1.  L'esempio seguente può essere usato in una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomation#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#62)]  
  
## <a name="vsto-add-in-example"></a>Esempio di componente aggiuntivo VSTO  
  
### <a name="to-format-text-using-a-vsto-add-in"></a>Per formattare il testo usando un componente aggiuntivo VSTO  
  
1.  L'esempio seguente può essere usato in un componente aggiuntivo VSTO. L'esempio usa il documento attivo. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#62)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#62](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#62)]  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: a livello di programmazione inserire testo nei documenti di Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)  
  
  