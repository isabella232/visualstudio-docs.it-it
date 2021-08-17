---
description: Apre una sessione per l'esecuzione di query sui simboli.
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1ea37d29745ede74e5f882b416c5a3f004587396
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097938"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
Apre una sessione per l'esecuzione di query sui simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT openSession ( 
   IDiaSession** ppSession
);
```

#### <a name="parameters"></a>Parametri
ppSession

[out] Restituisce un [oggetto IDiaSession](../../debugger/debug-interface-access/idiasession.md) che rappresenta la sessione aperta.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Nella tabella seguente vengono illustrati i valori restituiti possibili per questo metodo.

|Valore|Descrizione|
|-----------|-----------------|
|E_UNEXPECTED|[L'oggetto IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) non è stato inizializzato in precedenza con un'origine di simboli.|
|E_INVALIDARG|Parametro `ppSession` non valido.|
|E_OUTOFMEMORY|Memoria insufficiente per aprire la sessione.|

## <a name="remarks"></a>Commenti
Questo metodo apre un [oggetto IDiaSession](../../debugger/debug-interface-access/idiasession.md) per un'origine dati.

`IDiaSession` Gli oggetti implementano query nell'origine dati. Una sessione gestisce uno spazio indirizzi per ogni set di simboli di debug. Se il file .exe o .dll descritto dai simboli dell'origine dati è attivo in più intervalli di indirizzi (ad esempio, perché è caricato da più processi), è necessario usare una sessione per ogni intervallo di indirizzi.

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
- [Overview](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
