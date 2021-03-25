---
title: Importazioni editor | Microsoft Docs
description: Informazioni su come importare i servizi dell'editor, le factory e i broker che forniscono un'estensione con diversi tipi di accesso all'editor principale.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0587ed6487ec3a1bb833a804bb5ffa76cbc101f9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070154"
---
# <a name="editor-imports"></a>Importazioni editor
È possibile importare un numero di servizi di editor, Factory e broker che forniscono un'estensione con diversi tipi di accesso all'editor principale. Ad esempio, è possibile importare per <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> fornire un oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> per un tipo di contenuto specifico. Questo strumento di spostamento consente di eseguire diversi tipi di ricerche in un buffer di testo.

 Per usare un'importazione di editor, è possibile importarla come campo o proprietà di una classe che esporta una parte del componente Managed Extensibility Framework.

> [!NOTE]
> Per ulteriori informazioni sulla Managed Extensibility Framework, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Importa sintassi
 Nell'esempio seguente viene illustrato come importare il servizio factory delle opzioni dell'editor.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Se si desidera importare il servizio come campo e non come proprietà, è necessario impostarlo su `null` nella dichiarazione per evitare gli avvisi del compilatore relativi alla mancata assegnazione a una variabile:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Per ulteriori esempi di utilizzo delle importazioni, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: creare un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Procedura dettagliata: personalizzare la visualizzazione di testo](../extensibility/walkthrough-customizing-the-text-view.md)

- [Procedura dettagliata: evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md)

- [Procedura dettagliata: visualizzare le descrizioni comandi di informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procedura dettagliata: visualizzare la guida per la firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)

- [Procedura dettagliata: visualizzare i suggerimenti della lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importazione del provider di servizi
 È anche possibile importare un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (presente nell'assembly Microsoft. VisualStudio. Shell. Immutable. 10.0) nello stesso modo per ottenere l'accesso ai servizi di Visual Studio:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Per ulteriori informazioni, vedere [procedura dettagliata: accesso all'oggetto DTE da un'estensione dell'editor](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) .

## <a name="services"></a>Servizi
 I servizi dell'editor sono in genere entità singole che forniscono un servizio e sono condivise tra più componenti.

|Importa|Fornisce|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relazione tra estensioni di file e <xref:Microsoft.VisualStudio.Utilities.IContentType> oggetti.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Raccolta di oggetti <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> oggetti.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Molti oggetti adapter dell'Editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch>Oggetto per una visualizzazione di testo specificata.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Oggetto <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> di differenze.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Oggetto <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> di differenze.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> o <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> per un set di <xref:Microsoft.VisualStudio.Text.ITextBuffer> oggetti.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per un oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Gestisce la raccolta di <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> oggetti.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per un buffer di testo.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> per l'ambito specificato.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ottiene il rientro automatico tramite gli <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> oggetti.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gestisce l'oggetto <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Genera testo formattato in formato RTF da un set di intervalli di snapshot.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Oggetto <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> per la formattazione di righe di testo in una visualizzazione.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations>Oggetto per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Esegue la ricerca in uno snapshot di testo.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> per un oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer> da <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Oggetto <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Set di glifi standard.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Tiene traccia della gestione della tastiera.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Oggetti standard.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relazione tra buffer di testo e  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> oggetti.|

## <a name="other-imports"></a>Altre importazioni
 Le factory e i broker del provider sono in genere entità che possono avere più istanze in più componenti.

|Importa|Fornisce|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> ) per il buffer specificato.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un codificatore del marcatore di testo ( <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Oggetto <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> per un oggetto specificato <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Vedi anche
- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
