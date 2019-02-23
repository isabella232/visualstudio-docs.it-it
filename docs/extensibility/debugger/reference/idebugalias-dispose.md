---
title: IDebugAlias::Dispose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d35b5819aa0354581721f02a931aa7bdf679b70d
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714959"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Contrassegna l'alias per la rimozione.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

#### <a name="parameters"></a>Parametri
 Nessuno.

## <a name="return-value"></a>Valore restituito
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Note
 Una volta che viene chiamato questo metodo, l'alias non è più disponibile.

## <a name="see-also"></a>Vedere anche
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)