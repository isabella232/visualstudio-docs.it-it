---
description: Ottiene un enumeratore per le proprietà all'interno di questo set.
title: 'IDiaPropertyStorage:: enum | Microsoft Docs'
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
ms.workload:
- multiple
ms.openlocfilehash: d113107621c3254b86356202e94eac6e3e3a8c66
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102148178"
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

out Restituisce un `IEnumSTATPROPSTG` oggetto (nello spazio dei nomi Microsoft. VisualStudio. OLE. Interop) che rappresenta un'enumerazione delle proprietà.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.

## <a name="see-also"></a>Vedi anche
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
