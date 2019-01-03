---
title: Plug-in del controllo di origine | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f45ffeb57db79edd6305c3195a87012dc7de26b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923640"
---
# <a name="source-control-plug-ins"></a>Plug-in del controllo del codice sorgente
La sezione di riferimento SDK dei plug-in controllo di origine contiene la specifica completa dell'interfaccia che consente ai sistemi di controllo di origine per l'integrazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Specifica la sintassi e semantica dei vari tipi di dati e funzioni che il plug-in del controllo del codice sorgente deve implementare per interfacciarsi con il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE).  
  
## <a name="in-this-section"></a>In questa sezione  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)  
 Elenca le funzioni che devono essere implementate per il plug-in del controllo del codice sorgente per garantire la conformità con l'API dei plug-in del controllo origine.  
  
 [Funzioni di callback implementate dall'IDE](../extensibility/callback-functions-implemented-by-the-ide.md)  
 Descrive funzioni che usa il plug-in del controllo del codice sorgente per passare informazioni tornare all'IDE, mentre alcuni comandi vengono eseguiti.  
  
 [Enumeratori](../extensibility/enumerators.md)  
 Elenca i tipi di dati di enumeratore nell'API dei plug-in controllo di origine che il plug-in del controllo del codice sorgente devono essere informati.  
  
 [Flag di funzionalità](../extensibility/capability-flags.md)  
 Viene descritto il `SCC_CAP_xxx` flag, quali sono indicano le funzionalità del provider.  
  
 [Flag di bit usati da comandi specifici](../extensibility/bitflags-used-by-specific-commands.md)  
 Elenca i flag sono utili nel contesto di comandi specifici.  
  
 [Codici di errore](../extensibility/error-codes.md)  
 Elenca i valori di errore comuni restituiti dalle funzioni come `SCCTRN`.  
  
 [Stringhe usate come chiavi per la ricerca di un plug-in del controllo del codice sorgente](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 Descrive le chiavi per l'accesso del Registro di sistema per trovare il controllo del codice sorgente del plug-in.  
  
 [File MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)  
 Descrive un file lato client che contiene informazioni opache per l'IDE, ma che viene utilizzato per il plug-in del controllo del codice sorgente per individuare la soluzione o il progetto nel controllo della versione.  
  
 [Procedure consigliate per implementare un plug-in del controllo del codice sorgente](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 Fornisce una raccolta di promemoria tecnici importanti da ricordare quando si implementa l'API dei plug-in del controllo origine.  
  
 [Limitazioni delle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)  
 Descrive le limitazioni nell'API dei plug-in controllo di origine nella lunghezze delle stringhe usate nelle varie funzioni.  
  
 [Glossario](../extensibility/source-control-plug-in-glossary.md)  
 Fornisce utili termini e le relative definizioni per leggere la documentazione del SDK dei plug-in controllo di origine.  
  
 [Procedura: Disattivare gli avvisi di compatibilità per Plug-in controllo codice sorgente](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 Viene descritto come disabilitare gli avvisi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Esempio di plug-in del controllo di origine](https://www.microsoft.com/download/details.aspx?id=55984)  
 Fornisce un esempio di plug-in del controllo del codice sorgente.  
  
 [Guida per il test dei plug-in del controllo del codice sorgente](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Descrive le procedure di test correlate a un plug-in del controllo del codice sorgente.  
  
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un controllo del codice sorgente del plug-in che fornisce funzionalità di controllo di origine mentre si utilizzano i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] interfaccia utente del controllo origine (UI).  
  
 [Riferimenti su Visual Studio SDK](../extensibility/visual-studio-sdk-reference.md)  
 Visualizza un elenco di argomenti di riferimento.