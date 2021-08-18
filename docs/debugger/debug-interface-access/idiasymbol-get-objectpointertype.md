---
description: Recupera il tipo del puntatore a oggetto per un metodo della classe.
title: IDiaSymbol::get_objectPointerType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_objectPointerType method
ms.assetid: bce193b9-67b0-4c35-96e5-6a664937322e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0695ba8dbe0c5846f8c7495600e71d89fb0aa5c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113403"
---
# <a name="idiasymbolget_objectpointertype"></a>IDiaSymbol::get_objectPointerType
Recupera il tipo del puntatore a oggetto per un metodo della classe.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_objectPointerType ( 
   IDiaSymbol** pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce un [oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il puntatore a oggetto per un metodo di classe.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Questa proprietà si applica solo ai simboli con tipo [di enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) di `SymTagFunctionType` .

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
- [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)
