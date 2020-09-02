---
title: 'Procedura dettagliata: visualizzazione di parentesi graffe corrispondenti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165784"
---
# <a name="walkthrough-displaying-matching-braces"></a>Procedura dettagliata: visualizzazione della corrispondenza parentesi graffe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile implementare funzionalità basate su linguaggio, ad esempio la corrispondenza tra parentesi graffe, definendo le parentesi graffe di cui si desidera trovare la corrispondenza, quindi aggiungendo un tag del marcatore di testo alle parentesi graffe corrispondenti quando il punto di inserimento si trova su una delle parentesi graffe. È possibile definire parentesi graffe nel contesto di una lingua oppure è possibile definire l'estensione del nome di file e il tipo di contenuto e applicare i tag solo a tale tipo oppure è possibile applicare i tag a un tipo di contenuto esistente, ad esempio "Text". Nella procedura dettagliata seguente viene illustrato come applicare tag di corrispondenza tra parentesi graffe al tipo di contenuto "Text".  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Per creare un progetto MEF  
  
1. Creare un progetto di classificatore editor. Assegnare alla soluzione il nome `BraceMatchingTest`.  
  
2. Aggiungere un modello di elemento classificatore editor al progetto. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Implementazione di un tag di corrispondenza tra parentesi graffe  
 Per ottenere un effetto di evidenziazione delle parentesi graffe simile a quello usato in Visual Studio, è possibile implementare un tag di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . Il codice seguente illustra come definire il tag per le coppie di parentesi graffe a qualsiasi livello di annidamento. In questo esempio, le coppie di parentesi graffe []. [] e {} sono definiti nel costruttore del tag, ma in un'implementazione di linguaggio completo le coppie di parentesi graffe pertinenti verranno definite nella specifica del linguaggio.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Per implementare un tag di corrispondenza tra parentesi graffe  
  
1. Aggiungere un file di classe e denominarlo corrispondenza parentesi graffe.  
  
2. Importare gli spazi dei nomi seguenti.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Definire una classe `BraceMatchingTagger` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Aggiungere le proprietà per la visualizzazione di testo, il buffer di origine e il punto dello snapshot corrente e anche un set di coppie di parentesi graffe.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. Nel costruttore del tag, impostare le proprietà e sottoscrivere gli eventi di modifica della vista <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . In questo esempio, a scopo illustrativo, le coppie corrispondenti sono definite anche nel costruttore.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. Come parte dell' <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementazione, dichiarare un evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. I gestori eventi aggiornano la posizione corrente del punto di inserimento della `CurrentChar` proprietà e generano l'evento TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo in modo che corrisponda alle parentesi graffe quando il carattere corrente è una parentesi graffa aperta o quando il carattere precedente è una parentesi graffa di chiusura, come in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa di apertura e uno per la parentesi graffa di chiusura.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. I metodi privati seguenti trovano la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo trova il carattere di chiusura che corrisponde al carattere aperto:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Il metodo helper seguente trova il carattere aperto che corrisponde a un carattere di chiusura:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Implementazione di un provider di tag per la corrispondenza tra parentesi graffe  
 Oltre a implementare un tag, è necessario implementare ed esportare anche un provider di tag. In questo caso, il tipo di contenuto del provider è "Text". Ciò significa che la corrispondenza tra parentesi graffe verrà visualizzata in tutti i tipi di file di testo, ma un'implementazione più completa applicherà la corrispondenza tra parentesi graffe solo per un tipo di contenuto specifico.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Per implementare un provider di tag per la corrispondenza tra parentesi graffe  
  
1. Dichiarare un provider di tag che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , denominarlo BraceMatchingTaggerProvider ed esportarlo con un valore <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "Text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodo per creare un'istanza di BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirla nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Per compilare e testare la soluzione BraceMatchingTest  
  
1. Compilare la soluzione.  
  
2. Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3. Creare un file di testo e digitare il testo che include le parentesi graffe corrispondenti.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Quando si posiziona il punto di inserimento prima di una parentesi graffa aperta, è necessario evidenziare sia la parentesi graffa che la parentesi graffa di chiusura corrispondente. Quando si posiziona il cursore immediatamente dopo la parentesi graffa di chiusura, è necessario evidenziare sia la parentesi graffa che la parentesi graffa aperta corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di file](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
