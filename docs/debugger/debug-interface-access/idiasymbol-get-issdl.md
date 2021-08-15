---
description: Specifica se il modulo viene compilato con l'opzione /SDL.
title: IDiaSymbol::get_isSdl | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: 6aa0e116-da75-4643-a4d7-d8e142231e21
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 28cb649e359b2164eb044f34df37d7997926c05a4ff00ea94b19637defe786e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121311758"
---
# <a name="idiasymbolget_issdl"></a>IDiaSymbol::get_isSdl
Specifica se il modulo viene compilato con l'opzione /SDL.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isSdl(
   BOOL *pRetVal);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Puntatore a un `BOOL` oggetto che specifica se il modulo viene compilato con l'opzione /SDL.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
