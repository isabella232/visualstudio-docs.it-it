---
description: Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore di dati del frame corrente.
title: IDiaEnumFrameData::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Clone Method
ms.assetid: 28a17300-1626-422f-a17a-3a4d3872c37c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1f22ad93668c617f687824c8825955fc63f537d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122113744"
---
# <a name="idiaenumframedataclone"></a>IDiaEnumFrameData::Clone
Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Clone( 
   IDiaEnumFrameData** ppenum
);
```

#### <a name="parameters"></a>Parametri
 ppenum

[out] Restituisce un [oggetto IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md) che contiene un duplicato dell'enumeratore. I dati del frame non vengono duplicati, ma solo l'enumeratore.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="see-also"></a>Vedi anche
- [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)
