---
title: Idiareadexeatrvacallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cf423ddc91926fb04adac849783b7c26b4c4f720
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828483"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Legge il numero specificato di byte a partire specificato indirizzo virtuale relativo (RVA) dal file eseguibile.

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

[in] il RVA del file eseguibile per iniziare la lettura.

 `cbData`

[in] Numero di byte da leggere.

 `pcbData`

[out] Restituisce il numero di byte letti.

 `data[]`

[in, out] Matrice che viene compilata con byte letti dal file.

## <a name="remarks"></a>Note
 Questo metodo viene chiamato dal codice di supporto di DIA per caricare i byte di dati da un eseguibile usando un indirizzo virtuale relativo. Questo metodo viene chiamato supportare le [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) (metodo).

## <a name="see-also"></a>Vedere anche
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)