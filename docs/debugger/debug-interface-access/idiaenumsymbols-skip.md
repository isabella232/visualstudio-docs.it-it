---
description: Ignora un numero specificato di simboli in una sequenza di enumerazione.
title: IDiaEnumSymbols::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSymbols::Skip method
ms.assetid: e601fbc9-b10b-41c7-8180-959e57efabe8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 34a278abc20ef939cd038813b4e2ed07b20b1bcf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630000"
---
# <a name="idiaenumsymbolsskip"></a>IDiaEnumSymbols::Skip
Ignora un numero specificato di simboli in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di simboli nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce ; in caso contrario, restituisce se non sono `S_OK` presenti altri simboli da `S_FALSE` ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
