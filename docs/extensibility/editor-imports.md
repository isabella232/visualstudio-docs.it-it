---
title: Importazioni dell'editor | Microsoft Docs
description: Informazioni su come importare servizi, factory e broker dell'editor che forniscono all'estensione diversi tipi di accesso all'editor principale.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a0e6aa0f19c8ae8f19fb49a1322e12cae0aa65305217d5ff8a8361132e347a37
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121360053"
---
# <a name="editor-imports"></a>Importazioni dell'editor
È possibile importare diversi servizi editor, factory e broker che forniscono all'estensione diversi tipi di accesso all'editor principale. Ad esempio, è possibile importare <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> per fornire un per un determinato tipo di <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> contenuto. Questo strumento di navigazione consente di eseguire diversi tipi di ricerche in un buffer di testo.

 Per usare un'importazione dell'editor, importarla come campo o proprietà di una classe che esporta una Managed Extensibility Framework componente.

> [!NOTE]
> Per altre informazioni sui Managed Extensibility Framework, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Sintassi di importazione
 Nell'esempio seguente viene illustrato come importare il servizio factory delle opzioni dell'editor.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Se si vuole importare il servizio come campo e non come proprietà, è necessario impostarlo su nella dichiarazione per evitare gli avvisi del compilatore relativi alla non assegnazione `null` a una variabile:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Per altri esempi di utilizzo delle importazioni, vedere le procedure dettagliate seguenti:

- [Procedura dettagliata: Creare un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Procedura dettagliata: Personalizzare la visualizzazione testo](../extensibility/walkthrough-customizing-the-text-view.md)

- [Procedura dettagliata: Evidenziare il testo](../extensibility/walkthrough-highlighting-text.md)

- [Procedura dettagliata: Visualizzare le descrizioni comando di Informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procedura dettagliata: Visualizzare la Guida per la firma](../extensibility/walkthrough-displaying-signature-help.md)

- [Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)

- [Procedura dettagliata: Visualizzare i suggerimenti per le lampadine](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importare il provider di servizi
 È anche possibile importare un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> oggetto (disponibile nell'assembly Microsoft.VisualStudio.Shell.Immutable.10.0) nello stesso modo per ottenere l'accesso Visual Studio servizi:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Per [altre informazioni, vedere Procedura dettagliata: Accedere all'oggetto DTE da un'estensione dell'editor.](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)

## <a name="services"></a>Servizi
 I servizi editor sono in genere singole entità che forniscono un servizio e sono condivise tra più componenti.

|Importa|Fornisce|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relazione tra estensioni di file e <xref:Microsoft.VisualStudio.Utilities.IContentType> oggetti.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Raccolta di oggetti <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> Oggetti.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Molti oggetti adattatore dell'editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> per una determinata visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Oggetto <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> di differenze.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Oggetto <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> di differenze.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> o <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> per un set di oggetti <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per un oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Oggetto <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Gestisce la raccolta di <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> oggetti .|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per un buffer di testo.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> per l'ambito specificato.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ottiene il rientro automatico tramite gli <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> oggetti .|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gestisce <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> l'oggetto per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Genera testo in formato RTF da un set di intervalli di snapshot.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Oggetto <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> per la formattazione delle righe di testo in una visualizzazione.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Cerca uno snapshot di testo.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Oggetto <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> per un oggetto di <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType> .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Oggetto <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Set standard di glifi.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Tiene traccia della gestione della tastiera.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Oggetti <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> standard.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relazione tra buffer di testo e  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> oggetti.|

## <a name="other-imports"></a>Altre importazioni
 Le factory e i broker del provider sono in genere entità che possono avere più istanze in più componenti.

|Importa|Fornisce|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> di tipo per il buffer <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> specificato.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Tagger marcatore di testo (di <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Oggetto <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> per un oggetto <xref:Microsoft.VisualStudio.Text.Editor.ITextView> specificato.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Vedi anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
