---
description: Ignora un numero specificato di file di origine in una sequenza di enumerazione.
title: IDiaEnumSourceFiles::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSourceFiles::Skip method
ms.assetid: 4821e6dd-d33f-403d-857d-e3ae81e4a9e3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 884f47cfaaf5db679b1d49ce925fe5267c8f1513
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630077"
---
# <a name="idiaenumsourcefilesskip"></a>IDiaEnumSourceFiles::Skip
Ignora un numero specificato di file di origine in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di file di origine nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, `S_OK` restituisce ; in caso contrario, restituisce se non sono presenti altri file di origine da `S_FALSE` ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)
