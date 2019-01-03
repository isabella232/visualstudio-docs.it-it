---
title: All'interno l'Editor principale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 01756778c7937654339fe0fc41b752ed02659d3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53828524"
---
# <a name="inside-the-core-editor"></a>All'interno dell'editor di base
Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale è un set di numerosi componenti che consentono di modificare ed eseguire query su informazioni testuali. Se l'editor principale è stata personalizzata tramite l'API legacy, è possibile continuare a usare queste personalizzazioni, verranno instradate tramite schede dell'editor. Si consiglia, tuttavia, che è adattare le personalizzazioni per il nuovo editor delle API.  
  
 Di seguito sono riportati alcuni aspetti importanti dell'editor principale:  
  
-   Buffer di testo  
  
-   Visualizzazione di testo  
  
-   Finestra del codice  
  
-   Marcatori di testo  
  
-   Gestione di testo  
  
-   Integrazione con servizi di linguaggio  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Creare un'istanza di editor principale con l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Vengono fornite istruzioni dettagliate su come usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> per creare un'istanza di base dell'editor.  
  
 [Accedere al buffer di testo usando l'API legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Viene descritto il ruolo del buffer di testo nell'editor principale, vengono illustrati i sistemi associati vengono utilizzati per accedere al buffer che fornisce un elenco delle interfacce implementate dall'oggetto del buffer di testo, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 [Eventi nel buffer di testo nell'API legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fornisce un elenco delle interfacce utilizzate per la notifica degli eventi del buffer di testo.  
  
 [Procedura: Eseguire la registrazione per gli eventi nel buffer di testo con l'API legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Descrive come informare gli eventi nel buffer di testo.  
  
 [Usare la gestione di testo per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Illustra come ricevere la notifica degli eventi di gestione di testo e illustrato come utilizzare la gestione di testo per condividere informazioni sulle preferenze globali con i componenti di base dell'editor.  
  
 [Visualizzazione di theText accesso usando l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Viene descritto il ruolo della visualizzazione di testo nell'editor principale e sono elencate le interfacce implementate dal <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 [Personalizzare le finestre di codice usando l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Fornisce informazioni su come una finestra del codice viene usata per racchiudere la visualizzazione di testo, viene illustrato come la gestione di finestre di codice viene utilizzata per fornire le decorazioni alla finestra del codice e fornisce la notifica di nuove visualizzazioni.  
  
 [Modificare le impostazioni di visualizzazione tramite l'API legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Vengono fornite istruzioni dettagliate su come forzare le impostazioni di visualizzazione e come rimuovere l'impostazione forzata.  
  
 [Servizi di linguaggio e l'editor principale di](../extensibility/language-services-and-the-core-editor.md)  
 Descrive la creazione di istanze di un servizio di linguaggio per le decorazioni di codice di controllo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura dettagliata: Creare un editor principale e la registrazione di un tipo di file dell'editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Vengono fornite istruzioni dettagliate su come avviare l'editor principale dal codice gestito.  
  
 [Barra di riepilogo a discesa](../extensibility/drop-down-bar.md)  
 Viene spiegato come la barra di riepilogo a discesa viene utilizzata nella finestra del codice e vengono descritte le interfacce che vengono usate quando si implementa una barra di riepilogo a discesa.  
  
 [Usare marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Viene illustrato il concetto di marcatori di testo e su come vengono usati nell'editor principale ed elenca le interfacce che consentono di accedere e gestire i marcatori di testo.  
  
 [Procedura: Aggiungere i marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md)  
 Vengono fornite istruzioni dettagliate su come creare un marcatore di testo e come aggiungere un comando personalizzato a un menu di scelta rapida.  
  
 [Procedura: Creare i marcatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)  
 Vengono fornite istruzioni dettagliate su come creare un marcatore di testo personalizzato e su come specificare il tipo di marcatore come servizio.