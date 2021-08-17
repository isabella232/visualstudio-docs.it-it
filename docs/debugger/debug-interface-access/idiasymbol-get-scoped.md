---
description: Recupera un flag che specifica se il tipo di dati definito dall'utente viene visualizzato in un ambito lessicale non globale.
title: IDiaSymbol::get_scoped | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_scoped method
ms.assetid: 588163f7-958e-4072-bf66-db5c5f07d3cb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 80392102edaa243e7a9a42fb5dbca4dca1c171de71cce73db91dcf63e6ec4c0f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404722"
---
# <a name="idiasymbolget_scoped"></a>IDiaSymbol::get_scoped
Recupera un flag che specifica se il tipo di dati definito dall'utente viene visualizzato in un ambito lessicale non globale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_scoped ( 
   BOOL* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce se il tipo di dati definito dall'utente viene visualizzato in un ambito `TRUE` lessicale non globale; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
