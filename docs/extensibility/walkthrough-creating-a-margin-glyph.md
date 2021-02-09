---
title: 'Procedura dettagliata: creazione di un glifo del margine | Microsoft Docs'
description: Per informazioni su come personalizzare l'aspetto dei margini dell'editor usando le estensioni dell'editor personalizzate, usare questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a2a1857edb8032d12cd23da5e2686ad90f15b574
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892463"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Procedura dettagliata: creare un glifo del margine
È possibile personalizzare l'aspetto dei margini dell'editor usando le estensioni dell'editor personalizzate. Questa procedura dettagliata inserisce un glifo personalizzato sul margine dell'indicatore ogni volta che la parola "TODO" viene visualizzata in un commento del codice.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `TodoGlyphTest` .

2. Aggiungere un elemento di progetto di classificatore editor. Per altre informazioni, vedere [creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="define-the-glyph"></a>Definire il glifo
 Definire un glifo eseguendo l' <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaccia.

### <a name="to-define-the-glyph"></a>Per definire il glifo

1. Aggiungere un file di classe e assegnargli il nome `TodoGlyphFactory`.

2. Aggiungere il codice seguente usando le dichiarazioni.

     [!code-csharp[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]

3. Aggiungere una classe denominata `TodoGlyphFactory` che implementi <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     [!code-csharp[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]

4. Aggiungere un campo privato che definisce le dimensioni dell'icona.

     [!code-csharp[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]

5. Implementare `GenerateGlyph` mediante la definizione dell'elemento dell'interfaccia utente del glifo. `TodoTag` viene definito più avanti in questa procedura dettagliata.

     [!code-csharp[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]

6. Aggiungere una classe denominata `TodoGlyphFactoryProvider` che implementi <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Esportare questa classe con un valore di <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di dopo vsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]

7. Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Metodo creando un'istanza di `TodoGlyphFactory` .

     [!code-csharp[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]

## <a name="define-a-todo-tag-and-tagger"></a>Definire un tag todo e un tag
 Definire la relazione tra l'elemento dell'interfaccia utente definito nei passaggi precedenti e il margine dell'indicatore. Creare un tipo di tag e un tag e esportarlo usando un provider del tag.

### <a name="to-define-a-todo-tag-and-tagger"></a>Per definire un tag todo e un codificatore

1. Aggiungere un nuovo file di classe al progetto e denominarlo `TodoTagger` .

2. Aggiungere le importazioni seguenti.

     [!code-csharp[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]

3. Aggiungere una classe denominata `TodoTag`.

     [!code-csharp[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]

4. Modificare la classe denominata `TodoTagger` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]

5. Alla `TodoTagger` classe, aggiungere campi privati per un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> e per il testo da trovare negli intervalli di classificazione.

     [!code-csharp[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]

6. Aggiungere un costruttore che imposta il classificatore.

     [!code-csharp[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]

7. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Metodo individuando tutti gli intervalli di classificazione i cui nomi includono la parola "comment" e il cui testo include il testo di ricerca. Ogni volta che viene trovato il testo di ricerca, restituisce un nuovo oggetto <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> di tipo `TodoTag` .

     [!code-csharp[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]

8. Dichiarare un `TagsChanged` evento.

     [!code-csharp[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]

9. Aggiungere una classe denominata `TodoTaggerProvider` che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ed esporti l'oggetto con un valore <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.

     [!code-csharp[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]

10. Importare il <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     [!code-csharp[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]

11. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Metodo creando un'istanza di `TodoTagger` .

     [!code-csharp[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Per compilare e testare la soluzione TodoGlyphTest

1. Compilare la soluzione.

2. Eseguire il progetto premendo **F5**. Viene avviata una seconda istanza di Visual Studio.

3. Verificare che sia visualizzato il margine indicatore. Scegliere **Opzioni** dal menu **strumenti** . Nella pagina **editor di testo** assicurarsi che sia selezionato **Margin indicatore** .

4. Aprire un file di codice con commenti. Aggiungere la parola "TODO" a una delle sezioni di commento.

5. Un cerchio blu chiaro con un contorno blu scuro viene visualizzato nel margine dell'indicatore a sinistra della finestra del codice.
