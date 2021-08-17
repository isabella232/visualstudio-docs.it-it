---
description: Recupera l'identificatore univoco del simbolo.
title: IDiaSymbol::get_symIndexId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_symIndexId method
ms.assetid: dd1fb3ba-31bf-497d-a6bf-79f1206e6642
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dff29f5b590cdbd1684cac4a06f130b96255f879
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074428"
---
# <a name="idiasymbolget_symindexid"></a>IDiaSymbol::get_symIndexId
Recupera l'identificatore univoco del simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_symIndexId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'ID simbolo del simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o il `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 L'identificatore è un valore univoco creato dal DIA SDK per contrassegnare tutti i simboli come univoci.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
