---
title: Salvataggio di query di modifica query (controllo del codice sorgente VSPackage) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705968"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Query Edit Query Save (VSPackage di controllo del codice sorgente)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gli editor possono trasmettere eventi QEQS (Query Edit Query Save). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Stub del controllo del codice sorgente implementa il servizio QEQS, in modo che sia il destinatario degli eventi QEQS. Questi eventi vengono quindi delegati al controllo del codice sorgente attualmente attivo VSPackage.These events are then delegated to the currently active source control VSPackage. Il controllo del codice <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> sorgente attivo VSPackage implementa i metodi e . I metodi `IVsQueryEditQuerySave2` dell'interfaccia vengono in genere chiamati immediatamente prima che un documento venga modificato per la prima volta e immediatamente prima del salvataggio di un documento.

## <a name="queryeditquerysave-events"></a>Eventi QueryEditQuerySave
 Il controllo del codice sorgente VSPackage deve gestire `IVsQueryEditQuerySave2` gli eventi QEQS implementando l'interfaccia e i metodi necessari. Di seguito è riportata una breve descrizione dei due metodi che il pacchetto VSPackage deve implementare almeno. L'implementazione effettiva deve essere conforme alla logica del modello di controllo del codice sorgente.

### <a name="queryeditfiles-method"></a>Metodo QueryEditFiles
 L'oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> viene chiamato quando un progetto o un editor desidera modificare un file. Idealmente, questo metodo viene chiamato *prima* che il file viene modificato e quando un file viene salvato. Quando viene richiamato, il `IVsQueryEditQuerySave2::QueryEditFiles` metodo controlla se i file specificato sono sotto controllo del codice sorgente, se devono essere estratti e se possono essere ricaricati. Se le circostanze impediscono che i `IVsQueryEditQuerySave2::QueryEditFiles` file siano modificabili, il metodo indica al programma chiamante di annullare la modifica. È anche possibile che il chiamante specifichi una modalità di chiamata. In modalità "silenziosa", questo metodo esegue un'azione solo se non causa la visualizzazione di alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.

 Il metodo si comporta in modo transazionale; ovvero, se la modifica viene annullata su un singolo file, la modifica viene annullata per tutti i file. Al contrario, se la modifica è consentita, è consentita per tutti i file. Se questo metodo consente la modifica una volta per un determinato set di file, deve sempre consentire la modifica nelle chiamate successive per lo stesso set di file. Il ciclo allow-edit continua fino a quando i file non vengono chiusi, salvati e ricaricati; fino a quando i loro attributi (proprietà) non cambiano; o fino a quando non viene modificato il pacchetto del controllo del codice sorgente. I casi da `IVsQueryEditQuerySave2::QueryEditFiles` considerare nell'implementazione del metodo includono più file, file speciali, annullare dall'utente e modifiche in memoria.

### <a name="querysavefiles-method"></a>Metodo QuerySaveFiles
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> viene chiamato quando qualsiasi progetto o editor deve salvare un set di file. Quando viene richiamato, il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo controlla se i file specificato sono di sola lettura e se sono in controllo del codice sorgente. Se i file devono essere estratti, la chiamata viene delegata al pacchetto del controllo del codice sorgente. Se le circostanze impediscono il `IVsQueryEditQuerySave2::QuerySaveFiles` salvataggio dei file, il metodo deve indicare all'editor di annullare il salvataggio. Come per `IVsQueryEditQuerySave2::QueryEditFiles` il metodo, è possibile che il chiamante specifichi una modalità di chiamata. In modalità "silenziosa", questo metodo esegue un'azione solo se non causa la visualizzazione di alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.

 Questo metodo deve comportarsi in modo transazionale; vale a dire, se il salvataggio viene annullato su un singolo file, il salvataggio viene annullato per tutti i file. Al contrario, se il salvataggio è consentito, deve essere consentito per tutti i file. Come con `IVsQueryEditQuerySave2::QueryEditFiles` il metodo, i `IVsQueryEditQuerySave2::QuerySaveFiles` casi da considerare nell'implementazione del metodo includono più file, file speciali, annullare dall'utente e modifiche in memoria.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
