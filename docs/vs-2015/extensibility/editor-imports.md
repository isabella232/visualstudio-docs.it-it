---
title: Importazioni dell'editor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - services
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1fc32d0126d912acab104ecefe3cb62d80b8513f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690314"
---
# <a name="editor-imports"></a>Importazioni dell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile importare un numero di servizi di editor, le factory e Broker che forniscono l'estensione con diversi tipi di accesso per l'editor principale. Ad esempio, è possibile importare il <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> per fornire un <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> per un determinato tipo di contenuto. (Questo strumento di spostamento consente che eseguire diversi tipi di ricerche in un buffer di testo).  
  
 Per usare l'importazione in un editor, importato come un campo o proprietà di una classe che consente di esportare una parte del componente Managed Extensibility Framework.  
  
> [!NOTE]
> Per altre informazioni su Managed Extensibility Framework, vedere [Managed Extensibility Framework (MEF)](https://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde).  
  
## <a name="import-syntax"></a>Sintassi di importazione  
 Nell'esempio seguente illustra come importare l'editor del servizio factory opzioni.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 Se si desidera importare il servizio come un campo e non una proprietà, è necessario impostarlo `null` nella dichiarazione per evitare gli avvisi del compilatore relativi a non assegnare a una variabile:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 Per altri esempi dell'uso di importazioni, vedere le procedure dettagliate seguenti:  
  
 [Procedura dettagliata: creazione di un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Procedura dettagliata: personalizzazione della visualizzazione di testo](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Procedura dettagliata: evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md)  
  
 [Procedura dettagliata: visualizzazione delle descrizioni comando di InformazioniBase](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Procedura dettagliata: visualizzazione della funzionalità di supporto alla firma](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Procedura dettagliata: visualizzazione del completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Procedura dettagliata: Visualizzazione degli smart tag](../misc/walkthrough-displaying-smarttags.md)  
  
## <a name="importing-the-service-provider"></a>Il Provider del servizio di importazione  
 È anche possibile importare un <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (trovato nell'assembly Microsoft.VisualStudio.Shell.Immutable.10.0) nello stesso modo per ottenere l'accesso ai servizi di Visual Studio:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 Vedere [Procedura dettagliata: L'accesso all'oggetto DTE da un'estensione dell'Editor](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) per altre informazioni.  
  
## <a name="services"></a>Servizi  
 Editor servizi sono in genere singole entità che forniscono un servizio e vengono condivise tra più componenti.  
  
|Import|Fornisce|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|La relazione tra le estensioni di file e <xref:Microsoft.VisualStudio.Utilities.IContentType> oggetti.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|Raccolta di oggetti <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|Oggetti <xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation>.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Molti oggetti adattatore dell'editor:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|Un <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> oggetto per una visualizzazione di testo specificato.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> delle differenze.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|Un <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> delle differenze.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|Un' <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> o un <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|Un' <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> per un set di <xref:Microsoft.VisualStudio.Text.ITextBuffer> oggetti.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|Un' <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per un <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|Un' <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|Un' <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|Un' <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Gestisce la raccolta di <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> oggetti.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per un buffer di testo.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> per una visualizzazione di testo.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|Il <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> per l'ambito specificato.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|Un <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> per una visualizzazione di testo.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Un' <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Ottiene il rientro automatico il <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> oggetti.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Gestisce il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> per un <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generare testo formattato RTF da un set di intervalli dello snapshot.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|Un' <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|Oggetto <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> per la formattazione di righe di testo in una vista.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|Oggetto <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> dell'oggetto per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Cerca uno snapshot di testo.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|Un' <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> per un <xref:Microsoft.VisualStudio.Text.ITextBuffer> da <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|Un <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> per una visualizzazione di testo.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|Un set di glifi standard.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|Un' <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> per un <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Tiene traccia della tastiera la gestione.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standard <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> oggetti.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Gestisce la relazione tra i buffer di testo e <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> oggetti.|  
  
## <a name="other-imports"></a>Altre importazioni  
 Broker e factory dei provider sono in genere di entità che possono avere più istanze in più componenti.  
  
|Import|Fornisce|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|Una <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) per il buffer specificato.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|Un tagger del marcatore di testo (un <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|Un' <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> per un determinato <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|Oggetto <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
