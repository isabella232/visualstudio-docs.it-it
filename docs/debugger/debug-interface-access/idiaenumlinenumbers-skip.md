---
description: Ignora un numero specificato di numeri di riga in una sequenza di enumerazione.
title: IDiaEnumLineNumbers::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Skip method
ms.assetid: d182c269-8c76-4d8b-8275-c6807c5ae4e1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: d6785472988543d1d439e08801170f94f4744d0d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074927"
---
# <a name="idiaenumlinenumbersskip"></a>IDiaEnumLineNumbers::Skip
Ignora un numero specificato di numeri di riga in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di numeri di riga nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce ; in caso contrario, restituisce se non sono `S_OK` presenti altri numeri di riga da `S_FALSE` ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
