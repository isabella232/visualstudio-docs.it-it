---
description: Indica se il simbolo corrisponde a un simbolo di funzione di primo livello per uno shader compilato per un acceleratore che corrisponde a una parallel_for_each chiamata.
title: IDiaSymbol::get_isAcceleratorStubFunction | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: cc4ea375-76f6-4ba8-baed-c5fa82108137
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4c5d32ec66b596510696bf81aa3bfc506047b54e64519304ca570a9ea88d39ca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121240504"
---
# <a name="idiasymbolget_isacceleratorstubfunction"></a>IDiaSymbol::get_isAcceleratorStubFunction
Indica se il simbolo corrisponde a un simbolo di funzione di primo livello per uno shader compilato per un acceleratore che corrisponde a una `parallel_for_each` chiamata.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_isAcceleratorStubFunction(
   BOOL* pFlag);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Puntatore a un oggetto che indica se il simbolo corrisponde a un simbolo di funzione di primo livello per uno shader compilato per un `BOOL` acceleratore che corrisponde a una `parallel_for_each` chiamata.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
