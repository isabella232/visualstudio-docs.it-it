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
ms.openlocfilehash: 7f84b3577b407fb8e60322b2de078815e6d3af81
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128743"
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
