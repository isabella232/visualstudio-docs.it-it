---
description: Apre e verifica che il file di database di programma (con estensione pdb) corrisponda alle informazioni sulla firma fornite e prepara il file con estensione pdb come origine dati di debug.
title: IDiaDataSource::loadAndValidateDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadAndValidateDataFromPdb method
ms.assetid: d66712dd-6c24-4192-919a-cce262066f0e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9a3d09b96f835b84399742a461b404bc4b75ddc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097946"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Apre e verifica che il file di database di programma (con estensione pdb) corrisponda alle informazioni sulla firma fornite e prepara il file con estensione pdb come origine dati di debug.

## <a name="syntax"></a>Sintassi

```C++
HRESULT loadAndValidateDataFromPdb ( 
   LPCOLESTR pdbPath,
   GUID*     pcsig70,
   DWORD     sig,
   DWORD     age
);
```

#### <a name="parameters"></a>Parametri
`pdbPath`

[in] Percorso del file con estensione pdb.

`pcsig70`

[in] Firma GUID da verificare rispetto alla firma del file con estensione pdb. Solo i file con estensione pdb in [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e versioni successive hanno firme GUID.

`sig`

[in] Firma a 32 bit da verificare rispetto alla firma del file con estensione pdb.

`age`

[in] Valore di età da verificare. L'età non corrisponde necessariamente a un valore di ora noto, ma viene usata per determinare se un file con estensione pdb non è sincronizzato con un file .exe corrispondente.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati i possibili valori restituiti per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Impossibile aprire il file o il formato del file non è valido.|
|E_PDB_FORMAT|Tentativo di accedere a un file con un formato obsoleto.|
|E_PDB_INVALID_SIG|La firma non corrisponde.|
|E_PDB_INVALID_AGE|L'età non corrisponde.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|L'origine dati è già stata preparata.|

## <a name="remarks"></a>Commenti
Un file con estensione pdb contiene sia i valori di firma che i valori di età. Questi valori vengono replicati nel .exe o .dll file corrispondente al file con estensione pdb. Prima di preparare l'origine dati, questo metodo verifica che la firma e l'età del file con estensione pdb denominato corrispondano ai valori specificati.

Per caricare un file con estensione pdb senza convalida, usare il [metodo IDiaDataSource::loadDataFromPdb.](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)

Per accedere al processo di caricamento dei dati (tramite un meccanismo di callback), usare il metodo [IDiaDataSource::loadDataForExe.](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

Per caricare un file con estensione pdb direttamente dalla memoria, usare il [metodo IDiaDataSource::loadDataFromIStream.](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)

## <a name="example"></a>Esempio

```C++
IDiaDataSource* pSource;  // Previously created data source.
DEFINE_GUID(expectedGUIDSignature,0x1234,0x5678,0x01,0x02,0x03,0x04,0x05,0x06,0x07,0x08);
DWORD expectedFileSignature = 0x12345678;
DWORD expectedAge           = 128;

HRESULT hr;
hr = pSource->loadAndValidateDataFromPdb( L"yprog.pdb",
                                          &expectedGUIDSignature,
                                          expectedFileSignature,
                                          expectedAge);
if (FAILED(hr))
{
    // Report an error
}

```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
