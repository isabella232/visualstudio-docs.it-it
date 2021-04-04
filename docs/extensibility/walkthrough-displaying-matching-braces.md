---
title: 'Procedura dettagliata: visualizzazione di parentesi graffe corrispondenti | Microsoft Docs'
description: Informazioni su come definire le parentesi graffe nel contesto di una lingua, applicando i tag corrispondenti alle parentesi graffe al tipo di contenuto text usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e4565e095c6bd8fe26f0bb72bd66d6df935ff16b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217268"
---
# <a name="walkthrough-display-matching-braces"></a>Procedura dettagliata: visualizzare le parentesi graffe corrispondenti
Implementare le funzionalità basate sul linguaggio, ad esempio la corrispondenza tra parentesi graffe definendo le parentesi graffe che si vuole trovare e aggiungere un tag del marcatore di testo alle parentesi graffe corrispondenti quando il cursore si trova su una delle parentesi graffe. È possibile definire parentesi graffe nel contesto di una lingua, definire l'estensione del nome di file e il tipo di contenuto e applicare i tag solo a tale tipo o applicare i tag a un tipo di contenuto esistente, ad esempio "Text". Nella procedura dettagliata seguente viene illustrato come applicare tag di corrispondenza tra parentesi graffe al tipo di contenuto "Text".

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto di Managed Extensibility Framework (MEF)

#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF

1. Creare un progetto di classificatore editor. Assegnare alla soluzione il nome `BraceMatchingTest`.

2. Aggiungere un modello di elemento classificatore editor al progetto. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="implement-a-brace-matching-tagger"></a>Implementare un tag di corrispondenza tra parentesi graffe
 Per ottenere un effetto di evidenziazione delle parentesi graffe simile a quello usato in Visual Studio, è possibile implementare un tag di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Il codice seguente illustra come definire il tag per le coppie di parentesi graffe a qualsiasi livello di annidamento. In questo esempio, le coppie di parentesi graffe di [] e {} sono definite nel costruttore del tag, ma in un'implementazione del linguaggio completo le coppie di parentesi graffe pertinenti verranno definite nella specifica del linguaggio.

### <a name="to-implement-a-brace-matching-tagger"></a>Per implementare un tag di corrispondenza tra parentesi graffe

1. Aggiungere un file di classe e denominarlo corrispondenza parentesi graffe.

2. Importare gli spazi dei nomi seguenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet1":::

3. Definire una classe `BraceMatchingTagger` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet2":::

4. Aggiungere proprietà per la visualizzazione di testo, il buffer di origine, il punto dello snapshot corrente e anche un set di coppie di parentesi graffe.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet3":::

5. Nel costruttore del tag, impostare le proprietà e sottoscrivere gli eventi di modifica della vista <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . In questo esempio, a scopo illustrativo, le coppie corrispondenti sono definite anche nel costruttore.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet4":::

6. Come parte dell' <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementazione, dichiarare un evento TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet5":::

7. I gestori eventi aggiornano la posizione corrente del punto di inserimento della `CurrentChar` proprietà e generano l'evento TagsChanged.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet6":::

8. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo in modo che corrisponda alle parentesi graffe quando il carattere corrente è una parentesi graffa aperta o quando il carattere precedente è una parentesi graffa di chiusura, come in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa di apertura e uno per la parentesi graffa di chiusura.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet7":::

9. I metodi privati seguenti trovano la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo trova il carattere di chiusura che corrisponde al carattere aperto:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet8":::

10. Il metodo helper seguente trova il carattere aperto che corrisponde a un carattere di chiusura:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet9":::

## <a name="implement-a-brace-matching-tagger-provider"></a>Implementare un provider di tag per la corrispondenza tra parentesi graffe
 Oltre a implementare un tag, è necessario implementare ed esportare anche un provider di tag. In questo caso, il tipo di contenuto del provider è "Text". Quindi, la corrispondenza tra parentesi graffe verrà visualizzata in tutti i tipi di file di testo, ma un'implementazione più completa applica la corrispondenza delle parentesi graffe solo a un tipo di contenuto specifico.

### <a name="to-implement-a-brace-matching-tagger-provider"></a>Per implementare un provider di tag per la corrispondenza tra parentesi graffe

1. Dichiarare un provider di tag che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , denominarlo BraceMatchingTaggerProvider ed esportarlo con un valore <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet10":::

2. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodo per creare un'istanza di BraceMatchingTagger.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb" id="Snippet11":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirla nell'istanza sperimentale.

#### <a name="to-build-and-test-bracematchingtest-solution"></a>Per compilare e testare la soluzione BraceMatchingTest

1. Compilare la soluzione.

2. Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

3. Creare un file di testo e digitare il testo che include le parentesi graffe corrispondenti.

    ```
    hello {
    goodbye}

    {}

    {hello}
    ```

4. Quando si posiziona il punto di inserimento prima di una parentesi graffa aperta, è necessario evidenziare sia la parentesi graffa che la parentesi graffa di chiusura corrispondente. Quando si posiziona il cursore immediatamente dopo la parentesi graffa di chiusura, è necessario evidenziare sia la parentesi graffa che la parentesi graffa aperta corrispondente.

## <a name="see-also"></a>Vedi anche
- [Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
