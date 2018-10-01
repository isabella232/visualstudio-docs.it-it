---
title: 'Procedura dettagliata: Creazione di un glifo del margine | Microsoft Docs'
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
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 83b721c7b0ac33d9a37d9705cd780edcd591d9aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527235"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Procedura dettagliata: creazione di un glifo di margine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura dettagliata: creazione di un glifo del margine](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-creating-a-margin-glyph).  
  
È possibile personalizzare l'aspetto dei margini dell'editor tramite le estensioni dell'editor personalizzato. Questa procedura dettagliata inserisce un'icona personalizzata sul margine indicatore ogni volta che viene visualizzata la parola "todo" in un commento del codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1.  Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Denominare la soluzione `TodoGlyphTest`.  
  
2.  Aggiungere un elemento di progetto di classificatore Editor. Per altre informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## <a name="defining-the-glyph"></a>Definire il glifo  
 Definire un glifo implementando il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaccia.  
  
#### <a name="to-define-the-glyph"></a>Per definire il glifo  
  
1.  Aggiungere un file di classe e denominarla `TodoGlyphFactory`.  
  
2.  Aggiungere quanto segue usando dichiarazioni.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3.  Aggiungere una classe denominata `TodoGlyphFactory` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4.  Aggiungere un campo privato che definisce le dimensioni dell'icona.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5.  Implementare `GenerateGlyph` definendo l'elemento dell'interfaccia utente di glifo. `TodoTag` è definito più avanti in questa procedura dettagliata.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6.  Aggiungere una classe denominata `TodoGlyphFactoryProvider` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Esportare questa classe con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "TodoGlyph", un' <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di dopo VsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodo creando il `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definizione di un Tag di Todo e Tagger  
 Creazione di un tipo di tag e un tagger ed esportandolo usando un provider di tagger, definire la relazione tra l'elemento dell'interfaccia utente che è definito nei passaggi precedenti e il margine indicatore.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Per definire un tag di todo e un tagger  
  
1.  Aggiungere un nuovo file di classe al progetto e denominarlo `TodoTagger`.  
  
2.  Aggiungere le istruzioni import seguenti.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3.  Aggiungere una classe denominata `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4.  Modificare la classe denominata `TodoTagger` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5.  Per il `TodoTagger` (classe), aggiungere campi privati per una <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> e per il testo da trovare nella classificazione si estende.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6.  Aggiungere un costruttore che imposta la funzione di classificazione.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo trovando tutti la classificazione si estende i cui nomi includono la parola "commenti" e il cui testo include il testo di ricerca. Ogni volta che viene trovato il testo di ricerca, produrre un nuovo nuovamente <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> di tipo `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8.  Dichiarare un `TagsChanged` evento.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Aggiungere una classe denominata `TodoTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importazione di <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodo creando il `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirlo nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Per compilare e testare la soluzione TodoGlyphTest  
  
1.  Compilare la soluzione.  
  
2.  Eseguire il progetto premendo F5. Viene creata un'istanza di una seconda istanza di Visual Studio.  
  
3.  Assicurarsi che venga visualizzato il margine indicatore. (Nel **degli strumenti** menu, fare clic su **opzioni**. Scegliere il **Editor di testo** pagina, assicurarsi che **margine indicatore** sia selezionata.)  
  
4.  Aprire un file di codice con commenti. Aggiungere la parola "todo" a una delle sezioni commento.  
  
5.  Margine indicatore a sinistra della finestra del codice dovrebbe essere visualizzato un cerchio blu chiaro che presenta un contorno blu scuro.

