---
title: Plug-in del controllo del codice sorgente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5a99ebdf2366ce6a60a6a724afc7d742db7150f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705796"
---
# <a name="source-control-plug-ins"></a>Plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La sezione di riferimento dell'SDK del plug-in del controllo del codice sorgente contiene la specifica dell'interfaccia completa che consente l'integrazione dei sistemi di controllo del codice sorgente con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Specifica la sintassi e la semantica delle varie funzioni e tipi di dati che il plug-in del controllo del codice sorgente deve implementare per l'interfaccia con il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Integrated Development Environment (IDE).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)  
 Elenca le funzioni che devono essere implementate dal plug-in del controllo del codice sorgente per garantire la conformità con l'API del plug-in del controllo del codice sorgente.  
  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Descrive le funzioni utilizzate dal plug-in del controllo del codice sorgente per passare le informazioni all'IDE mentre vengono eseguiti determinati comandi.  
  
 [Enumerators](../extensibility/enumerators.md)  
 Elenca i tipi di dati dell'enumeratore nell'API del plug-in del controllo del codice sorgente di cui il plug-in del controllo del codice sorgente deve essere a conoscenza.  
  
 [Flag di funzionalità](../extensibility/capability-flags.md)  
 Vengono descritti i `SCC_CAP_xxx` flag, che indicano le funzionalità di un provider.  
  
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)  
 Elenca i flag che risultano utili nel contesto di particolari comandi.  
  
 [Codici errore](../extensibility/error-codes.md)  
 Elenca i valori di errore comuni restituiti dalle funzioni come `SCCTRN` .  
  
 [Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Descrive le chiavi per l'accesso al registro di sistema per trovare il plug-in del controllo del codice sorgente.  
  
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Descrive un file sul lato client che contiene informazioni opache nell'IDE, ma che viene utilizzato dal plug-in del controllo del codice sorgente per individuare la soluzione o il progetto nel controllo della versione.  
  
 [Procedure consigliate per implementare un plug-in del controllo del codice sorgente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fornisce una raccolta di importanti promemoria tecnici da ricordare durante l'implementazione dell'API del plug-in del controllo del codice sorgente.  
  
 [Limitazioni delle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)  
 Descrive le limitazioni nell'API del plug-in del controllo del codice sorgente sulle lunghezze delle stringhe utilizzate in varie funzioni.  
  
 [Glossario](../extensibility/source-control-plug-in-glossary.md)  
 Fornisce termini utili e le relative definizioni per leggere la documentazione dell'SDK del plug-in del controllo del codice sorgente.  
  
 [Procedura: Disabilitare gli avvisi di compatibilità per i plug-in del controllo del codice sorgente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Viene descritto come disabilitare gli avvisi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Esempio di plug-in del controllo del codice sorgente](https://msdn.microsoft.com/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 Fornisce un esempio di funzionalità del plug-in del controllo del codice sorgente.  
  
 [Guida per il test dei plug-in del controllo del codice sorgente](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Descrive le procedure di test correlate a un plug-in del controllo del codice sorgente.  
  
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un plug-in del controllo del codice sorgente che fornisce la funzionalità di controllo del codice sorgente mentre si utilizza l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfaccia utente del controllo del codice sorgente.  
  
 [Informazioni di riferimento su Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Viene presentato un elenco di argomenti di riferimento.
