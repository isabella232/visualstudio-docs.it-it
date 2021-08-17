---
description: Questa funzione recupera un puntatore a un simbolo che rappresenta l'elemento padre/contenitore di questo simbolo.
title: IDiaSymbol::get_container | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_container method
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 48a146ab67b0677bcfe7a8c55fc9feee0fa52bf2af043b67fa3388653e51c080
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420758"
---
# <a name="idiasymbolget_container"></a>IDiaSymbol::get_container
Questa funzione recupera un puntatore a un simbolo che rappresenta l'elemento padre/contenitore di questo simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_container(
   IDiaSymbol **pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un puntatore a `IDiaSymbol` un oggetto contenente informazioni sul contenitore di questo simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce S_FALSE o un codice di errore.

> [!NOTE]
> Un valore restituito S_FALSE indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
