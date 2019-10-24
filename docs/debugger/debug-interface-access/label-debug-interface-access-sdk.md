---
title: Etichetta (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locations, in program code
- Label symbol
ms.assetid: 8cef7620-5bc8-4500-8bd0-e9e638bccb24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d76238e11ebb30d98465836115505ab25d247524
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738684"
---
# <a name="label-debug-interface-access-sdk"></a>Etichetta (Debug Interface Access SDK)
Un percorso nel codice programma è identificato da un simbolo di `SymTagLabel`.

## <a name="properties"></a>Proprietà
 Nella tabella seguente vengono illustrate le proprietà valide per questo tipo di simbolo.

|proprietà|Tipo di dati|Descrizione|
|--------------|---------------|-----------------|
|[IDiaSymbol::get_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|`DWORD`|Offset parte della posizione; per informazioni dettagliate, vedere l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|`DWORD`|Parte della sezione della posizione; per informazioni dettagliate, vedere l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md).|
|[IDiaSymbol::get_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|`BOOL`|`TRUE` se l'etichetta utilizza una convenzione di chiamata personalizzata.|
|[IDiaSymbol::get_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|`BOOL`|`TRUE` se l'etichetta esegue un ritorno a lungo.|
|[IDiaSymbol::get_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|`BOOL`|`TRUE` se l'etichetta contiene un valore restituito da interrupt.|
|[IDiaSymbol::get_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|Simbolo per il modulo, il blocco o la funzione di inclusione.|
|[IDiaSymbol::get_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|
|[IDiaSymbol::get_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|`DWORD`|Le etichette hanno posizioni statiche; per informazioni dettagliate, vedere l'enumerazione [percorsi simboli](../../debugger/debug-interface-access/symbol-locations.md) .|
|[IDiaSymbol::get_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|`BSTR`|Nome dell'etichetta.|
|[IDiaSymbol::get_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|`BOOL`|`TRUE` se l'etichetta è stata specificata con l'attributo [noinline](/cpp/cpp/noinline) .|
|[IDiaSymbol::get_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|`BOOL`|`TRUE` se l'etichetta è stata specificata con l'attributo [noreturn](/cpp/cpp/noreturn) .|
|[IDiaSymbol::get_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|`BOOL`|`TRUE` se l'etichetta non viene mai chiamata.|
|[IDiaSymbol::get_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|`LONG`|Offset del simbolo nella memoria; per informazioni dettagliate, vedere l' [enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md), `LocIsRegRel`.|
|[IDiaSymbol::get_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|`BOOL`|`TRUE` se il codice contiene informazioni di debug per il codice ottimizzato.|
|[IDiaSymbol::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|`DWORD`|Posizione relativa dell'etichetta all'interno del modulo.|
|[IDiaSymbol::get_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|ID di indice del simbolo.|
|[IDiaSymbol::get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagFuncDebugLabel` (uno dei valori di [enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) ).|
|[IDiaSymbol::get_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|`ULONGLONG`|Posizione dell'etichetta all'interno dell'immagine eseguibile.|

## <a name="see-also"></a>Vedere anche
- [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [Enumerazione LocationType](../../debugger/debug-interface-access/locationtype.md)
- [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)