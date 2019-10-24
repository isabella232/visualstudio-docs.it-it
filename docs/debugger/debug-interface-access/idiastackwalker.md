---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741513"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
Fornisce metodi per eseguire un percorso stack usando le informazioni nel file con estensione pdb.

## <a name="syntax"></a>Sintassi

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaStackWalker`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|Recupera un enumeratore stack frame per le piattaforme x86.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|Recupera un enumeratore di stack frame per un tipo di piattaforma specifico.|

## <a name="remarks"></a>Note
Questa interfaccia viene usata per ottenere un elenco di stack frame per un modulo caricato. A ognuno dei metodi viene passato un oggetto [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) (implementato dall'applicazione client) che fornisce le informazioni necessarie per creare l'elenco di stack frame.

## <a name="notes-for-callers"></a>Note per i chiamanti
Questa interfaccia viene ottenuta chiamando il metodo `CoCreateInstance` con l'identificatore di classe `CLSID_DiaStackWalker` e l'ID di interfaccia di `IID_IDiaStackWalker`. Nell'esempio viene illustrato come ottenere questa interfaccia.

## <a name="example"></a>Esempio
Questo esempio illustra come ottenere l'interfaccia `IDiaStackWalker`.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
