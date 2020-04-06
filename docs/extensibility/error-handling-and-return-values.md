---
title: Gestione degli errori e valori restituiti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711926"
---
# <a name="error-handling-and-return-values"></a>Gestione degli errori e valori restituiti
VSPackage e COM utilizzano la stessa architettura per gli errori. Le `SetErrorInfo` `GetErrorInfo` funzioni e fanno parte dell'API (Application Programming Interface) Win32. Qualsiasi VSPackage nell'ambiente di sviluppo integrato (IDE) può chiamare queste API Win32 globali per registrare informazioni dettagliate sull'errore quando si riceve una notifica di errore. Fornisce [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] assembly di interoperabilità per gestire le informazioni sugli errori.

## <a name="interop-methods"></a>Metodi di interoperabilitàInterop methods
 Per comodità, l'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>fornisce un metodo, , da utilizzare anziché chiamare le API Win32. Nel codice <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>gestito utilizzare . Quando un `HRESULT` errore arriva al livello in cui deve essere visualizzato il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> messaggio di errore (spesso l'oggetto che implementa un gestore di comando), l'IDE utilizza un altro metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>, per visualizzare la finestra di messaggio appropriata. Nel codice gestito <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> utilizzare il metodo .

 Come implementatore VSPackage, gli oggetti `ISupportErrorInfo`COM implementano in genere . L'interfaccia `ISupportErrorInfo` assicura che le informazioni dettagliate sull'errore possano spostarsi verticalmente verso l'alto nella catena di chiamate. Gli oggetti che possono essere utilizzati tra `ISupportErrorInfo` processi o tra thread devono supportare per garantire che le informazioni dettagliate sull'errore venga eseguito correttamente il marshalling al chiamante.

 Tutti gli oggetti correlati a VSPackage e che sono coinvolti nell'estensione dell'IDE, incluse factory dell'editor, editor, gerarchie e servizi offerti, devono supportare informazioni dettagliate sull'errore. Mentre l'IDE non richiede questi `ISupportErrorInfo`oggetti VSPackage per implementare , è sempre consigliato.

 L'IDE è responsabile della segnalazione delle [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] informazioni `HRESULT` sugli errori e la visualizzazione a un utente di ogni volta che un viene propagato all'IDE. L'IDE è anche `ErrorInfo` il meccanismo per la creazione di oggetti.

## <a name="general-guidelines"></a>Linee guida generali
 È possibile <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> i metodi e per impostare e segnalare gli errori interni all'implementazione di VSPackage. Tuttavia, come regola generale, seguire queste linee guida per la gestione dei messaggi di errore nel pacchetto VSPackage:However, as a general rule, follow these guidelines for handling error messages in your VSPackage:

- Implementare negli oggetti COM VSPackage.Implement `ISupportErrorInfo` in your VSPackage COM objects.

- Creare un meccanismo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> segnalazione degli <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>errori che chiama il metodo negli oggetti che implementano .

- Consentire all'IDE di visualizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> gli errori agli utenti tramite il metodo.

## <a name="error-information-in-the-ide"></a>Informazioni sull'errore nell'IDE
 Le regole seguenti indicano come [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gestire le informazioni sugli errori nell'IDE:

- Come strategia difensiva per garantire che le informazioni di errore <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> non aggiornate <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> non vengano segnalate agli utenti, le funzioni che chiamano il metodo devono prima chiamare il metodo . Passare `null` per cancellare i messaggi di errore memorizzati nella cache prima di chiamare qualsiasi elemento che potrebbe impostare nuove informazioni sull'errore.

- Le funzioni che non segnalano direttamente i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> messaggi di errore possono `HRESULT`chiamare il metodo solo se restituiscono un errore. È consentito cancellare il `ErrorInfo` movimento sulla voce di <xref:Microsoft.VisualStudio.VSConstants.S_OK>una funzione o quando si restituisce . L'unica eccezione a questa regola `HRESULT` è quando una chiamata restituisce un errore da cui l'entità ricevente può ripristinare o ignorare in modo esplicito.

- Qualsiasi entità che ignora `HRESULT` in modo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> esplicito un errore deve chiamare il metodo con <xref:Microsoft.VisualStudio.VSConstants.S_OK>. In caso `ErrorInfo` contrario, l'oggetto potrebbe essere utilizzato accidentalmente quando un'altra parte genera un errore senza fornire il proprio `ErrorInfo`oggetto .

- Tutti i metodi `HRESULT` che hanno origine <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> un errore sono invitati a chiamare il metodo per fornire informazioni dettagliate sull'errore. Se l'oggetto `HRESULT` restituito `FACILITY_ITF` è un errore speciale, il `ErrorInfo`metodo è necessario per fornire un oggetto appropriato. Se l'errore restituito è un errore <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>di <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>sistema <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>standard (ad esempio, , , , e così <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> via.) è accettabile restituire il codice di errore senza chiamare in modo esplicito il metodo . Come strategia di codifica difensiva, `HRESULT` quando si origina <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> un errore `ErrorInfo` (inclusi gli errori di `null`sistema), chiamare sempre il metodo , descrivendo l'errore in modo più dettagliato o .

- Tutte le funzioni che restituiscono un errore originato da un'altra `HRESULT` chiamata devono `ErrorInfo` passare le informazioni ricevute dalla chiamata non riuscita nell'oggetto senza modificare l'oggetto.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automazione dei componenti)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Interfaccia ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
