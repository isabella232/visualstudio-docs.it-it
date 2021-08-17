---
description: Recupera un flag che specifica se la compilazione o la funzione è stata compilata con i controlli di sicurezza del sovraccarico del buffer (ad esempio, l'opzione del compilatore /GS (controllo di sicurezza del buffer)).
title: IDiaSymbol::get_hasSecurityChecks | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasSecurityChecks method
ms.assetid: 4bb51f62-8645-41a4-bc44-1451010623fd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e417293cec0cf25a1a288633e06b6eb05926ac71b7d39ed7d02e41123f0b5ad6
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121436528"
---
# <a name="idiasymbolget_hassecuritychecks"></a>IDiaSymbol::get_hasSecurityChecks
Recupera un flag che specifica se il compilatore o la funzione è stata compilata con i controlli di sicurezza del sovraccarico del buffer, ad esempio l'opzione del compilatore [/GS (controllo](/cpp/build/reference/gs-buffer-security-check) di sicurezza del buffer).

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_hasSecurityChecks(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 `pFlag`

[out] Restituisce `TRUE` se la funzione dispone di controlli di sicurezza; in caso contrario, restituisce `FALSE` .

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
