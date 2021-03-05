---
description: Recupera un enumeratore per tutte le tabelle contenute nell'archivio dei simboli.
title: 'IDiaSession:: getEnumTables | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d75ac2a4bca7051c6fe80f80b7a8063ef7ec6c86
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102157021"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Recupera un enumeratore per tutte le tabelle contenute nell'archivio dei simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parametri
`ppEnumTables`

out Restituisce un oggetto [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) . Utilizzare questa interfaccia per enumerare le tabelle nell'archivio simboli.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="example"></a>Esempio
Questo esempio presenta una funzione generale che usa il `getEnumTables` metodo per ottenere un oggetto enumeratore specifico. Se l'enumeratore viene trovato, la funzione restituisce un puntatore di cui è possibile eseguire il cast all'interfaccia desiderata. in caso contrario, la funzione restituisce `NULL` .

```C++
IUnknown *GetTable(IDiaSession *pSession, REFIID iid)
{
    IUnknown *pUnknown = NULL;
    if (pSession != NULL)
    {
        CComPtr<IDiaEnumTables> pEnumTables;
        if (pSession->getEnumTables(&pEnumTables) == S_OK)
        {
            CComPtr<IDiaTable> pTable;
            DWORD celt = 0;
            while(pEnumTables->Next(1,&pTable,&celt) == S_OK &&
                  celt == 1)
            {
                if (pTable->QueryInterface(iid, (void **)pUnknown) == S_OK)
                {
                    break;
                }
                pTable = NULL;
            }
        }
    }
    return(pUnknown);
}
```

## <a name="see-also"></a>Vedi anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
