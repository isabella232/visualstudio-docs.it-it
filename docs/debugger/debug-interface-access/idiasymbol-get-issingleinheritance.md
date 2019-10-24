---
title: IDiaSymbol::get_isSingleInheritance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 46cde656-059b-4c20-9476-3ca68ccc9912
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 96a8ce072fc57dc236dd2025b8ea3c9c5a4b9b79
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72740062"
---
# <a name="idiasymbolget_issingleinheritance"></a>IDiaSymbol::get_isSingleInheritance
Specifica se il puntatore `this` punta a un membro dati con ereditarietà singola.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isSingleInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un `BOOL` che specifica se il puntatore `this` punta a un membro dati con ereditarietà singola.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)