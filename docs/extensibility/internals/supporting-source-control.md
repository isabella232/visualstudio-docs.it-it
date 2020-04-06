---
title: Supporto del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704736"
---
# <a name="supporting-source-control"></a>Supporto del controllo del codice sorgente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]supporta estrazioni di file, archiviazioni e altre operazioni di controllo del codice sorgente per il progetto o l'editor. Come client del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controllo del codice sorgente, è progettato per interagire con un pacchetto di controllo del codice sorgente, ad [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]esempio , che fornisce funzionalità di archiviazione, controllo delle versioni e controllo per un set di file definito dinamicamente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Modello per i pacchetti del controllo del codice sorgente](../../extensibility/internals/model-for-source-control-packages.md)

 Vengono descritte le interfacce che un tipo di progetto deve implementare per supportare il controllo del codice sorgente.

- [Decisioni sulla progettazione](../../extensibility/internals/source-control-design-decisions.md)

 Vengono fornite domande le cui risposte modificano la modalità di implementazione di un tipo di progetto.

- [Dettagli di configurazione](../../extensibility/internals/source-control-configuration-details.md)

 Viene descritto come il supporto del controllo del codice sorgente modifica l'implementazione di un tipo di progetto.

- [Linee guida aggiuntive per progetti ed editor](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Vengono illustrate le procedure consigliate per i tipi di progetto e gli editor.

- [Dettagli del runtime](../../extensibility/internals/source-control-runtime-details.md)

 Viene descritto come registrare un progetto quando un utente lo aggiunge a un sistema di controllo del codice sorgente.

## <a name="reference"></a>Informazioni di riferimento
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>Indica all'ambiente o al pacchetto del controllo del codice sorgente che un file sta per essere modificato in memoria o salvato.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>Consente ai progetti e alle gerarchie di registrarsi con il controllo del codice sorgente e di ottenere informazioni sullo stato del controllo del codice sorgente.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>Implementato in un sistema di progetto per fornire il controllo del codice sorgente per i file di progetto e gli elementi di progetto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>Utilizzato dai progetti per eseguire una query sull'ambiente per ottenere l'autorizzazione per aggiungere, rimuovere o rinominare un file o una directory in una soluzione.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>Notifica ai client le modifiche apportate ai file o alle directory di progetto.

## <a name="related-sections"></a>Sezioni correlate
- [Tipi di progetto](../../extensibility/internals/project-types.md)

 Fornisce una panoramica dei progetti come [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] blocchi predefiniti di base dell'ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
