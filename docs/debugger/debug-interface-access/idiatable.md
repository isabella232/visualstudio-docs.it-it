---
description: Enumera una tabella di origine dati DIA.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7f8dc87343a425d87c2936b6667f350c456b45cf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628013"
---
# <a name="idiatable"></a>IDiaTable
Enumera una tabella di origine dati DIA.

## <a name="syntax"></a>Sintassi

```
IDiaTable : IEnumUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaTable` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaTable::get__NewEnum](../../debugger/debug-interface-access/idiatable-get-newenum.md)|Recupera la [versione dell'interfaccia IEnumVARIANT](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-ienumvariant) di questo enumeratore.|
|[IDiaTable::get_name](../../debugger/debug-interface-access/idiatable-get-name.md)|Recupera il nome della tabella.|
|[IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md)|Recupera il numero di elementi nella tabella.|
|[IDiaTable::Item](../../debugger/debug-interface-access/idiatable-item.md)|Recupera un riferimento a un indice di voce specifico.|

## <a name="remarks"></a>Commenti
Questa interfaccia implementa i metodi di enumerazione nello spazio dei `IEnumUnknown` nomi Microsoft.VisualStudio.OLE.Interop. L'interfaccia di enumerazione è molto più efficiente per l'iterazione del contenuto della tabella rispetto ai metodi `IEnumUnknown` [IDiaTable::get_Count](../../debugger/debug-interface-access/idiatable-get-count.md) [e IDiaTable::Item.](../../debugger/debug-interface-access/idiatable-item.md)

L'interpretazione dell'interfaccia restituita dal metodo o dal metodo (nello spazio dei nomi `IUnknown` `IDiaTable::Item` `Next` Microsoft.VisualStudio.OLE.Interop) dipende dal tipo di tabella. Ad esempio, se l'interfaccia rappresenta un elenco di origini iniettate, è necessario eseguire query sull'interfaccia `IDiaTable` `IUnknown` [IDiaInjectedSource.](../../debugger/debug-interface-access/idiainjectedsource.md)

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando i [metodi IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md) o [IDiaEnumTables::Next.](../../debugger/debug-interface-access/idiaenumtables-next.md)

Le interfacce seguenti vengono implementate con l'interfaccia , ovvero è possibile eseguire query sull'interfaccia `IDiaTable` per una delle interfacce `IDiaTable` seguenti:

- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)

- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

- [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)

- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)

- [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)

- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)

## <a name="example"></a>Esempio
La prima funzione, `ShowTableNames` , visualizza i nomi di tutte le tabelle nella sessione. La seconda funzione, `GetTable` , cerca in tutte le tabelle una tabella che implementa un'interfaccia specificata. La terza funzione, `UseTable` , illustra come usare la funzione `GetTable` .

> [!NOTE]
> `CDiaBSTR` è una classe che esegue il wrapping di un oggetto e gestisce automaticamente la liberatura della stringa quando la creazione di `BSTR` un'istanza esce dall'ambito.

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
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
- [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
- [IDiaEnumTables::Next](../../debugger/debug-interface-access/idiaenumtables-next.md)
