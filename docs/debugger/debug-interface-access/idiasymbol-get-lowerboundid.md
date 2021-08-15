---
description: Recupera l'identificatore del simbolo del limite inferiore di una dimensione di matrice FORTRAN.
title: IDiaSymbol::get_lowerBoundId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_lowerBoundId method
ms.assetid: 12ce98e9-a225-4947-88c9-5fda39dd67e4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 86a621414c020dcb34845d0b94b802e14532d4c4a5b72252e753ed687f4fba86
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121311623"
---
# <a name="idiasymbolget_lowerboundid"></a>IDiaSymbol::get_lowerBoundId
Recupera l'identificatore del simbolo del limite inferiore di una dimensione di matrice FORTRAN.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_lowerBoundId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce l'ID simbolo del simbolo che rappresenta il limite inferiore di una dimensione di matrice ARRAYRAN.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 L'identificatore è un valore univoco creato dal DIA SDK per contrassegnare tutti i simboli come univoci.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
