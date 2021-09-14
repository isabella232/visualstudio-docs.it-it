---
description: Recupera il tipo di un puntatore di tabella di base virtuale.
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 6a254663eab843e35e733f1c380f93c2a33ebc74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635364"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Recupera il tipo di un puntatore di tabella di base virtuale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|`pRetVal`|[out] Restituisce un [oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che specifica il tipo di tabella di base.|

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Un valore restituito `S_FALSE` di indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Un puntatore di tabella di base virtuale ( `vbtptr` ) è un puntatore nascosto in una tabella vtable che gestisce [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] l'ereditarietà dalle classi di base virtuali. Un `vbtptr` può avere dimensioni diverse a seconda delle classi ereditate.

 Questo metodo restituisce un [oggetto IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che può essere usato per determinare le dimensioni di vbtptr.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
