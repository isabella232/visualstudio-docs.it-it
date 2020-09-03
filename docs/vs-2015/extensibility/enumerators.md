---
title: Enumeratori | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65a03a8dc741ec86aca3137f49cd753722ede215
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204571"
---
# <a name="enumerators"></a>Enumerators
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa sezione sono elencati i tipi di dati dell'enumeratore nell'API del plug-in del controllo del codice sorgente che il plug-in del controllo del codice sorgente deve conoscere.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Codice di comando](../extensibility/command-code-enumerator.md)  
 Enumera le opzioni per le funzioni [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) .  
  
 [Message](../extensibility/message-enumerator.md)  
 Enumera i flag utilizzati per il callback di stampa, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Codice di stato dei file](../extensibility/file-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di un file nel controllo del codice sorgente.  
  
 [Codice di stato directory](../extensibility/directory-status-code-enumerator.md)  
 Contiene valori costanti denominati che specificano lo stato di una directory nel controllo del codice sorgente.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce l'SDK del plug-in del controllo del codice sorgente e descrive le risorse incluse.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Richiede all'utente le opzioni avanzate per il comando specificato.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Esamina l'elenco dei file per il relativo stato corrente. USA inoltre la `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per l'oggetto `nCommand` .  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Viene descritta la funzione di callback utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in del controllo del codice sorgente tramite l'IDE.  
  
 [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)  
 Fornisce un elenco completo di tutti gli elementi nell'API del plug-in del controllo del codice sorgente.
