---
description: Recupera il tipo di un puntatore a una tabella di base virtuale.
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
ms.workload:
- multiple
ms.openlocfilehash: f67affafd1984f811432a0b69fdcdfec0521e377
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102155516"
---
# <a name="idiasymbolget_virtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Recupera il tipo di un puntatore a una tabella di base virtuale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|`pRetVal`|out Restituisce un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che specifica il tipo di tabella di base.|

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Un valore restituito di `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Commenti
 Un puntatore a tabella di base virtuale ( `vbtptr` ) è un puntatore nascosto in un oggetto [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable che gestisce l'ereditarietà dalle classi base virtuali. Un oggetto `vbtptr` può avere dimensioni diverse a seconda delle classi ereditate.

 Questo metodo restituisce un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che può essere utilizzato per determinare le dimensioni di vbtptr.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2. h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
