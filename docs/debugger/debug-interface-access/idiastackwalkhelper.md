---
description: Facilita l'analisi dello stack usando il file di database di debug del programma (con estensione pdb).
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 06ba4964be340bd5d087a73fb5af9e9d48ded02d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128823"
---
# <a name="idiastackwalkhelper"></a>IDiaStackWalkHelper
Facilita l'analisi dello stack usando il file di database di debug del programma (con estensione pdb).

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
|[IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)|Legge un blocco di dati dall'immagine del file eseguibile in memoria.|
|[IDiaStackWalkHelper::searchForReturnAddress](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddress.md)|Cerca l'indirizzo stack frame specificato per l'indirizzo restituito della funzione più vicino.|
|[IDiaStackWalkHelper::searchForReturnAddressStart](../../debugger/debug-interface-access/idiastackwalkhelper-searchforreturnaddressstart.md)|Cerca nell'oggetto stack frame un indirizzo mittente in corrispondenza o vicino all'indirizzo dello stack specificato.|
|[IDiaStackWalkHelper::frameForVA](../../debugger/debug-interface-access/idiastackwalkhelper-frameforva.md)|Recupera l'stack frame contenente l'indirizzo virtuale specificato.|
|[IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)|Recupera il simbolo che contiene l'indirizzo virtuale specificato. **Nota:**  Symbol deve avere il tipo `SymTagFunctionType` (un valore [dell'enumerazione SymTagEnum).](../../debugger/debug-interface-access/symtagenum.md)|
|[IDiaStackWalkHelper::pdataForVA](../../debugger/debug-interface-access/idiastackwalkhelper-pdataforva.md)|Restituisce il blocco di dati PDATA associato all'indirizzo virtuale specificato.|
|[IDiaStackWalkHelper::imageForVA](../../debugger/debug-interface-access/idiastackwalkhelper-imageforva.md)|Recupera l'indirizzo virtuale iniziale di un eseguibile, dato un indirizzo virtuale da qualche parte nello spazio di memoria del file eseguibile.|

## <a name="remarks"></a>Commenti
 Questa interfaccia viene chiamata dal codice DIA per ottenere informazioni sull'eseguibile per costruire un elenco di stack frame durante l'esecuzione del programma.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Un'applicazione client implementa questa interfaccia per supportare l'esecuzione dello stack durante l'esecuzione del programma. Un'istanza di questa interfaccia viene passata ai metodi [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md) o [IDiaStackWalker::getEnumFrames2.](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)

## <a name="requirements"></a>Requisiti
 Intestazione: Dia2.h

 Libreria: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
- [IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)
