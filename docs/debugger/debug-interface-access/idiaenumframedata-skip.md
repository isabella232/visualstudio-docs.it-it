---
description: Ignora un numero specificato di elementi dati del frame in una sequenza di enumerazione.
title: IDiaEnumFrameData::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Skip method
ms.assetid: 67140b4c-7125-4895-932d-42412326da29
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 50c7069e47533e65273ffd988eed676a59376a1e
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630318"
---
# <a name="idiaenumframedataskip"></a>IDiaEnumFrameData::Skip
Ignora un numero specificato di elementi dati del frame in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di elementi di dati del frame nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce ; in caso contrario, restituisce se non sono `S_OK` presenti altri record da `S_FALSE` ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
