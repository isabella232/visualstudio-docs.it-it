---
title: Query Edit Query Save (VSPackage del controllo del codice sorgente) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ad0cf7c3e1d3269dbe7ebee051cc32e2e8531ef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148894"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Query Edit Query Save (VSPackage di controllo del codice sorgente)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gli editor possono trasmettere gli eventi Query Edit Query Save (QEQS). [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Lo stub del controllo del codice sorgente implementa il servizio QEQS, in modo che sia il destinatario degli eventi QEQS. Questi eventi vengono quindi delegati al pacchetto VSPackage del controllo del codice sorgente attualmente attivo. Il VSPackage del controllo del codice sorgente attivo implementa i <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> metodi e. I metodi dell' `IVsQueryEditQuerySave2` interfaccia vengono in genere chiamati immediatamente prima che un documento venga modificato per la prima volta e immediatamente prima del salvataggio di un documento.  
  
## <a name="queryeditquerysave-events"></a>Eventi QueryEditQuerySave  
 Il pacchetto VSPackage del controllo del codice sorgente deve gestire gli eventi QEQS implementando l' `IVsQueryEditQuerySave2` interfaccia e i metodi necessari. Di seguito è riportata una breve descrizione dei due metodi che il pacchetto VSPackage deve implementare come minimo. L'implementazione effettiva deve essere conforme alla logica del modello del controllo del codice sorgente.  
  
### <a name="queryeditfiles-method"></a>Metodo QueryEditFiles  
 Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> viene chiamato quando un progetto o un editor desidera modificare un file. Idealmente, questo metodo viene chiamato *prima* che il file venga modificato e quando un file viene salvato. Quando viene richiamato, il `IVsQueryEditQuerySave2::QueryEditFiles` metodo controlla se i file specificati sono inclusi nel controllo del codice sorgente, se devono essere estratti e se possono essere ricaricati. Se le circostanze impediscono la modifica dei file, il `IVsQueryEditQuerySave2::QueryEditFiles` metodo indica al programma chiamante di annullare la modifica. È anche possibile che il chiamante specifichi una modalità di chiamata. In modalità "invisibile", questo metodo esegue un'azione solo se non viene visualizzata alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.  
  
 Il metodo si comporta in modo transazionale. ovvero, se la modifica viene annullata in un singolo file, la modifica viene annullata per tutti i file. Viceversa, se la modifica è consentita, è consentita per tutti i file. Se questo metodo consente di modificare una sola volta per un determinato set di file, deve sempre consentire la modifica nelle chiamate successive per lo stesso set di file. Il ciclo Allow-Edit continua fino a quando i file vengono chiusi, salvati e ricaricati. finché non cambiano gli attributi (proprietà); o fino a quando non viene modificato il pacchetto del controllo del codice sorgente. I casi da considerare nell'implementazione del `IVsQueryEditQuerySave2::QueryEditFiles` Metodo includono più file, file speciali, Annulla dall'utente e modifiche in memoria.  
  
### <a name="querysavefiles-method"></a>Metodo QuerySaveFiles  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A>Viene chiamato quando qualsiasi progetto o editor deve salvare un set di file. Quando viene richiamato, il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo controlla se i file specificati sono di sola lettura e se sono inclusi nel controllo del codice sorgente. Se i file devono essere estratti, la chiamata viene delegata al pacchetto del controllo del codice sorgente. Se le circostanze impediscono il salvataggio dei file, il `IVsQueryEditQuerySave2::QuerySaveFiles` metodo deve indicare all'editor di annullare il salvataggio. Come nel `IVsQueryEditQuerySave2::QueryEditFiles` metodo, è possibile che il chiamante specifichi una modalità di chiamata. In modalità "invisibile", questo metodo esegue un'azione solo se non viene visualizzata alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.  
  
 Questo metodo deve comportarsi in modo transazionale. ovvero, se il salvataggio viene annullato in un singolo file, il salvataggio viene annullato per tutti i file. Viceversa, se il salvataggio è consentito, è necessario che sia consentito per tutti i file. Come per il `IVsQueryEditQuerySave2::QueryEditFiles` metodo, i casi da considerare nell'implementazione del `IVsQueryEditQuerySave2::QuerySaveFiles` Metodo includono più file, file speciali, Annulla dall'utente e modifiche in memoria.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
