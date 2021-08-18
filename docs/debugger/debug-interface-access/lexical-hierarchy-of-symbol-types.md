---
description: La tabella seguente illustra i tipi di simboli nella gerarchia lessicale.
title: Gerarchia lessicale dei tipi di simboli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9c3892267d47cf48fc5fcd8b7e0179478b4c324a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031032"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Gerarchia lessicale dei tipi di simboli
La tabella seguente illustra i tipi di simboli nella gerarchia lessicale.

## <a name="symbol-types"></a>Tipi di simboli

|Tipo di simbolo|Descrizione|
|-----------------|-----------------|
|[Annotazione](../../debugger/debug-interface-access/annotation.md)|Specifica una posizione annotata nel codice del programma.|
|[Bloccato](../../debugger/debug-interface-access/block.md)|Specifica gli ambiti annidati nelle funzioni.|
|`Compiland`|Specifica un `compiland` oggetto collegato al .exe file.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Specifica i dati di compilazione che possono richiedere il caricamento di dettagli aggiuntivi del compilatore e pertanto comportano un sovraccarico in fase di esecuzione per il recupero.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Specifica eventuali variabili di ambiente aggiuntive significative per la compilazione del compilazione.|
|[Custom (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Specifica un simbolo definito dall'utente.|
|[Dati (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Specifica variabili quali parametri, variabili locali, variabili globali e membri di classe.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Specifica l'ambito globale dei dati. corrisponde a un intero .exe o .dll file.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Specifica una funzione con un punto definito in corrispondenza del quale deve terminare il debug.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Specifica una funzione con un punto definito in corrispondenza del quale deve iniziare il debug.|
|[Funzione (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Specifica una funzione.|
|[Etichetta (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Specifica una posizione nel codice del programma.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Specifica un simbolo esterno che viene visualizzato durante la compilazione del programma eseguibile.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Specifica un oggetto `thunk` .|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Specifica un `namespace` identificatore.|

> [!NOTE]
> A seconda del tipo di simbolo possono essere disponibili proprietà aggiuntive del simbolo. Queste proprietà sono elencate negli argomenti relativi ai singoli simboli.

## <a name="see-also"></a>Vedi anche
- [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
