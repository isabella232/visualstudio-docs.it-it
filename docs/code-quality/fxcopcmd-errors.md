---
title: errori di FxCopCmd
ms.date: 10/19/2016
description: Informazioni sui codici di errore restituiti dal comando FxCopCmd. Vedere il tipo di errore rappresentato da ogni codice e scoprire come riconoscere gli errori irreversibili.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: c06c996245dfba796d4ab7e71fdbb28ad486f017
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098034"
---
# <a name="fxcopcmd-tool-errors"></a>Errori dello strumento FxCopCmd

FxCopCmd non considera tutti gli errori irreversibili. Se FxCopCmd dispone di informazioni sufficienti per eseguire un'analisi parziale, esegue l'analisi e segnala gli errori che si sono verificati. Il codice di errore, ovvero un intero a 32 bit, contiene una combinazione bit per bit di valori numerici che corrispondono agli errori.

La tabella seguente descrive i codici di errore restituiti da FxCopCmd:

|Errore|Valore numerico|
|-----------|-------------------|
|Nessun errore|0x0|
|Errore di analisi|0x1|
|Eccezioni alle regole|0x2|
|Project errore di caricamento|0x4|
|Errore di caricamento dell'assembly|0x8|
|Errore di caricamento della libreria delle regole|0x10|
|Errore di caricamento del report di importazione|0x20|
|Errore di output|0x40|
|Errore di opzione della riga di comando|0x80|
|Errore di inizializzazione|0x100|
|Errore dei riferimenti all'assembly|0x200|
|BuildBreakingMessage|0x400|
|Errore sconosciuto|0x1000000|

**Viene restituito un** errore di analisi per gli errori irreversibili. Indica che non è stato possibile completare l'analisi. Se applicabile, il codice di errore contiene anche la causa sottostante dell'errore irreversibile. Le condizioni seguenti generano errori irreversibili:

- Impossibile eseguire l'analisi a causa di input insufficiente.

- L'analisi ha generato un'eccezione non gestita da FxCopCmd.

- Il file di progetto specificato non è stato trovato o è danneggiato.

- L'opzione di output non è stata specificata o non è stato possibile scrivere il file.

> [!NOTE]
> Il codice restituito FxCopCmd **L'assembly** fa riferimento 0x200 errore è di per sé un avviso anziché un errore. Questo codice restituito indica che mancano riferimenti indiretti, ma che FxCopCmd è stato in grado di gestirli. L'avviso indica che è possibile che alcuni risultati dell'analisi siano stati compromessi. Considerare **l'errore dei riferimenti** all'assembly come un errore quando viene combinato con qualsiasi altro codice restituito.

## <a name="see-also"></a>Vedi anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)
