---
title: Gerarchia lessicale dei tipi di simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a92f3f8f5174717b3fe3e992706a0f16478f99df
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56612803"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Gerarchia lessicale dei tipi di simboli
La tabella seguente illustra i tipi di simboli nella gerarchia lessicale.

## <a name="symbol-types"></a>Tipi di simboli

|Tipo di simbolo|Description|
|-----------------|-----------------|
|[Annotazione](../../debugger/debug-interface-access/annotation.md)|Specifica un percorso con annotazione nel codice del programma.|
|[Blocco](../../debugger/debug-interface-access/block.md)|Specifica gli ambiti annidati in funzioni.|
|`Compiland`|Specifica un `compiland` collegati file .exe.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Specifica i dati compilando che potrebbero richiedere il caricamento dei dettagli aggiuntivi compilando e in questo modo incorrere in fase di esecuzione sovraccarico per recuperare.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Specifica delle variabili di ambiente aggiuntive significative per la compilazione del modulo diversamente.|
|[Custom (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Specifica un simbolo definito dall'utente.|
|[Dati (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Specifica le variabili come parametri, variabili locali, le variabili globali e i membri della classe.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Specifica l'ambito globale dei dati. corrisponde a un intero file .exe o DLL.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Specifica una funzione che dispone di un punto definito in cui il debug è necessario terminare.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Specifica una funzione che dispone di un punto definito quale debug ha inizio.|
|[Funzione (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Specifica una funzione.|
|[Etichetta (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Specifica una posizione nel codice del programma.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Specifica un simbolo esterno che viene visualizzato quando si compila il programma eseguibile.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Specifica un `thunk`.|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Specifica un `namespace`identificatore.|

> [!NOTE]
>  Proprietà dei simboli aggiuntive potrebbero essere disponibili a seconda del tipo di simbolo. Queste proprietà sono elencate negli argomenti simbolo singoli.

## <a name="see-also"></a>Vedere anche
- [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)