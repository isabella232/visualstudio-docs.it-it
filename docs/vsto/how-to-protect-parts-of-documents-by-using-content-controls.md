---
title: 'Procedura: Proteggere parti di documenti usando i controlli contenuto'
description: Informazioni su come usare i Visual Studio per proteggere parti di un Microsoft Word documento usando i controlli contenuto.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- restricted permissions [Office development in Visual Studio]
- partial document protection [Office development in Visual Studio]
- content controls [Office development in Visual Studio], protecting documents
- Word [Office development in Visual Studio], partial document protection
- document protection [Office development in Visual Studio]
- Word [Office development in Visual Studio], restricted permissions
- GroupContentControl
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 49988266ebee5821323ee3a9994312d99033c9f3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633867"
---
# <a name="how-to-protect-parts-of-documents-by-using-content-controls"></a>Procedura: Proteggere parti di documenti usando i controlli contenuto
  Quando si protegge parte di un documento, si impedisce agli utenti di modificare o eliminare il contenuto in quella parte del documento. È possibile proteggere parti di un documento di Microsoft Office Word usando i controlli contenuto in diversi modi.

- È possibile proteggere un controllo del contenuto.

- È possibile proteggere una parte di un documento non presente in un controllo del contenuto.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="protect-a-content-control"></a><a name="EditDeleteControl"></a> Proteggere un controllo contenuto
 È possibile impedire agli utenti di modificare o eliminare un controllo del contenuto impostando le proprietà del controllo in un progetto a livello di documento in fase di progettazione o di esecuzione.

 È anche possibile proteggere i controlli del contenuto aggiunti a un documento in fase di esecuzione con un progetto di componente aggiuntivo VSTO. Per altre informazioni, vedere [Procedura: Aggiungere controlli contenuto ai documenti di Word.](../vsto/how-to-add-content-controls-to-word-documents.md)

### <a name="to-protect-a-content-control-at-design-time"></a>Per proteggere un controllo del contenuto in fase di progettazione

1. Nel documento contenuto nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], selezionare il controllo del contenuto da proteggere.

2. Nella finestra **Proprietà** impostare una o entrambe le proprietà seguenti:

    - Per impedire agli utenti di modificare il controllo, **impostare LockContents** su **True.**

    - Per impedire agli utenti di eliminare il controllo, impostare **LockContentControl** su **True.**

3. Fare clic su **OK**.

### <a name="to-protect-a-content-control-at-run-time"></a>Per proteggere un controllo del contenuto in fase di esecuzione

1. Impostare la proprietà del controllo contenuto su true per impedire agli utenti di modificare il controllo e impostare la proprietà su true per impedire agli utenti `LockContents` di eliminare il  `LockContentControl` controllo. 

     L'esempio di codice seguente illustra l'uso delle proprietà <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> e <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> di due oggetti <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diversi in un progetto a livello di documento. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddProtectedContentControls` dal gestore eventi `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet2":::

     L'esempio di codice seguente illustra l'uso delle proprietà <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> e <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> di due oggetti <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diversi in un progetto di componente aggiuntivo VSTO. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddProtectedContentControls` dal gestore eventi `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet14":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet14":::

## <a name="protect-a-part-of-a-document-that-is-not-in-a-content-control"></a>Proteggere una parte di un documento che non si trova in un controllo contenuto
 È possibile impedire agli utenti di modificare un'area di un documento inserendo l'area in un controllo <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Questa operazione è utile negli scenari seguenti:

- Si vuole proteggere un'area che non contiene i controlli del contenuto.

- Si vuole proteggere un'area che contiene i controlli del contenuto, ma il testo o gli altri elementi da proteggere non sono nei controlli del contenuto.

> [!NOTE]
> Se si crea un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> che include controlli contenuto incorporati, questi non vengono automaticamente protetti. Per impedire agli utenti di modificare un controllo contenuto incorporato, usare la **proprietà LockContents** del controllo.

### <a name="to-protect-an-area-of-a-document-at-design-time"></a>Per proteggere un'area di un documento in fase di progettazione

1. Nel documento contenuto nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], selezionare l'area da proteggere.

2. Sulla barra multifunzione fare clic sulla scheda **Sviluppatore** .

    > [!NOTE]
    > Se la scheda **Sviluppatore** non viene mostrata, è necessario abilitarne la visualizzazione. Per altre informazioni, vedere [Procedura: Visualizzare la scheda Sviluppatore sulla barra multifunzione.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

3. Nel gruppo **Controlli** fare clic sul **pulsante a** discesa Gruppo e quindi su **Gruppo**.

     L'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> contenente l'area protetta viene automaticamente generato nella classe `ThisDocument` del progetto. Un bordo che rappresenta il controllo di gruppo è visibile in fase di progettazione, ma non esiste alcun bordo visibile in fase di esecuzione.

### <a name="to-protect-an-area-of-a-document-at-run-time"></a>Per proteggere un'area di un documento in fase di esecuzione

1. Selezionare a livello di codice l'area da proteggere, quindi chiamare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> per creare un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl>.

     L'esempio di codice seguente per un progetto a livello di documento aggiunge del testo al primo paragrafo del documento, seleziona il primo paragrafo e quindi crea un'istanza di <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `ProtectFirstParagraph` dal gestore eventi `ThisDocument_Startup` .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ContentControlHowToProtect/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ContentControlHowToProtect/ThisDocument.vb" id="Snippet1":::

     L'esempio di codice seguente per un progetto di componente aggiuntivo VSTO aggiunge del testo al primo paragrafo del documento attivo, seleziona il primo paragrafo e quindi crea un'istanza di <xref:Microsoft.Office.Tools.Word.GroupContentControl>. Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `ProtectFirstParagraph` dal gestore eventi `ThisAddIn_Startup` .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddindynamiccontrols/ThisAddIn.vb" id="Snippet15":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_WordAddInDynamicControls/ThisAddIn.cs" id="Snippet15":::

## <a name="see-also"></a>Vedi anche
- [Automatizzare Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)
- [Controlli contenuto](../vsto/content-controls.md)
- [Procedura: Aggiungere controlli contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Panoramica degli elementi host e dei controlli host](../vsto/host-items-and-host-controls-overview.md)
- [Limitazioni a livello di codice di elementi host e controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Aggiungere controlli ai Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)
