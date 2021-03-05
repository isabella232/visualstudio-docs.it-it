---
description: Recupera il valore della firma del simbolo.
title: IDiaSymbol::get_signature | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_signature method
ms.assetid: 0efefa39-49a5-4282-9d41-e50832d927e0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eee113e7998d983b601b93a90ad3ed6a9a97fa5d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161816"
---
# <a name="idiasymbolget_signature"></a>IDiaSymbol::get_signature
Recupera il valore della firma del simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_signature ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce il valore della firma del simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
