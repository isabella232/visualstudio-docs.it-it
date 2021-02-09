---
title: Enumeratori | Microsoft Docs
description: Informazioni sui tipi di dati dell'enumeratore nell'API del plug-in del controllo del codice sorgente, inclusi codice del comando, messaggio, codice di stato del file e codice di stato della directory.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 28de569ea19feff0a81a81d072575dfb89610e98
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880749"
---
# <a name="enumerators"></a>Enumerators
In questa sezione sono elencati i tipi di dati dell'enumeratore nell'API del plug-in del controllo del codice sorgente che il plug-in del controllo del codice sorgente deve conoscere.

## <a name="in-this-section"></a>Contenuto della sezione
- [Codice comando](../extensibility/command-code-enumerator.md) Enumera le opzioni per le funzioni [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) .

- [Messaggio](../extensibility/message-enumerator.md) di Enumera i flag utilizzati per il callback di stampa, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Codice di stato file](../extensibility/file-status-code-enumerator.md) Contiene valori costanti denominati che specificano lo stato di un file nel controllo del codice sorgente.

- [Codice di stato della directory](../extensibility/directory-status-code-enumerator.md) Contiene valori costanti denominati che specificano lo stato di una directory nel controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creazione di un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md) Definisce l'SDK del plug-in del controllo del codice sorgente e descrive le risorse incluse.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Richiede all'utente le opzioni avanzate per il comando specificato.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Esamina l'elenco dei file per il relativo stato corrente. USA inoltre la `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per l'oggetto `nCommand` .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Viene descritta la funzione di callback utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in del controllo del codice sorgente tramite l'IDE.

- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md) Fornisce un elenco completo di tutti gli elementi nell'API del plug-in del controllo del codice sorgente.
