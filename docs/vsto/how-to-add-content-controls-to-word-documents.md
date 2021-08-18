---
title: 'Procedura: Aggiungere controlli contenuto ai documenti di Word'
description: Si apprenderà che nei progetti Word a livello di documento è possibile aggiungere controlli contenuto al documento nel progetto in fase di progettazione o di esecuzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- DropDownListContentControl, adding to documents
- BuildingBlockGalleryContentControl, adding to documents
- partial document protection [Office development in Visual Studio]
- RichTextContentControl, adding to documents
- Word [Office development in Visual Studio], partial document protection
- content controls [Office development in Visual Studio], protecting
- PictureContentControl, adding to documents
- GroupContentControl, adding to documents
- document protection [Office development in Visual Studio]
- PlainTextContentControl, adding to documents
- content controls [Office development in Visual Studio], adding
- ComboBoxContentControl, adding to documents
- DatePickerContentControl, adding to documents
- Word [Office development in Visual Studio], restricted permissions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: a9df9bebf1ff731b20f4a5673b3450e5ccc0c10a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122100205"
---
# <a name="how-to-add-content-controls-to-word-documents"></a>Procedura: Aggiungere controlli contenuto ai documenti di Word
  Nei progetti di Word a livello di documento è possibile aggiungere controlli contenuto al documento nel progetto in fase di progettazione o di esecuzione. Nei progetti di componente aggiuntivo VSTO di Word è possibile aggiungere controlli contenuto a qualsiasi documento aperto in fase di esecuzione.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Questo argomento descrive le attività seguenti:

- [Aggiungere controlli contenuto in fase di progettazione](#designtime)

- [Aggiungere controlli contenuto in fase di esecuzione in un progetto a livello di documento](#runtimedoclevel)

- [Aggiungere controlli contenuto in fase di esecuzione in un VSTO di componente aggiuntivo](#runtimeaddin)

  Per informazioni sui controlli contenuto, vedere [Controlli contenuto](../vsto/content-controls.md).

## <a name="add-content-controls-at-design-time"></a><a name="designtime"></a> Aggiungere controlli contenuto in fase di progettazione
 Sono disponibili varie modalità di aggiunta di controlli contenuto al documento in un progetto a livello di documento in fase di progettazione:

- Aggiungere un controllo contenuto dalla scheda **Controlli Word** della **Casella degli strumenti**.

- Aggiungere un controllo contenuto al documento nello stesso modo in cui si aggiunge un controllo contenuto nativo in Word.

- Trascinare un controllo contenuto nel documento dalla finestra **Origini dati** . Questa modalità è utile quando si vuole associare il controllo ai dati al momento della creazione del controllo. Per altre informazioni, vedere [Procedura: Popolare](../vsto/how-to-populate-documents-with-data-from-objects.md) documenti con dati da oggetti e [Procedura: Popolare](../vsto/how-to-populate-documents-with-data-from-a-database.md)documenti con dati da un database .

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-content-control-to-a-document-by-using-the-toolbox"></a>Per aggiungere un controllo contenuto a un documento tramite la casella degli strumenti

1. Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il controllo contenuto o selezionare il testo che deve essere sostituito dal controllo contenuto.

2. Aprire la **Casella degli strumenti** e fare clic sulla scheda **Controlli Word** .

3. Aggiungere il controllo in uno dei modi seguenti:

    - Fare doppio clic su un controllo contenuto nella **Casella degli strumenti**.

         oppure

    - Fare clic su un controllo contenuto **nella casella degli strumenti** e quindi premere INVIO. 

         oppure

    - Trascinare un controllo contenuto dalla **Casella degli strumenti** nel documento. Il controllo contenuto viene aggiunto in corrispondenza della selezione corrente nel documento, non in corrispondenza della posizione del puntatore del mouse.

> [!NOTE]
> Non è possibile aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> usando la **Casella degli strumenti**. È possibile aggiungere un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> solo in Word o in fase di esecuzione.

> [!NOTE]
> Visual Studio non fornisce un controllo contenuto casella di controllo nella casella degli strumenti. Per aggiungere un controllo contenuto casella di controllo al documento, è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> a livello di codice. Per altre informazioni, vedere [Controlli contenuto](../vsto/content-controls.md).

#### <a name="to-add-a-content-control-to-a-document-in-word"></a>Per aggiungere un controllo contenuto a un documento in Word

1. Nel documento ospitato nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] posizionare il cursore dove si vuole aggiungere il controllo contenuto o selezionare il testo che deve essere sostituito dal controllo contenuto.

2. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

3. Nel gruppo **Controlli** fare clic sull'icona del controllo contenuto che si desidera aggiungere.

## <a name="add-content-controls-at-run-time-in-a-document-level-project"></a><a name="runtimedoclevel"></a> Aggiungere controlli contenuto in fase di esecuzione in un progetto a livello di documento
 È possibile aggiungere controlli contenuto a livello di codice al documento in fase di esecuzione usando i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> della classe `ThisDocument` nel progetto. Ogni metodo ha tre overload che è possibile usare per aggiungere un controllo contenuto nei modi seguenti:

- Aggiungere un controllo in corrispondenza della selezione corrente.

- Aggiungere un controllo in corrispondenza di un intervallo specificato.

- Aggiungere un controllo basato su un controllo contenuto nativo nel documento.

  I controlli contenuto creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un controllo contenuto nativo rimane nel documento. È possibile ricreare un controllo contenuto basato su un controllo contenuto nativo alla successiva apertura del documento. Per altre informazioni, vedere [Aggiungere controlli Office documenti in fase di esecuzione.](../vsto/adding-controls-to-office-documents-at-run-time.md)

> [!NOTE]
> Per aggiungere un controllo contenuto casella di controllo a un documento in un progetto di Word 2010, è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> . Per altre informazioni, vedere [Controlli contenuto](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Per aggiungere un controllo contenuto in corrispondenza della selezione corrente

1. Usare un metodo con il nome (dove classe di controllo è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio ) e che dispone di un singolo parametro per il nome del <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> nuovo  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> controllo.

     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddRichTextControlAtSelection` dal gestore eventi `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet700":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet700":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Per aggiungere un controllo contenuto in corrispondenza di un intervallo specificato

1. Usare un metodo con il nome (dove classe di controllo è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio ), e che <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> dispone di un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parametro <xref:Microsoft.Office.Interop.Word.Range> .

     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddRichTextControlAtRange` dal gestore eventi `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet701":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet701":::

### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Per aggiungere un controllo contenuto basato su un controllo contenuto nativo

1. Usare un metodo con il nome (dove classe di controllo è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio ), e che <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> dispone di un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parametro `Microsoft.Office.Interop.Word.ContentControl` .

     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per creare un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> per ogni controllo in formato RTF nativo nel documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `CreateRichTextControlsFromNativeControls` dal gestore eventi `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/RichText.cs" id="Snippet702":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/RichText.vb" id="Snippet702":::

## <a name="add-content-controls-at-run-time-in-a-vsto-add-in-project"></a><a name="runtimeaddin"></a>Aggiungere controlli contenuto in fase di esecuzione in un progetto VSTO componente aggiuntivo
 È possibile aggiungere controlli contenuto a livello di codice a qualsiasi documento aperto in fase di esecuzione usando un componente aggiuntivo VSTO. A tale scopo, generare un elemento host <xref:Microsoft.Office.Tools.Word.Document> basato su un documento aperto e quindi usare i metodi della proprietà <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> di tale elemento host. Ogni metodo ha tre overload che è possibile usare per aggiungere un controllo contenuto nei modi seguenti:

- Aggiungere un controllo in corrispondenza della selezione corrente.

- Aggiungere un controllo in corrispondenza di un intervallo specificato.

- Aggiungere un controllo basato su un controllo contenuto nativo nel documento.

  I controlli contenuto creati dinamicamente non vengono salvati in modo permanente nel documento quando questo viene chiuso. Tuttavia, un controllo contenuto nativo rimane nel documento. È possibile ricreare un controllo contenuto basato su un controllo contenuto nativo alla successiva apertura del documento. Per altre informazioni, vedere [Rendere persistenti i controlli dinamici nei Office documenti.](../vsto/persisting-dynamic-controls-in-office-documents.md)

  Per altre informazioni sulla generazione di elementi host nei progetti di componente aggiuntivo VSTO, vedere Estendere documenti di Word e cartelle di lavoro Excel in VSTO componenti aggiuntivi in fase di [esecuzione.](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)

> [!NOTE]
> Per aggiungere un controllo contenuto casella di controllo a un documento è necessario creare un oggetto <xref:Microsoft.Office.Tools.Word.ContentControl> . Per altre informazioni, vedere [Controlli contenuto](../vsto/content-controls.md).

### <a name="to-add-a-content-control-at-the-current-selection"></a>Per aggiungere un controllo contenuto in corrispondenza della selezione corrente

1. Usare un metodo con il nome (dove classe di controllo è il nome della classe del controllo contenuto che si desidera aggiungere, ad esempio ) e che dispone di un singolo parametro per il nome del <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> nuovo  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> controllo.

     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento attivo. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddRichTextControlAtSelection` dal gestore eventi `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet1":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet1":::

### <a name="to-add-a-content-control-at-a-specified-range"></a>Per aggiungere un controllo contenuto in corrispondenza di un intervallo specificato

1. Usare un metodo con il nome (dove classe di controllo è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio ), e che <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> dispone di un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parametro <xref:Microsoft.Office.Interop.Word.Range> .

     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per aggiungere un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> all'inizio del documento attivo. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddRichTextControlAtRange` dal gestore eventi `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet2":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet2":::

#### <a name="to-add-a-content-control-that-is-based-on-a-native-content-control"></a>Per aggiungere un controllo contenuto basato su un controllo contenuto nativo

1. Usare un metodo con il nome (dove classe di controllo è il nome della classe del controllo contenuto che si vuole aggiungere, ad esempio ), e che <xref:Microsoft.Office.Tools.Word.ControlCollection> `Add` \<*control class*> dispone di un  <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> parametro `Microsoft.Office.Interop.Word.ContentControl` .

     L'esempio di codice seguente usa il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddRichTextContentControl%2A> per creare un nuovo oggetto <xref:Microsoft.Office.Tools.Word.RichTextContentControl> per ogni controllo in formato RTF nativo in un documento, dopo l'apertura del documento. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet3":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet3":::

     Per C#, è anche necessario collegare il gestore eventi `Application_DocumentOpen` all'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet6":::

## <a name="see-also"></a>Vedi anche
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Aggiungere controlli per Office documenti in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Componenti VSTO programma](../vsto/programming-vsto-add-ins.md)
- [Programmare personalizzazioni a livello di documento](../vsto/programming-document-level-customizations.md)
