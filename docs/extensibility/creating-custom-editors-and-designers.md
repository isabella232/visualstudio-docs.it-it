---
title: Creazione di editor e finestre di progettazione personalizzati | Microsoft Docs
description: "Informazioni sui diversi tipi di editor che possono essere ospitati dall'IDE di Visual Studio: editor principale, editor personalizzati, editor esterni e finestre di progettazione."
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
ms.workload:
- vssdk
ms.openlocfilehash: c2882cfa103627672e5c96a0e3d4b2a23b4b4ba9
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055778"
---
# <a name="create-custom-editors-and-designers"></a>Creazione di editor e finestre di progettazione personalizzati

Visual Studio Integrated Development Environment (IDE) può ospitare tipi diversi di Editor:

- Editor principale di Visual Studio

- Editor personalizzati

- Editor esterni

- Finestre di progettazione

Le informazioni seguenti consentono di scegliere il tipo di editor necessario.

## <a name="types-of-editor"></a>Tipi di editor

Per informazioni sull'editor principale di Visual Studio, vedere [estendere l'editor e i servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Editor personalizzati
 Un editor personalizzato è uno progettato per funzionare in circostanze specializzate. Ad esempio, è possibile creare un editor la cui funzione è leggere e scrivere dati in un repository specifico, ad esempio un server Microsoft Exchange. Scegliere un editor personalizzato se si desidera un editor che funzioni solo con il tipo di progetto o se si desidera un editor con solo alcuni comandi specifici. Si noti, tuttavia, che gli utenti non saranno in grado di utilizzare un editor personalizzato per modificare i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti standard.

 Un editor personalizzato può utilizzare una factory dell'editor e aggiungere informazioni sull'editor al registro di sistema. Il tipo di progetto associato all'editor personalizzato può tuttavia creare un'istanza dell'editor personalizzato in altri modi.

 Un editor personalizzato può usare l'attivazione sul posto o l'incorporamento semplificato per implementare una visualizzazione.

### <a name="external-editors"></a>Editor esterni
 Gli editor esterni sono editor che non sono integrati in Visual Studio, ad esempio Microsoft Word, blocco note o Microsoft FrontPage. È possibile chiamare un editor di questo tipo se, ad esempio, si passa il testo dal pacchetto VSPackage. Gli editor esterni si registrano e possono essere usati all'esterno di Visual Studio. Quando si chiama un editor esterno e può essere incorporato in una finestra host, viene visualizzato in una finestra nell'IDE. In caso contrario, l'IDE crea una finestra separata.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo imposta la priorità del documento tramite l' <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione. Se il `DP_External` valore è specificato, il file può essere aperto da un editor esterno.

## <a name="editor-design-decisions"></a>Decisioni di progettazione dell'editor
 Le seguenti domande di progettazione consentiranno di scegliere il tipo di editor più adatto all'applicazione:

- L'applicazione salverà i dati nei file? Se i dati verranno salvati nei file, saranno in formato personalizzato o standard?

   Se si usa un formato di file standard, altri tipi di progetto in aggiunta al progetto saranno in grado di aprire e leggere/scrivere dati in essi contenuti. Se si usa un formato di file personalizzato, tuttavia, solo il tipo di progetto sarà in grado di aprire e leggere/scrivere i dati.

   Se il progetto usa file, è necessario personalizzare l'editor standard. Se il progetto non usa file, ma usa invece elementi in un database o in un altro repository, è necessario creare un editor personalizzato.

- L'editor deve ospitare i controlli ActiveX?

   Se l'editor ospita controlli ActiveX, implementare un editor di attivazione sul posto, come descritto nell' [attivazione sul posto](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015). Se non ospita controlli ActiveX, usare un editor di incorporamento semplificato o personalizzare l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predefinito.

- L'editor supporterà più visualizzazioni? È necessario supportare più visualizzazioni Se si desidera che le visualizzazioni dell'editor siano visibili nello stesso momento dell'editor predefinito.

   Se l'editor deve supportare più visualizzazioni, gli oggetti dati del documento e visualizzazione documento per l'editor devono essere oggetti separati. Per altre informazioni, vedere [supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

   Se l'editor supporta più visualizzazioni, si prevede di usare l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementazione del buffer di testo dell'editor principale ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto) per l'oggetto dati del documento? Ovvero si desidera supportare la visualizzazione dell'editor side-by-side con l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale? La possibilità di eseguire questa operazione è la base della finestra di progettazione dei form.

- Se è necessario ospitare un editor esterno, è possibile incorporare l'editor all'interno di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ?

   Se può essere incorporata, è necessario creare una finestra host per l'editor esterno, quindi chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo e impostare il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valore di enumerazione su `DP_External` . Se non è possibile incorporare l'editor, l'IDE creerà automaticamente una finestra separata.

## <a name="in-this-section"></a>Contenuto della sezione

[Procedura dettagliata: creare un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md)\
Viene illustrato come creare un editor personalizzato.

[Procedura dettagliata: aggiungere funzionalità a un editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Viene illustrato come aggiungere funzionalità a un editor personalizzato.

[Inizializzazione della finestra di progettazione e configurazione dei metadati](../extensibility/designer-initialization-and-metadata-configuration.md)\
Viene illustrato come inizializzare una finestra di progettazione.

[Fornire il supporto per l'annullamento alle finestre di progettazione](../extensibility/supplying-undo-support-to-designers.md)\
Viene illustrato come fornire supporto di annullamento per le finestre di progettazione.

[Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)\
Viene illustrata la differenza tra la colorazione della sintassi nell'editor principale e negli editor personalizzati.

[Documenti e visualizzazione dei documenti negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Viene illustrato come implementare i dati del documento e le visualizzazioni documento negli editor personalizzati.

## <a name="related-sections"></a>Sezioni correlate

[Interfacce legacy nell'editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/legacy-interfaces-in-the-editor?preserve-view=true&view=vs-2015)\
Viene illustrato come accedere all'editor principale per mezzo dell'API legacy.

[Sviluppare un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)\
Viene illustrato come implementare un servizio di linguaggio.

[Estendi altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Viene illustrato come creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>
