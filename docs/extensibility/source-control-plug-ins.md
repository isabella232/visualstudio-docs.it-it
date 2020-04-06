---
title: Plug-in del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699897"
---
# <a name="source-control-plug-ins"></a>Plug-in del controllo del codice sorgente
La sezione di riferimento dell'SDK del plug-in del controllo del [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]codice sorgente contiene la specifica completa dell'interfaccia che consente l'integrated dei sistemi di controllo del codice sorgente con . Specifica la sintassi e la semantica delle varie funzioni e tipi di dati [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] che il plug-in del controllo del codice sorgente deve implementare per interfacciarsi con l'ambiente di sviluppo integrato (IDE).

## <a name="in-this-section"></a>Contenuto della sezione
- [Funzioni API plug-in del controllo del codice sorgenteSource Control Plug-in API Functions](../extensibility/source-control-plug-in-api-functions.md) Elenca le funzioni che devono essere implementate dal plug-in del controllo del codice sorgente per essere conformi all'API del plug-in del controllo del codice sorgente.

- [Funzioni di callback implementate dall'IDECallback Functions Implemented by the IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Vengono descritte le funzioni utilizzate dal plug-in del controllo del codice sorgente per passare informazioni all'IDE durante l'esecuzione di determinati comandi.

- [Enumeratori](../extensibility/enumerators.md) Elenca i tipi di dati dell'enumeratore nell'API del plug-in del controllo del codice sorgente che il plug-in del controllo del codice sorgente deve conoscere.

- [Flag di capacitàCapability Flags](../extensibility/capability-flags.md) Vengono descritti `SCC_CAP_xxx` i flag, che indicano le funzionalità di un provider.

- [Flag di bit utilizzati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) Elenca i flag utili nel contesto di comandi particolari.

- [Codici di errore](../extensibility/error-codes.md) Elenca i valori di errore `SCCTRN`comuni restituiti dalle funzioni come .

- Stringhe utilizzate come chiavi per la ricerca di [un plug-in del controllo del codice sorgenteStrings Used as Keys for Finding a Source Control Plug-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Vengono descritte le chiavi per l'accesso al Registro di sistema per trovare il plug-in del controllo del codice sorgente.

- [DI MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md) Descrive un file sul lato client che contiene informazioni opache all'IDE, ma che viene utilizzato dal plug-in del controllo del codice sorgente per individuare la soluzione o il progetto nel controllo della versione.

- [Procedure consigliate per l'implementazione di un plug-in del controllo del codice sorgenteBest Practices for Implementing a Source Control Plug-in](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Fornisce una raccolta di importanti promemoria tecnici da ricordare durante l'implementazione dell'API del plug-in del controllo del codice sorgente.

- [Restrizioni sulle lunghezze delle stringheRestrictions on String Lengths](../extensibility/restrictions-on-string-lengths.md) Vengono descritte le limitazioni dell'API del plug-in del controllo del codice sorgente sulle lunghezze delle stringhe utilizzate in varie funzioni.

- [Glossario](../extensibility/source-control-plug-in-glossary.md) Fornisce termini utili e le relative definizioni per la lettura della documentazione di Source Control Plug-in SDK.

- [Procedura: disattivare gli avvisi di compatibilità per i plug-in del controllo del codice sorgenteHow to: Turn Off Compatibility Warnings for Source Control Plug-ins](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Viene descritto come disabilitare gli avvisi.

## <a name="related-sections"></a>Sezioni correlate
- [Esempio di plug-in del controllo del codice sorgenteSource Control Plug-in Sample](https://www.microsoft.com/download/details.aspx?id=55984) Fornisce un esempio della funzionalità del plug-in del controllo del codice sorgente.

- [Guida di test per i plug-in del controllo del codice sorgenteTest Guide for Source Control Plug-ins](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Vengono descritte le procedure di test relative a un plug-in del controllo del codice sorgente.

- [Creazione di un plug-in del controllo del codice sorgenteCreating a Source Control Plug-in](../extensibility/internals/creating-a-source-control-plug-in.md) Viene illustrato come creare un plug-in del controllo del codice [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sorgente che fornisce funzionalità di controllo del codice sorgente mentre si utilizza l'interfaccia utente del controllo del codice sorgente.

- [Guida di riferimento a Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md) Presenta un elenco di argomenti di riferimento.
