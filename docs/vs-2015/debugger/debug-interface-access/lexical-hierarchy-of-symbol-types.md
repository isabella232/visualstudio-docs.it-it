---
title: Gerarchia lessicale dei tipi di simboli | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK], type hierarchies
ms.assetid: 912da653-ddfe-45a4-84aa-64281283739a
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f9fa295a7faa85a0b7a7b3268702c4199869754
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783259"
---
# <a name="lexical-hierarchy-of-symbol-types"></a>Gerarchia lessicale dei tipi di simboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La tabella seguente illustra i tipi di simboli nella gerarchia lessicale.  
  
## <a name="symbol-types"></a>Tipi di simboli  
  
|Tipo di simbolo|Descrizione|  
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
 [Gerarchia delle classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)   
 [I simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)



