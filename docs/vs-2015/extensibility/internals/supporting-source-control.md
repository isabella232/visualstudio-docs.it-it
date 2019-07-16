---
title: Supporto di controllo del codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1166197a5c79dcb0d1ddf4018227914346a6172
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156072"
---
# <a name="supporting-source-control"></a>Supporto del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta estrazioni di file, le archiviazioni e altre operazioni di controllo per il progetto o un editor. Come un client, controllo codice sorgente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è progettato per interagire con un pacchetto di controllo del codice sorgente, ad esempio [!INCLUDE[vsvss](../../includes/vsvss-md.md)], che fornisce l'archiviazione, il controllo delle versioni e funzionalità di controllo per un set di file definito dinamicamente.  
  
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
 Viene fornita una panoramica di progetti come blocchi predefiniti di base del [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come progetti consentono di controllare la creazione e compilazione di codice.
