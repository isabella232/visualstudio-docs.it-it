---
title: IDiaSymbol::get_virtualTableShapeId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualTableShapeId method
ms.assetid: cbee9944-817a-4805-9c08-fac8e0da58b7
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: af945892bfc99e86e30457084481c8675804ffad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99862430"
---
# <a name="idiasymbolget_virtualtableshapeid"></a>IDiaSymbol::get_virtualTableShapeId
Recupera l'identificatore del simbolo di forma della tabella virtuale del simbolo.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_virtualTableShapeId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

out Restituisce l'ID simbolo di forma della tabella virtuale del simbolo.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 L'identificatore è un valore univoco creato dal DIA SDK per contrassegnare tutti i simboli come univoci.

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)