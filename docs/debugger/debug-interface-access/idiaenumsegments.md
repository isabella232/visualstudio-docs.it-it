---
title: IDiaEnumSegments | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments interface
ms.assetid: 0c9edd5e-b9ce-43e1-a791-cd4c5d16d923
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eff457d539317d2f8c7d77dfc85eb16063650c14
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744151"
---
# <a name="idiaenumsegments"></a>IDiaEnumSegments
Enumera i vari segmenti contenuti nell'origine dati.

## <a name="syntax"></a>Sintassi

```
IDiaEnumSegments : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaEnumSegments`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumSegments::get__NewEnum](../../debugger/debug-interface-access/idiaenumsegments-get-newenum.md)|Recupera la versione dell' [interfaccia IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) dell'enumeratore.|
|[IDiaEnumSegments::get_Count](../../debugger/debug-interface-access/idiaenumsegments-get-count.md)|Recupera il numero di segmenti.|
|[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)|Recupera un segmento per mezzo di un indice.|
|[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)|Recupera un numero specificato di segmenti nella sequenza di enumerazione.|
|[IDiaEnumSegments::Skip](../../debugger/debug-interface-access/idiaenumsegments-skip.md)|Ignora un numero specificato di segmenti in una sequenza di enumerazione.|
|[IDiaEnumSegments::Reset](../../debugger/debug-interface-access/idiaenumsegments-reset.md)|Reimposta l'inizio di una sequenza di enumerazione.|
|[IDiaEnumSegments::Clone](../../debugger/debug-interface-access/idiaenumsegments-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|

## <a name="remarks"></a>Note

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il metodo `QueryInterface` su un oggetto [IDiaTable](../../debugger/debug-interface-access/idiatable.md) . Per informazioni dettagliate, vedere l'esempio.

## <a name="example"></a>Esempio
In questo esempio viene illustrato come ottenere l'interfaccia `IDiaEnumSections` da una tabella. Per un esempio più completo dell'uso dei segmenti, vedere l'interfaccia [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md) .

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                __uuidof( IDiaEnumSegments ),
                                (void**)&pSegments )
                  )
       )
    {
        // Do something with this enumeration
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaTable](../../debugger/debug-interface-access/idiatable.md)
- [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
