---
description: Recupera l'identificatore del tipo di indice della matrice del simbolo.
title: IDiaSymbol::get_arrayIndexTypeId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_arrayIndexTypeId method
ms.assetid: 124f86e2-6f66-4541-87c3-799f435b731e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e955b1bda01d81a97ad196ca767a5232a9bc37c324a47d8a81470448acc0a2b1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264202"
---
# <a name="idiasymbolget_arrayindextypeid"></a>IDiaSymbol::get_arrayIndexTypeId
Recupera l'identificatore del tipo di indice della matrice del simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_arrayIndexTypeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'ID del tipo di indice della matrice del simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 L'identificatore è un valore univoco creato dal DIA SDK per contrassegnare tutti i simboli come univoci.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v7.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
