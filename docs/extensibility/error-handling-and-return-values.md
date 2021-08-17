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
ms.openlocfilehash: 187b2896026b7550d4e67df7cbf85d69dae99ac99184be5f456b19d7a862b16d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376885"
---
# <a name="error-handling-and-return-values"></a>Gestione degli errori e valori restituiti
I pacchetti VSPackage e COM usano la stessa architettura per gli errori. Le `SetErrorInfo` funzioni e fanno parte `GetErrorInfo` dell'API Win32. Qualsiasi VSPackage nell'ambiente di sviluppo integrato (IDE) può chiamare queste API Win32 globali per registrare informazioni dettagliate sugli errori quando si riceve una notifica di errore. fornisce [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] assembly di interoperabilità per gestire le informazioni sugli errori.

## <a name="interop-methods"></a>Metodi di interoperabilità
 Per praticità, l'IDE fornisce un metodo, , da usare invece di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> chiamare le API Win32. Nel codice gestito usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Quando un errore arriva al livello in cui deve essere visualizzato il messaggio di errore (spesso si tratta dell'oggetto che implementa un gestore comandi), l'IDE usa un altro metodo, , per visualizzare la finestra di messaggio `HRESULT` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> appropriata. Nel codice gestito usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo .

 In quanto implementatore di VSPackage, gli oggetti COM in genere implementano `ISupportErrorInfo` . `ISupportErrorInfo`L'interfaccia garantisce che le informazioni dettagliate sugli errori possano essere spostate verticalmente verso l'alto nella catena di chiamate. Gli oggetti che possono essere usati tra processi o thread devono supportare per garantire che venga eseguito correttamente il marshalling delle informazioni dettagliate sugli errori `ISupportErrorInfo` al chiamante.

 Tutti gli oggetti correlati ai pacchetti VSPackage e coinvolti nell'estensione dell'IDE, incluse le factory dell'editor, gli editor, le gerarchie e i servizi offerti, devono supportare informazioni dettagliate sugli errori. Anche se l'IDE non richiede questi oggetti VSPackage per implementare `ISupportErrorInfo` , è sempre consigliato.

 L'IDE è responsabile della segnalazione delle informazioni sugli errori e della visualizzazione a un utente di ogni volta che un oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` viene propagato all'IDE. L'IDE è anche il meccanismo per la creazione di `ErrorInfo` oggetti.

## <a name="general-guidelines"></a>Linee guida generali
 È possibile usare i metodi e anche per impostare e segnalare errori interni <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> all'implementazione di VSPackage. Tuttavia, come regola generale, seguire queste linee guida per la gestione dei messaggi di errore nel pacchetto VSPackage:

- Implementare `ISupportErrorInfo` negli oggetti COM del pacchetto VSPackage.

- Creare un meccanismo di segnalazione errori che chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> il metodo negli oggetti che implementano <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Consentire all'IDE di visualizzare gli errori agli utenti tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodo .

## <a name="error-information-in-the-ide"></a>Informazioni sugli errori nell'IDE
 Le regole seguenti indicano come gestire le informazioni sugli errori [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nell'IDE:

- Come strategia difensiva per garantire che le informazioni sull'errore non aggiornamento non vengono segnalate agli utenti, le funzioni che chiamano il metodo devono <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> prima chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Passare per `null` cancellare i messaggi di errore memorizzati nella cache prima di chiamare qualsiasi elemento che potrebbe impostare nuove informazioni sull'errore.

- Le funzioni che non segnalano direttamente messaggi di errore possono chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> solo se restituiscono un errore `HRESULT` . È consentito cancellare l'oggetto `ErrorInfo` nella voce di una funzione o quando viene restituito <xref:Microsoft.VisualStudio.VSConstants.S_OK> . L'unica eccezione a questa regola è quando una chiamata restituisce un errore da cui l'entità ricevente può recuperare o `HRESULT` ignorare in modo esplicito.

- Qualsiasi parte che ignora in modo esplicito un `HRESULT` errore deve chiamare il metodo con <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.VSConstants.S_OK> . In caso contrario, `ErrorInfo` l'oggetto potrebbe essere usato accidentalmente quando un'altra parte genera un errore senza fornire il proprio `ErrorInfo` .

- Tutti i metodi che hanno origine un `HRESULT` errore sono invitati a chiamare il metodo per fornire informazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> dettagliate sull'errore. Se `HRESULT` l'oggetto restituito è `FACILITY_ITF` un errore speciale, il metodo è necessario per fornire un oggetto `ErrorInfo` appropriato. Se l'errore restituito è un errore di sistema standard ,ad esempio , , , e così via, è accettabile restituire il codice di errore senza chiamare in modo esplicito <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> il metodo <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Come strategia di scrittura di codice difensiva, quando si ha origine un errore (inclusi gli errori di sistema), chiamare sempre il metodo , con una descrizione più dettagliata dell'errore `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> o `ErrorInfo` `null` .

- Tutte le funzioni che restituiscono un errore originato da un'altra chiamata devono passare le informazioni ricevute dalla chiamata non riuscita in `HRESULT` senza modificare `ErrorInfo` l'oggetto.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automazione dei componenti)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Interfaccia ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
