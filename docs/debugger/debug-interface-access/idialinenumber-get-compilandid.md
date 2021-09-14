---
description: Recupera un identificatore univoco per il compilando che ha contribuito a questa riga.
title: IDiaLineNumber::get_compilandId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaLineNumber::get_compilandId method
ms.assetid: 2cd6f551-8091-47c7-803f-3f79a766a211
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f9ad433c8341369cc8b6ca04a0d9b272cfbc8b22
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629693"
---
# <a name="idialinenumberget_compilandid"></a>IDiaLineNumber::get_compilandId
Recupera un identificatore univoco per il compilando che ha contribuito a questa riga.

## <a name="syntax"></a>Sintassi

```C++
HRESULT get_compilandId ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>Parametri
 `pRetVal`

[out] Restituisce `DWORD` che contiene l'identificatore univoco per il compilando che ha contribuito a questa riga.

## <a name="return-value"></a>Valore restituito
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se questa proprietà non è supportata. In caso contrario, verrà restituito un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
