---
title: IDiaStackWalkHelper | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2 interface
ms.assetid: d66e5c84-565d-494e-8486-f91db9a34548
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bdf2f54c585a8a5406a0772dc1c580112036671d
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85464625"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Facilita l'analisi dello stack utilizzando il file di database (con estensione pdb) di debug del programma.

## <a name="syntax"></a>Sintassi

```

IDiaStackWalkHelper: IUnknown

```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi di `IDiaStackWalkHelper` :

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaStackWalkHelper::get_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-get-registervalue.md)|Recupera il valore di un registro.|
|[IDiaStackWalkHelper::put_registerValue](../../debugger/debug-interface-access/idiastackwalkhelper-put-registervalue.md)|Imposta il valore di un registro.|
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Legge un blocco di dati dall'immagine dell'eseguibile in memoria.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Cerca nell'stack frame specificato l'indirizzo restituito della funzione più vicino.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Cerca nell'stack frame specificato un indirizzo restituito in corrispondenza o in prossimità dell'indirizzo dello stack specificato.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera la stack frame che contiene l'indirizzo virtuale specificato.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera il simbolo che contiene l'indirizzo virtuale specificato. **Nota:**  Il tipo del simbolo deve essere `SymTagFunctionType` un valore dell'enumerazione [SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) .|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Restituisce il blocco di dati PDATA associato all'indirizzo virtuale specificato.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera l'indirizzo virtuale iniziale di un eseguibile, dato un indirizzo virtuale in un punto qualsiasi dello spazio di memoria dell'eseguibile.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene chiamata dal codice DIA per ottenere informazioni sull'eseguibile per costruire un elenco di stack frame durante l'esecuzione del programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un'applicazione client implementa questa interfaccia per supportare l'analisi dello stack durante l'esecuzione del programma. Un'istanza di questa interfaccia viene passata ai metodi [IDiaStackWalker:: getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) o [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) .

## <a name="requirements"></a>Requisiti
 Intestazione: dia2. h

 Libreria: diaguids. lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)