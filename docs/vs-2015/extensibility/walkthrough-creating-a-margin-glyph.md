---
title: 'Procedura dettagliata: creazione di un glifo del margine | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148851"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Procedura dettagliata: creazione di un glifo di margine
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile personalizzare l'aspetto dei margini dell'editor usando le estensioni dell'editor personalizzate. Questa procedura dettagliata inserisce un glifo personalizzato sul margine dell'indicatore ogni volta che la parola "TODO" viene visualizzata in un commento del codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `TodoGlyphTest` .  
  
2. Aggiungere un elemento di progetto di classificatore editor. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Eliminare i file di classe esistenti.  
  
## <a name="defining-the-glyph"></a>Definizione del glifo  
 Definire un glifo implementando l' <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaccia.  
  
#### <a name="to-define-the-glyph"></a>Per definire il glifo  
  
1. Aggiungere un file di classe e assegnargli il nome `TodoGlyphFactory`.  
  
2. Aggiungere le seguenti dichiarazioni using.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Aggiungere una classe denominata `TodoGlyphFactory` che implementi <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Aggiungere un campo privato che definisce le dimensioni dell'icona.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Implementare `GenerateGlyph` mediante la definizione dell'elemento dell'interfaccia utente del glifo. `TodoTag` viene definito più avanti in questa procedura dettagliata.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Aggiungere una classe denominata `TodoGlyphFactoryProvider` che implementi <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Esportare questa classe con un valore di <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di dopo vsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Metodo creando un'istanza di `TodoGlyphFactory` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Definizione di tag e tag todo  
 Definire la relazione tra l'elemento dell'interfaccia utente definito nei passaggi precedenti e il margine dell'indicatore creando un tipo di tag e un codificatore ed esportandolo usando un provider di tag.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Per definire un tag todo e un codificatore  
  
1. Aggiungere un nuovo file di classe al progetto e denominarlo `TodoTagger` .  
  
2. Aggiungere le importazioni seguenti.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Aggiungere una classe denominata `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Modificare la classe denominata `TodoTagger` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. Alla `TodoTagger` classe, aggiungere campi privati per un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> e per il testo da trovare negli intervalli di classificazione.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Aggiungere un costruttore che imposta il classificatore.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Metodo individuando tutti gli intervalli di classificazione i cui nomi includono la parola "comment" e il cui testo include il testo di ricerca. Ogni volta che viene trovato il testo di ricerca, restituisce un nuovo oggetto <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> di tipo `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Dichiarare un `TagsChanged` evento.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Aggiungere una classe denominata `TodoTaggerProvider` che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ed esporti l'oggetto con un valore <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Importare il <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Metodo creando un'istanza di `TodoTagger` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirla nell'istanza sperimentale.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Per compilare e testare la soluzione TodoGlyphTest  
  
1. Compilare la soluzione.  
  
2. Eseguire il progetto premendo F5. Viene creata un'istanza di una seconda istanza di Visual Studio.  
  
3. Verificare che sia visualizzato il margine indicatore. Scegliere **Opzioni**dal menu **strumenti** . Nella pagina **editor di testo** assicurarsi che sia selezionato **Margin indicatore** .  
  
4. Aprire un file di codice con commenti. Aggiungere la parola "TODO" a una delle sezioni di commento.  
  
5. Un cerchio blu chiaro con un contorno blu scuro dovrebbe essere visualizzato nel margine indicatore a sinistra della finestra del codice.
