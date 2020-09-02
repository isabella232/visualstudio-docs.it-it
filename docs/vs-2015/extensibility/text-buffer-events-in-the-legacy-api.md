---
title: Eventi del buffer di testo nell'API legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186409"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventi del buffer di testo nell'API legacy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'oggetto buffer di testo emette diversi eventi che consentono di rispondere a situazioni diverse.  
  
 Quando si usa l'API legacy, è necessario implementare le interfacce seguenti per ricevere una notifica delle modifiche apportate al buffer di testo. Esporre le interfacce al buffer di testo usando l' `IConnectionPointContainer` interfaccia sul buffer di testo per ricevere la notifica delle modifiche della riga dal buffer. Per altre informazioni, vedere [procedura: registrare gli eventi del buffer di testo con l'API legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). Nel caso di `IVsTextStreamEvents` interfacce o `IVsTextLinesEvents` , le modifiche vengono restituite rispettivamente in coordinate unidimensionali o bidimensionali.  
  
## <a name="text-buffer-interfaces"></a>Interfacce del buffer di testo  
 Di seguito sono riportate le interfacce implementate dall'oggetto buffer di testo.  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Consente la creazione di azioni composte, ovvero azioni raggruppate in una singola unità di annullamento/ripristino.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Abilita la persistenza dei dati del documento gestiti dal buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornisce servizi di base; utilizzato da molti client.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornisce funzionalità di lettura e scrittura con coordinate bidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fornisce accesso sequenziale veloce e orientato al flusso al testo nel buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornisce funzionalità di lettura e scrittura usando coordinate unidimensionali. Eredita dall'oggetto `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornisce l'accesso a una raccolta generica di proprietà. La proprietà più importante è il nome, o moniker, del buffer. È possibile archiviare i dati casuali nel buffer con questa interfaccia creando un GUID e usandolo come chiave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Supporta i punti di connessione per gli eventi.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfacce di eventi del buffer di testo  
 Di seguito sono riportate le interfacce per la notifica degli eventi del buffer di testo  
  
|Interfaccia|Descrizione|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica ai client quando un nuovo servizio di linguaggio viene associato a un buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica ai client quando viene inizializzato un buffer di testo e quando vengono apportate modifiche ai dati nel buffer di testo.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica ai client le modifiche apportate al buffer di testo sottostante in coordinate unidimensionali.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica ai client le modifiche apportate al buffer di testo sottostante in coordinate bidimensionali.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica ai client le modifiche apportate ai dati utente.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica ai client l'ultimo movimento di commit per attivare l'evento e fornisce l'intervallo di testo modificato. L' `IVsPreliminaryTextChangeCommitEvents` interfaccia non viene attivata in risposta ai comandi Annulla o Ripeti. Gli eventi vengono attivati solo per i buffer che dispongono di un gestore di annullamento. `IVsPreliminaryTextChangeCommitEvents` viene generato prima di altri eventi, ad esempio un elenco, per assicurarsi che gli altri eventi non modifichino il testo prima del commit delle modifiche. Il pacchetto VSPackage deve monitorare l' `IVsPreliminaryTextChangeCommitEvents` interfaccia o l' `IVsFinalTextChangeCommitEvents` interfaccia, ma non entrambi.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica ai client l'ultimo movimento di commit per attivare l'evento e fornisce l'intervallo di testo modificato. L' `IVsFinalTextChangeCommitEvents` interfaccia non viene attivata in risposta ai comandi Annulla o Ripeti. Gli eventi vengono attivati solo per i buffer che dispongono di un gestore di annullamento. `IVsFinalTextChangeCommitEvents` deve essere utilizzato solo da servizi di linguaggio o da altri oggetti che dispongono di un controllo completo sulla modifica. Il pacchetto VSPackage deve monitorare l' `IVsPreliminaryTextChangeCommitEvents` interfaccia o l' `IVsFinalTextChangeCommitEvents` interfaccia, ma non entrambi.|  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso al buffer di testo tramite l'API legacy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Procedura: eseguire la registrazione per gli eventi del buffer di testo con l'API legacy](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
