---
description: Legge il numero specificato di byte a partire dall'indirizzo RVA (Relative Virtual Address) specificato dal file eseguibile.
title: IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d98eb6f6a50b7dace957b7012775746e90564bbd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122161613"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Legge il numero specificato di byte a partire dall'indirizzo RVA (Relative Virtual Address) specificato dal file eseguibile.

## <a name="syntax"></a>Sintassi

```C++
HRESULT ReadExecutableAtRVA ( 
   DWORD  relativeVirtualAddress,
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>Parametri
 `relativeVirtualAddress`

[in] RVA nel file eseguibile per iniziare la lettura.

 `cbData`

[in] Numero di byte da leggere.

 `pcbData`

[out] Restituisce il numero di byte letti.

 `data[]`

[in, out] Matrice compilata con i byte letti dal file.

## <a name="remarks"></a>Commenti
 Questo metodo viene chiamato dal codice di supporto DIA per caricare byte di dati da un eseguibile usando un indirizzo virtuale relativo. Questo metodo viene chiamato a supporto del [metodo IDiaDataSource::loadDataForExe.](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

## <a name="see-also"></a>Vedi anche
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
