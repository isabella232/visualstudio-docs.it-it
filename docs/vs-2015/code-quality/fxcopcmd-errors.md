---
title: errori di FxCopCmd
ms.date: 10/19/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.author: gewarren
author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d723065e224058b7e269299aad2900f97a1425d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936647"
---
# <a name="fxcopcmd-tool-errors"></a>Errori di FxCopCmd strumento

FxCopCmd non considera tutti gli errori irreversibili. Se FxCopCmd sono disponibili informazioni sufficienti per eseguire un'analisi parziale, esegue l'analisi e segnala gli errori che si sono verificati. Il codice di errore che è un integer a 32 bit, contiene una combinazione bit per bit di valori numerici corrispondenti a errori.

Nella tabella seguente vengono descritti i codici di errore restituiti da FxCopCmd:

|Error|Valore numerico|
|-----------|-------------------|
|Nessun errore|0x0|
|Errore di analisi|0x1|
|Eccezioni alla regola|0x2|
|Errore di caricamento progetto|0x4|
|Errore di caricamento assembly|0x8|
|Errore di caricamento della libreria di regola|0x10|
|Errore di caricamento di report di importazione|0x20|
|Errore di output|0x40|
|Errore di opzione della riga di comando|0x80|
|Errore di inizializzazione|0x100|
|Errore di riferimento ad assembly|0x200|
|BuildBreakingMessage|0x400|
|Errore sconosciuto|0x1000000|

**Errore di analisi** viene restituito per gli errori irreversibili. Indica che non è stato possibile completare l'analisi. Quando applicabile, il codice di errore contiene anche la causa sottostante dell'errore irreversibile. Le condizioni seguenti generano errori irreversibili:

- L'analisi potrebbe non essere eseguita a causa di input insufficienti.

- L'analisi ha generato un'eccezione non gestita dal FxCopCmd.

- Il file di progetto specificato non è stato trovato o è danneggiato.

- L'opzione di output non è stato specificato o non è stato possibile scrivere il file.

> [!NOTE]
> Codice restituito di FxCopCmd **Assembly fa riferimento all'errore** 0x200 per sé è un avviso anziché un errore. Questo codice restituito indica che mancano i riferimenti indiretti, ma tale FxCopCmd è stata in grado di gestirle. Il messaggio di avviso indica che è possibile che alcuni dei risultati dell'analisi potrebbero essere stati compromessi. Considerare **Assembly fa riferimento all'errore** come un errore quando viene combinato con qualsiasi altro codice.

## <a name="see-also"></a>Vedere anche

- [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)