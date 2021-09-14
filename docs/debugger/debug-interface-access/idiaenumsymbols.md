---
description: Enumera i vari simboli contenuti nell'origine dati.
title: IDiaEnumSymbols | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols interface
ms.assetid: 649f7bfd-86ac-49a5-8533-aff77e1bc62e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6f8578ca439d32dbaae13356b0f76fb890d2d5ff
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629999"
---
# <a name="idiaenumsymbols"></a>IDiaEnumSymbols
Enumera i vari simboli contenuti nell'origine dati.

## <a name="syntax"></a>Sintassi

```
IDiaEnumSymbols : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaEnumSymbols` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaEnumSymbols::get__NewEnum](../../debugger/debug-interface-access/idiaenumsymbols-get-newenum.md)|Recupera la versione `IEnumVARIANT Interface` di questo enumeratore.|
|[IDiaEnumSymbols::get_Count](../../debugger/debug-interface-access/idiaenumsymbols-get-count.md)|Recupera il numero di simboli.|
|[IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)|Recupera un simbolo tramite un indice.|
|[IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)|Recupera un numero specificato di simboli nella sequenza di enumerazione.|
|[IDiaEnumSymbols::Skip](../../debugger/debug-interface-access/idiaenumsymbols-skip.md)|Ignora un numero specificato di simboli in una sequenza di enumerazione.|
|[IDiaEnumSymbols::Reset](../../debugger/debug-interface-access/idiaenumsymbols-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[IDiaEnumSymbols::Clone](../../debugger/debug-interface-access/idiaenumsymbols-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|

## <a name="remarks"></a>Commenti
Questa interfaccia fornisce simboli raggruppati in base a un tipo specifico di simbolo, ad esempio (tipi definiti `SymTagUDT` dall'utente) o `SymTagBaseClass` . Per usare i simboli raggruppati per indirizzo, usare [l'interfaccia IDiaEnumSymbolsByAddr.](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando i metodi seguenti:

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)

## <a name="example"></a>Esempio
In questo esempio viene illustrato come ottenere l'interfaccia e quindi usare tale enumerazione per elencare i tipi `IDiaEnumSymbols` definiti dall'utente.

> [!NOTE]
> `CDiaBSTR` è una classe che esegue il wrapping di un oggetto e gestisce automaticamente la liberatura della stringa quando la creazione di `BSTR` un'istanza esce dall'ambito.

```C++
void ShowUDTs(IDiaSymbol *pGlobals)
{
    CComPtr<IDiaEnumSymbols> pEnum;
    CComPtr<IDiaSymbol> pSymbol;
    HRESULT hr;

    hr = pGlobals->findChildren(SymTagUDT,
                                NULL,
                                nsfCaseInsensitive | nsfUndecoratedName,
                                &pEnum);
    if (hr == S_OK)
    {
        while ( SUCCEEDED( hr = pEnum->Next( 1, &pSymbol, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR name;
            if ( pSymbol->get_name( &name ) != S_OK )
                Fatal( "get_name" );
            printf( "Found UDT: %ws\n", name );
            pSymbol = 0;
        }
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
