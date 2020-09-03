---
title: All'interno dell'editor principale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - core editor
ms.assetid: 8265f31c-c45b-4858-882c-6d9f1e3b9083
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cf9bc42aec3aac5acc996487f99c7e1f29ca252c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203949"
---
# <a name="inside-the-core-editor"></a>Analisi dell'editor principale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] editor principale è costituito da un set di diversi componenti che consentono di modificare ed eseguire query sulle informazioni testuali. Se l'editor principale è stato personalizzato usando l'API legacy, è possibile continuare a usare queste personalizzazioni, che verranno instradate tramite gli adattatori dell'editor. È tuttavia consigliabile adattare le personalizzazioni alla nuova API dell'editor.  
  
 Di seguito sono riportati alcuni aspetti importanti dell'editor principale:  
  
- Buffer di testo  
  
- Visualizzazione testo  
  
- Finestra del codice  
  
- Marcatori di testo  
  
- Gestione testo  
  
- Integrazione con i servizi di linguaggio  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Creazione di un'istanza dell'editor principale tramite l'API legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)  
 Vengono fornite istruzioni dettagliate su come utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> per creare un'istanza dell'editor principale.  
  
 [Accesso al buffer di testo tramite l'API legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)  
 Viene illustrato il ruolo del buffer di testo nell'editor principale, vengono illustrati i sistemi associati utilizzati per accedere al buffer e viene fornito un elenco delle interfacce implementate dall'oggetto buffer di testo <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 [Eventi del buffer di testo nell'API legacy](../extensibility/text-buffer-events-in-the-legacy-api.md)  
 Fornisce un elenco delle interfacce utilizzate per la notifica di eventi del buffer di testo.  
  
 [Procedura: eseguire la registrazione per gli eventi del buffer di testo con l'API legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)  
 Viene descritto come consigliare gli eventi del buffer di testo.  
  
 [Uso della gestione testi per monitorare le impostazioni globali](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Viene illustrato il modo in cui gestione testo viene utilizzato per condividere le informazioni sulle preferenze globali con i componenti principali dell'editor e come ricevere notifiche di eventi di gestione del testo.  
  
 [Accesso alla visualizzazione testo tramite l'API legacy](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
 Descrive il ruolo della visualizzazione di testo nell'editor principale ed elenca le interfacce implementate dall' <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> oggetto.  
  
 [Personalizzazione delle finestre di codice tramite l'API legacy](../extensibility/customizing-code-windows-by-using-the-legacy-api.md)  
 Vengono fornite informazioni sulla modalità di utilizzo di una finestra del codice per racchiudere la visualizzazione di testo, viene illustrata la modalità di utilizzo di gestione finestre del codice per fornire decorazioni alla finestra del codice e viene fornita la notifica di nuove visualizzazioni.  
  
 [Modifica delle impostazioni di visualizzazione tramite l'API legacy](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Fornisce istruzioni dettagliate su come forzare le impostazioni di visualizzazione e su come rimuovere le impostazioni forzate.  
  
 [Servizi di linguaggio ed editor principale](../extensibility/language-services-and-the-core-editor.md)  
 Viene descritta la creazione di un'istanza di un servizio di linguaggio per controllare le decorazioni del codice.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Procedura dettagliata: Creazione di un editor principale e registrazione di un tipo di file dell'editor](../extensibility/walkthrough-creating-a-core-editor-and-registering-an-editor-file-type.md)  
 Vengono fornite istruzioni dettagliate su come avviare l'editor principale dal codice gestito.  
  
 [Barra a discesa](../extensibility/drop-down-bar.md)  
 Viene illustrato come viene utilizzata la barra a discesa nella finestra del codice e vengono descritte le interfacce utilizzate quando si implementa una barra a discesa.  
  
 [Uso di marcatori di testo con l'API legacy](../extensibility/using-text-markers-with-the-legacy-api.md)  
 Viene illustrato il concetto di marcatori di testo e il modo in cui vengono usati nell'editor principale ed elenca le interfacce usate per accedere e gestire i marcatori di testo.  
  
 [Procedura: Aggiungere marcatori di testo standard](../extensibility/how-to-add-standard-text-markers.md)  
 Fornisce istruzioni dettagliate su come creare un marcatore di testo e su come aggiungere un comando personalizzato a un menu di scelta rapida.  
  
 [Procedura: Creare marcatori di testo personalizzati](../extensibility/how-to-create-custom-text-markers.md)  
 Vengono fornite istruzioni dettagliate su come creare un marcatore di testo personalizzato e come specificare il tipo di marcatore come servizio.
