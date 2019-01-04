---
title: Supporto di controllo del codice sorgente | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 523c7de972958eff9224896d3a59543163eb7b9e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936815"
---
# <a name="supporting-source-control"></a>Supporto del controllo del codice sorgente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta estrazioni di file, le archiviazioni e altre operazioni di controllo per il progetto o un editor. Come un client, controllo codice sorgente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è progettato per interagire con un pacchetto di controllo del codice sorgente, ad esempio [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], che fornisce l'archiviazione, il controllo delle versioni e funzionalità di controllo per un set di file definito dinamicamente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Modello per i pacchetti del controllo del codice sorgente](../../extensibility/internals/model-for-source-control-packages.md)  
 Vengono descritte le interfacce deve implementare un tipo di progetto per il supporto di controllo del codice sorgente.  
  
 [Decisioni sulla progettazione](../../extensibility/internals/source-control-design-decisions.md)  
 Fornisce le domande con risposte cambiare modalità di implementazione un tipo di progetto.  
  
 [Dettagli configurazione](../../extensibility/internals/source-control-configuration-details.md)  
 Viene descritto il supporto di controllo del codice sorgente come cambia l'implementazione di un tipo di progetto.  
  
 [Linee guida aggiuntive per progetti ed editor](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Illustra le procedure consigliate per i tipi di progetto ed editor.  
  
 [Dettagli del runtime](../../extensibility/internals/source-control-runtime-details.md)  
 Viene descritto come registrare un progetto quando un utente viene aggiunto a un sistema di controllo del codice sorgente.  
  
## <a name="reference"></a>Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica all'ambiente o pacchetto controllo del codice sorgente che un file sta per essere modificato in memoria o salvato.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Consente ai progetti e le gerarchie di registrarsi con controllo del codice sorgente e ottenere informazioni sullo stato di controllo di origine.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementata in un sistema di progetto per fornire controllo del codice sorgente per i file di progetto ed elementi del progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Utilizzato dai progetti per l'ambiente per l'autorizzazione per aggiungere, rimuovere o rinominare un file o directory in una soluzione di query.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica ai client le modifiche apportate ai file di progetto o alle directory.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 Viene fornita una panoramica di progetti come blocchi predefiniti di base del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come progetti consentono di controllare la creazione e compilazione di codice.