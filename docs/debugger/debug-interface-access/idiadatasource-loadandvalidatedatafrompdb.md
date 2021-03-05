---
description: Apre e verifica che il file del database di programma (con estensione pdb) corrisponda alle informazioni di firma fornite e prepara il file con estensione PDB come origine dati di debug.
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
ms.workload:
- multiple
ms.openlocfilehash: 0d55053271e38ee87533a11a8c5f6cd30d7e7333
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158288"
---
# <a name="idiadatasourceloadandvalidatedatafrompdb"></a>IDiaDataSource::loadAndValidateDataFromPdb
Apre e verifica che il file del database di programma (con estensione pdb) corrisponda alle informazioni di firma fornite e prepara il file con estensione PDB come origine dati di debug.

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

in Percorso del file con estensione pdb.

`pcsig70`

in Firma GUID da verificare rispetto alla firma del file con estensione pdb. Solo i file con estensione PDB in [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e versioni successive presentano firme GUID.

`sig`

in Firma a 32 bit da verificare rispetto alla firma del file con estensione pdb.

`age`

in Valore Age da verificare. L'età non corrisponde necessariamente a un valore di ora noto, viene utilizzata per determinare se un file con estensione PDB non è sincronizzato con un file con estensione exe corrispondente.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. La tabella seguente illustra i possibili valori restituiti per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_PDB_NOT_FOUND|Non è stato possibile aprire il file o il formato del file non è valido.|
|E_PDB_FORMAT|Tentativo di accedere a un file con un formato obsoleto.|
|E_PDB_INVALID_SIG|La firma non corrisponde.|
|E_PDB_INVALID_AGE|Age non corrisponde a.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|L'origine dati è già stata preparata.|

## <a name="remarks"></a>Commenti
Un file con estensione PDB contiene sia la firma che i valori di età. Questi valori vengono replicati nel file con estensione exe o dll che corrisponde al file con estensione pdb. Prima di preparare l'origine dati, questo metodo verifica che la firma del file con estensione PDB denominata e l'età corrispondano ai valori specificati.

Per caricare un file con estensione pdb senza convalida, usare il metodo [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Per ottenere l'accesso al processo di caricamento dei dati (tramite un meccanismo di callback), usare il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

Per caricare un file con estensione PDB direttamente dalla memoria, usare il metodo [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

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
