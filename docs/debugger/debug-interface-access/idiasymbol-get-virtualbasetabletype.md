---
title: IDiaSymbol::get_virtualBaseTableType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_virtualBaseTableType method
ms.assetid: e0581c4f-0343-49b5-9754-a48477460e9f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edbd1d8ae66e58611ab538cf0bfe695cb22b3412
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/12/2019
ms.locfileid: "64793022"
---
# <a name="idiasymbolgetvirtualbasetabletype"></a>IDiaSymbol::get_virtualBaseTableType
Recupera il tipo di puntatore una tabella di base virtuale.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_virtualBaseTableType(
   IDiaSymbol *pRetVal
};
```

#### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|`pRetVal`|[out] Restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che specifica il tipo di tabella di base.|

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.

> [!NOTE]
> Valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.

## <a name="remarks"></a>Note
 Un puntatore alla tabella di base virtuale (`vbtptr`) è un puntatore nascosto in un [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] vtable che gestisce l'ereditarietà da classi base virtuali. Oggetto `vbtptr` possono avere dimensioni diverse a seconda delle classi ereditate.

 Questo metodo restituisce un [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) oggetto che può essere utilizzato per determinare le dimensioni della finestra di vbtptr.

## <a name="requirements"></a>Requisiti

|Requisito|DESCRIZIONE|
|-----------------|-----------------|
|Intestazione:|DIA2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedere anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)