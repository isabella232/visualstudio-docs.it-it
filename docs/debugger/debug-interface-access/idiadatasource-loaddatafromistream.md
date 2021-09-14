---
description: Prepara i dati di debug archiviati in un file di database di programma (con estensione pdb) a cui si accede tramite un flusso di dati in memoria.
title: IDiaDataSource::loadDataFromIStream | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromIStream method
ms.assetid: 8fe33eea-1457-4b8c-ae19-f1ede5578483
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 005c423df13f2d1b906a229665c79d6ee52627a7
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630492"
---
# <a name="idiadatasourceloaddatafromistream"></a>IDiaDataSource::loadDataFromIStream
Prepara i dati di debug archiviati in un file di database di programma (con estensione pdb) a cui si accede tramite un flusso di dati in memoria.

## <a name="syntax"></a>Sintassi

```C++
HRESULT loadDataFromIStream ( 
   IStream* pIStream
);
```

#### <a name="parameters"></a>Parametri
 pIStream

[in] Oggetto <xref:IStream> che rappresenta il flusso di dati da utilizzare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati i possibili valori restituiti per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_PDB_FORMAT|Tentativo di accedere a un file con un formato obsoleto.|
|E_INVALIDARG|Parametro non valido.|
|E_UNEXPECTED|L'origine dati è già stata preparata.|

## <a name="remarks"></a>Commenti
 Questo metodo consente di ottenere i dati di debug di un eseguibile dalla memoria tramite un <xref:IStream> oggetto .

 Per caricare un file con estensione pdb senza convalida, usare il [metodo IDiaDataSource::loadDataFromPdb.](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)

 Per convalidare il file con estensione pdb in base a criteri specifici, usare il metodo [IDiaDataSource::loadAndValidateDataFromPdb.](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)

 Per accedere al processo di caricamento dei dati (tramite un meccanismo di callback), usare il metodo [IDiaDataSource::loadDataForExe.](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

## <a name="see-also"></a>Vedi anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
