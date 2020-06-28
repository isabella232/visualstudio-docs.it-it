---
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b003fcbd1b38eb5dc919b7f4f361e0b56b585f08
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85461224"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Gerarchia lessicale dei tipi di simboli
Nella tabella seguente vengono illustrati i tipi di simboli della gerarchia lessicale.

## <a name="symbol-types"></a>Tipi di simboli

|Tipo di simbolo|Descrizione|
|-----------------|-----------------|
|[Annotazione](../../debugger/debug-interface-access/annotation.md)|Specifica una posizione con annotazioni nel codice del programma.|
|[Bloccato](../../debugger/debug-interface-access/block.md)|Specifica gli ambiti annidati nelle funzioni.|
|`Compiland`|Specifica un oggetto `compiland` collegato al file exe.|
|[CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)|Specifica i dati di modulo che possono richiedere il caricamento di dettagli modulo aggiuntivi e pertanto comportare un sovraccarico in fase di esecuzione da recuperare.|
|[CompilandEnv](../../debugger/debug-interface-access/compilandenv.md)|Specifica le variabili di ambiente aggiuntive significative per la compilazione di modulo.|
|[Custom (Debug Interface Access SDK)](../../debugger/debug-interface-access/custom-debug-interface-access-sdk.md)|Specifica un simbolo definito dall'utente.|
|[Dati (Debug Interface Access SDK)](../../debugger/debug-interface-access/data-debug-interface-access-sdk.md)|Specifica tali variabili come parametri, variabili locali, variabili globali e membri della classe.|
|[Exe](../../debugger/debug-interface-access/exe.md)|Specifica l'ambito globale dei dati; corrisponde a un intero file con estensione exe o dll.|
|[FuncDebugEnd](../../debugger/debug-interface-access/funcdebugend.md)|Specifica una funzione che dispone di un punto definito in corrispondenza del quale deve terminare il debug.|
|[FuncDebugStart](../../debugger/debug-interface-access/funcdebugstart.md)|Specifica una funzione che ha un punto definito da cui iniziare il debug.|
|[Funzione (Debug Interface Access SDK)](../../debugger/debug-interface-access/function-debug-interface-access-sdk.md)|Specifica una funzione.|
|[Etichetta (Debug Interface Access SDK)](../../debugger/debug-interface-access/label-debug-interface-access-sdk.md)|Specifica una posizione nel codice del programma.|
|[PublicSymbol](../../debugger/debug-interface-access/publicsymbol.md)|Specifica un simbolo esterno visualizzato quando si compila il programma eseguibile.|
|[Thunk](../../debugger/debug-interface-access/thunk.md)|Specifica un oggetto `thunk` .|
|[UsingNameSpace](../../debugger/debug-interface-access/usingnamespace.md)|Specifica un `namespace` identificatore.|

> [!NOTE]
> È possibile che siano disponibili ulteriori proprietà dei simboli a seconda del tipo di simbolo. Queste proprietà sono elencate nei singoli argomenti dei simboli.

## <a name="see-also"></a>Vedi anche
- [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)
- [IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)
- [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)