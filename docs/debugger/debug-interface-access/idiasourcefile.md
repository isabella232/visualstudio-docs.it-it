---
title: IDiaSourceFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile interface
ms.assetid: 6e9be757-797f-4960-ba62-c14092620bbd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c28559eb3b936505cf03c6499dd79178554645bf
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2020
ms.locfileid: "85465164"
---
# <a name="idiasourcefile"></a>IDiaSourceFile
Rappresenta un file di origine.

## <a name="syntax"></a>Sintassi

```
IDiaSourceFile : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaSourceFile` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaSourceFile::get_uniqueId](../../debugger/debug-interface-access/idiasourcefile-get-uniqueid.md)|Recupera un valore di chiave Integer semplice univoco per questa immagine.|
|[IDiaSourceFile::get_fileName](../../debugger/debug-interface-access/idiasourcefile-get-filename.md)|Recupera il nome del file di origine.|
|[IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)|Recupera il tipo di checksum.|
|[IDiaSourceFile::get_compilands](../../debugger/debug-interface-access/idiasourcefile-get-compilands.md)|Recupera un enumeratore di moduli con i numeri di riga che fanno riferimento a questo file.|
|[IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)|Recupera i byte di checksum.|

## <a name="remarks"></a>Commenti

## <a name="notes-for-callers"></a>Note per i chiamanti
Ottenere questa interfaccia chiamando il metodo [IDiaEnumSourceFiles:: Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md) o [IDiaEnumSourceFiles:: Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md) . Per informazioni dettagliate, vedere l'esempio.

## <a name="example"></a>Esempio
Questa funzione consente di visualizzare i nomi di tutti i file di origine che contribuiscono alla tabella specificata.

```C++
void ShowSourceFiles(IDiaTable *pTable)
{
    CComPtr<IDiaEnumSourceFiles> pSourceFiles;
    if ( SUCCEEDED( pTable->QueryInterface(
                                _uuidof( IDiaEnumSourceFiles ),
                               (void**)&pSourceFiles )
                  )
       )
    {
        CComPtr<IDiaSourceFile> pSourceFile;
        while ( SUCCEEDED( hr = pSourceFiles->Next( 1, &pSourceFile, &celt ) ) &&
                celt == 1 )
        {
            CDiaBSTR fileName;
            if ( pSourceFile->get_fileName( &fileName) == S_OK )
            {
                printf( "file name: %ws\n", fileName );
            }
            pSourceFile = NULL;
        }
    }
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaEnumSourceFiles::Item](../../debugger/debug-interface-access/idiaenumsourcefiles-item.md)
- [IDiaEnumSourceFiles::Next](../../debugger/debug-interface-access/idiaenumsourcefiles-next.md)
- [IDiaLineNumber::get_sourceFile](../../debugger/debug-interface-access/idialinenumber-get-sourcefile.md)
- [IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)
- [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)
- [IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)
