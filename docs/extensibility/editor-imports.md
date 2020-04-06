---
title: Importazioni dell'Editor Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6af95b452166aa71950ac1e869d333d12d857b9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712004"
---
# <a name="editor-imports"></a>Importazioni dell'editor
È possibile importare un numero di servizi di editor, fabbriche e broker che forniscono all'estensione diversi tipi di accesso all'editor principale. Ad esempio, è <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> possibile importare l'oggetto per fornire un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> per un determinato tipo di contenuto. Questo strumento di navigazione consente di eseguire diversi tipi di ricerche in un buffer di testo.

 Per utilizzare un'importazione dell'editor, importarla come campo o proprietà di una classe che esporta una parte del componente Managed Extensibility Framework.

> [!NOTE]
> Per ulteriori informazioni su Managed Extensibility Framework, vedere [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).

## <a name="import-syntax"></a>Sintassi di importazione
 Nell'esempio seguente viene illustrato come importare il servizio factory delle opzioni dell'editor.

```
[Import]
internal IEditorOptionsFactoryService EditorOptions { get; set; }
```

 Se si desidera importare il servizio come campo e non `null` come proprietà, è necessario impostarlo su nella dichiarazione per evitare gli avvisi del compilatore relative alla non assegnazione a una variabile:If you want to import the service as a field and not a property, you should set it to in the declaration in order in order in order for avoid the compiler warnings about not assigning to a variable:

```
[Import]
internal IEditorOptionsFactoryService m_editorOptions = null;
```

 Per altri esempi di utilizzo delle importazioni, vedere le procedure dettagliate seguenti:For more examples of using imports, see the following walkthroughs:

- [Procedura dettagliata: Creare un glifo di margineWalkthrough: Create a margin glyph](../extensibility/walkthrough-creating-a-margin-glyph.md)

- [Procedura dettagliata: Personalizzare la visualizzazione di testoWalkthrough: Customize the text view](../extensibility/walkthrough-customizing-the-text-view.md)

- [Procedura dettagliata: Evidenziare il testoWalkthrough: Highlight text](../extensibility/walkthrough-highlighting-text.md)

- [Procedura dettagliata: Visualizzare le descrizioni comandi di informazioni rapideWalkthrough: Display QuickInfo tooltips](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)

- [Procedura dettagliata: Visualizza guida firmaWalkthrough: Display Signature Help](../extensibility/walkthrough-displaying-signature-help.md)

- [Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)

- [Procedura dettagliata: Visualizzare i suggerimenti per le lampadine](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)

## <a name="import-the-service-provider"></a>Importare il provider di servizi
 È inoltre possibile <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> importare un (trovato nell'assembly Microsoft.VisualStudio.Shell.Immutable.10.0) nello stesso modo per ottenere l'accesso ai servizi di Visual Studio:You can also import a (found in the assembly Microsoft.VisualStudio.Shell.Immutable.10.0) in the same way to get access to Visual Studio services:

```csharp
[Import]
internal SVsServiceProvider ServiceProvider = null;
```

 Per ulteriori informazioni, vedere [Procedura dettagliata: accedere all'oggetto DTE da un'estensione dell'editor.](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md)

## <a name="services"></a>Servizi
 I servizi editor sono in genere singole entità che forniscono un servizio e sono condivise tra più componenti.

|Importa|Fornisce|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|Relazione tra estensioni <xref:Microsoft.VisualStudio.Utilities.IContentType> di file e oggetti.|
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Raccolta di oggetti <xref:Microsoft.VisualStudio.Utilities.IContentType>.|
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>Oggetti.|
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Molti oggetti adattatore dell'editor:Many editor adapter objects:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> per una determinata visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Valore <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Valore <xref:Microsoft.VisualStudio.Text.ITextDocument>.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> dispari.|
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> dispari.|
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> o <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>un file .|
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> per un <xref:Microsoft.VisualStudio.Text.ITextBuffer> insieme di oggetti.|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per <xref:Microsoft.VisualStudio.Text.ITextBuffer>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Un <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Mantiene la raccolta <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> di oggetti.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per un buffer di testo.|
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> per l'ambito specificato.|
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Un <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ottiene il rientro automatico <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> attraverso gli oggetti.|
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gestisce <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> l'oggetto for a <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Valore <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Genera testo in formato RTF da un set di intervalli di snapshot.|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un file .|
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Oggetto <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> per la formattazione delle righe di testo in una vista.|
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un oggetto .|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Esegue la ricerca in un'istantanea di testo.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> per <xref:Microsoft.VisualStudio.Text.ITextBuffer> <xref:Microsoft.VisualStudio.Utilities.IContentType>un by .|
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Oggetto <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> per una visualizzazione di testo.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un set standard di glifi.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Tiene traccia della gestione della tastiera.|
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Oggetti <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> standard.|
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Mantiene la relazione tra buffer <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> di testo e oggetti.|

## <a name="other-imports"></a>Altre importazioni
 Le factory di provider e i broker sono in genere entità che possono avere più istanze in più componenti.

|Importa|Fornisce|
|------------|--------------|
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Oggetto <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> di <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>tipo ) per il buffer specificato.|
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un tagger marcatore <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>testo (un di tipo ).|
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Oggetto <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> per <xref:Microsoft.VisualStudio.Text.Editor.ITextView>un dato di fatto .|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Valore <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Valore <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Valore <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
