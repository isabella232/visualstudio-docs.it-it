---
title: Gestione degli errori e i valori restituiti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85eee51941f6fb549c96dcc257335f9d77b6b0f2
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057132"
---
# <a name="error-handling-and-return-values"></a>Gestione degli errori e valori restituiti
I pacchetti VSPackage e COM utilizzano la stessa architettura per gli errori. Il `SetErrorInfo` e `GetErrorInfo` funzioni fanno parte delle Win32 application programming interface (API). Qualsiasi pacchetto VSPackage nell'ambiente di sviluppo integrato (IDE) possibile chiamare queste API Win32 globale al record informazioni dettagliate sull'errore quando si riceve una notifica di errore. Il [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce gli assembly di interoperabilità per gestire le informazioni sull'errore.  
  
## <a name="interop-methods"></a>Metodi di interoperabilità  
 Per maggiore praticità, l'IDE offre un metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, usare invece di chiamare le API Win32. Nel codice gestito, utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>. Quando un errore `HRESULT` raggiunge il livello in cui deve essere visualizzato il messaggio di errore (si tratta spesso dell'oggetto che implementa un' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> gestore comando), l'IDE Usa un altro metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, per visualizzare la finestra di messaggio appropriato. Nel codice gestito, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> (metodo).  
  
 Come responsabile dell'implementazione pacchetto VSPackage, in genere implementano gli oggetti COM `ISupportErrorInfo`. Il `ISupportErrorInfo` interfaccia garantisce che informazioni dettagliate sull'errore è possibile spostare verticalmente lungo la catena di chiamata. Gli oggetti che possono essere utilizzati in più processi o tra thread devono supportare `ISupportErrorInfo` per garantire che le informazioni dettagliate sull'errore viene eseguito correttamente il marshalling al chiamante.  
  
 Tutti gli oggetti che sono correlati ai pacchetti VSPackage e che sono interessati a estendere l'IDE, tra cui factory dell'editor, Editor, gerarchie e offerte di servizi, devono supportare informazioni dettagliate sull'errore. L'IDE non richiede questi oggetti VSPackage a implementare `ISupportErrorInfo`, è sempre consigliabile.  
  
 L'IDE è responsabile per la segnalazione delle informazioni di errore e la relativa visualizzazione a un utente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ogni volta che un `HRESULT` viene propagato all'IDE. L'IDE è inoltre il meccanismo per la creazione di `ErrorInfo` oggetti.  
  
## <a name="general-guidelines"></a>Indicazioni generali  
 È possibile usare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodi per impostare e segnalare gli errori interni a anche l'implementazione di VSPackage. Tuttavia, come regola generale, seguire queste linee guida per la gestione dei messaggi di errore nel pacchetto VSPackage:  
  
-   Implementare `ISupportErrorInfo` negli oggetti VSPackage COM.  
  
-   Creare un segnalazione meccanismo che chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo negli oggetti che implementano <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
-   Lasciare l'IDE visualizza errori agli utenti tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> (metodo).  
  
## <a name="error-information-in-the-ide"></a>Informazioni sugli errori nell'IDE  
 Le regole seguenti indicano come gestire le informazioni di errore nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:  
  
-   Come una strategia difensiva per garantire che le informazioni di errore non aggiornate non viene segnalata agli utenti, le funzioni che chiamano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo chiamare prima il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (metodo). Passare `null` cancellare i messaggi di errore memorizzato nella cache prima di chiamare qualsiasi elemento che potrebbe impostare nuove informazioni sull'errore.  
  
-   Le funzioni che non comunicano direttamente i messaggi di errore sono consentite solo per chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo se restituiscano un errore `HRESULT`. È possibile cancellare il `ErrorInfo` sulla voce a una funzione o la restituzione <xref:Microsoft.VisualStudio.VSConstants.S_OK>. L'unica eccezione a questa regola è quando una chiamata restituisce un errore `HRESULT` da cui l'entità ricevente può ripristinare in modo esplicito o ignorare.  
  
-   Qualsiasi entità che un errore viene ignorato in modo esplicito `HRESULT` necessario chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo con <xref:Microsoft.VisualStudio.VSConstants.S_OK>. In caso contrario, il `ErrorInfo` oggetto può essere usato quando un'altra entità genera un errore senza fornire le proprie accidentalmente `ErrorInfo`.  
  
-   Tutti i metodi che hanno origine di un errore `HRESULT` consigliabile chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo per fornire informazioni dettagliate sull'errore. Se l'oggetto restituito `HRESULT` è una speciale `FACILITY_ITF` errore, quindi il metodo deve fornire il giusto `ErrorInfo`oggetto. Se l'errore restituito è un errore di sistema standard (ad esempio, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>, <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>, <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>e così via.) accettabile per restituire il codice di errore senza chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> (metodo). Una strategia di codifica difensive, quando un errore proveniente `HRESULT` (tra cui errori di sistema), chiamare sempre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo, con `ErrorInfo` che descrive l'errore illustrato più dettagliatamente il o `null`.  
  
-   Tutte le funzioni che restituiscono un errore ha avuto origine da un'altra chiamata deve passare le informazioni che è stato ricevuto l'errore chiamano nel `HRESULT` senza modificare il `ErrorInfo` oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (componente di automazione)](http://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)   
 [Interfaccia ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
