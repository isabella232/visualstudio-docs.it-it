---
description: Verifica se due simboli sono equivalenti.
title: IDiaSession::symsAreEquiv | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::symsAreEquiv method
ms.assetid: 9941d520-e203-46c0-83c3-b3a967f4fc59
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c5f887b13195bdde133c4bca845291b1255b99ea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102156986"
---
# <a name="idiasessionsymsareequiv"></a>IDiaSession::symsAreEquiv
Verifica se due simboli sono equivalenti.

## <a name="syntax"></a>Sintassi

```C++
HRESULT symsAreEquiv ( 
   IDiaSymbol* symbolA,
   IDiaSymbol* symbolB
);
```

#### <a name="parameters"></a>Parametri
 `symbolA`

in Primo oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) usato nel confronto.

 `symbolB`

in Secondo `IDiaSymbol` oggetto utilizzato nel confronto.

## <a name="return-value"></a>Valore restituito
 Se i simboli sono equivalenti, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` , i simboli non sono equivalenti. In caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
