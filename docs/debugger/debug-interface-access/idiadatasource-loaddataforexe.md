---
title: Loaddataforexe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 4f95e8a9321ff7ae518e72496289f8ad0c7b4682
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56609644"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Viene aperto e prepara i dati di debug associati al file.exe/.dll.

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

[in] Percorso di file con estensione dll o .exe.

searchPath

[in] Percorso alternativo per cercare i dati di debug.

pCallback

[in] Un' `IUnknown` interfaccia per un oggetto che supporta un'interfaccia di callback di debug, ad esempio il [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), il [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), e/o il [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfacce.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. La tabella seguente illustra alcuni dei possibili codici di errore per questo metodo.

|Valore|Description|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Non è stato possibile aprire il file o il file di formato non è valido.|
|E_PDB_FORMAT|È stato effettuato un tentativo di accedere a un file con formato obsoleto.|
|E_PDB_INVALID_SIG|Firma non corrisponde.|
|E_PDB_INVALID_AGE|Non corrisponde a età.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|Origine dati è già stata preparata.|

## <a name="remarks"></a>Osservazioni
L'intestazione di debug del file.exe/.dll denomina la posizione di debug associati dati.

Questo metodo legge l'intestazione di debug e quindi Cerca e prepara i dati di debug. Lo stato di avanzamento della ricerca potrebbe, facoltativamente, essere segnalato e controllato tramite callback. Ad esempio, il [Notifydebugdir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) viene richiamato quando il `IDiaDataSource::loadDataForExe` metodo consente di individuare ed elabora una directory di debug.

Il [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) e [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfacce consentono all'applicazione client di fornire metodi alternativi per la lettura dei dati dal file eseguibile file quando il file non è accessibile direttamente tramite i/o file standard.

Per caricare un file con estensione pdb senza convalida, usare il [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) (metodo).

Per convalidare il file con estensione PDB in base ai criteri specifici, usare il [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) (metodo).

Per caricare un file con estensione pdb direttamente dalla memoria, usare il [Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) (metodo).

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
