---
description: Specifica se il puntatore punta a un membro dati con ereditarietà virtuale.
title: IDiaSymbol::get_isVirtualInheritance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 72906b92-dd4a-42e3-9b24-b77628fa48c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3119b10a23d9ba6b624c40bbb44a0a77d07725fb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102162047"
---
# <a name="idiasymbolget_isvirtualinheritance"></a>IDiaSymbol::get_isVirtualInheritance
Specifica se il `this` puntatore punta a un membro dati con ereditarietà virtuale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isVirtualInheritance(
   BOOL* pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Puntatore a un oggetto `BOOL` che specifica se il `this` puntatore punta a un membro dati con ereditarietà virtuale.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
