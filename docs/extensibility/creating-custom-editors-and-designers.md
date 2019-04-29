---
title: Creazione di editor personalizzati e finestre di progettazione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- designers [Visual Studio SDK]
- editors [Visual Studio SDK], custom
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a806e434bebb5a561534fb8aec19d16dc9e28ffd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62891045"
---
# <a name="create-custom-editors-and-designers"></a>Creare finestre di progettazione ed editor personalizzati

L'ambiente di sviluppo integrato (IDE) di Visual Studio può ospitare diversi tipi di editor:

- L'editor principale di Visual Studio

- Editor personalizzati

- Editor esterno

- Finestre di progettazione

Le informazioni seguenti consentono di scegliere il tipo dell'editor che è necessario.

## <a name="types-of-editor"></a>Tipi di editor

Per informazioni su editor principale di Visual Studio, vedere [estendere l'editor e servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md).

### <a name="custom-editors"></a>Editor personalizzati
 Un editor personalizzato è quello che è progettato per funzionare in circostanze particolari. Ad esempio, si potrebbe creare un editor la cui funzione consiste nel leggere e scrivere dati in un repository specifico, ad esempio un server Microsoft Exchange. Se si desidera un editor che funziona con solo il tipo di progetto o se si desidera che un editor che ha solo alcuni comandi specifici, scegliere un editor personalizzato. Si noti tuttavia che gli utenti non saranno in grado di utilizzare un editor personalizzato per modificare standard [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetti.

 Un editor personalizzato è possibile usare una factory dell'editor e aggiungere informazioni sull'editor nel Registro di sistema. Tuttavia, il tipo di progetto associato all'editor personalizzato può creare un'istanza all'editor personalizzato in altri modi.

 Un editor personalizzato è possibile usare l'attivazione sul posto o incorporamento semplificato per implementare una visualizzazione.

### <a name="external-editors"></a>Editor esterno
 Gli editor esterni sono gli editor che non sono integrati in Visual Studio, ad esempio Microsoft Word, il blocco note o Microsoft FrontPage. Se, ad esempio, si passa il testo a esso dal pacchetto VSPackage, è possibile chiamare questo tipo di un editor. Editor esterno effettuano la registrazione e può essere utilizzato all'esterno di Visual Studio. Quando si chiama un editor esterno, e può essere incorporato in una finestra host, viene visualizzato in una finestra dell'IDE. In caso contrario, l'IDE crea quindi una finestra separata per tale.

 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo imposta la priorità di documento utilizzando il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> enumerazione. Se il `DP_External` valore viene specificato, il file può essere aperto da un editor esterno.

## <a name="editor-design-decisions"></a>Decisioni di progettazione dell'editor
 Le domande di progettazione seguenti consentono di scegliere il tipo di editor migliore adatto alla propria applicazione:

- L'applicazione salverà i dati nei file o No? Se salverà i dati nei file, saranno in un formato standard o personalizzato?

   Se si usa un formato di file standard, altri tipi di progetto oltre il progetto sarà in grado di aprire e leggere o scrivere dati a essi. Se si usa un formato di file personalizzati, tuttavia, solo il tipo di progetto sarà in grado di aprire e leggere o scrivere dati a essi.

   Se il progetto usa i file, è necessario personalizzare l'editor standard. Se il progetto non usa i file, ma piuttosto Usa gli elementi in un database o altri repository, è necessario creare un editor personalizzato.

- È necessario che l'editor per ospitare i controlli ActiveX?

   Se l'editor ospita controlli ActiveX, quindi implementare un editor di attivazione sul posto, come descritto [attivazione sul posto](../extensibility/in-place-activation.md). Se non ospita controlli ActiveX, quindi usare un editor di incorporamento semplificato oppure personalizzare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor predefinito.

- L'editor supporteranno più viste? Se si desidera che le visualizzazioni dell'editor sia visibile allo stesso tempo come editor predefinito, è necessario supportare più visualizzazioni.

   Se l'editor deve supportare visualizzazioni multiple, i dati del documento e oggetti di visualizzazione di documenti per l'editor devono essere oggetti separati. Per altre informazioni, vedere [supporta più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

   Se l'editor supporta più visualizzazioni, si prevede di usare la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] implementazione del buffer di testo dell'editor di base (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> oggetto) per l'oggetto dati del documento? Vale a dire, con cui si desidera supportare l'editor visualizza side-by-side con la [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale? La possibilità di eseguire questa operazione è la base di progettazione Windows Form...

- Se è necessario ospitare un editor esterno, l'editor incorporabili in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]?

   Se può essere incorporato, è necessario creare una finestra host per l'editor esterno e quindi chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> metodo e impostare il <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> valore di enumerazione da `DP_External`. Se l'editor non può essere incorporato, l'IDE creerà automaticamente una finestra separata per tale.

## <a name="in-this-section"></a>In questa sezione

[Procedura dettagliata: Creare un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md)\
Viene illustrato come creare un editor personalizzato.

[Procedura dettagliata: Aggiungere funzionalità a un editor personalizzato](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)\
Viene illustrato come aggiungere funzionalità a un editor personalizzato.

[Configurazione di inizializzazione e i metadati della finestra di progettazione](../extensibility/designer-initialization-and-metadata-configuration.md)\
Viene illustrato come inizializzare una finestra di progettazione.

[Alimentatore supporto dell'annullamento alle finestre di progettazione](../extensibility/supplying-undo-support-to-designers.md)\
Viene illustrato come fornire supporto per l'annullamento per le finestre di progettazione.

[Colorazione della sintassi negli editor personalizzati](../extensibility/syntax-coloring-in-custom-editors.md)\
Illustra la differenza tra nell'editor principale e negli editor personalizzati di colorazione della sintassi.

[I dati del documento e visualizzazione documento negli editor personalizzati](../extensibility/document-data-and-document-view-in-custom-editors.md)\
Viene illustrato come implementare i dati del documento e le visualizzazioni di documento negli editor personalizzati.

## <a name="related-sections"></a>Sezioni correlate

[Interfacce legacy nell'editor](../extensibility/legacy-interfaces-in-the-editor.md)\
Viene illustrato come accedere all'editor di base tramite l'API legacy.

[Sviluppare un servizio di linguaggio legacy](../extensibility/internals/developing-a-legacy-language-service.md)\
Viene illustrato come implementare un servizio di linguaggio.

[Estendere altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)\
Viene illustrato come creare elementi dell'interfaccia utente che corrispondono al resto del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>