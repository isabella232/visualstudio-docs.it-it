---
title: 'Procedura dettagliata: Personalizzazione della visualizzazione di testo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c328925fd558e01138354427a80db7a692753710
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924915"
---
# <a name="walkthrough-customize-the-text-view"></a>Procedura dettagliata: Personalizzare la visualizzazione di testo
È possibile personalizzare una visualizzazione di testo, modificando le proprietà seguenti nella mappa dell'editor-format:  
  
-   Margine indicatore  
  
-   Punto di inserimento  
  
-   Sovrascrittura del punto di inserimento  
  
-   Testo selezionato  
  
-   Testo selezionato inattivo (vale a dire, selezionato testo che ha perso lo stato attivo)  
  
-   Spazio vuoto visibile  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-mef-project"></a>Creare un progetto MEF  
  
1.  Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `ViewPropertyTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="define-the-content-type"></a>Definire il tipo di contenuto  
  
1. Aggiungere un file di classe e assegnargli il nome `ViewPropertyModifier`.  
  
2. Aggiungere il codice seguente `using` direttive:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3. Dichiarare una classe denominata `TestViewCreationListener` che eredita da <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Esportare questa classe con gli attributi seguenti:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Per specificare il tipo di contenuto a cui si applica questo listener.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Per specificare il ruolo di questo listener.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4. In questa classe, importare il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="change-the-view-properties"></a>Modificare le proprietà di visualizzazione  
  
1.  Configurare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che le proprietà della vista vengono modificate quando viene aperta la visualizzazione. Per apportare la modifica, trovare prima il <xref:System.Windows.ResourceDictionary> che corrisponde all'aspetto della visualizzazione da trovare. Quindi, modificare la proprietà appropriata nel dizionario risorse e impostare le proprietà. Batch le chiamate per il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metodo chiamando il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metodo prima di impostare le proprietà e quindi il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> dopo aver impostato le proprietà.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="build-and-test-the-code"></a>Compilare e testare il codice  
  
1.  Compilare la soluzione.  
  
     Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.  
  
2.  Creare un file di testo e digitare alcune parole.  
  
    -   Il punto di inserimento deve essere magenta e il punto di inserimento di sovrascrittura deve essere turchese.  
  
    -   Il margine indicatore (a sinistra della visualizzazione di testo) deve essere luce verde.  
  
3.  Selezionare il testo digitato. Il colore del testo selezionato deve essere chiaro rosa.  
  
4.  Mentre il testo è selezionato, fare clic su un punto qualsiasi all'esterno dell'intervallo di testo. Il colore del testo selezionato deve essere Rosa scuro.  
  
5.  Attivare lo spazio vuoto visibile. (Nelle **Edit** dal menu **avanzate** e quindi fare clic su **Mostra/Nascondi spazi**). Digitare alcune schede nel testo. Le frecce rosse rappresentano le schede devono essere visualizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione del servizio e l'editor di linguaggio](../extensibility/language-service-and-editor-extension-points.md)