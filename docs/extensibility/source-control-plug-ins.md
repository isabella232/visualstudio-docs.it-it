---
title: Plug-in del controllo del codice sorgente | Microsoft Docs
description: Negli articoli di questa sezione viene illustrata la specifica di interfaccia completa che consente l'integrazione dei sistemi di controllo del codice sorgente con Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a6788d738d37ac62156958acb15c1bcd5d536515
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089953"
---
# <a name="source-control-plug-ins"></a>Plug-in del controllo del codice sorgente
La sezione di riferimento dell'SDK del plug-in del controllo del codice sorgente contiene la specifica dell'interfaccia completa che consente l'integrazione dei sistemi di controllo del codice sorgente con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Specifica la sintassi e la semantica delle varie funzioni e tipi di dati che il plug-in del controllo del codice sorgente deve implementare per l'interfaccia con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE).

## <a name="in-this-section"></a>Contenuto della sezione
- [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md) Elenca le funzioni che devono essere implementate dal plug-in del controllo del codice sorgente per garantire la conformità con l'API del plug-in del controllo del codice sorgente.

- [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md) Descrive le funzioni utilizzate dal plug-in del controllo del codice sorgente per passare le informazioni all'IDE mentre vengono eseguiti determinati comandi.

- [Enumeratori](../extensibility/enumerators.md) Elenca i tipi di dati dell'enumeratore nell'API del plug-in del controllo del codice sorgente di cui il plug-in del controllo del codice sorgente deve essere a conoscenza.

- [Flag funzionalità](../extensibility/capability-flags.md) Vengono descritti i `SCC_CAP_xxx` flag, che indicano le funzionalità di un provider.

- [Flag utilizzato da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) Elenca i flag che risultano utili nel contesto di particolari comandi.

- [Codici di errore](../extensibility/error-codes.md) Elenca i valori di errore comuni restituiti dalle funzioni come `SCCTRN` .

- [Stringhe utilizzate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) Descrive le chiavi per l'accesso al registro di sistema per trovare il plug-in del controllo del codice sorgente.

- [Mssccprj. File SCC](../extensibility/mssccprj-scc-file.md) descrive un file sul lato client che contiene informazioni opache nell'IDE, ma che viene usato dal plug-in del controllo del codice sorgente per individuare la soluzione o il progetto nel controllo della versione.

- [Procedure consigliate per l'implementazione di un plug-in del controllo del codice sorgente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Fornisce una raccolta di importanti promemoria tecnici da ricordare durante l'implementazione dell'API del plug-in del controllo del codice sorgente.

- [Restrizioni sulle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md) Descrive le limitazioni nell'API del plug-in del controllo del codice sorgente sulle lunghezze delle stringhe utilizzate in varie funzioni.

- [Glossario](../extensibility/source-control-plug-in-glossary.md) Fornisce termini utili e le relative definizioni per leggere la documentazione dell'SDK del plug-in del controllo del codice sorgente.

- [Procedura: disattivare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Viene descritto come disabilitare gli avvisi.

## <a name="related-sections"></a>Sezioni correlate
- [Esempio di plug-in del controllo del codice sorgente](https://www.microsoft.com/download/details.aspx?id=55984) Fornisce un esempio di funzionalità del plug-in del controllo del codice sorgente.

- [Guida di test per i plug-in del controllo del codice sorgente](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Descrive le procedure di test correlate a un plug-in del controllo del codice sorgente.

- [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md) Viene illustrato come creare un plug-in del controllo del codice sorgente che fornisce la funzionalità di controllo del codice sorgente mentre si utilizza l' [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo del codice sorgente.

- [Riferimenti per Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md) Viene presentato un elenco di argomenti di riferimento.
