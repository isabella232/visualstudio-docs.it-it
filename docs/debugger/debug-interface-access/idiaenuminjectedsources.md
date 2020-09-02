---
title: IDiaEnumInjectedSources | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumInjectedSources interface
ms.assetid: f97e2392-22e1-48da-b7ce-ad94c8b684b0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ecd669e546f12972c2a11c3b038322ceaf18fc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468245"
---
# <a name="idiaenuminjectedsources"></a>IDiaEnumInjectedSources
Enumerare le varie origini inserite contenute nell'origine dati.

## <a name="syntax"></a>Sintassi

```
IDiaEnumInjectedSources : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaEnumInjectedSources` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumInjectedSources::get__NewEnum](../../debugger/debug-interface-access/idiaenuminjectedsources-get-newenum.md)|Recupera la versione dell' [interfaccia IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) dell'enumeratore.|
|[IDiaEnumInjectedSources::get_Count](../../debugger/debug-interface-access/idiaenuminjectedsources-get-count.md)|Recupera il numero di origini inserite.|
|[IDiaEnumInjectedSources::Item](../../debugger/debug-interface-access/idiaenuminjectedsources-item.md)|Recupera un'origine inserita per mezzo di un indice.|
|[IDiaEnumInjectedSources::Next](../../debugger/debug-interface-access/idiaenuminjectedsources-next.md)|Recupera un numero specificato di origini inserite nella sequenza di enumerazione.|
|[IDiaEnumInjectedSources::Skip](../../debugger/debug-interface-access/idiaenuminjectedsources-skip.md)|Ignora un numero specificato di origini inserite in una sequenza di enumerazione.|
|[IDiaEnumInjectedSources::Reset](../../debugger/debug-interface-access/idiaenuminjectedsources-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[IDiaEnumInjectedSources::Clone](../../debugger/debug-interface-access/idiaenuminjectedsources-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|

## <a name="remarks"></a>Osservazioni

## <a name="notes-for-callers"></a>Note per i chiamanti
Questa interfaccia viene ottenuta chiamando il metodo [IDiaSession:: findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md) con il nome di un file di origine specifico oppure chiamando il metodo [IDiaSession:: GETENUMTABLES](../../debugger/debug-interface-access/idiasession-getenumtables.md) con il GUID dell' `IDiaEnumInjectedSources` interfaccia.

## <a name="example"></a>Esempio
Questo esempio illustra come ottenere (la `GetEnumInjectedSources` funzione) e usare (la `DumpAllInjectedSources` funzione) l' `IDiaEnumInjectedSources` interfaccia. Vedere l'interfaccia [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md) per un'implementazione della `PrintPropertyStorage` funzione. Per un output alternativo, vedere l'interfaccia [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .

```C++

IDiaEnumInjectedSources* GetEnumInjectedSources(IDiaSession *pSession)
{
    IDiaEnumInjectedSources* pUnknown    = NULL;
    REFIID                   iid         = __uuidof(IDiaEnumInjectedSources);
    IDiaEnumTables*          pEnumTables = NULL;
    IDiaTable*               pTable      = NULL;
    ULONG                    celt        = 0;

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

void DumpAllInjectedSources( IDiaSession* pSession)
{
    IDiaEnumInjectedSources* pEnumInjSources;

    pEnumInjSources = GetEnumInjectedSources(pSession);
    if (pEnumInjSources != NULL)
    {
        IDiaInjectedSource* pInjSource;
        ULONG celt = 0;

        while(pEnumInjSources->Next(1, &pInjSource, &celt) == S_OK &&
              celt == 1)
        {
            IDiaPropertyStorage *pPropertyStorage;
            if (pInjSource->QueryInterface(__uuidof(IDiaPropertyStorage),
                                          (void **)&pPropertyStorage) == S_OK)
            {
                PrintPropertyStorage(pPropertyStorage);
                pPropertyStorage->Release();
            }
            pInjSource->Release();
        }
        pEnumInjSources->Release();
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)
- [IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
- [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)
