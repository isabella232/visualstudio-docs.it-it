---
title: 'Procedura dettagliata: Visualizzazione delle parentesi graffe corrispondenti | Microsoft Docs'
description: Informazioni su come definire le parentesi graffe nel contesto di un linguaggio, applicando tag corrispondenti alle parentesi graffe al tipo di contenuto di testo usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dacf3ffff56580e445f2eeda851d30082ba90f45
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628841"
---
# <a name="walkthrough-display-matching-braces"></a>Procedura dettagliata: Visualizzare le parentesi graffe corrispondenti
Implementare funzionalità basate sul linguaggio, ad esempio la corrispondenza delle parentesi graffe definendo le parentesi graffe di cui si vuole trovare la corrispondenza e aggiungendo un tag indicatore di testo alle parentesi graffe corrispondenti quando il punto di inserimento si trova su una delle parentesi graffe. È possibile definire le parentesi graffe nel contesto di un linguaggio, definire l'estensione e il tipo di contenuto del nome file e applicare i tag solo a quel tipo o applicare i tag a un tipo di contenuto esistente,ad esempio "text". La procedura dettagliata seguente illustra come applicare tag corrispondenti alle parentesi graffe al tipo di contenuto "text".

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto di classificatore editor. Assegnare alla soluzione il nome `BraceMatchingTest`.

2. Aggiungere un modello di elemento Editor Classifier al progetto. Per altre informazioni, vedere Creare [un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="implement-a-brace-matching-tagger"></a>Implementare un tagger corrispondente alle parentesi graffe
 Per ottenere un effetto di evidenziazione della parentesi graffa simile a quello usato in Visual Studio, è possibile implementare un tagger di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Il codice seguente illustra come definire il tagger per le coppie di parentesi graffe a qualsiasi livello di annidamento. In questo esempio le coppie di parentesi graffe di [] e sono definite nel costruttore del tagger, ma in un'implementazione completa del linguaggio le coppie di parentesi graffe pertinenti vengono definite nella specifica del {} linguaggio.

### <a name="to-implement-a-brace-matching-tagger"></a>Per implementare un tagger corrispondente alle parentesi graffe

1. Aggiungere un file di classe e assegnare al file il nome BraceMatching.

2. Importare gli spazi dei nomi seguenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet1":::

3. Definire una classe `BraceMatchingTagger` che eredita da di tipo <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet2":::

4. Aggiungere proprietà per la visualizzazione testo, il buffer di origine, il punto di snapshot corrente e anche un set di coppie di parentesi graffe.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet3":::

5. Nel costruttore del tagger impostare le proprietà e sottoscrivere gli eventi di modifica della visualizzazione <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . In questo esempio, a scopo illustrativo, anche le coppie corrispondenti vengono definite nel costruttore .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet4":::

6. Come parte <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> dell'implementazione, dichiarare un evento TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet5":::

7. I gestori eventi aggiornano la posizione corrente del cursore della `CurrentChar` proprietà e generano l'evento TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet6":::

8. Implementare il metodo in modo che corrisponda alle parentesi graffe quando il carattere corrente è una parentesi graffa aperta o quando il carattere precedente è una parentesi graffa chiusa, come <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa aperta e uno per la parentesi graffa di chiusura.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet7":::

9. I metodi privati seguenti trovano la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo trova il carattere di chiusura che corrisponde al carattere aperto:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet8":::

10. Il metodo helper seguente trova il carattere aperto che corrisponde a un carattere di chiusura:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet9":::

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementare un provider di tagger corrispondente alle parentesi graffe
 Oltre a implementare un tagger, è necessario implementare ed esportare un provider di tagger. In questo caso, il tipo di contenuto del provider è "text". Pertanto, la corrispondenza delle parentesi graffe verrà visualizzata in tutti i tipi di file di testo, ma un'implementazione più completa applica la corrispondenza delle parentesi graffe solo a un tipo di contenuto specifico.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Per implementare un provider di tagger corrispondente alle parentesi graffe

1. Dichiarare un provider di tagger che eredita da , assegnare al provider il nome BraceMatchingTaggerProvider ed esportarlo con <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "text" e <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> con <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet10":::

2. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodo per creare un'istanza di BraceMatchingTagger.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet11":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Per compilare e testare la soluzione BraceMatchingTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda Visual Studio di .

3. Creare un file di testo e digitare testo che includa parentesi graffe corrispondenti.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Quando si posiziona il cursore prima di una parentesi graffa aperta, sia la parentesi graffa che la parentesi graffa di chiusura corrispondente devono essere evidenziate. Quando si posiziona il cursore subito dopo la parentesi graffa di chiusura, sia la parentesi graffa aperta che la parentesi graffa aperta corrispondente devono essere evidenziate.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
