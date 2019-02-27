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
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56618627"
---
# <a name="idialoadcallbackrestrictsymbolserveraccess"></a>IDiaLoadCallback::RestrictSymbolServerAccess
Determina se l'accesso è consentito in un server di simboli per risolvere i simboli.

## <a name="syntax"></a>Sintassi

```C++
HRESULT RestrictSymbolServerAccess();
```

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 Diverso da qualsiasi codice restituito `S_OK` impedisce l'uso di un server di simboli per risolvere i simboli.

## <a name="see-also"></a>Vedere anche
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)