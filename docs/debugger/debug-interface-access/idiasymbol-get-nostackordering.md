---
description: Questa funzione recupera un flag che indica se non è possibile eseguire l'ordinamento dello stack come parte del controllo del buffer dello stack (opzione del compilatore[/GS (controllo di sicurezza](/cpp/build/reference/gs-buffer-security-check) del buffer).
title: IDiaSymbol::get_noStackOrdering | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_noStackOrdering method
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8cd2015951612495e936b742fbb7877b1474bbcffa466b52795226487020bb55
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420598"
---
# <a name="idiasymbolget_nostackordering"></a>IDiaSymbol::get_noStackOrdering
Questa funzione recupera un flag che indica se non è possibile eseguire l'ordinamento dello stack come parte del controllo del buffer dello stack (opzione del compilatore[/GS (controllo di sicurezza](/cpp/build/reference/gs-buffer-security-check) del buffer).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_noStackOrdering(
   BOOL *pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `TRUE` se non è possibile eseguire l'ordinamento dello stack come parte del controllo del buffer dello stack; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [/GS (Controllo di sicurezza del buffer)](/cpp/build/reference/gs-buffer-security-check)
