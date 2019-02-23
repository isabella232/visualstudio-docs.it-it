---
title: 'Procedura dettagliata: Visualizzazione della corrispondenza parentesi graffe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a137f5ee777785fe3709ace14b5af3385cdaa19
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56682544"
---
# <a name="walkthrough-display-matching-braces"></a>Procedura dettagliata: Visualizzare le parentesi graffe corrispondenti
Implementare funzionalità basata sul linguaggio, ad esempio, parentesi graffa corrispondente definizione di una corrispondenza parentesi graffe e aggiungendo un tag del marcatore di testo per le parentesi graffe corrispondenti quando il cursore si trova su una delle parentesi graffe. È possibile definire le parentesi graffe nel contesto di una lingua, definire il proprio estensione di file e il tipo di contenuto e applicare i tag semplicemente digitare o applicano i tag per un tipo di contenuto esistente (ad esempio "text"). Procedura dettagliata illustra come applicare i tag per il tipo di contenuto "text" corrispondenza tra parentesi graffe.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, Visual Studio SDK è non installare dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1.  Creare un progetto di classificatore editor. Assegnare alla soluzione il nome `BraceMatchingTest`.

2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3.  Eliminare i file di classe esistenti.

## <a name="implement-a-brace-matching-tagger"></a>Implementare una tagger di corrispondenza parentesi graffe
 Per ottenere un'effetto simile a quello usato in Visual Studio di evidenziazione parentesi graffe, è possibile implementare un tagger del tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Il codice seguente viene illustrato come definire il tagger per coppie di parentesi graffe a qualsiasi livello di annidamento. In questo esempio, le coppie di parentesi graffa di [] e {} definiti nel costruttore tagger, ma in un'implementazione completa del linguaggio, la parentesi graffa rilevante coppie deve essere definite nella specifica del linguaggio.

### <a name="to-implement-a-brace-matching-tagger"></a>Per implementare una tagger di corrispondenza parentesi graffe

1.  Aggiungere un file di classe e denominarla corrispondenza parentesi graffe.

2.  Importare gli spazi dei nomi seguenti.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3.  Definire una classe `BraceMatchingTagger` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4.  Aggiungere le proprietà per la visualizzazione di testo, il buffer di origine, il punto dello snapshot corrente e anche un set di coppie di parentesi graffe.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5.  Nel costruttore del tagger, impostare le proprietà e sottoscrivere gli eventi di modifica visualizzazione <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In questo esempio, a scopo illustrativo, le coppie corrispondente vengono definite anche nel costruttore.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6.  Come parte di <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementazione, dichiarare un evento TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7.  I gestori eventi aggiornano la posizione corrente del cursore del `CurrentChar` proprietà e generare l'evento TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo per la corrispondenza delle parentesi graffe di uno quando il carattere corrente è una parentesi graffa aperta o se il carattere precedente è una parentesi graffa di chiusura, come in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa aperta e uno per la parentesi graffa di chiusura.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. I seguenti metodi privati trovare la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo consente di trovare il carattere di chiuso che corrisponde al carattere aperto:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Il metodo helper seguente consente di trovare il carattere aperto che corrisponde a un carattere di chiuso:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementare un provider di tagger parentesi graffa corrispondente
 Oltre a implementare un tagger, è inoltre necessario implementare ed esportare un provider di tagger. In questo caso, il tipo di contenuto del provider è "text". Quindi, corrispondenza parentesi graffe verrà visualizzati tutti i tipi di file di testo, ma un'implementazione più completa si applica solo a un tipo di contenuto specifico corrispondenza parentesi graffe.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Implementare un provider di tagger parentesi graffa corrispondente

1.  Dichiarare un provider di tagger che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, denominarlo BraceMatchingTaggerProvider ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodo per creare un'istanza di un BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirlo nell'istanza sperimentale.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Per compilare e testare soluzioni BraceMatchingTest

1.  Compilare la soluzione.

2.  Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3.  Creare un file di testo e digitare un testo che include parentesi graffe corrispondenti.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4.  Quando si posiziona il cursore prima di una parentesi graffa aperta, sia la parentesi graffa e la parentesi graffa di chiusura corrispondente dovrebbe essere evidenziata. Quando si posiziona il cursore subito dopo la parentesi graffa di chiusura, sia la parentesi graffa e la parentesi graffa di apertura corrisponda dovrebbe essere evidenziata.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)