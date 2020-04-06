---
title: 'Procedura dettagliata: visualizzazione di parentesi graffe corrispondenti Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 107610733ab9b5c8085b3f987fa999250b453d63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697447"
---
# <a name="walkthrough-display-matching-braces"></a>Procedura dettagliata: Visualizzazione di parentesi graffe corrispondentiWalkthrough: Display matching braces
Implementare funzionalità basate sul linguaggio, ad esempio la corrispondenza tra parentesi graffe definendo le parentesi graffe che si desidera associare e aggiungendo un tag del marcatore di testo alle parentesi graffe corrispondenti quando il punto di inserimento si trova su una delle parentesi graffe. È possibile definire le parentesi graffe nel contesto di un linguaggio, definire la propria estensione di file e il tipo di contenuto e applicare i tag solo a quel tipo o applicare i tag a un tipo di contenuto esistente (ad esempio "testo"). Nella procedura dettagliata seguente viene illustrato come applicare tag corrispondenti tra parentesi graffe al tipo di contenuto "testo".

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto di classificatore editor. Assegnare alla soluzione il nome `BraceMatchingTest`.

2. Aggiungere un modello di elemento Classificatore editor al progetto. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="implement-a-brace-matching-tagger"></a>Implementare un tagger corrispondente alle parentesi graffe
 Per ottenere un effetto di evidenziazione della parentesi graffa simile a quello utilizzato <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>in Visual Studio, è possibile implementare un tagger di tipo . Il codice seguente mostra come definire il tagger per le coppie di parentesi graffe a qualsiasi livello di annidamento. In questo esempio, le coppie di {} parentesi graffe di [] e sono definite nel costruttore tagger, ma in un'implementazione completa del linguaggio, le coppie di parentesi graffe pertinenti verrebbero definite nella specifica del linguaggio.

### <a name="to-implement-a-brace-matching-tagger"></a>Per implementare un tagger corrispondente tra parentesi graffeTo implement a brace matching tagger

1. Aggiungere un file di classe e denominarlo BraceMatching.Add a class file and name it BraceMatching.

2. Importare gli spazi dei nomi seguenti.

     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]

3. Definire una `BraceMatchingTagger` classe che <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> eredita <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>da di tipo .

     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]

4. Aggiungere proprietà per la visualizzazione di testo, il buffer di origine, il punto snapshot corrente e anche un set di coppie di parentesi graffe.

     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]

5. Nel costruttore del tagger impostare le proprietà <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>e sottoscrivere gli eventi di modifica della visualizzazione e . In questo esempio, a scopo illustrativo, le coppie corrispondenti sono definite anche nel costruttore.

     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]

6. Come parte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> dell'implementazione, dichiarare un TagsChanged evento.

     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]

7. I gestori eventi aggiornano la `CurrentChar` posizione corrente del caret della proprietà e generano l'evento TagsChanged.

     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]

8. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> il metodo per trovare la corrispondenza tra parentesi graffe quando il carattere corrente è una parentesi graffa aperta o quando il carattere precedente è una parentesi graffa chiusa, come in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa aperta e uno per la parentesi graffa chiusa.

     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]

9. I metodi privati seguenti trovano la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo trova il carattere di chiusura che corrisponde al carattere aperto:

     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]

10. Il metodo helper seguente trova il carattere aperto che corrisponde a un carattere di chiusura:The following helper method finds the open character that matches a close character:

     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementare un provider di tagger corrispondente alle parentesi graffe
 Oltre a implementare un tagger, è necessario implementare ed esportare un provider di tagger. In questo caso, il tipo di contenuto del provider è "text". Pertanto, la corrispondenza tra parentesi graffe verrà visualizzata in tutti i tipi di file di testo, ma un'implementazione più completa applica la corrispondenza tra parentesi graffe solo a un tipo di contenuto specifico.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Per implementare un provider di tagger corrispondente alle parentesi graffeTo implement a brace matching tagger provider

1. Dichiarare <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>un provider di tagger che eredita da , denominarlo BraceMatchingTaggerProvider ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.

     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]

2. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> il metodo per creare un'istanza di BraceMatchingTagger.Implement the method to instantiate a BraceMatchingTagger.

     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Per compilare e testare la soluzione BraceMatchingTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare del testo che includa le parentesi graffe corrispondenti.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Quando si posiziona il livello di inserimento prima di una parentesi graffa aperta, devono essere evidenziati sia tale parentesi graffa che la parentesi graffa chiusa corrispondente. Quando si posiziona il cursore subito dopo la parentesi graffa chiusa, devono essere evidenziate sia la parentesi graffa che la parentesi graffa aperta corrispondente.

## <a name="see-also"></a>Vedere anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
