---
title: 'Procedura dettagliata: creazione di un glifo del margine | Microsoft Docs'
description: Per informazioni su come personalizzare l'aspetto dei margini dell'editor usando le estensioni dell'editor personalizzate, usare questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ec5eecef40220c2cf2d4e3f1ece8eb5eb763bdeb
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/02/2021
ms.locfileid: "106217411"
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

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet1":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet1":::

3. Aggiungere una classe denominata `TodoGlyphFactory` che implementi <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet2":::

4. Aggiungere un campo privato che definisce le dimensioni dell'icona.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet3":::

5. Implementare `GenerateGlyph` mediante la definizione dell'elemento dell'interfaccia utente del glifo. `TodoTag` viene definito più avanti in questa procedura dettagliata.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet4":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet4":::

6. Aggiungere una classe denominata `TodoGlyphFactoryProvider` che implementi <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Esportare questa classe con un valore di <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di dopo vsTextMarker, un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet5":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet5":::

7. Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> Metodo creando un'istanza di `TodoGlyphFactory` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb" id="Snippet6":::

## <a name="define-a-todo-tag-and-tagger"></a>Definire un tag todo e un tag
 Definire la relazione tra l'elemento dell'interfaccia utente definito nei passaggi precedenti e il margine dell'indicatore. Creare un tipo di tag e un tag e esportarlo usando un provider del tag.

### <a name="to-define-a-todo-tag-and-tagger"></a>Per definire un tag todo e un codificatore

1. Aggiungere un nuovo file di classe al progetto e denominarlo `TodoTagger` .

2. Aggiungere le importazioni seguenti.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet7":::

3. Aggiungere una classe denominata `TodoTag`.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet8":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet8":::

4. Modificare la classe denominata `TodoTagger` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet9":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet9":::

5. Alla `TodoTagger` classe, aggiungere campi privati per un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> e per il testo da trovare negli intervalli di classificazione.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet10":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet10":::

6. Aggiungere un costruttore che imposta il classificatore.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet11":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet11":::

7. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> Metodo individuando tutti gli intervalli di classificazione i cui nomi includono la parola "comment" e il cui testo include il testo di ricerca. Ogni volta che viene trovato il testo di ricerca, restituisce un nuovo oggetto <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> di tipo `TodoTag` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet12":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet12":::

8. Dichiarare un `TagsChanged` evento.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet13":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet13":::

9. Aggiungere una classe denominata `TodoTaggerProvider` che implementi <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> ed esporti l'oggetto con un valore <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet14":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet14":::

10. Importare il <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet15":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet15":::

11. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> Metodo creando un'istanza di `TodoTagger` .

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs" id="Snippet16":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb" id="Snippet16":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirla nell'istanza sperimentale.

### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Per compilare e testare la soluzione TodoGlyphTest

1. Compilare la soluzione.

2. Eseguire il progetto premendo **F5**. Viene avviata una seconda istanza di Visual Studio.

3. Verificare che sia visualizzato il margine indicatore. Scegliere **Opzioni** dal menu **strumenti** . Nella pagina **editor di testo** assicurarsi che sia selezionato **Margin indicatore** .

4. Aprire un file di codice con commenti. Aggiungere la parola "TODO" a una delle sezioni di commento.

5. Un cerchio blu chiaro con un contorno blu scuro viene visualizzato nel margine dell'indicatore a sinistra della finestra del codice.
