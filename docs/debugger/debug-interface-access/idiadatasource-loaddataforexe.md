---
description: Apre e prepara i dati di debug associati al file .exe/.dll.
title: IDiaDataSource::loadDataForExe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6e11a6d85e8a33803b7cbf8b912d3db834996753
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122154695"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Apre e prepara i dati di debug associati al file .exe/.dll.

## <a name="syntax"></a>Sintassi

```C++
HRESULT loadDataForExe (
   LPCOLESTR executable,
   LPCOLESTR searchPath,
   IUnknown* pCallback
);
```

#### <a name="parameters"></a>Parametri
eseguibile

[in] Percorso del file .exe o .dll.

searchPath

[in] Percorso alternativo in cui cercare i dati di debug.

pCallback

[in] Interfaccia per un oggetto che supporta un'interfaccia di callback di debug, ad esempio `IUnknown` [IDiaLoadCallback,](../../debugger/debug-interface-access/idialoadcallback.md) [IDiaLoadCallback2,](../../debugger/debug-interface-access/idialoadcallback2.md) [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)e/o le interfacce [IDiaReadExeAtRVACallback.](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati alcuni dei possibili codici di errore per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossibile aprire il file o il formato del file non è valido.|
|E_PDB_FORMAT|Si è tentato di accedere a un file con un formato obsoleto.|
|E_PDB_INVALID_SIG|La firma non corrisponde.|
|E_PDB_INVALID_AGE|L'età non corrisponde.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|L'origine dati è già stata preparata.|

## <a name="remarks"></a>Commenti
L'intestazione di debug del file .exe/.dll il percorso dei dati di debug associato.

Se si caricano dati di debug da un server di simboli, *symsrv.dll* deve essere presente nella stessa directory in cui è installata l'applicazione dell'utente o *msdia140.dll* oppure deve essere presente nella directory di sistema.

Questo metodo legge l'intestazione di debug e quindi cerca e prepara i dati di debug. Facoltativamente, lo stato di avanzamento della ricerca può essere segnalato e controllato tramite callback. Ad esempio, [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) viene richiamato quando il metodo trova `IDiaDataSource::loadDataForExe` ed elabora una directory di debug.

Le [interfacce IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) e [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) consentono all'applicazione client di fornire metodi alternativi per la lettura dei dati dal file eseguibile quando non è possibile accedere al file direttamente tramite I/O standard del file.

Per caricare un file con estensione pdb senza convalida, usare il [metodo IDiaDataSource::loadDataFromPdb.](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)

Per convalidare il file con estensione pdb in base a criteri specifici, usare il metodo [IDiaDataSource::loadAndValidateDataFromPdb.](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)

Per caricare un file con estensione pdb direttamente dalla memoria, usare il [metodo IDiaDataSource::loadDataFromIStream.](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)

## <a name="example"></a>Esempio

```C++
class MyCallBack: public IDiaLoadCallback
{
...
};
MyCallBack callback;
...
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);
if (FAILED(hr))
{
    // Report error
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
