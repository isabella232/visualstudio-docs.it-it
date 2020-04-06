---
title: Proprietà Enumerators . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711850"
---
# <a name="enumerators"></a>Enumerators
In questa sezione sono elencati i tipi di dati dell'enumeratore nell'API del plug-in del controllo del codice sorgente che il plug-in del controllo del codice sorgente deve conoscere.

## <a name="in-this-section"></a>Contenuto della sezione
- [Codice di comando](../extensibility/command-code-enumerator.md) Enumera le opzioni per le funzioni [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) e [SccPopulateList.](../extensibility/sccpopulatelist-function.md)

- [Messaggio](../extensibility/message-enumerator.md) Enumera i flag utilizzati per il callback di stampa, [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Codice di stato del file](../extensibility/file-status-code-enumerator.md) Contiene valori costanti denominati che specificano lo stato di un file nel controllo del codice sorgente.

- [Codice di stato della directory](../extensibility/directory-status-code-enumerator.md) Contiene valori costanti denominati che specificano lo stato di una directory nel controllo del codice sorgente.

## <a name="related-sections"></a>Sezioni correlate
- [Creare un plug-in del controllo del codice sorgenteCreate a source control plug-in](../extensibility/internals/creating-a-source-control-plug-in.md) Definisce l'SDK del plug-in del controllo del codice sorgente e descrive le risorse incluse.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Richiede all'utente le opzioni avanzate per il comando specificato.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Esamina l'elenco dei file per il relativo stato corrente. Viene inoltre utilizzata `pfnPopulate` la funzione per notificare al chiamante `nCommand`quando un file non corrisponde ai criteri per il file .

- [LPTEXTOUTPROC (LAPTEXTOUTPROC)](../extensibility/lptextoutproc.md) Viene descritta la funzione di callback utilizzata da [SccOpenProject](../extensibility/sccopenproject-function.md) per visualizzare i messaggi dal plug-in del controllo del codice sorgente tramite l'IDE.

- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md) Fornisce un elenco completo di tutti gli elementi nell'API del plug-in del controllo del codice sorgente.
