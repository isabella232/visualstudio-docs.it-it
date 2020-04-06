---
title: 'Procedura dettagliata: creazione di un glifo del margine Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9588b150dd795fc2bc5e6c55d8f6e2359f609939
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697694"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Procedura dettagliata: Creare un glifo di margineWalkthrough: Create a margin glyph
È possibile personalizzare l'aspetto dei margini dell'editor utilizzando le estensioni personalizzate dell'editor. Questa procedura dettagliata inserisce un glifo personalizzato sul margine dell'indicatore ogni volta che la parola "todo" viene visualizzata in un commento di codice.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `TodoGlyphTest`la soluzione .

2. Aggiungere un elemento di progetto Classificatore editor. Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="define-the-glyph"></a>Definire il glifo
 Definire un glifo <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> eseguendo l'interfaccia.

### <a name="to-define-the-glyph"></a>Per definire il glifo

1. Aggiungere un file di classe e assegnargli il nome `TodoGlyphFactory`.

2. Aggiungere il codice seguente utilizzando le dichiarazioni.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Aggiungere una `TodoGlyphFactory` classe <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>denominata che implementa .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Aggiungere un campo privato che definisce le dimensioni del glifo.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementare `GenerateGlyph` definendo l'elemento dell'interfaccia utente del glifo. `TodoTag`è definito più avanti in questa procedura dettagliata.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Aggiungere una `TodoGlyphFactoryProvider` classe <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>denominata che implementa . Esportare questa <xref:Microsoft.VisualStudio.Utilities.NameAttribute> classe con un "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di After VsTextMarker, un di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implementare <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> il metodo mediante `TodoGlyphFactory`la creazione di un'istanza di .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definire un tag Todo e un tagger
 Definire la relazione tra l'elemento dell'interfaccia utente definito nei passaggi precedenti e il margine dell'indicatore. Creare un tipo di tag e tagger ed esportarlo utilizzando un provider di tagger.

### <a name="to-define-a-todo-tag-and-tagger"></a>Per definire un tag todo e un tagger

1. Aggiungere un nuovo file di classe `TodoTagger`al progetto e denominarlo .

2. Aggiungere le importazioni seguenti.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Aggiungere una classe denominata `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Modificare la `TodoTagger` classe <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> denominata `TodoTag`che implementa di tipo .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Alla `TodoTagger` classe, aggiungere campi <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> privati per un oggetto e per il testo da trovare negli intervalli di classificazione.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Aggiungere un costruttore che imposta il classificatore.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> il metodo individuando tutti gli intervalli di classificazione i cui nomi includono la parola "commento" e il cui testo include il testo di ricerca. Ogni volta che viene trovato il <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> testo `TodoTag`di ricerca, restituire un nuovo di tipo .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Dichiarare `TagsChanged` un evento.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Aggiungere una `TodoTaggerProvider` classe <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>denominata che implementa <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> ed esportarla <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> con un di "code" e un di TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importare <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>il file .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> il metodo mediante `TodoTagger`la creazione di un'istanza di .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Per compilare e testare la soluzione TodoGlyphTest

1. Compilare la soluzione.

2. Eseguire il progetto premendo **F5**. Viene avviata una seconda istanza di Visual Studio.

3. Assicurarsi che il margine dell'indicatore sia visualizzato. Scegliere **Opzioni**dal menu **Strumenti** . Nella pagina **Editor di testo** verificare che l'opzione Margine **indicatore** sia selezionata.)

4. Aprire un file di codice con commenti. Aggiungere la parola "todo" a una delle sezioni di commento.

5. Un cerchio azzurro con un contorno blu scuro viene visualizzato nel margine dell'indicatore a sinistra della finestra del codice.
