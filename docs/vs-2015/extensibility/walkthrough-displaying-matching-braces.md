---
title: 'Procedura dettagliata: Visualizzazione della corrispondenza parentesi graffe | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 11021dc98acfd80f1e91443cc834eb4ae0126455
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517765"
---
# <a name="walkthrough-displaying-matching-braces"></a>Procedura dettagliata: visualizzazione della corrispondenza parentesi graffe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: visualizzazione delle parentesi graffe corrispondenti](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-displaying-matching-braces).  
  
È possibile implementare funzionalità basate sul linguaggio, come corrispondenza che definisce le parentesi graffe che si desidera trovare una corrispondenza, e quindi aggiungendo un tag del marcatore di testo per le parentesi graffe corrispondenti quando il cursore si trova su una delle parentesi graffe tra parentesi graffe. È possibile definire le parentesi graffe nel contesto di un linguaggio, è possibile definire il tipo di contenuto e l'estensione di nome file e applicare i tag per solo tale tipo o è possibile applicare i tag per un tipo di contenuto esistente (ad esempio "text"). Procedura dettagliata illustra come applicare i tag per il tipo di contenuto "text" corrispondenza tra parentesi graffe.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1.  Creare un progetto di classificatore editor. Denominare la soluzione `BraceMatchingTest`.  
  
2.  Aggiungere un modello di elemento di classificatore Editor al progetto. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementare una Tagger di corrispondenza parentesi graffe  
 Per ottenere un'effetto simile a quello usato in Visual Studio di evidenziazione parentesi graffe, è possibile implementare un tagger del tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Il codice seguente viene illustrato come definire il tagger per coppie di parentesi graffe a qualsiasi livello di annidamento. In questo esempio, la parentesi graffa coppie []. [], e {} definiti nel costruttore tagger, ma in un'implementazione del linguaggio completa le coppie di parentesi graffa rilevanti deve essere definite nella specifica del linguaggio.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Per implementare una tagger di corrispondenza parentesi graffe  
  
1.  Aggiungere un file di classe e denominarla corrispondenza parentesi graffe.  
  
2.  Importare gli spazi dei nomi seguenti.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3.  Definire una classe `BraceMatchingTagger` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4.  Aggiungere le proprietà per la visualizzazione di testo, il buffer di origine e il punto dello snapshot corrente e anche un set di coppie di parentesi graffe.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5.  Nel costruttore del tagger, impostare le proprietà e sottoscrivere gli eventi di modifica visualizzazione <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In questo esempio, a scopo illustrativo, le coppie corrispondente vengono definite anche nel costruttore.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6.  Come parte di <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementazione, dichiarare un evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7.  I gestori eventi aggiornano la posizione corrente del cursore del `CurrentChar` proprietà e generare l'evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo per la corrispondenza delle parentesi graffe di uno quando il carattere corrente è una parentesi graffa aperta o se il carattere precedente è una parentesi graffa di chiusura, come in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa aperta e uno per la parentesi graffa di chiusura.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. I seguenti metodi privati trovare la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo consente di trovare il carattere di chiuso che corrisponde al carattere aperto:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Il metodo helper seguente consente di trovare il carattere aperto che corrisponde a un carattere di chiuso:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementazione di una Provider di Tagger di corrispondenza parentesi graffe  
 Oltre a implementare un tagger, è inoltre necessario implementare ed esportare un provider di tagger. In questo caso, il tipo di contenuto del provider è "text". Ciò significa che corrispondenza delle parentesi graffe verrà visualizzati tutti i tipi di file di testo, ma un'implementazione più completa è applicabile solo a un tipo di contenuto specifico corrispondenza parentesi graffe.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Implementare un provider di tagger parentesi graffa corrispondente  
  
1.  Dichiarare un provider di tagger che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, denominarlo BraceMatchingTaggerProvider ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> impostato su "text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodo per creare un'istanza di un BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Per compilare e testare soluzioni BraceMatchingTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include parentesi graffe corrispondenti.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Quando si posiziona il cursore prima di una parentesi graffa aperta, sia la parentesi graffa e la parentesi graffa di chiusura corrispondente dovrebbe essere evidenziata. Quando si posiziona il cursore subito dopo la parentesi graffa di chiusura, sia la parentesi graffa e la parentesi graffa di apertura corrisponda dovrebbe essere evidenziata.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

