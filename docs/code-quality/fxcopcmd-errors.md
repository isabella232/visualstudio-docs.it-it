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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c900ec10ea13e7f9d7092769565703bf52fe8c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348932"
---
# <a name="fxcopcmd-tool-errors"></a>Errori dello strumento FxCopCmd

FxCopCmd non considera fatali tutti gli errori. Se FxCopCmd dispone di informazioni sufficienti per eseguire un'analisi parziale, esegue l'analisi e segnala gli errori che si sono verificati. Il codice di errore, che è un Integer a 32 bit, contiene una combinazione bit per bit di valori numerici che corrispondono agli errori.

La tabella seguente descrive i codici di errore restituiti da FxCopCmd:

|Errore|Valore numerico|
|-----------|-------------------|
|Nessun errore|0x0|
|Errore di analisi|0x1|
|Eccezioni alle regole|0x2|
|Errore di caricamento del progetto|0x4|
|Errore di caricamento dell'assembly|0x8|
|Errore di caricamento della libreria regole|0x10|
|Errore di caricamento del report di importazione|0x20|
|Errore di output|0x40|
|Errore di opzione della riga di comando|0x80|
|Errore di inizializzazione|0x100|
|Errore riferimenti assembly|0x200|
|BuildBreakingMessage|0x400|
|Errore sconosciuto|0x1000000|

Per gli errori irreversibili viene restituito l' **errore di analisi** . Indica che non è stato possibile completare l'analisi. Se applicabile, il codice di errore contiene anche la cause sottostante dell'errore irreversibile. Le condizioni seguenti generano errori irreversibili:

- Non è stato possibile eseguire l'analisi a causa di un input insufficiente.

- L'analisi ha generato un'eccezione che non viene gestita da FxCopCmd.

- Il file di progetto specificato non è stato trovato o è danneggiato.

- L'opzione di output non è stata specificata o non è stato possibile scrivere il file.

> [!NOTE]
> L'assembly di codice restituito FxCopCmd **fa riferimento all'errore** 0x200 da solo è un avviso anziché un errore. Questo codice restituito indica che non sono presenti riferimenti indiretti mancanti, ma che FxCopCmd è stato in grado di gestirli. L'avviso indica che è possibile che alcuni risultati dell'analisi siano stati compromessi. Considera l' **errore di riferimento all'assembly** come un errore quando viene combinato con qualsiasi altro codice restituito.

## <a name="see-also"></a>Vedere anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)
