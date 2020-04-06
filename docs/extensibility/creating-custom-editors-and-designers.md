---
title: Creazione di editor personalizzati e finestre di progettazione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b9f56b82225e1e40782b6753bea03d3c1780f596
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739483"
---
# <a name="create-custom-editors-and-designers"></a>Creare editor e finestre di progettazione personalizzatiCreate custom editors and designers

L'ambiente di sviluppo integrato (IDE) di Visual Studio può ospitare diversi tipi di editor:The Visual Studio integrated development environment (IDE) can host different types of editor:

- L'editor principale di Visual Studio

- Editor personalizzati

- Editor esterni

- Finestre di progettazione

Le seguenti informazioni ti aiutano a scegliere il tipo di editor che ti serve.

## <a name="types-of-editor"></a>Tipi di editor

Per informazioni sull'editor principale di Visual Studio, vedere [Estendere l'editor e](../extensibility/extending-the-editor-and-language-services.md)i servizi di linguaggio .

### <a name="custom-editors"></a>Editor personalizzati
 Un editor personalizzato è progettato per funzionare in circostanze specializzate. Ad esempio, è possibile creare un editor la cui funzione consiste nel leggere e scrivere dati in un repository specifico, ad esempio un server di Microsoft Exchange. Scegliere un editor personalizzato se si desidera un editor che funziona solo con il tipo di progetto o se si desidera un editor che dispone solo di alcuni comandi specifici. Si noti, tuttavia, che gli utenti non [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] saranno in grado di utilizzare un editor personalizzato per modificare i progetti standard.

 Un editor personalizzato può utilizzare una factory dell'editor e aggiungere informazioni sull'editor al Registro di sistema. Tuttavia, il tipo di progetto associato all'editor personalizzato può creare un'istanza dell'editor personalizzato in altri modi.

 Un editor personalizzato può usare l'attivazione sul posto o l'incorporamento semplificato per implementare una visualizzazione.

### <a name="external-editors"></a>Editor esterni
 Gli editor esterni sono editor non integrati in Visual Studio, ad esempio Microsoft Word, Blocco note o Microsoft FrontPage. You might call such an editor if, for example, you are passing text to it from your VSPackage. Gli editor esterni si registrano e possono essere utilizzati all'esterno di Visual Studio.External editors register themselves and can be used outside Visual Studio. Quando si chiama un editor esterno e può essere incorporato in una finestra host, quindi viene visualizzato in una finestra nell'IDE. In caso contrario, l'IDE crea una finestra separata per esso.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo imposta la priorità <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> del documento utilizzando l'enumerazione . Se `DP_External` viene specificato il valore, il file può essere aperto da un editor esterno.

## <a name="editor-design-decisions"></a>Decisioni di progettazione dell'editore
 Le seguenti domande di progettazione ti aiuteranno a scegliere il tipo di editor più adatto alla tua applicazione:

- L'applicazione salverà i dati in file o no? Se salverà i suoi dati in file, saranno in un formato personalizzato o standard?

   Se si utilizza un formato di file standard, altri tipi di progetto oltre al progetto saranno in grado di aprire e leggere/scrivere dati. Se si utilizza un formato di file personalizzato, tuttavia, solo il tipo di progetto sarà in grado di aprire e leggere/scrivere dati.

   Se il progetto utilizza file, è necessario personalizzare l'editor standard. Se il progetto non utilizza file, ma utilizza elementi in un database o in un altro repository, è necessario creare un editor personalizzato.

- L'editor deve ospitare i controlli ActiveX?

   Se l'editor ospita controlli ActiveX, implementare un editor di attivazione sul posto, come descritto in [Attivazione sul posto](/visualstudio/misc/in-place-activation?view=vs-2015). Se non ospita controlli ActiveX, utilizzare un editor di incorporamento [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] semplificato o personalizzare l'editor predefinito.

- Il tuo editor supporterà più visualizzazioni? È necessario supportare più visualizzazioni se si desidera che le visualizzazioni dell'editor siano visibili contemporaneamente all'editor predefinito.

   Se l'editor deve supportare più visualizzazioni, i dati del documento e gli oggetti visualizzazione documento per l'editor devono essere oggetti separati. Per ulteriori informazioni, consultate [Supporto di più visualizzazioni documento.](../extensibility/supporting-multiple-document-views.md)

   Se l'editor supporta più visualizzazioni, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] si prevede di utilizzare<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> l'implementazione del buffer di testo (oggetto) dell'editor di base per l'oggetto dati del documento? Vale a dire, si desidera supportare la visualizzazione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dell'editor side-by-side con l'editor di base? La possibilità di eseguire questa operazione è la base della finestra di progettazione dei moduli.

- Se è necessario ospitare un editor esterno, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]l'editor può essere incorporato all'interno di ?

   Se è possibile incorporarlo, è necessario creare una finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> host per <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> l'editor `DP_External`esterno, quindi chiamare il metodo e impostare il valore di enumerazione su . Se l'editor non può essere incorporato, l'IDE creerà automaticamente una finestra separata per esso.

## <a name="in-this-section"></a>Contenuto della sezione

[Procedura dettagliata: Creare un editor personalizzatoWalkthrough: Create a custom editor](../extensibility/walkthrough-creating-a-custom-editor.md)\
Viene illustrato come creare un editor personalizzato.

[Procedura dettagliata: Aggiungere funzionalità a un editor personalizzatoWalkthrough: Add features to a custom editor](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Viene illustrato come aggiungere funzionalità a un editor personalizzato.

[Inizializzazione della finestra di progettazione e configurazione dei metadati](../extensibility/designer-initialization-and-metadata-configuration.md)\
Viene illustrato come inizializzare una finestra di progettazione.

[Fornire supporto di annullamento ai progettisti](../extensibility/supplying-undo-support-to-designers.md)\
Viene illustrato come fornire il supporto di annullamento per le finestre di progettazione.

[Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)\
Viene illustrata la differenza tra la colorazione della sintassi nell'editor principale e negli editor personalizzati.

[Dati del documento e visualizzazione del documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Viene illustrato come implementare i dati del documento e le visualizzazioni del documento negli editor personalizzati.

## <a name="related-sections"></a>Sezioni correlate

[Interfacce legacy nell'editor](/visualstudio/extensibility/legacy-interfaces-in-the-editor?view=vs-2015)\
Viene illustrato come accedere all'editor principale tramite l'API legacy.

[Sviluppare un servizio di linguaggio legacyDevelop a legacy language service](../extensibility/internals/developing-a-legacy-language-service.md)\
Viene illustrato come implementare un servizio di linguaggio.

[Estendere altre parti di Visual StudioExtend other parts of Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Viene illustrato come creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
