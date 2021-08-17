---
description: Apre e prepara un file di database di programma (con estensione pdb) come origine dati di debug.
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 053a09d770069bc0030025fb6be130276b9942d327dc971b400e7a434e038a2c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121345252"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Apre e prepara un file di database di programma (con estensione pdb) come origine dati di debug.

## <a name="syntax"></a>Sintassi

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parametri
pdbPath

[in] Percorso del file con estensione pdb.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati i valori restituiti possibili per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossibile aprire il file o determinare che il formato del file non è valido.|
|E_PDB_FORMAT|Si è tentato di accedere a un file con un formato obsoleto.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|L'origine dati è già stata preparata.|

## <a name="remarks"></a>Commenti
Questo metodo carica i dati di debug direttamente da un file con estensione pdb.

Per convalidare il file con estensione pdb in base a criteri specifici, usare il metodo [IDiaDataSource::loadAndValidateDataFromPdb.](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)

Per ottenere l'accesso al processo di caricamento dei dati (tramite un meccanismo di callback), usare il [metodo IDiaDataSource::loadDataForExe.](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

Per caricare un file con estensione pdb direttamente dalla memoria, usare il [metodo IDiaDataSource::loadDataFromIStream.](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)

## <a name="example"></a>Esempio

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
