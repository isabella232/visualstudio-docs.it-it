---
title: Plug-in del controllo del codice sorgente | Microsoft Docs
description: Gli articoli di questa sezione descrivono la specifica completa dell'interfaccia che consente l'integrazione dei sistemi di controllo del codice sorgente con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: abc8c8f439fa104ae84de8ffdc6f8d96a0909998
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028644"
---
# <a name="source-control-plug-ins"></a>Plug-in del controllo del codice sorgente
La sezione di riferimento sull'SDK del plug-in del controllo del codice sorgente contiene la specifica completa dell'interfaccia che consente l'integrazione dei sistemi di controllo del codice sorgente con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Specifica la sintassi e la semantica delle varie funzioni e tipi di dati che il plug-in del controllo del codice sorgente deve implementare per interfacciarsi con l'ambiente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sviluppo integrato (IDE).

## <a name="in-this-section"></a>Contenuto della sezione
- [Funzioni API plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md) Elenca le funzioni che devono essere implementate dal plug-in del controllo del codice sorgente per essere conformi all'API del plug-in del controllo del codice sorgente.

- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Descrive le funzioni utilizzate dal plug-in del controllo del codice sorgente per passare informazioni all'IDE mentre vengono eseguiti determinati comandi.

- [Enumeratori](../extensibility/enumerators.md) Elenca i tipi di dati dell'enumeratore nell'API plug-in del controllo del codice sorgente che il plug-in del controllo del codice sorgente deve conoscere.

- [Flag di funzionalità](../extensibility/capability-flags.md) Descrive i `SCC_CAP_xxx` flag , che indicano le funzionalità di un provider.

- [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) Elenca i flag che sono utili nel contesto di comandi specifici.

- [Codici di errore](../extensibility/error-codes.md) Elenca i valori di errore comuni restituiti dalle funzioni come `SCCTRN` .

- [Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Descrive le chiavi per l'accesso al Registro di sistema per trovare il plug-in del controllo del codice sorgente.

- [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md) Descrive un file sul lato client che contiene informazioni opache nell'IDE, ma che viene usato dal plug-in di controllo del codice sorgente per individuare la soluzione o il progetto nel controllo della versione.

- [Procedure consigliate per l'implementazione di un plug-in del controllo del codice sorgente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Fornisce una raccolta di importanti promemoria tecnici da ricordare durante l'implementazione dell'API plug-in del controllo del codice sorgente.

- [Restrizioni sulle lunghezze delle stringhe](../extensibility/restrictions-on-string-lengths.md) Vengono descritte le limitazioni dell'API plug-in del controllo del codice sorgente per le lunghezze delle stringhe usate in varie funzioni.

- [Glossario](../extensibility/source-control-plug-in-glossary.md) Fornisce termini utili e relative definizioni per la lettura della documentazione dell'SDK del plug-in del controllo del codice sorgente.

- [Procedura: Disattivare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Viene descritto come disabilitare gli avvisi.

## <a name="related-sections"></a>Sezioni correlate
- [Esempio di plug-in del controllo del codice sorgente](https://www.microsoft.com/download/details.aspx?id=55984) Fornisce un esempio di funzionalità del plug-in del controllo del codice sorgente.

- [Guida di test per i plug-in del controllo del codice sorgente](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Vengono descritte le procedure di test correlate a un plug-in del controllo del codice sorgente.

- [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md) Viene illustrato come creare un plug-in del controllo del codice sorgente che fornisce funzionalità di controllo del codice sorgente mentre si usa l'interfaccia utente del controllo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del codice sorgente.

- [informazioni di Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md) Presenta un elenco di argomenti di riferimento.
