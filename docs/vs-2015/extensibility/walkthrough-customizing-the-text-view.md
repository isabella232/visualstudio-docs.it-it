---
title: 'Procedura dettagliata: personalizzazione della visualizzazione di testo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202030"
---
# <a name="walkthrough-customizing-the-text-view"></a>Procedura dettagliata: personalizzazione della visualizzazione di testo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare una visualizzazione di testo modificando una delle proprietà seguenti nella mappa di formato dell'Editor:  
  
- Margine indicatore  
  
- Inserimento cursore  
  
- Sovrascrivi punto di inserimento  
  
- Testo selezionato  
  
- Testo selezionato inattivo (ovvero testo selezionato che ha perso lo stato attivo)  
  
- Spazi vuoti visibili  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `ViewPropertyTest` .  
  
2. Aggiungere un modello di elemento classificatore editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
## <a name="defining-the-content-type"></a>Definizione del tipo di contenuto  
  
1. Aggiungere un file di classe e assegnargli il nome `ViewPropertyModifier`.  
  
2. Aggiungere le direttive `using` seguenti:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Dichiarare una classe denominata `TestViewCreationListener` che eredita da <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Esportare questa classe con gli attributi seguenti:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> per specificare il tipo di contenuto a cui si applica questo listener.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> per specificare il ruolo di questo listener.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. In questa classe importare il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Modifica delle proprietà di visualizzazione  
  
1. Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che le proprietà di visualizzazione vengano modificate quando viene aperta la visualizzazione. Per apportare la modifica, trovare prima di tutto l'oggetto <xref:System.Windows.ResourceDictionary> che corrisponde all'aspetto della visualizzazione che si desidera trovare. Modificare quindi la proprietà appropriata nel dizionario risorse e impostare le proprietà. Eseguire il batch delle chiamate al <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> metodo chiamando il <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> metodo prima di impostare le proprietà e quindi <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> dopo l'impostazione delle proprietà.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
  
1. Compilare la soluzione.  
  
     Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
2. Creare un file di testo e digitare alcune parole.  
  
    - Il cursore di inserimento deve essere magenta e il punto di inserimento della sovrascrittura deve essere turchese.  
  
    - Il margine dell'indicatore (a sinistra della visualizzazione di testo) dovrebbe essere verde chiaro.  
  
3. Selezionare il testo appena digitato. Il colore del testo selezionato dovrebbe essere rosa chiaro.  
  
4. Mentre il testo è selezionato, fare clic in un punto qualsiasi all'esterno della finestra di testo. Il colore del testo selezionato dovrebbe essere rosa scuro.  
  
5. Attivare lo spazio vuoto visibile. Scegliere **Avanzate** dal menu **modifica** , quindi fare clic su **Visualizza spazi vuoti**. Digitare alcune schede nel testo. Verranno visualizzate le frecce rosse che rappresentano le schede.  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
