---
title: IDiaTable | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaTable interface
ms.assetid: c99a2c44-7b72-4e3c-b963-25fe3df3a555
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b44d7ad28ff2fdc5c6f71daca1d5479cd05263ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862402"
---
# <a name="idiatable"></a>IDiaTable
Enumera una tabella di origine dati DIA.

## <a name="syntax"></a>Sintassi

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaTable` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera la versione dell' [interfaccia IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) dell'enumeratore.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera il nome della tabella.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera il numero di elementi nella tabella.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera un riferimento a un indice di voce specifico.|

## <a name="remarks"></a>Commenti
Questa interfaccia implementa i `IEnumUnknown` metodi di enumerazione nello spazio dei nomi Microsoft. VisualStudio. OLE. Interop. L' `IEnumUnknown` interfaccia di enumerazione è molto più efficiente per scorrere il contenuto della tabella rispetto ai metodi [IDiaTable:: Get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) e [IDiaTable:: Item](../../debugger/debug-interface-access/idiatable-item.md) .

L'interpretazione dell' `IUnknown` interfaccia restituita dal `IDiaTable::Item` metodo o dal `Next` Metodo (nello spazio dei nomi Microsoft. VisualStudio. OLE. Interop) dipende dal tipo di tabella. Se, ad esempio, l' `IDiaTable` interfaccia rappresenta un elenco di origini inserite, l'interfaccia deve essere sottoposta `IUnknown` a query per l'interfaccia [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md) .

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il metodo [IDiaEnumTables:: Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o [IDiaEnumTables:: Next](../../debugger/debug-interface-access/idiaenumtables-next.md) .

Le interfacce seguenti sono implementate con l' `IDiaTable` interfaccia, ovvero è possibile eseguire una query sull' `IDiaTable` interfaccia per una delle interfacce seguenti:

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Esempio
La prima funzione, `ShowTableNames` , Visualizza i nomi di tutte le tabelle della sessione. La seconda funzione, `GetTable` , esegue la ricerca in tutte le tabelle di una tabella che implementa un'interfaccia specificata. La terza funzione, `UseTable` , Mostra come usare la `GetTable` funzione.

> [!NOTE]
> `CDiaBSTR` è una classe che esegue il wrapping `BSTR` di un oggetto e gestisce automaticamente la liberazione della stringa quando la creazione dell'istanza esce dall'ambito.

```C++
void ShowTableNames(IDiaSession *pSession)
{
    CComPtr<IDiaEnumTables> pTables;
    if ( FAILED( psession->getEnumTables( &pTables ) ) )
    {
        Fatal( "getEnumTables" );
    }
    CComPtr< IDiaTable > pTable;
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) )
            && celt == 1 )
    {
        CDiaBSTR bstrTableName;
        if ( pTable->get_name( &bstrTableName ) != 0 )
        {
            Fatal( "get_name" );
        }
        printf( "Found table: %ws\n", bstrTableName );
    }

// Searches the list of all tables for a table that supports
// the specified interface.  Use this function to obtain an
// enumeration interface.
HRESULT GetTable(IDiaSession* pSession,
                 REFIID       iid,
                 void**       ppUnk)
{
    CComPtr<IDiaEnumTables> pEnumTables;
    HRESULT hResult;

    if (FAILED(pSession->getEnumTables(&pEnumTables)))
        Fatal("getEnumTables");

    CComPtr<IDiaTable> pTable;
    ULONG celt = 0;
    while (SUCCEEDED(hResult = pEnumTables->Next(1, &pTable, &celt)) &&
           celt == 1)
    {
        if (pTable->QueryInterface(iid, (void**)ppUnk) == S_OK)
        {
            return S_OK;
        }
        pTable = NULL;
    }

    if (FAILED(hResult))
        Fatal("EnumTables->Next");

    return E_FAIL;
}

// This function shows how to use the GetTable function.
void UseTable(IDiaSession *pSession)
{
    CComPtr<IDiaEnumSegments> pEnumSegments;
    if (SUCCEEDED(GetTable(pSession, __uuidof(IDiaEnumSegments), &pEnumSegments)))
    {
        // Do something with pEnumSegments.
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
