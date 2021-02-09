---
title: Gestione degli errori e valori restituiti | Microsoft Docs
description: Informazioni su come Visual Studio SDK fornisce assembly di interoperabilità per registrare informazioni dettagliate sugli errori durante la ricezione di una notifica di errore.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 530430852d621ea4aaf62bf2c86365609f26cf8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883363"
---
# <a name="error-handling-and-return-values"></a>Gestione degli errori e valori restituiti
I pacchetti VSPackage e COM usano la stessa architettura per gli errori. Le `SetErrorInfo` `GetErrorInfo` funzioni e fanno parte dell'Application Programming Interface Win32 (API). Qualsiasi VSPackage nel Integrated Development Environment (IDE) può chiamare queste API Win32 globali per registrare informazioni dettagliate sugli errori durante la ricezione di una notifica di errore. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Fornisce assembly di interoperabilità per gestire le informazioni sugli errori.

## <a name="interop-methods"></a>Metodi di interoperabilità
 Per praticità, l'IDE fornisce un metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> , da usare anziché chiamare le API Win32. Nell'uso del codice gestito <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Quando un errore `HRESULT` raggiunge il livello in cui deve essere visualizzato il messaggio di errore (spesso è l'oggetto che implementa un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> gestore di comandi), l'IDE utilizza un altro metodo, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> , per visualizzare la finestra di messaggio appropriata. Nel codice gestito usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo.

 Come implementatore VSPackage, gli oggetti COM implementano in genere `ISupportErrorInfo` . L' `ISupportErrorInfo` interfaccia garantisce che le informazioni dettagliate sugli errori possano essere spostate verticalmente verso l'alto nella catena di chiamate. Gli oggetti che possono essere utilizzati tra processi o tra thread devono supportare `ISupportErrorInfo` per garantire che le informazioni dettagliate sugli errori vengano correttamente sottoposte a marshalling al chiamante.

 Tutti gli oggetti correlati a VSPackage e che sono interessati all'estensione dell'IDE, incluse le factory dell'editor, gli editor, le gerarchie e i servizi offerti, devono supportare informazioni dettagliate sugli errori. Sebbene l'IDE non richieda l'implementazione di questi oggetti VSPackage `ISupportErrorInfo` , è sempre consigliato.

 L'IDE è responsabile della segnalazione delle informazioni sugli errori e della relativa visualizzazione a un utente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando un `HRESULT` viene propagato all'IDE. L'IDE è anche il meccanismo per la creazione di `ErrorInfo` oggetti.

## <a name="general-guidelines"></a>Linee guida generali
 È possibile usare i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodi e per impostare e segnalare gli errori interni all'implementazione di VSPackage. Tuttavia, come regola generale, attenersi alle linee guida seguenti per la gestione dei messaggi di errore nel pacchetto VSPackage:

- Implementare `ISupportErrorInfo` negli oggetti com VSPackage.

- Creare un meccanismo di segnalazione degli errori che chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo in oggetti che implementano <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Consentire all'IDE di visualizzare gli errori agli utenti tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo.

## <a name="error-information-in-the-ide"></a>Informazioni sugli errori nell'IDE
 Le regole seguenti indicano come gestire le informazioni sugli errori nell' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:

- Come strategia difensiva per garantire che le informazioni sugli errori non aggiornate non vengano segnalate agli utenti, le funzioni che chiamano il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo devono prima chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo. Passare `null` per cancellare i messaggi di errore memorizzati nella cache prima di chiamare qualsiasi elemento che potrebbe impostare nuove informazioni sull'errore.

- Le funzioni che non segnalano direttamente i messaggi di errore sono autorizzati a chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo solo se restituiscono un errore `HRESULT` . È possibile cancellare l'oggetto `ErrorInfo` sulla voce di una funzione o quando viene restituito <xref:Microsoft.VisualStudio.VSConstants.S_OK> . L'unica eccezione a questa regola è rappresentata dal caso in cui una chiamata restituisce un errore `HRESULT` da cui l'entità ricevente può eseguire il ripristino o ignorare in modo esplicito.

- Qualsiasi entità che ignori esplicitamente un errore `HRESULT` deve chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo con <xref:Microsoft.VisualStudio.VSConstants.S_OK> . In caso contrario, l' `ErrorInfo` oggetto potrebbe essere accidentalmente utilizzato quando un'altra parte genera un errore senza specificarne uno `ErrorInfo` .

- Tutti i metodi che hanno origine a un errore `HRESULT` sono invitati a chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo per fornire informazioni dettagliate sugli errori. Se l' `HRESULT` oggetto restituito è un `FACILITY_ITF` errore speciale, il metodo è necessario per fornire un `ErrorInfo` oggetto appropriato. Se l'errore restituito è un errore di sistema standard (ad esempio,,, <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> , <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> e così via), è accettabile restituire il codice di errore senza chiamare esplicitamente il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo. Come strategia di codifica difensiva, quando viene originato un errore `HRESULT` (inclusi gli errori di sistema), chiamare sempre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodo, con la `ErrorInfo` Descrizione dell'errore in modo più dettagliato o `null` .

- Tutte le funzioni che restituiscono un errore originato da un'altra chiamata devono passare le informazioni ricevute dalla chiamata non riuscita in `HRESULT` senza modificare l' `ErrorInfo` oggetto.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automazione componenti)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Interfaccia ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
