---
title: Salvataggio query di modifica query (VSPackage del controllo del codice sorgente) | Microsoft Docs
description: Informazioni sul ruolo degli eventi Query-Edit Query-Save e su come vengono gestiti dal pacchetto VSPackage del controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d1945628c68002db457fd0a6751542e3009ded9a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636060"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>Query Edit Query Save (VSPackage di controllo del codice sorgente)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Gli editor possono trasmettere gli eventi di query di salvataggio di query (QEQS). [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Lo stub del controllo del codice sorgente implementa il servizio QEQS, in modo che sia il destinatario degli eventi QEQS. Questi eventi vengono quindi delegati al VSPackage del controllo del codice sorgente attualmente attivo. Il pacchetto VSPackage del controllo del codice sorgente attivo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> implementa e i relativi metodi. I metodi dell'interfaccia vengono in genere chiamati immediatamente prima che un documento venga modificato per la prima volta e immediatamente `IVsQueryEditQuerySave2` prima del salvataggio di un documento.

## <a name="queryeditquerysave-events"></a>Eventi QueryEditQuerySave
 Il pacchetto VSPackage del controllo del codice sorgente deve gestire gli eventi QEQS implementando `IVsQueryEditQuerySave2` l'interfaccia e i metodi necessari. Di seguito è riportata una breve descrizione dei due metodi che il pacchetto VSPackage deve implementare almeno. L'implementazione effettiva deve essere conforme alla logica del modello di controllo del codice sorgente.

### <a name="queryeditfiles-method"></a>Metodo QueryEditFiles
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A>L'oggetto viene chiamato quando un progetto o un editor desidera modificare un file. Idealmente, questo metodo viene chiamato *prima* della modifica del file e del salvataggio di un file. Quando viene richiamato, il metodo controlla se i file sono sotto controllo del codice sorgente, se devono essere estratti e se possono `IVsQueryEditQuerySave2::QueryEditFiles` essere ricaricati. Se le circostanze impediscono la modifica dei file, il metodo indica `IVsQueryEditQuerySave2::QueryEditFiles` al programma chiamante di annullare la modifica. È anche possibile che il chiamante specifica una modalità di chiamata. In modalità "invisibile all'utente", questo metodo esegue un'azione solo se non causa la visualizzazione di alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.

 Il metodo si comporta in modo transazionale. ciò significa che se la modifica viene annullata in un singolo file, la modifica viene annullata per tutti i file. Al contrario, se la modifica è consentita, è consentita per tutti i file. Se questo metodo consente la modifica una sola volta per un determinato set di file, deve sempre consentire la modifica nelle chiamate successive per lo stesso set di file. Il ciclo allow-edit continua fino a quando i file non vengono chiusi, salvati e ricaricati. fino a quando i relativi attributi (proprietà) non cambiano; o fino a quando il pacchetto di controllo del codice sorgente non viene modificato. I casi da considerare nell'implementazione del metodo includono più file, file speciali, annullamento da parte dell'utente e modifiche `IVsQueryEditQuerySave2::QueryEditFiles` in memoria.

### <a name="querysavefiles-method"></a>Metodo QuerySaveFiles
 Viene <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> chiamato quando un progetto o un editor deve salvare un set di file. Quando viene richiamato, il metodo controlla se i file sono di sola lettura e se sono `IVsQueryEditQuerySave2::QuerySaveFiles` nel controllo del codice sorgente. Se i file devono essere estratti, la chiamata viene delegata al pacchetto di controllo del codice sorgente. Se le circostanze impediscono il salvataggio dei file, il metodo `IVsQueryEditQuerySave2::QuerySaveFiles` deve indicare all'editor di annullare il salvataggio. Come per il `IVsQueryEditQuerySave2::QueryEditFiles` metodo , è possibile che il chiamante specifica una modalità di chiamata. In modalità "invisibile all'utente", questo metodo esegue un'azione solo se non causa la visualizzazione di alcuna interfaccia utente. Se l'interfaccia utente è inevitabile, è necessario restituire un flag per indicare il problema.

 Questo metodo deve comportarsi in modo transazionale. ciò significa che se il salvataggio viene annullato in un singolo file, il salvataggio viene annullato per tutti i file. Al contrario, se il salvataggio è consentito, deve essere consentito per tutti i file. Come con il metodo , i casi da considerare nell'implementazione del metodo includono più file, file speciali, annullamento dall'utente e `IVsQueryEditQuerySave2::QueryEditFiles` `IVsQueryEditQuerySave2::QuerySaveFiles` modifiche in memoria.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
