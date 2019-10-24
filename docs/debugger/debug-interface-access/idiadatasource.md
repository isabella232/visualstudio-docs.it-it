---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 453be1d77f1d2b1759e3de4433225cf97d026054
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744909"
---
# <a name="idiadatasource"></a>IDiaDataSource
Avvia l'accesso a un'origine di simboli di debug.

## <a name="syntax"></a>Sintassi

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
La tabella seguente illustra i metodi di `IDiaDataSource`.

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera il nome del file per l'ultimo errore di caricamento.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Apre e prepara un file di database di programma (con estensione pdb) come origine dati di debug.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Apre e verifica che il file del database di programma (con estensione pdb) corrisponda alle informazioni di firma fornite; prepara il file con estensione PDB come origine dati di debug.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Apre e prepara i dati di debug associati al file con estensione exe/dll.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara i dati di debug archiviati in un file di database di programma (con estensione pdb) a cui si accede tramite un flusso di dati in memoria.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Apre una sessione per l'esecuzione di query sui simboli.|

## <a name="remarks"></a>Note
Una chiamata a uno dei metodi Load dell'interfaccia `IDiaDataSource` apre l'origine del simbolo. Una chiamata riuscita al metodo [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) restituisce un'interfaccia [IDiaSession](../../debugger/debug-interface-access/idiasession.md) che supporta l'esecuzione di query sull'origine dati. Se il metodo Load restituisce un errore relativo al file, il valore restituito dal metodo [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) contiene il nome file associato all'errore.

## <a name="notes-for-callers"></a>Note per i chiamanti
Questa interfaccia viene ottenuta chiamando la funzione `CoCreateInstance` con l'identificatore di classe `CLSID_DiaSource` e l'ID di interfaccia di `IID_IDiaDataSource`. Nell'esempio viene illustrato come ottenere questa interfaccia.

## <a name="example"></a>Esempio

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Requisiti
Intestazione: dia2. h

Libreria: diaguids. lib

DLL: Msdia80. dll

## <a name="see-also"></a>Vedere anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
