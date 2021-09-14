---
title: Supporto del controllo del codice sorgente | Microsoft Docs
description: Informazioni su Visual Studio le estrazioni di file, le archiviazioni e altre operazioni di controllo del codice sorgente per il progetto o l'editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 4601c7e10d3f3092ad274e0570148bb348a7f41a
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626058"
---
# <a name="supporting-source-control"></a>Supporto del controllo del codice sorgente
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta estrazioni di file, archiviazioni e altre operazioni di controllo del codice sorgente per il progetto o l'editor. Come client di controllo del codice sorgente, è progettato per interagire con un pacchetto di controllo del codice sorgente, ad esempio , che fornisce funzionalità di archiviazione, controllo delle versioni e controllo per un set di file definito [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] dinamicamente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Modello per i pacchetti del controllo del codice sorgente](../../extensibility/internals/model-for-source-control-packages.md)

 Descrive le interfacce che un tipo di progetto deve implementare per supportare il controllo del codice sorgente.

- [Decisioni sulla progettazione](../../extensibility/internals/source-control-design-decisions.md)

 Fornisce domande le cui risposte modificano la modalità di implementazione di un tipo di progetto.

- [Dettagli di configurazione](../../extensibility/internals/source-control-configuration-details.md)

 Viene descritto come il supporto del controllo del codice sorgente modifica l'implementazione di un tipo di progetto.

- [Linee guida aggiuntive per progetti ed editor](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 Vengono illustrate le procedure consigliate per i tipi di progetto e gli editor.

- [Dettagli del runtime](../../extensibility/internals/source-control-runtime-details.md)

 Viene descritto come registrare un progetto quando un utente lo aggiunge a un sistema di controllo del codice sorgente.

## <a name="reference"></a>Riferimento
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> Indica all'ambiente o al pacchetto di controllo del codice sorgente che un file sta per essere modificato in memoria o salvato.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> Consente ai progetti e alle gerarchie di registrarsi con il controllo del codice sorgente e di ottenere informazioni sullo stato del controllo del codice sorgente.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Implementato in un sistema di progetto per fornire il controllo del codice sorgente per i file di progetto e gli elementi di progetto.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> Usato dai progetti per eseguire query sull'ambiente per ottenere l'autorizzazione per aggiungere, rimuovere o rinominare un file o una directory in una soluzione.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2> Notifica ai client le modifiche apportate ai file o alle directory di progetto.

## <a name="related-sections"></a>Sezioni correlate
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)

 Viene fornita una panoramica dei progetti come blocchi predefiniti di base [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'ambiente di sviluppo integrato (IDE). Vengono forniti collegamenti ad argomenti aggiuntivi che illustrano come i progetti controllano la compilazione e la compilazione del codice.
