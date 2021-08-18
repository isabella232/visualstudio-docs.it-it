---
title: 'Procedura dettagliata: Creazione di un glifo | Microsoft Docs'
description: Informazioni su come personalizzare l'aspetto dei margini dell'editor usando estensioni dell'editor personalizzate usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 5e5bd2d49f1bc2af8f90a1fb92e42a08a6de5c11
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078570"
---
# <a name="walkthrough-create-a-margin-glyph"></a>Procedura dettagliata: Creare un glifo del margine
È possibile personalizzare l'aspetto dei margini dell'editor usando estensioni dell'editor personalizzate. Questa procedura dettagliata inserisce un glifo personalizzato sul margine dell'indicatore ogni volta che la parola "todo" viene visualizzata in un commento del codice.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Project** nuova versione selezionare Visual **C# /Extensibility**, quindi **VSIX Project**. Assegnare alla soluzione il nome `TodoGlyphTest` .

2. Aggiungere un elemento di progetto Editor Classifier. Per altre informazioni, vedere Creare [un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Eliminare i file di classe esistenti.

## <a name="define-the-glyph"></a>Definire il glifo
 Definire un glifo eseguendo <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> l'interfaccia .

### <a name="to-define-the-glyph"></a>Per definire il glifo

1. Aggiungere un file di classe e assegnargli il nome `TodoGlyphFactory`.

2. Aggiungere il codice seguente usando le dichiarazioni .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Aggiungere una classe denominata `TodoGlyphFactory` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Aggiungere un campo privato che definisce le dimensioni del glifo.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. Implementare `GenerateGlyph` definendo l'elemento dell'interfaccia utente del glifo. `TodoTag` viene definito più avanti in questa procedura dettagliata.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Aggiungere una classe denominata `TodoGlyphFactoryProvider` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Esportare questa classe con <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", after <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> VsTextMarker, a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e di <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Implementare <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> il metodo creando un'istanza di `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Definire un tag Todo e un tagger
 Definire la relazione tra l'elemento dell'interfaccia utente definito nei passaggi precedenti e il margine dell'indicatore. Creare un tipo di tag e un tagger ed esportarlo usando un provider di tag.

### <a name="to-define-a-todo-tag-and-tagger"></a>Per definire un tag todo e un tagger

1. Aggiungere un nuovo file di classe al progetto e assegnare al progetto il nome `TodoTagger` .

2. Aggiungere le importazioni seguenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Aggiungere una classe denominata `TodoTag`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Modificare la classe denominata `TodoTagger` che implementa di tipo <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. Alla classe aggiungere campi privati per un oggetto e per il testo `TodoTagger` <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> da trovare negli intervalli di classificazione.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Aggiungere un costruttore che imposta il classificatore.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Implementare il metodo individuando tutti gli intervalli di classificazione i cui nomi includono la parola "comment" e il cui testo <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> include il testo di ricerca. Ogni volta che viene trovato il testo di ricerca, restituisce un nuovo <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> di tipo `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Dichiarare un `TagsChanged` evento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Aggiungere una classe `TodoTaggerProvider` denominata che implementa ed <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> esportarla con <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "code" e <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> todoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Importare <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Implementare <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> il metodo creando un'istanza di `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Per compilare e testare la soluzione TodoGlyphTest

1. Compilare la soluzione.

2. Eseguire il progetto premendo **F5.** Viene avviata una seconda Visual Studio di .

3. Assicurarsi che il margine dell'indicatore sia visualizzato. Scegliere **Opzioni** dal menu **Strumenti.** Nella pagina **Editor di** testo verificare che l'opzione **Margine indicatore** sia selezionata.

4. Aprire un file di codice con commenti. Aggiungere la parola "todo" a una delle sezioni di commento.

5. Nel margine dell'indicatore a sinistra della finestra del codice viene visualizzato un cerchio blu chiaro con un contorno blu scuro.
