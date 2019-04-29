---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 393abb3b1e1872a416865cbfee5c142bef98ce78
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62838454"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Apre una sessione per eseguire query sui simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parametri
ppSession

[out] Restituisce un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) oggetto che rappresenta la sessione aperta.

## <a name="return-value"></a>Valore restituito
Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore. Nella tabella seguente mostra i valori restituiti possibili per questo metodo.

|Value|Descrizione|
|-----------|-----------------|
|E_UNEXPECTED|Il [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) oggetto non è già stato inizializzato con un'origine dei simboli.|
|E_INVALIDARG|Parametro `ppSession` non valido.|
|E_OUTOFMEMORY|Memoria insufficiente per aprire la sessione.|

## <a name="remarks"></a>Note
Questo metodo consente di aprire una [IDiaSession](../../debugger/debug-interface-access/idiasession.md) oggetti per un'origine dati.

`IDiaSession` le query che gli oggetti nell'origine dati. Una sessione gestisce uno spazio di indirizzi per ogni set di simboli di debug. Se il file DLL o .exe descritto dai simboli di origine dati è attivo nell'indirizzo più intervalli (ad esempio, poiché più processi averlo caricato), quindi deve essere usata una sola sessione per ogni intervallo di indirizzi.

## <a name="example"></a>Esempio

```C++
IDiaSession* pSession;
HRESULT hr = pSource->openSession( &pSession );
if (FAILED(hr))
{
   // report error
}
```

## <a name="see-also"></a>Vedere anche
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
