---
title: Costanti (Debug Interface Access SDK) | Microsoft Docs
description: Vedere un elenco di costanti stringa che possono essere usate per identificare varie sezioni di un file di database di debug del programma (PDB) tramite l'SDK di accesso all'interfaccia di debug (DIA).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3db5105f310bdb3493262965f313620b66393651
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036701"
---
# <a name="constants-debug-interface-access-sdk"></a>Costanti (Debug Interface Access SDK)
Queste costanti stringa possono essere usate per identificare varie sezioni di un file di database di debug del programma (PDB) tramite il DIA SDK.

## <a name="constants"></a>Costanti
Gli elementi seguenti vengono dichiarati come macro C/C++.

|Macro|Valore|
|-----------|-----------|
|`DiaTable_Symbols`|L"Simboli"|
|`DiaTable_Sections`|L"Sections"|
|`DiaTable_SrcFiles`|L"SourceFiles"|
|`DiaTable_LineNums`|L"LineNumbers"|
|`DiaTable_SegMap`|L"SegmentMap"|
|`DiaTable_Dbg`|L"Dbg"|
|`DiaTable_InjSrc`|L"InjectedSource"|
|`DiaTable_FrameData`|L"FrameData"|

## <a name="example"></a>Esempio
Di seguito è riportato un esempio che usa uno di questi simboli:

```C++
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)
{
    HRESULT hr;
    VARIANT var;
    var.vt      = VT_BSTR;
    var.bstrVal = SysAllocString( DiaTable_Symbols );
    hr = pEnumTables->Item( var, pTable );
    return(hr);
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2.h

## <a name="see-also"></a>Vedi anche
- [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
- [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
