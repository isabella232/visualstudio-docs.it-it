---
description: Avvia l'accesso a un'origine di simboli di debug.
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2c524025a5117406ad8de3737226495253f297e9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630474"
---
# <a name="idiadatasource"></a>IDiaDataSource
Avvia l'accesso a un'origine di simboli di debug.

## <a name="syntax"></a>Sintassi

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
Nella tabella seguente vengono illustrati i metodi di `IDiaDataSource` .

|Metodo|Descrizione|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera il nome file per l'ultimo errore di caricamento.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Apre e prepara un file di database di programma (con estensione pdb) come origine dati di debug.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Apre e verifica che il file di database di programma (con estensione pdb) corrisponda alle informazioni sulla firma fornite. prepara il file con estensione pdb come origine dati di debug.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Apre e prepara i dati di debug associati al file .exe/.dll.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara i dati di debug archiviati in un file di database di programma (con estensione pdb) a cui si accede tramite un flusso di dati in memoria.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Apre una sessione per l'esecuzione di query sui simboli.|

## <a name="remarks"></a>Commenti
Una chiamata a uno dei metodi di caricamento `IDiaDataSource` dell'interfaccia apre l'origine dei simboli. Una chiamata riuscita al metodo [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) restituisce [un'interfaccia IDiaSession](../../debugger/debug-interface-access/idiasession.md) che supporta l'esecuzione di query sull'origine dati. Se il metodo load restituisce un errore correlato al file, il valore restituito del metodo [IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) contiene il nome file associato all'errore.

## <a name="notes-for-callers"></a>Note per i chiamanti
Questa interfaccia viene ottenuta chiamando la `CoCreateInstance` funzione con l'identificatore di classe `CLSID_DiaSource` e l'ID di interfaccia di `IID_IDiaDataSource` . L'esempio mostra come viene ottenuta questa interfaccia.

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
Intestazione: Dia2.h

Libreria: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
