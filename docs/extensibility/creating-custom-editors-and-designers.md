---
title: Creazione di editor e finestre di progettazione | Microsoft Docs
description: "Informazioni sui diversi tipi di editor che possono essere ospitati dall'IDE di Visual Studio: editor di base, editor personalizzati, editor esterni e finestre di progettazione."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9510626a5e884a63e6237ffa6dd3d68a47b61047
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043687"
---
# <a name="create-custom-editors-and-designers"></a>Creare editor e finestre di progettazione personalizzati

L Visual Studio'ambiente di sviluppo integrato (IDE) può ospitare diversi tipi di editor:

- Editor Visual Studio core

- Editor personalizzati

- Editor esterni

- Finestre di progettazione

Le informazioni seguenti consentono di scegliere il tipo di editor necessario.

## <a name="types-of-editor"></a>Tipi di editor

Per informazioni sull'editor Visual Studio core, vedere [Estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Editor personalizzati
 Un editor personalizzato è progettato per funzionare in circostanze specifiche. Ad esempio, è possibile creare un editor la cui funzione è la lettura e la scrittura di dati in un repository specifico, ad esempio un server microsoft Exchange. Scegliere un editor personalizzato se si vuole un editor che funzioni solo con il tipo di progetto o se si vuole un editor che abbia solo alcuni comandi specifici. Si noti, tuttavia, che gli utenti non potranno usare un editor personalizzato per modificare i progetti [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] standard.

 Un editor personalizzato può usare una factory dell'editor e aggiungere informazioni sull'editor al Registro di sistema. Tuttavia, il tipo di progetto associato all'editor personalizzato può creare un'istanza dell'editor personalizzato in altri modi.

 Un editor personalizzato può usare l'attivazione sul posto o l'incorporamento semplificato per implementare una visualizzazione.

### <a name="external-editors"></a>Editor esterni
 Gli editor esterni sono editor non integrati in Visual Studio, ad esempio Microsoft Word, Blocco note o Microsoft FrontPage. È possibile chiamare un editor di questo tipo se, ad esempio, si passa del testo dal pacchetto VSPackage. Gli editor esterni si registrano e possono essere usati all'esterno Visual Studio. Quando si chiama un editor esterno e può essere incorporato in una finestra host, viene visualizzato in una finestra nell'IDE. In caso contrario, l'IDE crea una finestra separata.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo imposta la priorità del documento usando l'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> . Se il `DP_External` valore viene specificato, il file può essere aperto da un editor esterno.

## <a name="editor-design-decisions"></a>Decisioni di progettazione dell'editor
 Le domande di progettazione seguenti consentono di scegliere il tipo di editor più adatto all'applicazione:

- L'applicazione salverà o meno i dati in file? Se i dati verranno salvate in file, saranno in un formato personalizzato o standard?

   Se si usa un formato di file standard, altri tipi di progetto oltre al progetto saranno in grado di aprire e leggere/scrivere dati in essi. Se si usa un formato di file personalizzato, tuttavia, solo il tipo di progetto sarà in grado di aprire e leggere/scrivere dati.

   Se il progetto usa file, è necessario personalizzare l'editor standard. Se il progetto non usa file, ma piuttosto elementi in un database o in un altro repository, è necessario creare un editor personalizzato.

- L'editor deve ospitare ActiveX controlli?

   Se l'editor ActiveX controlli, implementare un editor di attivazione sul posto, come descritto in [Attivazione sul posto](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Se non ospita controlli ActiveX, usare un editor di incorporamento semplificato o personalizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'editor predefinito.

- L'editor supporterà più visualizzazioni? È necessario supportare più visualizzazioni se si vuole che le visualizzazioni dell'editor siano visibili contemporaneamente all'editor predefinito.

   Se l'editor deve supportare più visualizzazioni, i dati del documento e gli oggetti visualizzazione documento per l'editor devono essere oggetti separati. Per altre informazioni, vedere Support multiple document views (Supporto [di più visualizzazioni documento).](../extensibility/supporting-multiple-document-views.md)

   Se l'editor supporta più visualizzazioni, si prevede di usare l'implementazione del buffer di testo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (oggetto) dell'editor principale per <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> l'oggetto dati del documento? In altri dettagli, si vuole supportare la visualizzazione dell'editor side-by-side con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'editor principale? La possibilità di eseguire questa operazione è alla base della finestra di progettazione dei form.

- Se è necessario ospitare un editor esterno, è possibile incorporare l'editor all'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ?

   Se può essere incorporato, è necessario creare una finestra host per l'editor esterno e quindi chiamare il metodo e impostare il valore <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> di enumerazione su `DP_External` . Se non è possibile incorporare l'editor, l'IDE creerà automaticamente una finestra separata.

## <a name="in-this-section"></a>Contenuto della sezione

[Procedura dettagliata: Creare un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md)\
Viene illustrato come creare un editor personalizzato.

[Procedura dettagliata: Aggiungere funzionalità a un editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Viene illustrato come aggiungere funzionalità a un editor personalizzato.

[Inizializzazione della finestra di progettazione e configurazione dei metadati](../extensibility/designer-initialization-and-metadata-configuration.md)\
Viene illustrato come inizializzare una finestra di progettazione.

[Fornire supporto di annullamento alle finestre di progettazione](../extensibility/supplying-undo-support-to-designers.md)\
Viene illustrato come fornire il supporto dell'annullamento per le finestre di progettazione.

[Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)\
Viene illustrata la differenza tra la colorazione della sintassi nell'editor principale e negli editor personalizzati.

[Dati del documento e visualizzazione del documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Viene illustrato come implementare i dati dei documenti e le visualizzazioni dei documenti negli editor personalizzati.

## <a name="related-sections"></a>Sezioni correlate

[Interfacce legacy nell'editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)\
Viene illustrato come accedere all'editor principale tramite l'API legacy.

[Sviluppare un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)\
Viene illustrato come implementare un servizio di linguaggio.

[Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Viene illustrato come creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
