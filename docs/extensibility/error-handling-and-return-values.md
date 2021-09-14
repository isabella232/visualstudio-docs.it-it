---
title: Gestione degli errori e valori restituiti | Microsoft Docs
description: Informazioni su come Visual Studio SDK fornisce assembly di interoperabilità per registrare informazioni dettagliate sugli errori quando si riceve una notifica di errore.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9f69f998dbfe984a272f86227640fe5eaec51cae
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634643"
---
# <a name="error-handling-and-return-values"></a>Gestione degli errori e valori restituiti
I pacchetti VSPackage e COM usano la stessa architettura per gli errori. Le `SetErrorInfo` funzioni e fanno parte `GetErrorInfo` dell'API (Application Programming Interface) Win32. Qualsiasi VSPackage nell'ambiente di sviluppo integrato (IDE) può chiamare queste API Win32 globali per registrare informazioni dettagliate sugli errori quando si riceve una notifica di errore. fornisce [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] assembly di interoperabilità per gestire le informazioni sugli errori.

## <a name="interop-methods"></a>Metodi di interoperabilità
 Per praticità, l'IDE fornisce un metodo, , da usare invece di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> chiamare le API Win32. Nel codice gestito usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Quando un errore arriva al livello in cui deve essere visualizzato il messaggio di errore (spesso si tratta dell'oggetto che implementa un gestore di comandi), l'IDE usa un altro metodo, , per visualizzare la finestra di messaggio `HRESULT` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> appropriata. Nel codice gestito usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo .

 In quanto implementatore di VSPackage, gli oggetti COM implementano in genere `ISupportErrorInfo` . `ISupportErrorInfo`L'interfaccia garantisce che le informazioni dettagliate sugli errori possano spostarsi verticalmente verso l'alto nella catena di chiamate. Gli oggetti che possono essere usati tra processi o tra thread devono supportare per garantire che venga eseguito correttamente il marshalling delle informazioni dettagliate sugli errori `ISupportErrorInfo` al chiamante.

 Tutti gli oggetti correlati a VSPackage e coinvolti nell'estensione dell'IDE, tra cui editor factory, editor, gerarchie e servizi offerti, devono supportare informazioni dettagliate sugli errori. Anche se l'IDE non richiede questi oggetti VSPackage per implementare `ISupportErrorInfo` , è sempre consigliato.

 L'IDE è responsabile della segnalazione di informazioni sugli errori e della visualizzazione a un utente di ogni volta che un oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` viene propagato all'IDE. L'IDE è anche il meccanismo per la creazione di `ErrorInfo` oggetti.

## <a name="general-guidelines"></a>Linee guida generali
 È possibile usare i metodi e per impostare e segnalare gli errori interni anche <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> all'implementazione di VSPackage. Tuttavia, come regola generale, seguire queste linee guida per la gestione dei messaggi di errore nel pacchetto VSPackage:

- Implementare `ISupportErrorInfo` negli oggetti COM VSPackage.

- Creare un meccanismo di segnalazione degli errori che chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> il metodo negli oggetti che implementano <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Consentire all'IDE di visualizzare gli errori agli utenti tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo .

## <a name="error-information-in-the-ide"></a>Informazioni sugli errori nell'IDE
 Le regole seguenti indicano come gestire le informazioni sugli errori [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nell'IDE:

- Come strategia difensiva per garantire che le informazioni sull'errore non disponibili non vengono segnalate agli utenti, le funzioni che chiamano il metodo devono prima <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo . Passare per `null` cancellare i messaggi di errore memorizzati nella cache prima di chiamare qualsiasi elemento che potrebbe impostare nuove informazioni sull'errore.

- Le funzioni che non segnalano direttamente messaggi di errore possono chiamare il metodo solo se <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> restituiscono un errore `HRESULT` . È consentito cancellare l'oggetto nella voce di una funzione `ErrorInfo` o quando viene restituito <xref:Microsoft.VisualStudio.VSConstants.S_OK> . L'unica eccezione a questa regola è quando una chiamata restituisce un errore da cui l'entità ricevente può recuperare `HRESULT` o ignorare in modo esplicito.

- Qualsiasi entità che ignora in modo esplicito un errore `HRESULT` deve chiamare il metodo con <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.VSConstants.S_OK> . In caso contrario, `ErrorInfo` l'oggetto potrebbe essere usato accidentalmente quando un'altra parte genera un errore senza fornire il proprio `ErrorInfo` .

- Tutti i metodi che hanno origine un `HRESULT` errore sono invitati a chiamare il metodo per fornire informazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> dettagliate sugli errori. Se l'oggetto `HRESULT` restituito è `FACILITY_ITF` un errore speciale, il metodo è necessario per fornire un oggetto `ErrorInfo` appropriato. Se l'errore restituito è un errore di sistema standard,ad esempio <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> , , , e così <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> via, è accettabile restituire il codice di errore senza chiamare in modo esplicito il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo . Come strategia di scrittura del codice difensiva, quando si ha origine un errore (inclusi gli errori di sistema), chiamare sempre il metodo , con la descrizione più dettagliata dell'errore, `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> o `ErrorInfo` `null` .

- Tutte le funzioni che restituiscono un errore originato da un'altra chiamata devono passare le informazioni ricevute dalla chiamata non riuscita in senza `HRESULT` modificare `ErrorInfo` l'oggetto .

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Automazione componenti)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Interfaccia ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
