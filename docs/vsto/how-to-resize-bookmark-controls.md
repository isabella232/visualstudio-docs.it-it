---
title: 'Procedura: Ridimensionare i controlli Bookmark'
description: Informazioni su come usare Visual Studio per impostare le dimensioni di un controllo Bookmark quando lo si aggiunge a un Microsoft Word documento.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- Bookmark control, resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 34026efaa0a5f9396c5daf3eb6b987435ca9e414
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155720"
---
# <a name="how-to-resize-bookmark-controls"></a>Procedura: Ridimensionare i controlli Bookmark
  Le dimensioni di un controllo <xref:Microsoft.Office.Tools.Word.Bookmark> vengono impostate quando il controllo viene aggiunto a un documento di Microsoft Office Word. È anche possibile ridimensionare tale controllo in un secondo momento.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Il ridimensionamento di un segnalibro può avvenire in tre modi:

- Aggiungere o rimuovere un testo nel controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .

   Ogni volta che si aggiunge del testo in un segnalibro, le dimensioni del segnalibro aumentano automaticamente al fine di contenere il nuovo testo. Quando si elimina il testo, le dimensioni del segnalibro si riducono automaticamente.

- Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> del controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .

   Questa funzionalità è utile se si modificano le dimensioni solo di un numero limitato di caratteri.

- Ricreare il controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .

   Questa funzionalità è utile in caso di una modifica sostanziale delle dimensioni o della posizione di un segnalibro.

  Nei progetti a livello di documento è possibile aggiungere controlli <xref:Microsoft.Office.Tools.Word.Bookmark> al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO è possibile aggiungere i controlli <xref:Microsoft.Office.Tools.Word.Bookmark> a qualsiasi documento aperto in fase di esecuzione. Per altre informazioni, vedere [Procedura: Aggiungere controlli Bookmark ai documenti di Word.](../vsto/how-to-add-bookmark-controls-to-word-documents.md)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="change-the-start-and-end-properties"></a>Modificare le proprietà di inizio e di fine

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-design-time"></a>Per ridimensionare un segnalibro in un progetto a livello di documento in fase di progettazione

1. Selezionare il segnalibro nella finestra **Proprietà** .

2. Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> .

3. Aumentare o ridurre il valore della proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> .

### <a name="to-resize-a-bookmark-in-a-document-level-project-at-run-time"></a>Per ridimensionare un segnalibro in un progetto a livello di documento in fase di esecuzione

1. Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> creato in fase di esecuzione o di progettazione.

     L'esempio di codice seguente aggiunge cinque caratteri all'inizio di un segnalibro denominato `SampleBookmark`. In questo codice si presuppone che prima del segnalibro siano presenti almeno cinque caratteri di testo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet2":::

     L'esempio di codice seguente aggiunge cinque caratteri alla fine dello stesso segnalibro. In questo codice si presuppone che dopo il segnalibro siano presenti almeno cinque caratteri di testo.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorehostcontrolsword/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreHostControlsWordVB/ThisDocument.vb" id="Snippet3":::

### <a name="to-resize-a-bookmark-in-a-vsto-add-in-project-at-run-time"></a>Per ridimensionare un segnalibro in VSTO progetto di componente aggiuntivo in fase di esecuzione

1. Modificare le proprietà <xref:Microsoft.Office.Tools.Word.Bookmark.Start%2A> e <xref:Microsoft.Office.Tools.Word.Bookmark.End%2A> di un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> creato in fase di esecuzione.

     L'esempio di codice seguente crea un oggetto <xref:Microsoft.Office.Tools.Word.Bookmark> che contiene il testo del primo paragrafo del documento attivo, quindi rimuove cinque caratteri dall'inizio e dalla fine dell'oggetto <xref:Microsoft.Office.Tools.Word.Bookmark>.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet16":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet16":::

## <a name="recreate-the-bookmark"></a>Ricreare il segnalibro
 È possibile ridimensionare un segnalibro in un progetto a livello di documento aggiungendo un nuovo segnalibro con lo stesso nome del segnalibro esistente, ma le cui dimensioni sono diverse.

### <a name="to-recreate-a-bookmark-in-a-document-level-project-at-design-time"></a>Per ricreare un segnalibro in un progetto a livello di documento in fase di progettazione

1. Selezionare il testo da includere nel nuovo controllo <xref:Microsoft.Office.Tools.Word.Bookmark> .

2. Scegliere **Segnalibro** dal menu **Inserisci**.

3. Nella finestra di dialogo **Segnalibro** selezionare il nome del segnalibro da ridimensionare e scegliere **Aggiungi**.

## <a name="see-also"></a>Vedi anche
- [Procedura: Aggiungere controlli Bookmark ai documenti di Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Procedura: Ridimensionare i controlli NamedRange](../vsto/how-to-resize-namedrange-controls.md)
- [Procedura: Ridimensionare i controlli ListObject](../vsto/how-to-resize-listobject-controls.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
