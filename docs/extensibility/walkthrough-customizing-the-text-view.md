---
title: 'Procedura dettagliata: personalizzazione della visualizzazione di testo Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697460"
---
# <a name="walkthrough-customize-the-text-view"></a>Procedura dettagliata: Personalizzare la visualizzazione di testoWalkthrough: Customize the text view
È possibile personalizzare una visualizzazione di testo modificando una delle seguenti proprietà nella relativa mappa in formato editor:

- Margine indicatore

- Punto di inserimento

- Sovrascrivere il punsicone

- Testo selezionato

- Testo selezionato inattivo (ovvero, testo selezionato che ha perso lo stato attivo)

- Spazio vuoto visibile

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `ViewPropertyTest`la soluzione .

2. Aggiungere un modello di elemento Classificatore editor al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="define-the-content-type"></a>Definire il tipo di contenuto

1. Aggiungere un file di classe e assegnargli il nome `ViewPropertyModifier`.

2. Aggiungere le direttive `using` seguenti:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Dichiarare una `TestViewCreationListener` classe denominata <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>che eredita da . Esportare questa classe con i seguenti attributi:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>per specificare il tipo di contenuto a cui si applica questo listener.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>per specificare il ruolo di questo listener.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. In questa classe <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>importare il file .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Modificare le proprietà della vista

1. Impostare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> il metodo in modo che le proprietà della vista vengano modificate all'apertura della vista. Per apportare la modifica, individuare innanzitutto l'oggetto <xref:System.Windows.ResourceDictionary> che corrisponde all'aspetto della visualizzazione che si desidera trovare. Quindi, modificare la proprietà appropriata nel dizionario risorse e impostare le proprietà. Eseguire in batch <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> le chiamate <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> al metodo chiamando il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> metodo prima di impostare le proprietà e quindi dopo aver impostato le proprietà.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code

1. Compilare la soluzione.

     Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

2. Creare un file di testo e digitare alcune parole.

    - Il punto di inserimento deve essere magenta e il punto di inserimento di sovrascrittura deve essere turchese.

    - Il margine dell'indicatore (a sinistra della visualizzazione di testo) deve essere verde chiaro.

3. Selezionare il testo digitato. Il colore del testo selezionato deve essere rosa chiaro.

4. Mentre il testo è selezionato, fate clic in un punto qualsiasi all'esterno della finestra di testo. Il colore del testo selezionato deve essere di colore rosa scuro.

5. Attivare gli spazi vuoti visibili. Scegliere **Avanzate** dal menu **Modifica,** quindi fare clic su **Visualizza spazio vuoto**. Digitare alcune tabulazioni nel testo. Devono essere visualizzate le frecce rosse che rappresentano le schede.

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
