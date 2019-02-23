---
title: Gli eventi nel Buffer di testo nell'API Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85c59ffd5b0289edf3b36fbd2ef7d0a62313af72
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715557"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventi nel buffer di testo nell'API legacy
Oggetto del buffer di testo genera vari eventi diversi che consentono di rispondere a situazioni diverse.

 Quando si usa l'API legacy, è necessario implementare le interfacce seguenti per ricevere la notifica delle modifiche al buffer di testo. Espone le interfacce per il buffer di testo tramite il `IConnectionPointContainer` interfaccia nel buffer di testo per ricevere la notifica della linea viene modificato dal buffer. Per altre informazioni, vedere [Procedura: Registrarsi per gli eventi nel buffer di testo con l'API legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Nel caso del `IVsTextStreamEvents` o `IVsTextLinesEvents` interfacce, le modifiche vengono restituite in entrambi unidimensionale o due coordinate, rispettivamente.

## <a name="text-buffer-interfaces"></a>Interfacce di buffer di testo
 Di seguito sono le interfacce implementate dall'oggetto del buffer di testo.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione delle azioni composte (vale a dire, azioni che vengono raggruppate in un'unità di annullamento/ripristino singolo).|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Abilita il salvataggio permanente dei dati del documento gestiti dal buffer di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti clienti.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Offre lettura e scrittura funzionalità usando le coordinate bidimensionali. Eredita da `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Consente di veloci e orientato al flusso e sequenziale al testo nel buffer.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Offre lettura e scrittura utilizzando coordinate unidimensionali di funzionalità. Eredita da `IVsTextBuffer`.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome o moniker, del buffer. È possibile archiviare i propri dati casuali nel buffer con questa interfaccia mediante la creazione di un GUID e usarlo come chiave.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta punti di connessione per gli eventi.|

## <a name="text-buffer-event-interfaces"></a>Interfacce di eventi del buffer di testo
 Di seguito sono le interfacce per la notifica di evento del buffer di testo.

|Interfaccia|Descrizione|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica ai client quando un nuovo servizio di linguaggio viene associato a un buffer di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica ai client quando un buffer di testo viene inizializzato e quando vengono apportate modifiche ai dati nel buffer di testo.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica ai client le modifiche apportate al buffer di testo sottostante in base alle coordinate unidimensionali.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica ai client le modifiche apportate al buffer di testo sottostante in base alle coordinate bidimensionali.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica ai client le modifiche ai dati dell'utente.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica ai client l'ultimo movimento di commit per attivare l'evento e fornisce l'intervallo di testo modificato. Il `IVsPreliminaryTextChangeCommitEvents` interfaccia non viene generata in risposta a annullare o ripristinare i comandi. Gli eventi vengono attivati solo per i buffer che dispongono di un gestore di annullamento. `IVsPreliminaryTextChangeCommitEvents` viene generato prima di altri eventi, ad esempio riformatta il listato, per assicurarsi che gli altri eventi non alterano il testo prima che le modifiche vengono salvate. Il pacchetto VSPackage deve monitorare uno il `IVsPreliminaryTextChangeCommitEvents` interfaccia o `IVsFinalTextChangeCommitEvents` interfaccia, ma non entrambi.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica ai client l'ultimo movimento di commit per attivare l'evento e fornisce l'intervallo di testo modificato. Il `IVsFinalTextChangeCommitEvents` interfaccia non viene generata in risposta a annullare o ripristinare i comandi. Gli eventi vengono attivati solo per i buffer che dispongono di un gestore di annullamento. `IVsFinalTextChangeCommitEvents` deve essere utilizzato solo da servizi di linguaggio o altri oggetti che detengono il controllo completo sulla modifica. Il pacchetto VSPackage deve monitorare uno il `IVsPreliminaryTextChangeCommitEvents` interfaccia o `IVsFinalTextChangeCommitEvents` interfaccia, ma non entrambi.|

## <a name="see-also"></a>Vedere anche

- [Accedere al buffer di testo usando l'API legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)
- [Procedura: Eseguire la registrazione per gli eventi nel buffer di testo con l'API legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)