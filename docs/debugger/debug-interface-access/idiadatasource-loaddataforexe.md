---
title: 'IDiaDataSource:: loadDataForExe | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ed61f8ffc95d0004213483d5b5d507c45ef2647
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85468518"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Apre e prepara i dati di debug associati al file con estensione exe/dll.

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

in Percorso del file con estensione exe o dll.

searchPath

in Percorso alternativo per la ricerca dei dati di debug.

pCallback

in `IUnknown` Interfaccia per un oggetto che supporta un'interfaccia di callback di debug, ad esempio [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)e/o le interfacce [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati alcuni dei possibili codici di errore per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Non è stato possibile aprire il file o il formato del file non è valido.|
|E_PDB_FORMAT|Tentativo di accedere a un file con un formato obsoleto.|
|E_PDB_INVALID_SIG|La firma non corrisponde.|
|E_PDB_INVALID_AGE|Age non corrisponde a.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|L'origine dati è già stata preparata.|

## <a name="remarks"></a>Osservazioni
L'intestazione di debug del file con estensione exe/dll assegna un nome al percorso dei dati di debug associato.

Questo metodo legge l'intestazione di debug e quindi Cerca e prepara i dati di debug. Lo stato di avanzamento della ricerca può, facoltativamente, essere segnalato e controllato tramite callback. Ad esempio, [IDiaLoadCallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) viene richiamato quando il `IDiaDataSource::loadDataForExe` metodo individua ed elabora una directory di debug.

Le interfacce [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) e [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) consentono all'applicazione client di fornire metodi alternativi per la lettura dei dati dal file eseguibile quando non è possibile accedere al file direttamente tramite i/O file standard.

Per caricare un file con estensione pdb senza convalida, usare il metodo [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Per convalidare il file con estensione PDB rispetto a criteri specifici, usare il metodo [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Per caricare un file con estensione PDB direttamente dalla memoria, usare il metodo [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

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
