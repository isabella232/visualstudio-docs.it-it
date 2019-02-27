---
title: Getenumtables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::getEnumTables method
ms.assetid: 66e0fba2-ca63-4e24-a46a-c99c7fb61dd1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 759972fa02c7645ae457e0b715d835b2d717e26f
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56608591"
---
# <a name="idiasessiongetenumtables"></a>IDiaSession::getEnumTables
Recupera un enumeratore per tutte le tabelle incluse nell'archivio simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT getEnumTables (
    IDiaEnumTables** ppEnumTables
);
```

#### <a name="parameters"></a>Parametri
`ppEnumTables`

[out] Restituisce un [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md) oggetto. Utilizzare questa interfaccia per enumerare le tabelle nell'archivio simboli.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="example"></a>Esempio
In questo esempio presenta una funzione generica che utilizza il `getEnumTables` metodo per ottenere un oggetto enumeratore specifico. Se l'enumeratore viene trovato, la funzione restituisce un puntatore che è possibile eseguire il cast all'interfaccia desiderata. in caso contrario, la funzione restituisce `NULL`.

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

## <a name="see-also"></a>Vedere anche
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
