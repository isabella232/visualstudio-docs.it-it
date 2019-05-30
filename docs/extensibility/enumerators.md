---
title: Gli enumeratori | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d3a0876dfd3a9d7b9cc86b18f6e9a6ba3b780d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334503"
---
# <a name="enumerators"></a>Enumeratori
Questa sezione elenca i tipi di dati di enumeratore nell'API dei plug-in controllo di origine che il plug-in del controllo del codice sorgente devono essere informati.

## <a name="in-this-section"></a>Contenuto della sezione
- [Codice di comando](../extensibility/command-code-enumerator.md) enumera le opzioni per il [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList](../extensibility/sccpopulatelist-function.md) funzioni.

- [Messaggio](../extensibility/message-enumerator.md) enumera i flag utilizzati per il callback di stampa, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [File di codice di stato](../extensibility/file-status-code-enumerator.md) Contains denominato valori costanti che specificano lo stato di un file di controllo del codice sorgente.

- [Codice di stato directory](../extensibility/directory-status-code-enumerator.md) Contains denominato valori costanti che specificano lo stato di una directory nel controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un controllo del codice sorgente del plug-in](../extensibility/internals/creating-a-source-control-plug-in.md) definisce il SDK dei plug-in controllo di origine e vengono descritte le risorse incluse.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) chiede all'utente le opzioni avanzate per il comando specificato.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) esamina l'elenco dei file per il relativo stato corrente. Inoltre, utilizza il `pfnPopulate` funzione per notificare al chiamante quando un file non corrisponde ai criteri per il `nCommand`.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) viene descritta la funzione di callback usato da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal controllo del codice sorgente del plug-in tramite l'IDE.

- [Plug-in del controllo di origine](../extensibility/source-control-plug-ins.md) fornisce un elenco completo di tutti gli elementi nell'API dei plug-in controllo di origine.