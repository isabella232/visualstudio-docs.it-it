---
description: Se una funzione ha un punto definito in cui deve iniziare il debug, tale punto viene identificato da un simbolo con un tag SymTagFuncDebugStart.
title: FuncDebugStart | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- FuncDebugStart symbol
- debugging [DIA SDK], start point
ms.assetid: 1cbc6ca5-87d0-4c30-a39e-0a9dc62ce1a9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 816228f0eb5d52e037192f9ed29c64638ce13876
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630588"
---
# <a name="funcdebugstart"></a>FuncDebugStart
Se una funzione ha un punto definito in cui deve iniziare il debug, tale punto viene identificato da un simbolo con un `SymTagFuncDebugStart` tag .

## <a name="properties"></a>Proprietà
 La tabella seguente illustra le proprietà valide per questo tipo di simbolo.

|Proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Offset della parte della posizione; Per informazioni dettagliate, vedere [l'enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte della sezione della posizione; Per informazioni dettagliate, vedere [l'enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` se la funzione usa una convenzione di chiamata personalizzata (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` se la funzione esegue un ritorno a lungo (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` se la funzione contiene un valore restituito dall'interrupt (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|`BOOL`|`TRUE` se la funzione è contrassegnata come statica (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per la funzione di inclusione.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|I punti di partenza hanno posizioni statiche; Per informazioni dettagliate, vedere [Posizioni dei simboli](../../debugger/debug-interface-access/symbol-locations.md).|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` se la funzione è stata specificata con [l'attributo noinline](/cpp/cpp/noinline) (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` se la funzione è stata specificata con l'attributo [noreturn](/cpp/cpp/noreturn) (solo DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` se la funzione non viene mai chiamata (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset del simbolo in memoria. Per informazioni dettagliate, vedere [l'enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel` .|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` se il codice contiene informazioni di debug per il codice ottimizzato (solo in DIA SDK versione 8.0 o successiva).|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa della funzione all'interno del blocco.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagFuncDebugStart` (uno dei valori [dell'enumerazione SymTagEnum).](../../debugger/debug-interface-access/symtagenum.md)|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione della funzione all'interno dell'eseguibile.|

## <a name="see-also"></a>Vedi anche
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
- [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)
