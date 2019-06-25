---
title: Restrictsymbolserveraccess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::RestrictSymbolServerAccess method
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0de567f0417714e1246e11ba074c9b0134e92ce8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839771"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Determina se l'accesso è consentito in un server di simboli per risolvere i simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Diverso da qualsiasi codice restituito `S_OK` impedisce l'uso di un server di simboli per risolvere i simboli.

## <a name="see-also"></a>Vedere anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)