---
description: Enumera in base all'indirizzo i vari simboli contenuti nell'origine dati.
title: IDiaEnumSymbolsByAddr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbolsbyAddr interface
ms.assetid: 37d3dcdf-e4fa-4354-b5e1-8843566b52ac
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 274fecb6e87e221360c2f97086155237d30a7148
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629963"
---
# <a name="idiaenumsymbolsbyaddr"></a>IDiaEnumSymbolsByAddr
Enumera in base all'indirizzo i vari simboli contenuti nell'origine dati.

## <a name="syntax"></a>Sintassi

```
IDiaEnumSymbolsByAddr : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaEnumSymbolsByAddr` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)|Posiziona l'enumeratore eseguendo una ricerca in base alla sezione e all'offset.|
|[IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)|Posiziona l'enumeratore eseguendo una ricerca in base all'indirizzo virtuale relativo.|
|[IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)|Posiziona l'enumeratore eseguendo una ricerca in base all'indirizzo virtuale .|
|[IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)|Recupera i simboli successivi in ordine in base all'indirizzo. Aggiorna la posizione dell'enumeratore in base al numero di elementi recuperati.|
|[IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)|Recupera i simboli precedenti in base all'indirizzo. Aggiorna la posizione dell'enumeratore in base al numero di elementi recuperati.|
|[IDiaEnumSymbolsByAddr::Clone](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-clone.md)|Crea una copia di un oggetto .|

## <a name="remarks"></a>Commenti
Questa interfaccia fornisce simboli raggruppati in base all'indirizzo. Per usare simboli raggruppati per tipo, ad esempio (tipo definito dall'utente) o `SymTagUDT` `SymTagBaseClass` , usare [l'interfaccia IDiaEnumSymbols.](../../debugger/debug-interface-access/idiaenumsymbols.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il [metodo IDiaSession::getSymbolsByAddr.](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)

## <a name="example"></a>Esempio
Questa funzione visualizza il nome e l'indirizzo di tutti i simboli ordinati in base all'indirizzo virtuale relativo.

```C++
void ShowSymbolsByAddress(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSymbolsByAddr> pEnumByAddr;
    if ( FAILED( psession->getSymbolsByAddr( &pEnumByAddr ) ) )
    {
        Fatal( "getSymbolsByAddr" );
    }
    CComPtr<IDiaSymbol> pSym;
    if ( FAILED( pEnumByAddr->symbolByAddr( 1, 0, &pSym ) ) )
    {
        Fatal( "symbolByAddr" );
    }
    DWORD rvaLast = 0;
    if ( pSym->get_relativeVirtualAddress( &rvaLast ) == S_OK )
    {
        pSym = 0;
        if ( FAILED( pEnumByAddr->symbolByRVA( rvaLast, &pSym ) ) )
        {
            Fatal( "symbolByAddr" );
        }
        printf( "Symbols in order\n" );
        do
        {
            CDiaBSTR name;
            if ( pSym->get_name( &name ) != S_OK )
            {
                printf( "\t0x%08X (%ws) <no name>\n", rvaLast );
            }
            else
            {
                printf( "\t0x%08X %ws\n", rvaLast, name );
            }
            pSym = 0;
            celt = 0;
            if ( FAILED( hr = pEnumByAddr->Next( 1, &pSym, &celt ) ) )
            {
                break;
            }
        } while ( celt == 1 );
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
