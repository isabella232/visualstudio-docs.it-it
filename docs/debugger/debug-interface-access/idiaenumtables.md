---
title: IDiaEnumTables | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables interface
ms.assetid: 016190c5-09e4-48f2-bf60-9b02603a03e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 44a74d0c11f6d3f7265455bd8df1d481408d8e7b
ms.sourcegitcommit: 34940a18f5b03a59567f54c7024a0b16d4272f1e
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/12/2019
ms.locfileid: "56155825"
---
# <a name="idiaenumtables"></a>IDiaEnumTables
Enumera le varie tabelle contenute nell'origine dati.

## <a name="syntax"></a>Sintassi

```
IDiaEnumTables : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente sono illustrati i metodi di `IDiaEnumTables`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumTables::get__NewEnum](../../debugger/debug-interface-access/idiaenumtables-get-newenum.md)|Recupera le [dell'interfaccia IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) versione l'enumeratore.|
|[IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)|Recupera il numero di tabelle.|
|[IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)|Recupera una tabella tramite un indice o un nome.|
|[IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)|Recupera un determinato numero di tabelle nella sequenza di enumerazione.|
|[IDiaEnumTables::Skip](../../debugger/debug-interface-access/idiaenumtables-skip.md)|Ignora un determinato numero di tabelle in una sequenza di enumerazione.|
|[IDiaEnumTables::Reset](../../debugger/debug-interface-access/idiaenumtables-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|
|[IDiaEnumTables::Clone](../../debugger/debug-interface-access/idiaenumtables-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|

## <a name="remarks"></a>Note

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il [Getenumtables](../../debugger/debug-interface-access/idiasession-getenumtables.md) (metodo).

## <a name="example"></a>Esempio
In questo esempio viene illustrato come ottenere il `IDiaEnumTables` interfaccia da una sessione. Per un esempio più completo di utilizzo di tabelle, vedere la [IDiaTable](../../debugger/debug-interface-access/idiatable.md) interfaccia.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    // Do something with table
}
```

## <a name="requirements"></a>Requisiti
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: MSDIA80

## <a name="see-also"></a>Vedere anche
[Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)
