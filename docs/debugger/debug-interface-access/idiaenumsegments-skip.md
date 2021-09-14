---
description: Ignora un numero specificato di segmenti in una sequenza di enumerazione.
title: IDiaEnumSegments::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::Skip method
ms.assetid: ec67039f-da8c-4e70-8db7-957d7d5281e8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 22479a35faf797969eb7936c6d630e91f7f6352b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630119"
---
# <a name="idiaenumsegmentsskip"></a>IDiaEnumSegments::Skip
Ignora un numero specificato di segmenti in una sequenza di enumerazione.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Skip ( 
   ULONG celt
);
```

#### <a name="parameters"></a>Parametri
 celt

[in] Numero di segmenti nella sequenza di enumerazione da ignorare.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce ; in caso contrario, restituisce se non sono presenti `S_OK` `S_FALSE` altri segmenti da ignorare.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)
