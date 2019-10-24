---
title: IDiaSymbol::get_virtualBaseDispIndex | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseDispIndex method
ms.assetid: 5561a3cb-2c82-41cf-9217-3ee2b1e1d1d1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b42c735c110208d563f908baef90a3bd0699fbe8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738882"
---
# <a name="idiasymbolget_virtualbasedispindex"></a>IDiaSymbol::get_virtualBaseDispIndex
Recupera l'indice del simbolo nella tabella di spostamento della base virtuale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_virtualBaseDispIndex (
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'indice nella tabella di spostamento della base virtuale.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)