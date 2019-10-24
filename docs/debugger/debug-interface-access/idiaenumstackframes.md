---
title: IDiaEnumStackFrames | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumStackFrames interface
ms.assetid: 3d1e8403-c9fc-42ff-ae35-0ab9a5ed2ad7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 83e6adb3157b67b89ef2c05f59eaaf2c7084d9d8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744012"
---
# <a name="idiaenumstackframes"></a>IDiaEnumStackFrames
Enumera i vari stack frame disponibili.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumStackFrames::Next](../../debugger/debug-interface-access/idiaenumstackframes-next.md)|Recupera un numero specificato di elementi stack frame dalla sequenza di enumerazione.|
|[IDiaEnumStackFrames::Reset](../../debugger/debug-interface-access/idiaenumstackframes-reset.md)|Reimposta l'inizio di una sequenza di enumerazione.|

## <a name="remarks"></a>Note

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il metodo [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) o [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="example"></a>Esempio
Questo esempio illustra come ottenere e usare l'interfaccia `IDiaEnumStackFrames`. Per un'implementazione della funzione `PrintStackFrame`, vedere l'interfaccia [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) .

```C++
void DumpStackFrames(IDiaStackWalker*     pStackWalker,
                     IDiaStackWalkHelper* pStackWalkHelper,
                     CV_CPU_TYPE_e        cpuType)
{
    if (pStackWalker != NULL && pStackWalkHelper != NULL)
    {
        CComPtr<IDiaEnumStackFrames> pEnumsFrames;
        HRESULT hr;
        hr = pStackWalker->getEnumFrames2(cpuType, pStackWalkHelper, &pEnumFrames);
        if (SUCCEEDED(hr) && pEnumFrames != NULL)
        {
            CComPtr<IDiaStackFrame> pStackFrame;
            DWORD celt = 0;

            while (pEnumFrames->Next(1, &pStackFrame, &celt) == S_OK)
            {
                PrintStackFrame(pStackFrame);
            }
            pStackFrame = NULL;
        }
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
