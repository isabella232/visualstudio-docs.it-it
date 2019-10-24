---
title: Query Edit Query Save (VSPackage del controllo del codice sorgente) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be12297bdaeb112d7421b02da1153ed62d6d14f8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724767"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Query Edit Query Save (VSPackage di controllo del codice sorgente)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] editor possono trasmettere eventi QEQS (query Edit Query Save). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] stub del controllo del codice sorgente implementa il servizio QEQS, in modo che sia il destinatario degli eventi QEQS. Questi eventi vengono quindi delegati al pacchetto VSPackage del controllo del codice sorgente attualmente attivo. Il VSPackage del controllo del codice sorgente attivo implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e i relativi metodi. I metodi dell'interfaccia `IVsQueryEditQuerySave2` vengono in genere chiamati immediatamente prima che un documento venga modificato per la prima volta e immediatamente prima del salvataggio di un documento.

## <a name="queryeditquerysave-events"></a>Eventi QueryEditQuerySave
 Il pacchetto VSPackage del controllo del codice sorgente deve gestire gli eventi QEQS implementando l'interfaccia `IVsQueryEditQuerySave2` e i metodi necessari. Di seguito è riportata una breve descrizione dei due metodi che il pacchetto VSPackage deve implementare come minimo. L'implementazione effettiva deve essere conforme alla logica del modello del controllo del codice sorgente.

### <a name="queryeditfiles-method"></a>Metodo QueryEditFiles
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> viene chiamato quando un progetto o un editor desidera modificare un file. Idealmente, questo metodo viene chiamato *prima* che il file venga modificato e quando un file viene salvato. Quando viene richiamato, il metodo `IVsQueryEditQuerySave2::QueryEditFiles` controlla se i file specificati sono inclusi nel controllo del codice sorgente, se devono essere estratti e se possono essere ricaricati. Se le circostanze impediscono la modifica dei file, il metodo `IVsQueryEditQuerySave2::QueryEditFiles` indica al programma chiamante di annullare la modifica. È anche possibile che il chiamante specifichi una modalità di chiamata. In modalità "invisibile", questo metodo esegue un'azione solo se non viene visualizzata alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.

 Il metodo si comporta in modo transazionale. ovvero, se la modifica viene annullata in un singolo file, la modifica viene annullata per tutti i file. Viceversa, se la modifica è consentita, è consentita per tutti i file. Se questo metodo consente di modificare una sola volta per un determinato set di file, deve sempre consentire la modifica nelle chiamate successive per lo stesso set di file. Il ciclo Allow-Edit continua fino a quando i file vengono chiusi, salvati e ricaricati. finché non cambiano gli attributi (proprietà); o fino a quando non viene modificato il pacchetto del controllo del codice sorgente. I casi da considerare nell'implementazione del metodo `IVsQueryEditQuerySave2::QueryEditFiles` includono più file, file speciali, Annulla dall'utente e modifiche in memoria.

### <a name="querysavefiles-method"></a>Metodo QuerySaveFiles
 Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> viene chiamato quando un progetto o un editor deve salvare un set di file. Quando viene richiamato, il metodo `IVsQueryEditQuerySave2::QuerySaveFiles` controlla se i file specificati sono di sola lettura e se sono inclusi nel controllo del codice sorgente. Se i file devono essere estratti, la chiamata viene delegata al pacchetto del controllo del codice sorgente. Se le circostanze impediscono il salvataggio dei file, il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo deve indicare all'editor di annullare il salvataggio. Come per il metodo `IVsQueryEditQuerySave2::QueryEditFiles`, è possibile che il chiamante specifichi una modalità di chiamata. In modalità "invisibile", questo metodo esegue un'azione solo se non viene visualizzata alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.

 Questo metodo deve comportarsi in modo transazionale. ovvero, se il salvataggio viene annullato in un singolo file, il salvataggio viene annullato per tutti i file. Viceversa, se il salvataggio è consentito, è necessario che sia consentito per tutti i file. Come per il metodo `IVsQueryEditQuerySave2::QueryEditFiles`, i casi da considerare nell'implementazione del metodo `IVsQueryEditQuerySave2::QuerySaveFiles` includono più file, file speciali, Annulla dall'utente e modifiche in memoria.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>