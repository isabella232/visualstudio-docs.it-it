---
title: Errori di FxCopCmd | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
caps.latest.revision: 12
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5c7b62ce9e117b348daaa54da3d397346b6eab0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965039"
---
# <a name="fxcopcmd-errors"></a>errori di FxCopCmd
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
  
 Viene restituito l'errore di analisi per gli errori irreversibili. Indica che non è stato possibile completare l'analisi. Quando applicabile, il codice di errore contiene anche la causa sottostante dell'errore irreversibile. Le condizioni seguenti generano errori irreversibili:  
  
-   L'analisi non è stato possibile eseguire causate da input insufficienti.  
  
-   L'analisi ha generato un'eccezione non gestita dal FxCopCmd.  
  
-   Il file di progetto specificato non è stato trovato o è danneggiato.  
  
-   L'opzione di output non è stato specificato o non è stato possibile scrivere il file.  
  
    > [!NOTE]
    >  Il codice restituito di FxCopCmd "Assembly fa riferimento all'errore" 0x200 per sé è un avviso anziché un errore. Questo codice restituito indica che sono stati trovati riferimenti indiretti mancanti, ma che è in grado di gestirli FxCopCmd. È un avviso che è possibile che alcuni dei risultati dell'analisi potrebbero essere stati compromessi. Prendere in considerazione "Assembly fa riferimento all'errore" il codice restituito come un errore quando viene combinato con qualsiasi altro codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Errori nell'applicazione dell'analisi del codice](../code-quality/code-analysis-application-errors.md)