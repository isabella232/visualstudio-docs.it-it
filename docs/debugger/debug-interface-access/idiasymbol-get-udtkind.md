---
description: Recupera l'ampia gamma di un tipo definito dall'utente (UDT).
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
ms.openlocfilehash: 9083d89c7e9e981e200182f493d6745466883d91
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074388"
---
# <a name="idiasymbolget_udtkind"></a>IDiaSymbol::get_udtKind
Recupera l'ampia gamma di un tipo definito dall'utente (UDT).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_udtKind ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un valore [dall'enumerazione UdtKind Enumeration](../../debugger/debug-interface-access/udtkind.md) che specifica il tipo di un tipo definito dall'utente: struttura, classe o unione.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o codice `S_FALSE` di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione UdtKind](../../debugger/debug-interface-access/udtkind.md)
