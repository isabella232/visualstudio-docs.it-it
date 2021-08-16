---
description: Recupera la varietà di un tipo definito dall'utente (UDT).
title: IDiaSymbol::get_udtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_udtKind method
ms.assetid: 4002f887-aea6-4475-b302-67c57079fe0a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e8e734163d5bbfcb3e43d477b8b8b260a76ebbeef996963f2896f6f8fcfd5791
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121362889"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
Recupera la varietà di un tipo definito dall'utente (UDT).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un valore [dall'enumerazione UdtKind Che](../../debugger/debug-interface-access/udtkind.md) specifica il tipo di un tipo definito dall'utente: struttura, classe o unione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o il `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione UdtKind](../../debugger/debug-interface-access/udtkind.md)
