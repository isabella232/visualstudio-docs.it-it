---
title: Costanti (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a120a1610e6ca62ba4c19bb5dd2289628e1d273
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987405"
---
# <a name="constants-debug-interface-access-sdk"></a>Costanti (Debug Interface Access SDK)
Queste costanti di stringa possono essere utilizzate per identificare diverse sezioni di un file di database (PDB) di debug programma tramite il DIA SDK.

## <a name="constants"></a>Costanti
Di seguito viene dichiarati come macro C/C++.

|Macro|Valore|
|-----------|-----------|
|`DiaTable_Symbols`|L "Simboli"|
|`DiaTable_Sections`|L "Sezioni"|
|`DiaTable_SrcFiles`|L"SourceFiles"|
|`DiaTable_LineNums`|L "LineNumbers"|
|`DiaTable_SegMap`|L"SegmentMap"|
|`DiaTable_Dbg`|L"Dbg"|
|`DiaTable_InjSrc`|L"InjectedSource"|
|`DiaTable_FrameData`|L"FrameData"|

## <a name="example"></a>Esempio
Di seguito è riportato un esempio con uno di questi simboli:

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

## <a name="see-also"></a>Vedere anche
[Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
[Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)  
[Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
