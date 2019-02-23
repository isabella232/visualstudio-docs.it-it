---
title: Plug-in del controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a717fdb885669ae4893dc4234c58233dec2957be
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691657"
---
# <a name="source-control-plug-ins"></a>Plug-in del controllo del codice sorgente
La sezione di riferimento SDK dei plug-in controllo di origine contiene la specifica completa dell'interfaccia che consente ai sistemi di controllo di origine per l'integrazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Specifica la sintassi e semantica dei vari tipi di dati e funzioni che il plug-in del controllo del codice sorgente deve implementare per interfacciarsi con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE).

## <a name="in-this-section"></a>In questa sezione
- [Funzioni API dei plug-in controllo dell'origine](../extensibility/source-control-plug-in-api-functions.md) Elenca le funzioni che devono essere implementate per il plug-in del controllo del codice sorgente per garantire la conformità con l'API dei plug-in del controllo origine.

- [Le funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md) vengono descritte le funzioni che usa il plug-in del controllo del codice sorgente per passare informazioni tornare all'IDE, mentre alcuni comandi vengono eseguiti.

- [Gli enumeratori](../extensibility/enumerators.md) sono elencati i tipi di dati di enumeratore nell'API dei plug-in controllo di origine che il plug-in del controllo del codice sorgente devono essere informati.

- [I flag funzionalità](../extensibility/capability-flags.md) descrive il `SCC_CAP_xxx` flag, quali sono indicano le funzionalità del provider.

- [I flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md) Elenca i flag sono utili nel contesto di comandi specifici.

- [Codici di errore](../extensibility/error-codes.md) sono elencati i valori di errore comuni restituiti dalle funzioni come `SCCTRN`.

- [Le stringhe utilizzate come chiavi per la ricerca di un plug-in controllo origine](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) descrive le chiavi per l'accesso del Registro di sistema per trovare il controllo del codice sorgente del plug-in.

- [MSSCCPRJ. File SCC](../extensibility/mssccprj-scc-file.md) descrive un file lato client che contiene informazioni opache per l'IDE, ma che viene utilizzato per il plug-in del controllo del codice sorgente per individuare la soluzione o il progetto nel controllo della versione.

- [Procedure consigliate per l'implementazione di un plug-in controllo sorgente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) fornisce una raccolta di promemoria tecnici importanti da ricordare quando si implementa l'API dei plug-in del controllo origine.

- [Limitazioni sulle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md) vengono descritte le limitazioni nell'API dei plug-in controllo di origine nella lunghezze delle stringhe usate nelle varie funzioni.

- [Glossario](../extensibility/source-control-plug-in-glossary.md) fornisce utili termini e le relative definizioni per leggere la documentazione del SDK dei plug-in controllo di origine.

- [Procedura: Attivare disattivare gli avvisi di compatibilità per i Plug-in controllo del codice sorgente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) viene descritto come disabilitare gli avvisi.

## <a name="related-sections"></a>Sezioni correlate
- [Esempio di plug-in controllo dell'origine](https://www.microsoft.com/download/details.aspx?id=55984) viene fornito un esempio di plug-in del controllo del codice sorgente.

- [Guida per i Plug-in controllo del codice sorgente di test](../extensibility/internals/test-guide-for-source-control-plug-ins.md) vengono descritte le procedure di test correlate a un plug-in del controllo del codice sorgente.

- [Creazione di un plug-in controllo di origine](../extensibility/internals/creating-a-source-control-plug-in.md) viene illustrato come creare un controllo del codice sorgente del plug-in che fornisce funzionalità di controllo di origine mentre si utilizzano i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo origine (UI).

- [Riferimenti di Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md) presenta un elenco di argomenti di riferimento.