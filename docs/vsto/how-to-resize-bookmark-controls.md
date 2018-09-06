---
title: 'Procedura: ridimensionare i controlli Bookmark'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 79b129a31439b175bde61f9a995abcf98a7a9708
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671908"
---
# <a name="how-to-resize-bookmark-controls"></a>Procedura: ridimensionare i controlli Bookmark
  Le dimensioni di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> vengono impostate quando il controllo viene aggiunto a un documento di Microsoft Office Word. È anche possibile ridimensionare tale controllo in un secondo momento.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Il ridimensionamento di un segnalibro può avvenire in tre modi:  
  
-   Aggiungere o rimuovere un testo nel controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Ogni volta che si aggiunge del testo in un segnalibro, le dimensioni del segnalibro aumentano automaticamente al fine di contenere il nuovo testo. Quando si elimina il testo, le dimensioni del segnalibro si riducono automaticamente.  
  
-   Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Questa funzionalità è utile se si modificano le dimensioni solo di un numero limitato di caratteri.  
  
-   Ricreare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
     Questa funzionalità è utile in caso di una modifica sostanziale delle dimensioni o della posizione di un segnalibro.  
  
 Nei progetti a livello di documento è possibile aggiungere controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO, è possibile aggiungere <xref:Microsoft.Office.Tools.Word.Bookmark> controlli a qualsiasi documento aperto in fase di esecuzione. Per altre informazioni, vedere [procedura: Aggiungi controllo Bookmark controlli ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="change-the-start-and-end-properties"></a>Modificare le proprietà start ed end  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Per ridimensionare un segnalibro in un progetto a livello di documento in fase di progettazione  
  
1.  Selezionare il segnalibro nella finestra **Proprietà** .  
  
2.  Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .  
  
3.  Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .  
  
### <a name="to-resize-a-bookmark-in-a-document-level-project-at-runtime"></a>Per ridimensionare un segnalibro in un progetto a livello di documento in fase di esecuzione  
  
1.  Modificare il <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> delle proprietà di un <xref:Microsoft.Office.Tools.Word.Bookmark> è stato creato in fase di esecuzione o in fase di progettazione.  
  
     L'esempio di codice seguente aggiunge cinque caratteri all'inizio di un segnalibro denominato `SampleBookmark`. In questo codice si presuppone che prima del segnalibro siano presenti almeno cinque caratteri di testo.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#2)]
     [!code-vb[Trin_VstcoreHostControlsWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#2)]  
  
     L'esempio di codice seguente aggiunge cinque caratteri alla fine dello stesso segnalibro. In questo codice si presuppone che dopo il segnalibro siano presenti almeno cinque caratteri di testo.  
  
     [!code-csharp[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb#3)]  
  
### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-runtime"></a>Per ridimensionare un segnalibro in un progetto di componente aggiuntivo VSTO in fase di esecuzione  
  
1.  Modificare il <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> delle proprietà di un <xref:Microsoft.Office.Tools.Word.Bookmark> creato in fase di esecuzione.  
  
     L'esempio di codice seguente crea un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> che contiene il testo del primo paragrafo del documento attivo, quindi rimuove cinque caratteri dall'inizio e dalla fine dell'oggetto <xref:Microsoft.Office.Tools.Word.Bookmark>.  
  
     [!code-vb[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb#16)]
     [!code-csharp[Trin_WordAddInDynamicControls#16](../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs#16)]  
  
## <a name="recreate-the-bookmark"></a>Ricreare il segnalibro  
 È possibile ridimensionare un segnalibro in un progetto a livello di documento aggiungendo un nuovo segnalibro con lo stesso nome del segnalibro esistente, ma le cui dimensioni sono diverse.  
  
### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Per ricreare un segnalibro in un progetto a livello di documento in fase di progettazione  
  
1.  Selezionare il testo da includere nel nuovo controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .  
  
2.  Scegliere **Segnalibro** dal menu **Inserisci**.  
  
3.  Nella finestra di dialogo **Segnalibro** selezionare il nome del segnalibro da ridimensionare e scegliere **Aggiungi**.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: aggiungere controlli segnalibro ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Cenni preliminari sui controlli host e gli elementi host](../vsto/host-items-and-host-controls-overview.md)   
 [Procedura: ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)   
 [Procedura: ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)   
 [Limitazioni a livello di codice degli elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  