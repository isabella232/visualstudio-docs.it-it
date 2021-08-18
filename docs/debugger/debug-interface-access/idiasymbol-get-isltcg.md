---
description: Recupera un flag che specifica se il compilatore è stato collegato all'opzione del linker /LTCG (Generazione di codice in fase di collegamento)(/cpp/build/reference/ltcg-link-time-code-generation), che consente l'ottimizzazione dell'intero programma.
title: IDiaSymbol::get_isLTCG | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_isLTCG method
ms.assetid: 5f7f05b8-6b71-4958-9e1e-e4924ef9c59b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0c7b73b33739ade2b83b5e9e2ae760845de1d7e6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122121505"
---
# <a name="idiasymbolget_isltcg"></a>IDiaSymbol::get_isLTCG
Recupera un flag che specifica [](../../debugger/debug-interface-access/compiland.md) se il compilatore è stato collegato all'opzione del linker [/LTCG (Generazione](/cpp/build/reference/ltcg-link-time-code-generation)di codice in fase di collegamento), che consente l'ottimizzazione dell'intero programma. Questa opzione si applica solo al codice gestito.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_iSLTCG(
   BOOL *pFlag
);
```

#### <a name="parameters"></a>Parametri
 pFlag

[out] Restituisce `TRUE` se `compiland` l'oggetto è stato collegato all'opzione del linker /LTCG; in caso contrario, restituisce `FALSE` .

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce o un `S_FALSE` codice di errore.

> [!NOTE]
> Il valore restituito `S_FALSE` indica che la proprietà non è disponibile per il simbolo.

## <a name="requirements"></a>Requisiti

|Requisito|Descrizione|
|-----------------|-----------------|
|Intestazione:|dia2.h|
|Version:|DIA SDK v8.0|

## <a name="see-also"></a>Vedi anche
- [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
