---
title: 'IDiaReadExeAtRVACallback:: ReadExecutableAtRVA | Microsoft Docs'
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
ms.openlocfilehash: ca1b1ec2bea56ad167951ad8b60cf849bd22e315
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742792"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
Legge il numero specificato di byte a partire dall'indirizzo RVA (relative Virtual Address) specificato dal file eseguibile.

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

in RVA nel file eseguibile da cui iniziare la lettura.

 `cbData`

in Numero di byte da leggere.

 `pcbData`

out Restituisce il numero di byte letti.

 `data[]`

[in, out] Matrice compilata con byte letti dal file.

## <a name="remarks"></a>Note
 Questo metodo viene chiamato dal codice di supporto DIA per caricare i byte di dati da un file eseguibile usando un indirizzo virtuale relativo. Questo metodo viene chiamato per supportare il metodo [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .

## <a name="see-also"></a>Vedere anche
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)