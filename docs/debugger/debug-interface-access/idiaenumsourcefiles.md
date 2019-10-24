---
title: IDiaEnumSourceFiles | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles interface
ms.assetid: 5c0779a6-a2ea-408a-90da-ebdecf2b83c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 091d2f5996d53341e57c5c1b2125609642a156eb
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744019"
---
# <a name="idiaenumsourcefiles"></a>IDiaEnumSourceFiles
Enumera i vari file di origine contenuti nell'origine dati.

## <a name="syntax"></a>Sintassi

```
IDiaEnumSourceFiles : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaEnumSourceFiles`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumSourceFiles::get__NewEnum](../../debugger/debug-interface-access/idiaenumsourcefiles-get-newenum.md)|Recupera la versione `IEnumVARIANT Interface` dell'enumeratore.|
|[IDiaEnumSourceFiles::get_Count](../../debugger/debug-interface-access/idiaenumsourcefiles-get-count.md)|Recupera il numero di file di origine.|
|[IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)|Recupera un file di origine per mezzo di un indice.|
|[IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)|Recupera un numero specificato di file di origine nella sequenza di enumerazione.|
|[IDiaEnumSourceFiles::Skip](../../debugger/debug-interface-access/idiaenumsourcefiles-skip.md)|Ignora un numero specificato di file di origine in una sequenza di enumerazione.|
|[IDiaEnumSourceFiles::Reset](../../debugger/debug-interface-access/idiaenumsourcefiles-reset.md)|Reimposta l'inizio di una sequenza di enumerazione.|
|[IDiaEnumSourceFiles::Clone](../../debugger/debug-interface-access/idiaenumsourcefiles-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|

## <a name="remarks"></a>Note

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il metodo `QueryInterface` su un oggetto [IDiaTable](../../debugger/debug-interface-access/idiatable.md) . Per informazioni dettagliate, vedere l'esempio.

## <a name="example"></a>Esempio
Questo esempio illustra come ottenere l'interfaccia `IDiaEnumSourceFiles` dall'elenco di tabelle in un oggetto di sessione DIA. Per un esempio di accesso alle informazioni sul file di origine, vedere l'interfaccia [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) .

```C++

IDiaEnumSourceFiles* GetEnumSourceFiles(IDiaSession *pSession)
{
    IDiaEnumSourceFiles * pUnknown    = NULL;
    REFIID                iid         = __uuidof(IDiaEnumSourceFiles);
    IDiaEnumTables*       pEnumTables = NULL;
    IDiaTable*            pTable      = NULL;
    ULONG                 celt        = 0;

    if (pSession->getEnumTables(&pEnumTables) != S_OK)
    {
        wprintf(L"ERROR - GetTable() getEnumTables\n");
        return NULL;
    }
    while (pEnumTables->Next(1, &pTable, &celt) == S_OK && celt == 1)
    {
        // There is only one table that matches the given iid
        HRESULT hr = pTable->QueryInterface(iid, (void**)&pUnknown);
        pTable->Release();
        if (hr == S_OK)
        {
            break;
        }
    }
    pEnumTables->Release();
    return pUnknown;
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
