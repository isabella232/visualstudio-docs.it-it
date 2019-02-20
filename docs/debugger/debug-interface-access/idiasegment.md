---
title: IDiaSegment | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSegment interface
ms.assetid: 384ae0e1-077e-4d4f-98de-ac43c32c882f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9507e7791f1ecd61a2f7a6321bdf45fe256feb4
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227550"
---
# <a name="idiasegment"></a>IDiaSegment
Esegue il mapping dei dati rispetto al numero di sezione ai segmenti dello spazio degli indirizzi.

## <a name="syntax"></a>Sintassi

```
IDiaSegment : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente sono illustrati i metodi di `IDiaSegment`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaSegment::get_frame](../../debugger/debug-interface-access/idiasegment-get-frame.md)|Recupera il numero di segmenti.|
|[IDiaSegment::get_offset](../../debugger/debug-interface-access/idiasegment-get-offset.md)|Recupera l'offset in segmenti in cui inizia la sezione.|
|[IDiaSegment::get_length](../../debugger/debug-interface-access/idiasegment-get-length.md)|Recupera il numero di byte nel segmento.|
|[IDiaSegment::get_read](../../debugger/debug-interface-access/idiasegment-get-read.md)|Recupera un flag che indica se il segmento può essere letto.|
|[IDiaSegment::get_write](../../debugger/debug-interface-access/idiasegment-get-write.md)|Recupera un flag che indica se il segmento può essere modificato.|
|[IDiaSegment::get_execute](../../debugger/debug-interface-access/idiasegment-get-execute.md)|Recupera un flag che indica se il segmento è eseguibile.|
|[IDiaSegment::get_addressSection](../../debugger/debug-interface-access/idiasegment-get-addresssection.md)|Recupera il numero di sezione che viene eseguito il mapping a questo segmento.|
|[IDiaSegment::get_relativeVirtualAddress](../../debugger/debug-interface-access/idiasegment-get-relativevirtualaddress.md)|Recupera l'indirizzo virtuale relativo (RVA) dell'inizio della sezione.|
|[IDiaSegment::get_virtualAddress](../../debugger/debug-interface-access/idiasegment-get-virtualaddress.md)|Recupera l'indirizzo virtuale (valutazione della vulnerabilità) dell'inizio della sezione.|

## <a name="remarks"></a>Osservazioni
Poiché il DIA SDK esegue già traduzioni dall'offset della sezione a indirizzi virtuali relativi, la maggior parte delle applicazioni non apporterà usare le informazioni nella mappa di segmenti.

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il [Idiaenumsegments](../../debugger/debug-interface-access/idiaenumsegments-item.md) oppure [Idiaenumsegments](../../debugger/debug-interface-access/idiaenumsegments-next.md) metodi. Vedere l'esempio per i dettagli.

## <a name="example"></a>Esempio
Questa funzione consente di visualizzare l'indirizzo di tutti i segmenti in una tabella e il simbolo più vicino.

```C++
void ShowSegments(IDiaTable *pTable, IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pSegments;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSegments ),
                               (void**)&pSegments )
                  )
       )
    {
        CComPtr<IDiaSegment> pSegment;
        while ( SUCCEEDED( hr = pSegments->Next( 1, &pSegment, &celt ) ) &&
                celt == 1 )
        {
            DWORD rva;
            DWORD seg;

            pSegment->get_addressSection( &seg );
            if ( pSegment->get_relativeVirtualAddress( &rva ) == S_OK )
            {
                printf( "Segment %i addr: 0x%.8X\n", seg, rva );
                pSegment = NULL;

                CComPtr<IDiaSymbol> pSym;
                if ( psession->findSymbolByRVA( rva, SymTagNull, &pSym ) == S_OK )
                {
                    CDiaBSTR name;
                    DWORD    tag;

                    pSym->get_symTag( &tag );
                    pSym->get_name( &name );
                    printf( "\tClosest symbol: %ws (%ws)\n",
                            name != NULL ? name : L"",
                            szTags[ tag ] );
                }
            }
        }
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: MSDIA80

## <a name="see-also"></a>Vedere anche
[Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)  
[IDiaEnumSegments::Next](../../debugger/debug-interface-access/idiaenumsegments-next.md)
