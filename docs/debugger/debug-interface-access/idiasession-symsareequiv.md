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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 2483a201da07fe45247e3ad0c389d969e2657772
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629064"
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

[in] Primo [oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) usato nel confronto.

 `symbolB`

[in] Secondo `IDiaSymbol` oggetto utilizzato nel confronto.

## <a name="return-value"></a>Valore restituito
 Se i simboli sono equivalenti, restituisce `S_OK` ; in caso contrario, restituisce , i `S_FALSE` simboli non sono equivalenti. In caso contrario, restituire un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
