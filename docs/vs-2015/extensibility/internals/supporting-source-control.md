---
title: Supporto del controllo del codice sorgente | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156072"
---
# <a name="supporting-source-control"></a>Supporto del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] supporta le estrazioni di file, le archiviazioni e altre operazioni di controllo del codice sorgente per il progetto o l'editor. Come client del controllo del codice sorgente, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] è progettato per interagire con un pacchetto di controllo del codice sorgente, ad esempio [!INCLUDE[vsvss](../../includes/vsvss-md.md)] , che fornisce funzionalità di archiviazione, controllo delle versioni e controllo per un set di file definito in modo dinamico.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Modello per i pacchetti del controllo del codice sorgente](../../extensibility/internals/model-for-source-control-packages.md)  
 Descrive le interfacce che devono essere implementate da un tipo di progetto per supportare il controllo del codice sorgente.  
  
 [Decisioni sulla progettazione](../../extensibility/internals/source-control-design-decisions.md)  
 Fornisce domande le cui risposte cambiano come si implementa un tipo di progetto.  
  
 [Dettagli di configurazione](../../extensibility/internals/source-control-configuration-details.md)  
 Descrive in che modo il supporto del controllo del codice sorgente modifica l'implementazione di un tipo di progetto.  
  
 [Linee guida aggiuntive per progetti ed editor](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)  
 Illustra le procedure consigliate per i tipi di progetto e gli editor.  
  
 [Dettagli del runtime](../../extensibility/internals/source-control-runtime-details.md)  
 Viene descritto come registrare un progetto quando un utente lo aggiunge a un sistema di controllo del codice sorgente.  
  
## <a name="reference"></a>Riferimento  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>  
 Indica all'ambiente o al pacchetto del controllo del codice sorgente che un file sta per essere modificato in memoria o salvato.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>  
 Consente a progetti e gerarchie di registrarsi con il controllo del codice sorgente e ottenere informazioni sullo stato del controllo del codice sorgente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>  
 Implementata in un sistema del progetto per fornire il controllo del codice sorgente per i file e gli elementi del progetto.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>  
 Utilizzato dai progetti per eseguire una query sull'ambiente per ottenere l'autorizzazione per aggiungere, rimuovere o rinominare un file o una directory in una soluzione.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>  
 Notifica ai client le modifiche apportate ai file o alle directory di progetto.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)  
 Viene fornita una panoramica dei progetti come blocchi predefiniti di base dell' [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Integrated Development Environment (IDE). Sono disponibili collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
