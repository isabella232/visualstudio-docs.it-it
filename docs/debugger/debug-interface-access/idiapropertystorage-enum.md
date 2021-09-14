---
description: Ottiene un enumeratore per le proprietà all'interno di questo set.
title: IDiaPropertyStorage::Enum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7458a0cd509567b52ab14b4489f5fded2f187882
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126629556"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Ottiene un enumeratore per le proprietà all'interno di questo set.

## <a name="syntax"></a>Sintassi

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>Parametri
 `ppenum`

[out] Restituisce un oggetto (nello spazio dei nomi `IEnumSTATPROPSTG` Microsoft.VisualStudio.OLE.Interop) che rappresenta un'enumerazione di proprietà.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, `S_OK` restituisce ; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
