---
title: Enumeratori | Microsoft Docs
description: Informazioni sui tipi di dati dell'enumeratore nell'API plug-in del controllo del codice sorgente, tra cui codice di comando, messaggio, codice di stato del file e codice di stato della directory.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 13442c34536382708de5531533afbd795a52b243ac3b5a264d7270e9ca0ccf2b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121376859"
---
# <a name="enumerators"></a>Enumerators
Questa sezione elenca i tipi di dati dell'enumeratore nell'API plug-in del controllo del codice sorgente che il plug-in del controllo del codice sorgente deve conoscere.

## <a name="in-this-section"></a>Contenuto della sezione
- [Codice di comando](../extensibility/command-code-enumerator.md) Enumera le opzioni per le [funzioni SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

- [Messaggio](../extensibility/message-enumerator.md) Enumera i flag utilizzati per il callback di [stampa, LPTEXTOUTPROC.](../extensibility/lptextoutproc.md)

- [Codice di stato del file](../extensibility/file-status-code-enumerator.md) Contiene valori costanti denominati che specificano lo stato di un file nel controllo del codice sorgente.

- [Codice di stato della directory](../extensibility/directory-status-code-enumerator.md) Contiene valori costanti denominati che specificano lo stato di una directory nel controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un plug-in del controllo del codice sorgente](../extensibility/internals/creating-a-source-control-plug-in.md) Definisce l'SDK del plug-in del controllo del codice sorgente e descrive le risorse incluse.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Richiede all'utente le opzioni avanzate per il comando specificato.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Esamina l'elenco dei file per il relativo stato corrente. Usa inoltre la funzione per inviare una notifica al chiamante quando un file non corrisponde `pfnPopulate` ai criteri per `nCommand` .

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Descrive la funzione di callback utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in del controllo del codice sorgente tramite l'IDE.

- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md) Fornisce un elenco completo di tutti gli elementi nell'API plug-in del controllo del codice sorgente.
